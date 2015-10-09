# 创建一个简单API
## 先决条件
- 需要: 安装StrongLoop
- 推荐: 读LoopBack核心概念

使用loopback命令行工具,slc,loopback来创建一个应用程序脚手架.脚手架简单的代表产生基本的代码节省你的时间.你能根据需要修改你的代码.

在继续往下读时,确保你的StrongLoop是最新的:
```shell
$ npm install -g strongloop
```
确保你运行这段代码在24小时以内,我们一直在改进LoopBack!

## 创建新的应用程序
为了创建一个新的程序,运行LoopBack应用程序生成器:
```shell
$ slc loopback
```
这个loopback生成器将产生一些友好的ASCII字符并询问应用的名字.

键入loopback-getting-started,然后生成器将询问包含这个项目的路径,按下Enter接受默认设置(和应用名字一样).
```shell
     _-----_
    |       |    .--------------------------.
    |--(o)--|    |  Let's create a LoopBack |
   `---------´   |       application!       |
    ( _´U`_ )    '--------------------------'
    /___A___\
     |  ~  |
   __'.___.'__
 ´   `  |° ´ Y `
[?] What's the name of your application? loopback-getting-started
[?] Enter name of the directory to contain the project: loopback-getting-started
```
提示: 你可以用不一样的应用程序名字,但是如果你这样做了,确保你在以后的文章中把loopback-getting-started和你的对应.

这个生成器创建的脚手架包括:
1. 初始化项目目录结构
2. 创建默认的JSON文件
3. 创建默认的JavaScript文件
4. 下载并安装node模块依赖(就像你手动 npm install一样)

## 创建模型
现在,你一样有了项目的脚手架,你将继续创建一个CoffeeShop的模型,这个模型将自动拥有REST API接口.

进入你新的项目目录,然后运行loopback模型生成器:
```shell
$ cd loopback-getting-started
$ slc loopback:model
```
生成器将询问模型名字,键入CoffeeShop:
```shell
[?] Enter the model name: CoffeeShop
```
下一步将询问你想把模型附加到哪个已经定义好的数据源.

我们现在只有内存数据源是可用的,按下Enter选择这个:
```shell
...
[?] Select the data-source to attach CoffeeShop to: (Use arrow keys)
❯ db (memory)
```
然后生成器将询问你模型的基类是哪个,由于将把这个模型连接到永久数据源,按下下箭头来选择PersistedModel,然后按下Enter:
```shell
[?] Select model's base class: (Use arrow keys)
  Model
❯ PersistedModel
  ACL
  AccessToken
  Application
  Change
  Checkpoint
```
PersistedModel是基本的对象来连接到永久数据源比如数据库.

Loopback的一个高级特性是自动为你的模型产生REST API接口.这个生成器将询问你是否暴露REST API接口.

敲击Enter来接受默认的通过REST暴露私有模型:
```shell
[?] Expose CoffeeShop via the REST API? (Y/n) Y
```
Loopback自动创建REST路由.默认的,名字会使用复数的形式(通过添加s),但是你也可以特殊的定制你想要的复数形式.

按下Enter来接受默认的复数形式(CoffeeShops):
```shell
[?] Custom plural form (used to build REST URL):
```
每个模型都有属性,现在,你将定义为CoffeeShop定义一个"name"属性.

选择string作为属性类型(按下Enter,因为string是默认的选项):
```shell
Let's add some CoffeeShop properties now.
Enter an empty property name when done.
[?] Property name: name
   invoke   loopback:property
[?] Property type: (Use arrow keys)
❯ string
  number
  boolean
  object
  array
  date
  buffer
  geopoint
  (other)
```
每个属性能可选或者必选.键入y来让name必选:
```shell
[?] Required? (y/N)
```
最终模型创建过程按输入时提示输入下一个属性的名称.

模型生成器将创建2个文件在common/models目录来定义模型:coffee-shop.json和coffee-shop.js.

注意:loopback模型生成器,slc,loopback:model自动把驼峰命令转换成-连接字符,比如,如果你创建一个模型叫"FooBar",它将自动转换成foo-bar.json和foo-bar.js文件.但是模型名字("FooBar")还是在程序中保留的.

## 检查项目结构
注意:slc loopback命令将创建下面的应用程序结构.loopback不是强制遵循这样的结构,不过,如果你不遵循这样的结构,将不能使用slc loopback的命令来修改或者扩展你的应用程序.

LoopBack项目文件和目录在程序根目录.在这个目录,应用程序有3个子目录:
- server node程序脚本和控制文件 
- client 客户端js,html,和css文件
- common 通用客户端和服务端文件.包含JSON文件和js文件

提示:你所有的JSON和js文件都放在/common/models目录(定义模型).

|File or directory|	Description	|How to access in code|
|------|------|------|
|Top-level application directory|
|package.json|Standard npm package specification. See package.json.
Additionally, the top-level directory contains the stub README.md file, and node_modules directory (for Node dependencies).|N/A|
|/server directory - Node application files| 
|server.js	|Main application program file.	 |N/A|
|config.json|	Application settings. See config.json.|	app.get('setting-name')|
|datasources.json |	Data source configuration file. See datasources.json. For an example, see Create new data source.	|app.datasources['datasource-name']|
|model-config.json	|Model configuration file. See model-config.json. For more information, see  Connecting models to data sources.	|N/A|
|middleware.json	|Middleware definition file. For more information, see Defining middleware.|N/A|
|/boot directory	|Add scripts to perform initialization and setup. See boot scripts.	Scripts are automatically executed in alphabetical order.||
|/client directory - Client application files|
|README.md	|LoopBack generators create empty README file in markdown format.	|N/A|
|Other	|Add your HTML, CSS, client JavaScript files.	 |
|/common directory - shared application files|
|/models directory	|Custom model files:Model definition JSON files, by convention named model-name.json; for example customer.json.Custom model scripts by convention named model-name.js; for example, customer.js.For more information, see Model definition JSON file and Customizing models.IconThe LoopBack model generator, slc loopback:model, automatically converts camel-case model names to lowercase dashed names.  For example, if you create a model named "FooBar" with the model generator, it creates files foo-bar.json and foo-bar.js in common/models.  However, the model name ("FooBar") will be preserved via the model's name property.|Node: myModel = app.models.myModelName|

参看更多loopback应用程序结构,参看[Project layout reference](https://docs.strongloop.com/display/LB/Project+layout+reference).

## 运行应用程序
开始启动应用程序:
```shell
$ node .
...
Browse your REST API at http://0.0.0.0:3000/explorer
Web server listening at: http://0.0.0.0:3000/
```
注意:在开发阶段用node命令来启动应用是合适的,一旦你准备移到生产环境,你能运行slc start来运行strongloop进程管理,这能提供集群,日志,监控和更多.

打开你的浏览器到http://0.0.0.0:3000(在一些机器上,你可能需要用http://localhost:3000来代替).你将看见程序默认响应了一个段JSON文件,像下面这样:
{"started":"2014-11-20T21:59:47.155Z","uptime":42.054}

现在,打开你浏览器到 http://0.0.0.0:3000/explorer 或者 http://localhost:3000/explorer. 你将看到strongloop API Explorer:
![https://docs.strongloop.com/download/attachments/3836321/gs%20api%20explorer%201.png?version=1&modificationDate=1418940570000&api=v2](https://docs.strongloop.com/download/attachments/3836321/gs%20api%20explorer%201.png?version=1&modificationDate=1418940570000&api=v2)

通过一系列简单的步骤,你创建了CoffeeShop模型,定义了它的属性并通过REST暴露它.

下一章:使用API Explorer,你将通过REST更加深层次的暴露你刚才定义的模型和练习一些操作.