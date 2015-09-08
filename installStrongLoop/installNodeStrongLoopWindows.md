# 在Windows系统上安装Node和StrongLoop
安装步骤如下:
- 安装先决条件
	- Git
	- Python
	- Visual Studio
- 安装nodejs
- 重安装npm
- 安装StrongLoop
- 疑难问题
	- 确认安装成功
	- 提示和技巧

注意:你不能将LoopBack的应用程序发布到windows系统中。然而，您可以在windows系统上建立和发布应用程序到苹果系统或者liunx系统.
## 安装先决条件
node的包管理工具npm,下面的几个软件包,通常不是windows系统的一部分.
### Git
`npm`使用Git来从Github下载包.
1. 下载windows版本的安装包 [http://git-scm.com/download](http://git-scm.com/download "http://git-scm.com/download")
2. 安装Git.

### Python
您需要安装Python,如果你想StrongLoop具有的构建、部署、监控和管理的功能.

npm使用Python 2.7(不是3.x,也不是2.6.x或更早的版本)与编译插件安装包(如strong-agent或websocket).

下载Python 2.7.x [http://python.org](http://python.org "http://python.org")
1. 去官网下载对应你系统版本的安装包
2. 安装python

### Visual Studio
您需要安装Visual Studio,如果你想StrongLoop具有的构建、部署、监控和管理的功能.
1. 去官网下载对应你系统版本的安装包
2. 安装Visual Studio

### 安装nodejs
1. 到官网下载安装包 [https://nodejs.org/en/](https://nodejs.org/en/ "https://nodejs.org/en/")
2. 下载.msi文件并安装

### 重新安装npm
node自带的npm有一些已知的问题,为了避免出错,请重新安装npm,重新安装的npm实际上是npm2.
```shell
C:\> npm install -g npm
```

### 安装StrongLoop
1. 打开windows命令行弹窗,注意:node不支持Cygwin,你必须用命令行弹窗(shell).
2. 安装StrongLoop:
```shell
C:\> npm install -g strongloop
```
注意下:在安装期间你可能会看见一些`node-gyp`和`python`错误如果你没有安装编译工具的话.这些错误只阻止你的监视和管理功能.如果你需要这些功能的话,可以先安装编译工具.否则,你可以忽略这些错误.

### 疑难问题
请自行百度,谢谢.

### 确定安装成功
1.打开命令行输入:
```shell
C:\> node -v
v0.12.6

C:\> npm -v
2.14.1

C:\> slc -v
strongloop v5.0.0(node v0.12.6)
```
如果你出现上面相似的结果,那么表明你安装成功

如果不是,请参考疑难问题.

### 提示和技巧
1. 如果安装了多个python版本,你能通过npm来配置你使用哪个版本的python:
```shell
C:\> npm config set python c:/Python2.7/python
```
2. 如果你安装了多个Microsoft Visual Studio版本,你能通过npm来配置你使用哪个版本的Microsoft Visual Studio:
```shell
C:\> npm config set GYP_MSVS_VERSION=2012
```
或者你可以选择在npm命令使用的时候选择使用哪个版本:
```shell
C:\> npm install -g strongloop --msvs_version=2012
```