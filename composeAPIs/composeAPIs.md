# 创作APIs
## 必要条件
你需要安装StrongLoop.如果你还没有一个node应用程序,你可以使用下面的命令创建基础模板:
```shell
slc loopback
```
这将会创建一个基础的loopback模板.

## 使用Arc创作器
注意:你可以使用Arc来构建或者发布,监控任何Node应用程序,但是创建api只能适用于loopback应用程序.

怎么使用API创作器:
1. 在你程序的根目录开始:
```shell
$ cd <my-project-dir>
$ slc arc
```
2. 浏览器自动打开,点击composer,你能看见下面的页面:
![https://docs.strongloop.com/download/attachments/4557559/arc%20composer%20init.png?version=1&modificationDate=1433796577000&api=v2](https://docs.strongloop.com/download/attachments/4557559/arc%20composer%20init.png?version=1&modificationDate=1433796577000&api=v2 "https://docs.strongloop.com/download/attachments/4557559/arc%20composer%20init.png?version=1&modificationDate=1433796577000&api=v2")
3. 创建一个或者更多数据源.
4. 创建模型:
	- 从scratch中创建
	- 从已存在的数据库中创建
5. 如果需要,根据你的模型创建数据库表
6. 使用slc添加额外的功能,如关系模型和访问控制(acl),请继续往下读.

## 使用slc
如果你更喜欢使用命令行,你可以使用slc来代替Arc:
1. 创建一个新的loopback应用程序:
```shell
$ slc loopback
```
2. 进入你的项目目录:
```shell
$ cd <my-project-dir>
```
3. 使用`slc loopback:datasource`创建新的数据源.
4. 创建模型,可以使用`slc loopback:model`创建,还可以从已存在的数据库创建模型.
5. 如果需要,根据你的模型创建数据库表.
6. 使用`slc loopback:relations`来建立模型之间的关系.
7. 使用`slc loopback:acl`来创建访问控制.
8. 增加其他API和特性.