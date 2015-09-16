# 调试应用程序

## 概述
使用node Inspector(用`slc debug`命令调用)来调试node应用程序.Node Inspector允许你:
- 设置断点(特殊触发条件),禁止/允许所有断点.
- Step over, step in, step out, 和从新执行.
- 监视作用域,变量,和对象属性.
- 通过移动鼠标到上面,显示表达式的值.
- 编辑变量和对象属性.
- 异常退出.

## 先决条件
确保你安装了strongloop管理器.
注意:Node Inspector当前只能在谷歌chrome和opera浏览器中运行.如果你不是用的这些,重新再这些浏览器中打开node inspector.

## 启动调试器
使用下面的命令来启动调试器:
```shell
$ slc debug
```
这个命令启动node Inspector并在你的默认浏览器中打开 http://localhost:8080/debug?port=5858

注意:默认状况下,slc debug在一开始会暂停程序执行.你需要在node Inspector恢复执行.

`slc debug`命令提供了一系列选项.

如果你不想用`slc debug`命令运行应用程序.你可以用node --debug-brk命令来停止程序执行.这允许你设置断点,调试程序.
![https://docs.strongloop.com/download/attachments/3834805/node-inspector-initial.png?version=1&modificationDate=1405037077000&api=v2](https://docs.strongloop.com/download/attachments/3834805/node-inspector-initial.png?version=1&modificationDate=1405037077000&api=v2)

## 调试一个运行中的程序
为了能调试一个运行中的程序:
1. 得到node进程的PID,例如:
```shell
$ pgrep -l node
2345 node your/node/server.js
```
2. 传递USR1信号
```shell
$ kill -s USR1 2345
```
注意:windows不支持UNIX信号,所以你需要用不同的技术.