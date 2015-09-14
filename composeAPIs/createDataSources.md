# 创建并编辑数据源
####先决条件:
1. 安装了strongLoop
2. 会使用Arc

数据源的后面就是真实的数据,这些数据可以永久的保存.模型依赖数据源来实现创建,更新,删除(CRUD)操作.

## 安装数据源连接器(data source connector)
LoopBack默认使用内置的内存连接器(memory connector)来开发和测试.使用`slc loopback`创建的应用程序包括了内存数据源和连接器.内存数据源保存你的数据只能当应用程序运行的时候,当应用停止,数据就会丢失.默认内存数据源命名是'db',并且写在了Data Sources文件里面.

注意:为了创建一个连接到数据库的数据源,你首先需要用npm安装连接器.

例如:
```shell
$ cd <your-app-dir>
$ npm install --save loopback-connector-mysql
```
参阅[连接数据源到数据库](https://docs.strongloop.com/display/public/LB/Connecting+models+to+data+sources)章节连接器的完整列表.

## 创建数据源
在创建数据源之前,就像上面说的,你需要安装对应的连接器.
创建数据源:
- 打开Arc,并进入composer面板
- 在导航里点击Add New Data source
- 点击![https://docs.strongloop.com/download/thumbnails/4557561/db%20icon.png?version=2&modificationDate=1433198306000&api=v2](https://docs.strongloop.com/download/thumbnails/4557561/db%20icon.png?version=2&modificationDate=1433198306000&api=v2)图标,选择对应的数据库类型.

提示:你也可以用命令行工具`slc loopback:datasource`来创建数据源.

## 编辑数据源
编辑一个已经存在的数据源,简单的点击导航中的Data sources文件夹,数据源将会显示出来.

你可以同时编辑多个数据源,因为每个都是独立的标签.

删除一个数据源,只需要点击导航中的![https://docs.strongloop.com/download/attachments/4557561/studio-glyph.png?version=2&modificationDate=1433198317000&api=v2](https://docs.strongloop.com/download/attachments/4557561/studio-glyph.png?version=2&modificationDate=1433198317000&api=v2)图标,选择delete即可.这个会删除/server/datasources.json中的条目,但不会删除任何js文件.

当你像上面创建或编辑数据源的时候,你会看见数据源编辑器.
![https://docs.strongloop.com/download/attachments/4557561/arc%20datasource%20editor.png?version=1&modificationDate=1433455815000&api=v2](https://docs.strongloop.com/download/attachments/4557561/arc%20datasource%20editor.png?version=1&modificationDate=1433455815000&api=v2)
数据源编辑器有3个主要的部分:
- 数据源名字
- credentials认证数据源
- 数据源属性
	- Host-数据库服务器的主机名或者ip地址
	- Port-数据库服务器用的TPC端口
	- Database-有时被称为一个“模式”的分组表或文件,如果没有指定,数据源将使用所有用户访问数据库或模式.
	- Connector-LoopBack使用的连接器

点击`Test Connection`来验证你的数据源配置是否正确.

## 模型发现(Model discovery)
对于将数据源连接到关系数据库中,compser可以自动从数据库表中创建模型通过使用loopback的发现功能(discovery):在导航面板中点击![https://docs.strongloop.com/download/attachments/4557561/studio-glyph.png?version=2&modificationDate=1433198317000&api=v2](https://docs.strongloop.com/download/attachments/4557561/studio-glyph.png?version=2&modificationDate=1433198317000&api=v2),这个图标在数据源名称的后面.然后点击discover models.
![https://docs.strongloop.com/download/attachments/4557561/discover%20models.png?version=1&modificationDate=1418673302000&api=v2](https://docs.strongloop.com/download/attachments/4557561/discover%20models.png?version=1&modificationDate=1418673302000&api=v2)
更多请参阅[从数据库映射模型](discoverModels.md)章节.