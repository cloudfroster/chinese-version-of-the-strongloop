# 性能分析
StrongLoop工具允许分析本地和远程的node程序.你可以:
- 用Arc分析本地或者远程的程序
- 用slc分析本地程序

## 使用strongloop分析器演示程序
strongLoop演示程序是简单的loopback程序用来显示cpu和堆的分析.

例子程序包含了2个post请求:
- POST /documents - 创建多个实例文档对象和热cpu.使用cpu分析器查看cpu使用率.
- POST /documents/content - 增加文档计数,使用堆分析器查看对象数量.

## 安装演示程序
从github安装演示程序:
```shell
$ git clone https://github.com/strongloop/profiler-demo-app.git
```

## 实施监控
运行程序:
```shell
$ slc start
```
然后显示应用程序状态,确保应用程序运行.
```shell
$ slc ctl
```
你应该看见这样的东西:
```shell
Service ID: 1
Service Name: profiling-app
Environment variables:
  No environment variables defined
Instances:
    Version  Agent version  Cluster size
     4.1.1       1.5.1            4
Processes:
        ID      PID   WID  Listening Ports  Tracking objects?  CPU profiling?
    1.1.63264  63264   0
    1.1.63267  63267   1     0.0.0.0:3001
    1.1.63268  63268   2     0.0.0.0:3001
    1.1.63269  63269   3     0.0.0.0:3001
    1.1.63270  63270   4     0.0.0.0:3001
```
现在,运行load脚本:
```shell
$ node loadtest.js
```
你能通过使用slc ctl和谷歌chrome工具搜集cpu和堆相关信息.
例如,分析第一个工作进程的CPU消耗:
```shell
$ slc ctl cpu-start 1
Profiler started, use cpu-stop to get profile
```
然后,几秒后,停止分析cpu:
```shell
$ slc ctl cpu-stop 1
CPU profile written to `node.1.cpuprofile`, load into Chrome Dev Tools
```
分析堆内存消耗:
```shell
$ slc ctl heap-snapshot 1
slc ctl heap-snapshot 1
Heap snapshot written to `node.1.heapsnapshot`, load into Chrome Dev Tools
```