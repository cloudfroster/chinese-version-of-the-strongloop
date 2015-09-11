# 疑难问题
## 界面卡住
strongloop arc使用的是angular前端框架,因此有任何不工作的时候,检查命令行是否运行`slc arc`或者程序是否崩溃.

如果你得到`bad state`提示的话,可以试着清除cookies并删除本地存储条目,然后重启arc.

## Composer不可用
如果你不是从项目根目录运行的Arc,那么Composer将会是禁止使用的.

## Build & Deploy不可用
如果你不是从项目根目录运行的Arc,那么Build & Deploy将会是禁止使用的.

## 错误:没有`Access-Control-Allow-Origin`头
如果你打开API Explorer,但是出现下面的错误:
```shell
XMLHttpRequest cannot load http://localhost:3000/explorer/resources. 
No 'Access-Control-Allow-Origin' header is present on the requested resource. 
Origin 'http://localhost:55386' is therefore not allowed access. (index):1
Error: Cannot fetch Explorer metadata, the project is not running.
```
在你程序根目录运行`npm update`,然后重启Arc.

## 防火墙问题
如果你在公司的防火墙内使用Arc,你也许会遇到一些问题,参看[防火墙内使用Arc](https://docs.strongloop.com/display/SL/Using+Arc+inside+a+firewall "https://docs.strongloop.com/display/SL/Using+Arc+inside+a+firewall")

## License问题
参看[管理你的License]()