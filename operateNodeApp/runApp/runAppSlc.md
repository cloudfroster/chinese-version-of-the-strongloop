# 用slc运行应用
使用StrongLoop Process Manager启动本地应用:
```shell
$ cd app-root-dir
$ slc start
```
app-root-dir是程序的根目录.

这将启动一个在StrongLoop Process Manager控制下的本地实例.如果PM无法启动应用程序,它将定期尝试启动应用程序,直到PM关闭.

StrongLoop PM 将显示一些有用的建议,还有一些日志信息,例如:
```shell
...
--- tail of /Users/rand/.strong-pm/start.log ---
slc start(32276): StrongLoop PM v5.0.49 (API v6.1.0) on port `8701`
slc start(32276): Base folder `/Users/rand/.strong-pm`
slc start(32276): Applications on port `3000 + service ID`
Run request for commit "default-app/local-directory" on current (none)
Start Runner: commit default-app/local-directory
2015-08-14T17:07:23.361Z pid:32289 worker:0 INFO strong-agent v1.6.54 profiling app 'default-app' pid '32289'
2015-08-14T17:07:23.368Z pid:32289 worker:0 INFO strong-agent[32289] started profiling agent
2015-08-14T17:07:23.369Z pid:32289 worker:0 INFO supervisor starting (pid 32289)
2015-08-14T17:07:23.374Z pid:32289 worker:0 INFO strong-agent strong-agent using strong-cluster-control v2.1.2
2015-08-14T17:07:23.377Z pid:32289 worker:0 INFO supervisor reporting metrics to `internal:`
2015-08-14T17:07:23.388Z pid:32289 worker:0 INFO supervisor size set to 1
2015-08-14T17:07:23.500Z pid:32289 worker:0 INFO supervisor started worker 1 (pid 32290)
2015-08-14T17:07:23.501Z pid:32289 worker:0 INFO supervisor resized to 1
2015-08-14T17:07:23.828Z pid:32290 worker:1 INFO strong-agent v1.6.54 profiling app 'default-app' pid '32290'
2015-08-14T17:07:23.832Z pid:32290 worker:1 INFO strong-agent[32290] started profiling agent
```
你也能从其他目录启动应用程序,例如,你的应用在myapp目录,你可以:
```shell
$ slc start myapp
```
可以使用`slc ctl`命令来查看应用状态,默认情况下显示本地运行的strongloop程序:
```shell
$ slc ctl
Service ID: 1
Service Name: myapp
Environment variables:
  No environment variables defined
Instances:
    Version  Agent version  Cluster size
     4.1.1       1.5.1            4
Processes:
        ID      PID   WID  Listening Ports  Tracking objects?  CPU profiling?
    1.1.48554  48554   0
    1.1.48557  48557   1     0.0.0.0:3001
    1.1.48563  48563   2     0.0.0.0:3001
    1.1.48565  48565   3     0.0.0.0:3001
    1.1.48566  48566   4     0.0.0.0:3001
```
myapp就是你的程序名字(这个名字默认是package.json文件中的name字段).

如果想查看日志,用下面的命令:
```shell
$ slc ctl log-dump myapp
```
如果PM没有成功启动应用程序,你可是更改源代码,PM将会自动尝试重新启动程序,你不需要再次输入`slc start`

可以用下面命令停止应用程序:
```shell
$ slc ctl stop myapp
```