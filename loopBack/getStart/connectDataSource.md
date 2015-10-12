# 连接API到数据源
## 先决条件
- 安装了strongloop
- 阅读了loopback核心概念

你将把前一章的应用连接到MySQL.
提示:如果你跟随上一章,跳读到增加数据源.如果你跳读到这里,继续往下读...

从github上得到应用并安装所有依赖:
```shell
$ git clone https://github.com/strongloop/loopback-getting-started.git
$ cd loopback-getting-started
$ git checkout step1
$ npm install
```

## 增加数据源
现在你将使用数据源生成器定义一个数据源:
```shell
$ slc loopback:datasource
```
这个询问你数据源的名字:
```shell
[?] Enter the data-source name:
```
键入mysqlDs并敲击Enter.
下一步,这个生成器将询问数据源类型:
```shell
[?] Select the connector for mysqlDS: (Use arrow keys)
  other
  In-memory db (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```
点击下箭头选择MYSQL,然后点击Enter.
该工具将数据源定义添加到server/datasources.json文件,它将看起来如下.注意着个mysqlDs数据源你增加的,同样的内存数据源名为"db",这是默认的.
datasource.json
```json
{
  "db": {
    "name": "db",
    "connector": "memory"
  },
  "mysqlDs": {
    "name": "mysqlDs",
    "connector": "mysql"
  }
}
```

## 安装MySQL连接器
现在增加loopback-connector-mysql模块并安装依赖:
```shell
$ npm install loopback-connector-mysql --save
```

## 配置数据源
编辑/server/datasource.json在这行后面

	"connector": "mysql"
增加host,port,database,username和password属性.
为了使用strongloop mysql 服务.运行demo.strongloop.com,然后用下面的值.

为了使用本机的mysql服务.键入hostname,port number和登录认证.
/server/datasources.json
```json
{
  "db": {
    "name": "db",
    "connector": "memory"
  },
  "mysqlDs": {
    "name": "mysqlDs",
    "connector": "mysql",
    "host": "demo.strongloop.com",
    "port": 3306,
    "database": "demo",
    "username": "demo",
    "password": "L00pBack"
  }
}
```

## 连接CoffeeShop模型到mysql
现在你已经有mysql数据源和CoffeeShop模型.你将需要连接他们.loopback应用使用model-config.json来连接模型到数据源.编辑/server/model-config.json并键入CoffeeShop入口:
/server/model-config.json
```shell
"CoffeeShop": {
  "dataSource": "db",
  "public": true
}
```

## 增加一些测试数据并查看
在/server/boot/create-sample-models.js中添加以下内容:
```shell
module.exports = function(app) {
  app.dataSources.mysqlDs.automigrate('CoffeeShop', function(err) {
    if (err) throw err;
 
    app.models.CoffeeShop.create([
      {name: 'Bel Cafe', city: 'Vancouver'},
      {name: 'Three Bees Coffee House', city: 'San Mateo'},
      {name: 'Caffe Artigiano', city: 'Vancouver'},
    ], function(err, coffeeShops) {
      if (err) throw err;
 
      console.log('Models created: \n', coffeeShops);
    });
  });
};
```
现在运行应用程序:
```shell
$ node .
```
在console中,你将看见:
```shell
...
Browse your REST API at http://0.0.0.0:3000/explorer
Web server listening at: http://0.0.0.0:3000/
Models created: [ { name: 'Bel Cafe',
    city: 'Vancouver',
    id: 1 },
  { name: 'Three Bees Coffee House',
    city: 'San Mateo',
    id: 3 },
  { name: 'Caffe Artigiano',
    city: 'Vancouver',
    id: 2 } ]
```
你也能使用API Explorer:
1. 浏览到http://0.0.0.0:3000/explorer/(你可能需要使用http://localhost:3000/explorer),依赖与你的浏览器和操作系统.
2. 点击GET  /CoffeeShops  Find all instance of the model matched by filter...
3. 点击Try it out!
4. 你将看见上面你创建的三个coffee shops的数据.