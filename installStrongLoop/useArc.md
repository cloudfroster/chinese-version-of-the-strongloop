# 防火墙内使用Arc
## 设置代理服务器上的环境变量
设置HTTP_PROXY 或者 HTTPS_PROXY环境变量到代理服务器用以下的命令格式:
```shell
HTTPS_PROXY=https://proxy.bigco.com:8443
```
StrongLoop代理将按照下面的顺序搜索环境变量的值,并且使用第一个搜索到的值:
- https_proxy
- HTTPS_PROXY
- http_proxy
- HTTP_PROXY

# 格式化
用以下格式指定环境变量的值作为一个完整的URL:
```shell
protocol://username:password@host:port
```
举个例子:
```shell
https://proxy.bigco.com:8443/
```
依赖你的网络配置,你也可以用一部分域名.例子如下:
```shell
https://proxy:8443
```
如果代理服务器需要认证,你可以提供用户名和密码:
```shell
https://johndoe:mypassword@proxy.bigco.com/
```