# 创建并编辑模型
####先决条件:
1. 安装了strongLoop
2. 会使用Arc

模型是LoopBack的核心:他们封装你应用程序的数据和你怎么处理这些数据的方法.LoopBack模型自动拥有Node API和REST API.一个模型对应一个数据源,API提供创建,读取,更新,删除(CRUD)能力.你能在开发阶段使用API explorer访问REST API.

模型编辑器能快速的让你创建LoopBack模型而不用写JSON文件或者代码.

注意:这个版本的StrongLoop composer允许您快速创建和编辑模型和属性。它目前并不提供能够添加或编辑更高级的特性,比如访问控制(acl),自定义远程方法,模型之间的关系,等等。使用slc loopback命令行工具使用这些特性.未来版本将提供定义和操纵这些高级编辑器.

## 创建一个新模型
创建新模型:
- 打开Arc,并进入composer面板
- 点击Add New Model
- 点击下方的+New按钮

这将打开模型编辑器,试着编辑新模型.

## 编辑一个模型
编辑一个存在的模型,简单的点击导航中的Models文件夹.

打开模型编辑器编辑模型.

你能同时编辑多个模型,因为每个都在不同的标签中打开的.

## 模型编辑器
当你像上面所述创建一个新模型或者存在的模型时,你将看见编辑器:
![https://docs.strongloop.com/download/attachments/4557560/arc%20composer%20edit%20model.png?version=1&modificationDate=1433455553000&api=v2](https://docs.strongloop.com/download/attachments/4557560/arc%20composer%20edit%20model.png?version=1&modificationDate=1433455553000&api=v2)

模型编辑器有3个主要部分:
- 模型名字
- 模型细节
- 模型属性

## 模型细节
下面描述模型细节:
- Plural-这个是模型复数(自动设置),你也可以重写它.
- Base model-这个是模型的基类,典型的比如Model或者persistedModel(模型将连接到持久性数据源比如数据库).
- Datasource-模型依附的数据源.(默认是内存)
- Public-模型是否通过REST API暴露.
- Strict-是否决定用loopback定义的模型类型,忽略其他人编程增加.

## 模型属性
一个模型有一个或多个属性,每个具有下面的属性:
- Name
- Type-数据类型(String,Number等等)
- Is ID-是否为模型的惟一的标识符
- Required-是否必须有一个值
- Index-是否有索引
- Comments-属性的详细注释

## 迁移模型
点击Migrate Model按钮来创建数据表,这会将每个模型新建一个数据表,每个模型的属性新建一个列.这就叫`auto-migration`.
注意:`auto-migration`只能在支持的数据库中运行.否则,Migrate Model按钮会被禁止.

下面的数据库支持`auto-migration`:
- Oracle
- PostgreSQL
- MySQL
- SQL Server
- MongoDB*

当你的应用程序连接到一个数据源之上时,Migrate Model按钮将可以使用,当你鼠标移上去时.点击就将开始自动迁移.

注意:MongoDB是无模型的数据库,迁移MongoDB将只更新索引.如果你改变现有的属性,MongoDB将保存着现有的记录,但是新的记录将用新定义的属性来更新.