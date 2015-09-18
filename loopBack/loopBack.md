# loopBack
提示:这一章是strongloop的核心.
## loopBack是什么
loopBack是一个高度可扩展,开源的node.js框架,它允许你:
- 少量代码或无须编码就能创建动态的端对端的REST API
- 从大型关系数据库访问数据,MongoDB,SOAP和REST api
- 合并模型关系和访问控制复杂的api
- 使用地理定位,文件,和为移动应用程序提供推动服务
- 用安卓,IOS和javascript SDK快捷的创建客户端程序
- 在本地或云端运行你的应用

## loopBack框架
loopBack框架是一组node.js模块,你可以单独使用这些模块或者组合使用来快速构建REST API应用程序.

应用通过REST API和数据源交互.使用这些API,应用程序可以查询数据库,存储数据,上传文件,发送邮件,创建消息推送,注册用户,并执行其他提供的操作数据源和服务.

使用strongloop的远程客户端可以直接调用loopback的api.

下面展示loopback的模型,这些模块之间的关系和他们的依赖:
![https://docs.strongloop.com/download/attachments/3836205/lb-modules.png?version=3&modificationDate=1421174776000&api=v2](https://docs.strongloop.com/download/attachments/3836205/lb-modules.png?version=3&modificationDate=1421174776000&api=v2)

## loopBack框架模块

|Category|Description|Use to...|Modules|
|--------|-----------|----------|--------|
|Initialization	|Application initialization	|Configure data-sources, custom models, configure models and attach them to data sources; Configure application settings and run custom boot scripts.|loopback-boot|
|Sequencing|	Middleware execution|	Configure middleware to be executed at various points during application lifecycle.|	loopback-phase|
|Integration|General system connectors|Connect to an existing system that expose APIs through common enterprise and web interfaces |loopback-connector-rest loopback-connector-soap|
|Abstraction|Model data abstraction to physical persistence|Connect to multiple data sources or services and get back an abstracted model with CRUD capabilities independent on how it is physically stored.|loopback-datasource-juggler|
|Clients|Client SDKs|Develop your client app using native platform objects (iOS, Android, AngularJS) that interact with LoopBack APIs via REST.|loopback-sdk-ios loopback-sdk-android loopback-sdk-angular|
|Data|RDBMS and noSQL physical data sources|Enable connections to RDBMS, noSQL data sources and get back an abstracted model.|loopback-connector-mongodb loopback-connector-mysql loopback-connector-postgresql loopback-connector-msssql loopback-connector-oracle|
|Services|Prebuilt services|Integrate with prebuilt services for common use cases to be utilized within LoopBack applications packaged into components.|loopback-component-push loopback-component-storage loopback-component-passport loopback-component-sync (in development)|
|Models|Model and API server|Quickly and dynamically mock up models and expose them as APIs without worrying about persisting.|loopback|
|Gateway|API gateway|Secure your APIs and inject quality of service aspects to the invocation and response workflow.|strong-gateway loopback-component-oauth2|
|Tooling|CLI and graphical tools|	Yeoman generator used by slc loopback comman; StrongLoop Arc graphical tool.	|generator-loopback strong-arc|