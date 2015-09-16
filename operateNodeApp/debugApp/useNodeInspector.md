# 用node inspector

## 概述
node检查器是基于Chrome开发的工具,因此用它调试一个node应用程序类似于在Chrome调试客户端的JavaScript.

node检测器加载并解析文件,然后自动加入GUI.

## 设置断点
为了设置一个应用程序断点:
1. 点击`show Navigator`图标.
![https://docs.strongloop.com/download/thumbnails/3834805/set%20breakpoint.png?version=1&modificationDate=1405037077000&api=v2](https://docs.strongloop.com/download/thumbnails/3834805/set%20breakpoint.png?version=1&modificationDate=1405037077000&api=v2)

2. 找到你想要的javascript文件,双击打开它.
3. 点击你想设置断点的行号.设置的断点node检测器会高光成蓝色.
![https://docs.strongloop.com/download/attachments/3834805/set%20breakpoint%202.png?version=1&modificationDate=1405037077000&api=v2](https://docs.strongloop.com/download/attachments/3834805/set%20breakpoint%202.png?version=1&modificationDate=1405037077000&api=v2)
按F10执行下一步,按F8重新执行.

## 断点和捕获异常
node检查器会在你重启应用程序的时候存储断点,把断点保存在浏览器的local storage(HTML5)里面.当你重启调试器或者几天后重新调试相同的程序.node检查器会恢复断点.

你也能捕获异常.node检查器也提供域名集成.这个特性需要node.js版本大于或等于v0.11.3.

## 在文件中设置断点
node检查器能让你在文件中设置断点.

## 显示和编辑变量
鼠标放在变量上能显示和编辑变量,就像下面的图一样:
![https://docs.strongloop.com/download/thumbnails/3834805/node-inspector-edit-var2.png?version=1&modificationDate=1405037077000&api=v2](https://docs.strongloop.com/download/thumbnails/3834805/node-inspector-edit-var2.png?version=1&modificationDate=1405037077000&api=v2)

## 支持source maps
node检查器支持source maps.
![https://docs.strongloop.com/download/attachments/3834805/node-inspector-source-maps.png?version=1&modificationDate=1405037077000&api=v2](https://docs.strongloop.com/download/attachments/3834805/node-inspector-source-maps.png?version=1&modificationDate=1405037077000&api=v2)

## 重新执行函数(Restart Frame)
在右边栏中右键单击调用框架(堆栈Frame),选择"Restart Frame"命令来重新执行当前函数.
