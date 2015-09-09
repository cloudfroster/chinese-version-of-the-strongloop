# 安装编译工具
- 概述
- 安装
	- Windows
	- Mac OSX
	- Linux
		- 增加交换空间
	- 安装Python

## 为什么我需要安装编译工具?
有些特性比如内存和cpu性能分析需要用到本地(c++)代码.StrongLoop用npm分发这些代码,但是npm不能分发二进制文件,当安装了编译工具后,就能在npm安装的时候编译成二进制文件了,因此,如果你需要strongloop的这些特性,你需要安装编译工具.

## 概述
如果你没有c++编译器(windows上的Visual C++或者OSX上的XCode),你将不能参看有用的性能分析报告,包括cpu性能,堆快照.

## 安装
npm使用node-gyp来编译本地模块,详细请访问[https://www.npmjs.org/package/node-gyp](https://www.npmjs.org/package/node-gyp "https://www.npmjs.org/package/node-gyp")

## Windows
需要安装下面的:
- Python(推荐v2.7.3版本,不推荐v3.x.x版本)
- Microsoft Visual Studio C++ 2012

## Mac OSX
安装:
- 苹果的XCode
- 命令行工具,你也许需要安装命令行工具,这需要看你的MacOS和Xcode版本.在Xcode中安装:
	1. 点击`Xcode > Preferences`.
	2. 选择 `Downloads`.
	3. 在`Command-line Tools`下点击安装.

大多数OSX系统默认自带python.如果你的没有,请安装python.

## Linux
大多数Linux都提供好了必要的工具,一些特别的要求:
- Python(推荐v2.7.3版本,不推荐v3.x.x版本)
- make工具
- 一个正确的C/C++编译器,比如GCC,注意:需要g++版本大于v4.2

在Debian和Debian衍生系统(Ubuntu,Mint,之类的),用下面的命令:
```shell
$ apt-get install build-essential
```
### 增加交换空间
如果安装中出现下面的错误:
```shell
virtual memory exhausted: Cannot allocate memory
```
那么,你需要增加交换空间来给编译器提供足够的RAM.
```shell
$ dd if=/dev/zero of=/swap bs=1M count=1024 
$ mkswap /swap 
$ swapon /swap
```
键入这些命令后,重新安装StrongLoop.
注意,上面的不是永久保证的,重启后会失效,你又需要重新运行swapon/swap命令.

## 安装Python
node-gyp模块依赖python.详细请看[https://github.com/nodejs/node-gyp/blob/master/README.md#installation](https://github.com/nodejs/node-gyp/blob/master/README.md#installation "https://github.com/nodejs/node-gyp/blob/master/README.md#installation").

如果你安装的Python不在标准的路径上,运行下面的命令配置npm:
```shell
$ npm config set python /path/to/python
```
/path/to/python这个路径就是python安装的路径.

