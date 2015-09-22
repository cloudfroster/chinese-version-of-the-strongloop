# loopBack FAQ
## 常见问题
StrongLoop支持以下操作系统:
- RHEL/CentOS 6.3(RPM)
- Debian/Ubuntu 12.10(DEB)
- Mac OSX Mountain Lion 10.8(PKG)
- Microsoft Windows 8,2008(MSI)
注意:node不支持使用Cygwin.使用Windows命令提示符命令行工具来代替.

## LoopBack是免费的吗? 要花多少钱?
LoopBack有免费和付费版本.参看[http://strongloop.com/node-js/subscription-plans/](http://strongloop.com/node-js/subscription-plans/).

LoopBack使用双重许可模型:你可以使用MIT许可,或者使用StrongLoop商业许可.参看[license](https://github.com/strongloop/loopback/blob/master/LICENSE).

## 有开发人员论坛或邮件列表吗?
是的![LoopBack谷歌小组](https://groups.google.com/forum/#!forum/loopbackjs)是一个开发人员问问题和讨论loopback和怎么使用它的地方.试试看!

还有一个loopback git渠道实时与同伴讨论 [loopBack开发商](https://gitter.im/strongloop/loopback)

StrongLoop还发布与LoopBack主题相关的博客.参看[博客](https://docs.strongloop.com/display/LB/Blog+posts)

## LoopBack有哪些客户端SDK?
LoopBack有3个客户端SDK:
- IOS SDK(objective C)为iPhone和iPad应用.参看[IOS SDK](https://docs.strongloop.com/display/LB/iOS+SDK).
- 安卓 SDK(Java)为安卓应用.参看[安卓 SDK](https://docs.strongloop.com/display/LB/Android+SDK).
- AngularJS(JavaScript)为HTML5前端.参看[angualrJs javascript SDK](https://docs.strongloop.com/display/LB/AngularJS+JavaScript+SDK).

## LoopBack有哪些连接器?
LoopBack提供了大量连接器访问企业和其他后端数据系统:
数据库连接器:
- Memory connector
- MongoDB connector
- MySQL connector
- Oracle connector
- PostgreSQL connector
- Redis connector
- SQL Server connector
其他连接器:
- Email connector
- Push connector
- Remote connector
- REST connector
- SOAP connector
- Storage connector

另外,还有开源社区人员创建的[社区连接器](https://docs.strongloop.com/display/LB/Community+connectors).

## 为什么curl请求LoopBack应用失败?
如果URL在浏览器中加载好,但当你发送一个curl请求到应用却出错:
```shell
curl: (7) Failed to connect to localhost port 3000: Connection refused
```
原因可能是由于不兼容的IP版本在应用程序之间和curl之间.

注意:在Mac OS 10.10(Yosemite),curl默认使用IP6版本.

LoopBack默认使用IP V4,而curl可能使用IP V6.如果你主机文件进入点是IP V6(localhost,fe80::1%lo0 localhost),这可能是curl使用的IP V6请求.为了让curl使用IP V4请求,设置--ipv4选项就像下面一样:
```shell
$ curl http://localhost:3000 --ipv4
```
你可以让你的loopBack应用通过指定一个IP地址使用IP6版本,如下所示:
```shell
app.start = function() {
  // start the web server
  return app.listen(3000, '::1',function() {
    app.emit('started');
    console.log('Web server listening at: %s', app.get('url'));
  });
};
```

## 细节问题
一旦你开始使用LoopBack,你可能有更详细的问题.一些一般的问题在这里收集了,其他的可以在文档中查阅.

## 你如何执行GET请求远程服务器?
首先,你用REST连接器配置数据源.在datasources.json文件配置数据源,你能用operations属性定义REST API.
简短的例子,参看[loopback-faq-rest-connector](https://github.com/strongloop/loopback-faq-rest-connector).

## 应用能回应XML来代替JSON吗?
是的!在server/config.json设置remoting.rest.xml属性成true.参看[config.json](https://docs.strongloop.com/display/LB/config.json).

## 我如何发送一份邮箱?
简要说明:
1. 用邮箱连接器配置数据源.
2. 内置邮箱模型设置成邮箱数据源.
3. 用Email.send()来发送配置的邮箱.
参看[loopback-faq-email](https://github.com/strongloop/loopback-faq-email)例子.

## 怎么使用静态中间件?
静态中间件允许应用发送静态文件例如,HTML,CSS,图片,和客户端js文件.为了增加:
1. 删除middleware.json文件中默认的routes属性.
2. 增加下面的"files"属性在middleware.json文件中.
```shell
"loopback#static": {      
  "params": "$!../client"
}
```
当然,这个值可以改成不同的目录.

## 支持什么样的钩子模型?
LoopBack模型支持:
- Operation hooks
- Remote hooks

## 用户管理问题
## 怎么注册一个新用户?
1. 创建一个表单来收集注册信息.
2. 创建远程hook来发送邮箱验证.

## 怎么登陆一个用户?
1. 创建一个表单来接受登陆凭证.
2. 创建一个路由来处理登陆请求.

## 怎么登出一个用户?
1. 创建一个登出连接来注销登陆.
2. 在access token调用User.logout函数.

## 问题排查
错误消息: loopback deprecated Routes "/methods" and "/models" are considered dangerous and should not be used

如果你看见这样的错误信息,你需要更新你的LoopBack版本.这个问题在LoopBack 2.14+得到解决.

如果你需要用LoopBack的老版本,或者希望允许这样的路由,你可以在[config.json文件中设置属性](https://docs.strongloop.com/display/LB/config.json#config.json-Top-levelproperties).