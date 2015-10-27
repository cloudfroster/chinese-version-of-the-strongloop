# 扩展你的API
## 先决条件
- 需要: 安装StrongLoop
- 推荐: 读LoopBack核心概念

在这篇文章中,你将增加为你的API定制一个远程方法.

提示:如果你跟随上一章,跳读到增加远程方法.如果你跳读到这里,继续往下读...

从github上得到程序,然后安装依赖:
```shell
$ git clone https://github.com/strongloop/loopback-getting-started.git
$ cd loopback-getting-started
$ git checkout step2
$ npm install
```

## 增加一个远程方法
跟随这些步骤:
1. 查看/common/models目录,你将看见coffee-shop.js和coffee-shop.json文件.
2. 打开coffee-shop.js文件,默认包括下面的代码:
```javascript
module.exports = function(CoffeeShop) {
};
```
3. 更改成下面的代码:
```javascript
module.exports = function(CoffeeShop) {
  CoffeeShop.status = function(cb) {
    var currentDate = new Date();
    var currentHour = currentDate.getHours();
    var OPEN_HOUR = 6;
    var CLOSE_HOUR = 20;
    console.log('Current hour is ' + currentHour);
    var response;
    if (currentHour > OPEN_HOUR && currentHour < CLOSE_HOUR) {
      response = 'We are open for business.';
    } else {
      response = 'Sorry, we are closed. Open daily from 6am to 8pm.';
    }
    cb(null, response);
  };
  CoffeeShop.remoteMethod(
    'status',
    {
      http: {path: '/status', verb: 'get'},
      returns: {arg: 'status', type: 'string'}
    }
  );
};
```
4. 保存文件

## 尝试远程方法
1. 返回应用程序根目录,运行应用程序:
```shell
$ node .
```
2. 导航到 http://localhost:3000/explorer 查看api explorer. 然后点击coffeeshops,你将看见一个新的接口.GET /CoffeeShop/status.
![https://docs.strongloop.com/download/attachments/3837214/gs%20remote%20method.png?version=1&modificationDate=1418940884000&api=v2](https://docs.strongloop.com/download/attachments/3837214/gs%20remote%20method.png?version=1&modificationDate=1418940884000&api=v2)
3. 点击try it out!
你将看见远程方法返回下面的值:
```javascript
{
  "status": "Open for business." 
}
```
这就是增加远程方法,多么的简单啊.

## 在远程方法中运行CRUD方法
在远程方法中运行标准的模型的CRUD方法.
```javascript
module.exports = function(CoffeeShop) {
...
  CoffeeShop.getName = function(shopId, cb) {
    CoffeeShop.findById( shopId, function (err, instance) {
        response = "Name of coffee shop is " + instance.name;
        cb(null, response);
        console.log(response);
    });
  }
...
  CoffeeShop.remoteMethod (
        'getName',
        {
          http: {path: '/getname', verb: 'get'},
          accepts: {arg: 'id', type: 'number', http: { source: 'query' } },
          returns: {arg: 'name', type: 'string'}
        }
    );
}
```
然后,你请求远程方法,比如:
```shell
http://0.0.0.0:3000/api/CoffeeShops/getname?id=1
```
你将得到返回的值:
```javascript
{
  "name": "Name of coffee shop is Bel Cafe"
}
```