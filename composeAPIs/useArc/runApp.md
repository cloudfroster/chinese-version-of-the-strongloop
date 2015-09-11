# 运行应用程序
跟随使用arc一章运行arc并且登录arc.

使用`Arc App Controller`来运行应用程序.
你的应用程序必须满足下面的条件之一:
- 根目录有`server.js`,`app.js`或者'index.js'命令的脚本文件.
- 根目录package.json的main属性有启动程序的脚本.

为了启动loopback程序:
1. 点击页面右上角的播放状按钮,大脑App Controller面板.
2. 点击'Start'按钮,启动应用程序
![https://docs.strongloop.com/download/thumbnails/6717558/arc%20app%20controller.png?version=1&modificationDate=1433800481000&api=v2](https://docs.strongloop.com/download/thumbnails/6717558/arc%20app%20controller.png?version=1&modificationDate=1433800481000&api=v2 "https://docs.strongloop.com/download/thumbnails/6717558/arc%20app%20controller.png?version=1&modificationDate=1433800481000&api=v2")
当应用程序启动成功后,会显示为'RUNNING',默认启动本机路径在`http://localhost:3000/`

点击`Stop`来停止应用程序.

你能从命令行看到一些有用的提示,比如:
```shell
Browse your REST API at http://localhost:3000/explorer
Web server listening at: http://localhost:3000/
```
应用程序停止后,可以点击`Restart`来重新启动应用程序.