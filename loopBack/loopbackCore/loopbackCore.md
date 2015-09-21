# LoopBack核心概念
首先读这个来理解LoopBack是如何工作的,然后开始用LoopBack来创建一个应用程序.
![https://docs.strongloop.com/download/attachments/4555926/Model%20inheritance.png?version=3&modificationDate=1415065235000&api=v2](https://docs.strongloop.com/download/attachments/4555926/Model%20inheritance.png?version=3&modificationDate=1415065235000&api=v2)

- 模型
- 应用逻辑
- 数据源和连接器
- LoopBack组件
- 开发工具

## 模型
模型是LoopBack的核心:他们封装你应用程序的数据和你怎么处理这些数据的方法.LoopBack模型自动拥有Node API和REST API.一个模型对应一个数据源,API提供创建,读取,更新,删除(CRUD)能力.你能在开发阶段使用API explorer访问REST API.

LoopBacky的一个强大特性是当你定义一个模型,它会自动预定义一套REST API附加到模型上.通过这些接口,可以实现创建,读取,更新和删除(CRUD)的操作.

## 内置模型
每个LoopBack程序都有一套预定义的内置模型,比如User,Role,和Application,这样你就不用自己创建这些通用模型了.

## 自定义模型
你可以定义你自己的自定义模型.你可以让你的自定义模型继承自内置模型.比如User,Application,或者其他内置模型.

你可以通过多种方式创建模型,这依赖于模型基于那个数据源.你可以创建模型:
- 用模型生成器,slc loopback:model
- 从一个存在的关系型数据库创建,使用模型的discovery.这样你可以让你的模型和数据库模型同步.
- 为自由格式的数据实例内省NoSQL数据库或REST API.

所有这些方法创建的模型都定义在一个JSON文件中.按照惯例放在common/models目录,例如,common/models/Account.json

你也可以通过用LoopBack API编程来定义模型,或者手动编辑JSON文件来定义模型.大多数来说,你不需要用这些技术来创建模型,但一般需要定制你的模型.

注意,JSON模型文件中包含了一个idInjection属性,它代表是否需要LoopBack自动增加一个唯一id属性到模型中.如果模型连接到数据库,这个id属性对应主键.

## 模型关系
你可以定义模型之间的关系,比如属于(BelongsTo),有许多(HasMany),和属于并有许多(HasAndBelongsTOMany).

## 模型的CRUD操作
当你连接一个模型到永久数据源比如数据库,它变成一个连接的模型拥有一套创建,读取,更新和删除操作.

|Operation|REST|LoopBack model method(Node API)*|Corresponding SQL Operation|
|--------|---------|--------|--------|
|Create|PUT /modelName POST /modelName|create()*|INSERT|
|Read(Retrieve)|GET /modelName?filter=...|find()*|SELECT|
|Update(Modify)|POST /modelName PUT /modelName|updateAll()*|UPDATE|
|Delete (Destroy)|DELETE /modelName/modelID|destroyById()*|DELETE|

注意:上面的只是常见的方法,其他模型的方法,例如:findById(),findOne(),和findOrCreate().参看[持久模型API文档](http://apidocs.strongloop.com/loopback/#persistedmodel).

## 应用逻辑
你可以用多种方式添加自定义应用逻辑:
- 通过远程方法(remote methods)添加应用逻辑到模型上.
- 添加程序启动脚本(boot script)
- 定义自定义中间件(middleware),类似于Express中间件.

## 中间件时期
中间件指的是当发送HTTP请求到REST端的执行函数.由于LoopBack是基于Express的,LoopBack中间件和Express中间件相同.但是LoopBack添加了phases的概念.可以明确的定义中间件调用的顺序.使用phases有助于避免可能发生在标准express中间件的顺序问题.

## 数据源和连接器
![https://docs.strongloop.com/download/attachments/3836252/Data%20sources%20and%20connectors.png?version=1&modificationDate=1408559677000&api=v2](https://docs.strongloop.com/download/attachments/3836252/Data%20sources%20and%20connectors.png?version=1&modificationDate=1408559677000&api=v2)
LoopBack把后端服务比如数据库,REST API,SOAP web服务,和存储服务抽象为数据源.

数据源后端使用连接器(直接和数据库和其他后端服务相连).应用程序不需要直接连接,而是通过数据源和永久数据模型的API.

## LoopBack 组件
LoopBack组件提供额外的插件功能:
- 消息推送-允许消息作为badge,alert或者pop-up立即显示在手机设备上.
- 存储服务-允许从提供的云端(amazon,rackspace,openstack和azure)上传和下载文件.
- 第三方登录-集成passport,允许用户使用第三方证书登录,比如facebook,Google,Twitter,Github,或者支持OAuth,OAuth 2或OpenID的系统.
- 同步-允许离线操作应用,当重连接时同步数据到服务器.
- OAuth 2.0-允许使用loopback应用程序函数作为oAuth 2.0提供者进行身份验证和授权客户机应用程序和用户访问受保护的API端点.

## 开发工具
LoopBack提供2个主要的开发工具:
- slc loopback,一个命令行工具来创建和修改loopBack应用.
- strongLoop Arc,一个图形工具来开发,部署和监控loopBack应用.

slc loopback命令行工具将指导您完成应用程序开发过程的交互提示:
1. 使用 slc loopback应用程序生成器来创建脚手架.
2. 使用 slc loopback:model模型生成器来添加模型.使用slc loopback:property属性生成器来添加属性.
3. 使用 slc loopback:datasource数据源生成器来添加数据源.
4. 使用 slc loopback:relation关系生成器来添加模型关系.