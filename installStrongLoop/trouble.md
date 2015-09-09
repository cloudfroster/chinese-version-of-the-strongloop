# 安装疑难问题
## 确保你有最新版本的node
确保你的node版本是最新的,你可以到[https://nodejs.org/en/](https://nodejs.org/en/ "https://nodejs.org/en/")找到最新版本的node

## 卸载老的版本
如果你在2014年8月6日之前安装的StrongLoop,你需要卸载后重新安装.查看[更新到最新版本](updateLastedVersion.md)

## 确保你有目录的权限
- /usr/local/bin 
- /usr/local/lib/node_modules
如果你看下以下的错误
```shell
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/strongloop'
...
npm ERR! Please try running this command again as root/Administrator
...
```
那么说明你没有权限来创建文件或目录.你可以使用`sudo`命令,不过更加好的方式是取得目录权限:
```shell
$ sudo chown -R $USER /usr/local
```
这条命令让你的账号拥有/usr/local目录.如果你不得不用`sudo`命令,可以使用一下的方式:
```shell
$ sudo npm -g --unsafe-perm install strongloop
```

# windows问题
## 不支持Cygwin
LoopBack不支持Cygwin(windows bash shell模拟器),因为它不支持node的交互式编程.使用windows命令行(shell).

## 安装错误
如果你想在windows上安装LoopBack和slc LoopBack命令行工具,但是使用nmp install strongloop -g却安装出错了,你可以用下面的方法:
```shell
$ npm install -g yo
$ npm install -g generator-loopback
```
这样就用yo loopback代替了slc loopback.举个例子,yo loopback:model就可以建立模型了.需要更多信息,参考[http://yeoman.io/](http://yeoman.io/. "http://yeoman.io/")

# npm错误
## 依赖冲突
如果你遇到了依赖冲突,你需要手动到安装目录删除不需要的模块,然后重新安装.

## 防火墙问题
防火墙可能会阻塞git://URLs.你需要配置git使用HTTPS:
```shell
$ git config --global url."https://".insteadOf git://
```
参考[git阻塞,怎么安装npm模块(stackOverflow)](http://stackoverflow.com/questions/15903275/git-is-blocked-how-to-install-npm-modules "http://stackoverflow.com/questions/15903275/git-is-blocked-how-to-install-npm-modules").

## 从github安装模块
你可以从github clone源代码下来,如果是压缩文件就解压拷贝到node_modules文件夹.

## 安装国内的源
对于国内用户来说,安装国外的包速度不快,很容易安装失败,所以可以用淘宝的源来替换当前的安装源.参看[http://npm.taobao.org/](http://npm.taobao.org/ "http://npm.taobao.org/")

## 如果你仍然有问题
看了上面的说明,你仍然有问题的话,请发邮件到[callback@strongloop.com](callback@strongloop.com)寻求帮助.
请包括以下内容:
- 你的操作系统和版本
- 你用的node的版本(用node --version查看)
- 你用的npm的版本(用npm --version查看)
- 你采取了什么措施
- 错误提示或者堆栈跟踪
- 任何其他相关信息