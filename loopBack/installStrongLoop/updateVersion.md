# 更新到最新版本
- 基础更新
- 清除旧的安装包
- 清除当前安装包
- 更新node.js

应用程序将根据package.json文件中定义的依赖来更新对应的包.

## 基础更新
当前的StrongLoop版本是5.0.0
用以下命令更新StrongLoop:
```shell
$ npm install -g strongloop
```
## 清除旧的安装包
如果你在2014年8月6日之前安装的StrongLoop,键入以下命令来清楚久的安装包:
```shell
$ npm uninstall -g strong-cli
$ npm uninstall -g loopback-sdk-angular-cli
```
想知道为什么这样做?参考这篇博客[传送门](https://strongloop.com/strongblog/update-to-installer/ "https://strongloop.com/strongblog/update-to-installer/")

如果你运行这些命令出错,你可能需要使用`sudo`或者使用管理员身份打开命令行.你也可以手动删除strongloop的安装目录.

然后你可以重新安装StrongLoop:
```shell
$ npm install -g strongloop
```

## 清除当前安装包
如果你在2014年8月6日之后安装的StrongLoop,你需要清楚重新安装StrongLoop:
```shell
$ npm uninstall -g strongloop
$ npm cache clear
$ npm install -g strongloop
```

## 如果你的是StrongLoop 1.x版本
参考升级1.0到2.0章节

## 更新你的node.js
为了更新node.js版本,你只需要简单的重新在nodejs官网下载安装包,重新安装即可.