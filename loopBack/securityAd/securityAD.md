# 安全建议
StrongLoop对安全问题非常认真,我们尽一切努力来确保StrongLoop支持安全模块,并修复任何漏洞或尽快提供解决方案.

这些已知的安全问题是很重要的建议:
- Security advisory 01-09-2015
- Security advisory 06-04-2015

注意:一些建议可能需要你自己来动手,比如升级strongLoop安装包.

## 怎样反馈一个安全问题
如果你认为你发现了一个新的关于strongLoop的安全问题,请不要直接在github上反馈,而是,你可以发送一个详细的关于问题的描述的邮箱到callback@strongloop.com.

# Security advisory 01-09-2015

## LoopBack 连接器SQL注入漏洞
如果你安装的LoopBack连接器PostgreSQL, Microsoft SQL Server, Oracle, or MySQL在2015年1月9日之前,你需要更新受影响的安装包.
- 日期: 20151月9日
- 危险等级: 高度危险
- 漏洞: SQL注入

## 描述
loopback允许你用数字类型定义模型的属性,一个危险是在模型关系之间可以使用SQL注入.

## 报告者
David Kirchner

## 影响版本
- loopback-connector-postgresql prior to 1.3.0
- loopback-connector-mssql prior to 1.3.0
- loopback-connector-oracle prior to 1.5.0
- loopback-connector-mysql prior to 1.5.0 (The SQL injection is not possible but invalid numbers are treated as NaN).

## 解决方案
请升级你的项目依赖到最新版本,通过使用npm update:
- loopback-connector-postgresql@1.3.0
- loopback-connector-mssql@1.3.0
- loopback-connector-oracle@1.5.0
- loopback-connector-mysql@1.5.0

注意,在运行npm update时候,确保你的package.json文件中写的正确的依赖版本,比如:
"loopback-connector-oracle": "^1.5.0"

## 怎么反馈安全漏洞
请发送邮件到callback@strongloop.com

# Security advisory 06-04-2015
## LoopBack和HTTP参数污染
HTTP参数污染是一个已知的express程序的漏洞.LoopBack使用下面的模块来解决,确保你的应用使用了这些:
- loopback版本大于或等于2.17.1
- strong-remoting版本大于或等于2.16.3
- loopback-datasource-juggler版本大于或等于2.26.1

如果你使用的是原生express,可以增加[hpp](https://www.npmjs.com/package/hpp)中间件来防止漏洞.

## 什么是HTTP参数污染?
让我们快速来个例子,考虑下面的HTTP请求:
```shell
GET /search?firstname=John&firstname=Jane
```
现在,req.query.firstname的值是多少?
正确答案是req.query.fristname被设置成一个2个值的数组,['john','jane'],因为express对待多次重复参数请求就会使用数组来填充.

虽然这是一个有用的功能,许多模块依赖这样的特性(包括loopback).但是这样允许攻击者有意污染请求参数,这样路由没有办法处理一个数组,或者导致拒绝服务.

举个例子,如果上面的例子使用一个post来更新一个人名的话,请求就是:
```json
{
 "firstname": ["John", "Jane"],
 "lastname": "Smith"
}
```
如果处理这个方法的程序期望firstname是一个字符串的话,而用了字符串的原型方法,就可能引起程序崩溃.
```shell
TypeError: Object John,Jane has no method 'trim'
(...)
```
 ## 对于loopback程序的影响
 幸运的是,loopback有一个在express上的抽象层strong-remoting模块.这个模块能觉察出请求的类型,从而避免HTTP请求污染.

 不幸的是处理参数类型转换的代码中没有正确实现对这个特殊的边界情况,例如,下面的代码片段允许攻击者崩溃你的服务器进程:
 ```javascript
 Car.greet = function(whom, cb) {
 process.nextTick(function() {
   cb(null, 'Hello ' + whom.toUpperCase());
 });
};
Car.remoteMethod('greet', {
 isStatic: true,
 accepts: { arg: 'whom', type: 'string', required: true },
 returns: { arg: 'message', type: 'string' },
 http: { verb: 'GET' }
});
 ```
 比如请求GET /cars/greet?whom=jane&whom=john就会在服务器端出现异常.
 ```javascript
cb(null, 'Hello ' + whom.toUpperCase());
                            ^
TypeError: undefined is not a function
 ```
 我们目前已经解决了这样的问题.更新你的strongloop.

 ## 除了HTTP请求
 这里还有一处Loopback处理请求参数:模型属性.当设置模型属性的时候,loopback会确保类型一致.

 比如,一个字符串的'123',在loop-back-juggler将会自动转换成模型定义的数字类型123.
 下面是转换数组的一个详细概述:
 - 如果模型的属性是字符串,数组将会转成逗号分隔的字符串,比如{name : ['a','b']}转换成{name : 'a,b'}
 - 如果模型的属性是数字,如果请求的是数组类型,将进行下面的转换:
 	- 一个空数组转换成0,比如{count:[]}转换成{count:0}
 	- 一个单一数字数组就转换成数字比如{count:[18]}转换成{count:18}
 	- 其他的转换成NaN,注意NaN是程序中的类型,在json中会表达成null.比如{count:[18,19]}转换成{count:NaN},但是响应使用{count:null}.
- 如果模型的属性是布尔类型,数组转换成true,比如{isChecked:[1,2]}转换成{isChecked:true}
- 如果模型的属性是日期类型,数组转换成时间字符串,比如{when: [2015,04,02]}转换成2015-04-02T00:00:00.000
- 如果模型的属性是对象或其他类型,数组不做转换.
- 如果是数组中的类型定义,转换规则和上面一样,比如:
	- {strings: [['a','b'], 'c']}转换成{strings: ['a,b', 'c']}.
	- {numbers: [[1,2], 3]}转换成{numbers: [NaN, 3]}.

尽管第一眼看上去不错,但是我还是发现了一点在转换时的缺陷,NaN被认为是true,从而可以通过验证,比如:
```json
> POST /api/records
{
  "count": [1,2,3]
}
< 200 OK
{
  "count": null
}
```
不过这个问题在[#568](https://github.com/strongloop/loopback-datasource-juggler/pull/568)已经得到解决了.