# 创建一个新的API
## 创建一个新的loopback程序.
如果你已经有了loopback程序,可以跳过.

为了创建一个新的loopback程序,你可以使用loopback应用程序生成器:
```shell
$ slc loopback
```
跟着提示一步步创建应用程序.

## 运行StrongLoop Arc
在你应用程序的根目录,用下面的命令启动strongloop Arc:
```shell
$ cd my-loopback-application
$ slc arc
Arc is running here: http://localhost:51230
```
StrongLoop Arc将打开默认浏览器,你会看见登录页面.
提示:StrongLoop Arc每次启动都用的随机端口,如果你想要Arc运行在固定的端口.可以采用下面的命令:
```shell
$ PORT=4800 slc arc
Arc is running here: http://localhost:4800
```