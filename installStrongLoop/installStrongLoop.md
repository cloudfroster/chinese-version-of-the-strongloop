# 安装 StrongLoop
如果你正在使用LoopBack开发一个node或者API程序它提供了无代码的API组件，同构模型，移动和AngularJS的SDK，安全，和许多额外的演变特征与一个蓬勃发展的社区,可以逛逛[谷歌LoopBack小组](https://groups.google.com/forum/#!forum/loopbackjs).

如果你有一个node应用程序,可以参看操作nodejs应用程序.

## 先决条件
在安装StrongLoop之前,你必须安装node.js或者io.js.(目前两个已经合并).


## 开发要求和限制
注意:StrongLoop Process Manager不能在windows系统上运行


## 构建和发布
为了用`git`发布你的程序,你需要安装git源码管理工具.


## windows上的配置
`git`在windows上默认路径不能超过260个字符,因此,为了避免出错,你可以通过以下命令来允许`git`支持长路径:
```shell
C:\> git config --system core.longpaths true
```
你不能将LoopBack的应用程序发布到windows系统中。然而，您可以在windows系统上建立和发布应用程序到苹果系统或者liunx系统.


## 性能分析
为了使用StrongLoop的性能分析功能,你必须:
* 在想性能分析的机器上安装c++编译器
* 使用的node版本大于或等于0.10.x

由于一些已知的nodejs问题,你不能在window8系统上生成性能报告文件.


## 下一步你需要做什么
现在,你就可以通过以下命令安装strongloop:
```shell
npm install -g strongloop
```
一旦运行成功,就意味着你已经安装了:
* LoopBack框架,包括 loopback, loopback-datasource-juggler模块和其他众多的和StrongLoop相关的模块.
* StrongLoop命令行工具,`slc`,这个工具能创建,运行和管理LoopBack程序.
* StrongLoop Arc,统一的图形API生命周期工具套件,包括用于构建、分析和监控应用.
* LoopBack Angular命令行工具(lb-ng和lb-ng-doc)
* 其他工具,包括`Yeoman`,创建LoopBack脚手架的Yeoman生成器,还有`Grunt`,javascript任务构建工具.


## 在你的系统上安装StrongLoop
下面将介绍以下系统的安装教程:
* Windows
* Mac OSX
* Linux


## Windows
#### 重新安装npm
windows系统上node自带的npm有一些已知的问题,为了避免这些问题,从新安装npm,这样安装的npm就是npm2:
```shell
$ npm install -g npm
```
#### 安装StrongLoop
跟随以下步骤安装StrongLoop:
1. 打开windows命令行弹窗,注意:node不支持Cygwin,你必须用命令行弹窗(shell).
2. 安装StrongLoop:
```shell
C:\> npm install -g strongloop
```
注意下:在安装期间你可能会看见一些`node-gyp`和`python`错误如果你没有安装编译工具的话.这些错误只阻止你的监视和管理功能.如果你需要这些功能的话,可以先安装编译工具.否则,你可以忽略这些错误.

如果你安装遇到了任何问题,参看安装疑难问题.


## Mac OSX
#### 文件和目录权限设置
为了安装node和strongloop,你需要允许以下目录有写的权限:
* /usr/local/bin 
* /usr/local/lib/node_modules
注意:如果这些目录不存在,你需要自己创建下.

虽然你可以通过在前面增加`sudo`来解决,不过一般来讲,最佳实践是明确的指出目录所有者和目录权限,就像下面这样:
```shell
$ sudo chown -R $USER /usr/local/bin
$ sudo chown -R $USER /usr/local/lib/node_modules
```
注意:这样改变权限只适合在本地开发系统,永远不要在服务器系统上这样做.
这些命令使你的用户账号拥有 /usr/local/bin和/usr/local/lib/node_modules目录.因此,你不需要使用`sudo`来安装node或者全局安装npm包.


### 安装node.js
下载最新版本的Node.js并安装.

### 安装strongloop
1. 打开终端窗口.
2. 键入以下命令:
```shell
$ npm install -g strongloop
```
如果你没有设置你的目录权限,可以使用这个命令:(不推荐)
```shell
$ sudo npm install -g strongloop
```
注意下:在安装期间你可能会看见一些`node-gyp`和`python`错误如果你没有安装编译工具的话.这些错误只阻止你的监视和管理功能.如果你需要这些功能的话,可以先安装编译工具.否则,你可以忽略这些错误.

如果你安装遇到了任何问题,参看安装疑难问题.


## Linux
#### 文件和目录权限设置
为了安装node和strongloop,你需要允许以下目录有写的权限:
* /usr/local/bin 
* /usr/local/lib/node_modules
注意:如果这些目录不存在,你需要自己创建下.

虽然你可以通过在前面增加`sudo`来解决,不过一般来讲,最佳实践是明确的指出目录所有者和目录权限,就像下面这样:
```shell
$ sudo chown -R $USER /usr/local/bin
$ sudo chown -R $USER /usr/local/lib/node_modules
```
注意:这样改变权限只适合在本地开发系统,永远不要在服务器系统上这样做.
这些命令使你的用户账号拥有 /usr/local/bin和/usr/local/lib/node_modules目录.因此,你不需要使用`sudo`来安装node或者全局安装npm包.


### 安装node.js
下载最新版本的Node.js并安装.

### 安装strongloop
1. 打开终端窗口.
2. 键入以下命令:
```shell
$ npm install -g strongloop
```
如果你没有设置你的目录权限,可以使用这个命令:(不推荐)
```shell
$ sudo npm install -g strongloop
```
注意下:在安装期间你可能会看见一些`node-gyp`和`python`错误如果你没有安装编译工具的话.这些错误只阻止你的监视和管理功能.如果你需要这些功能的话,可以先安装编译工具.否则,你可以忽略这些错误.

如果你安装遇到了任何问题,参看安装疑难问题.


## 确认安装
可以通过在命令行键入slc help来确定是否安装成功:
```shell
$ slc --help
```
你将看见以下标准"man page":
```shell
usage: slc <-h|--help|-v|--version>
usage: slc <command> [--help] [...]
 
Command-line tool for development and control of a Node application.
 ...
```
如果你看见了这个,那么你安装成功啦~.

如果没有,参看安装疑难问题.