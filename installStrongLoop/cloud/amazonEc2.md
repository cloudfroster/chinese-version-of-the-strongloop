# Amazon EC2
- 启动一个StrongLoop AWS实例
- 连接到AWS实例

## 启动一个StrongLoop AWS实例
StrongLoop已经提供了Amazon Machine Image(AMI)预安装了Node,loopBack和slc命令行工具.在[Amazon Marketplace](https://aws.amazon.com/marketplace/)里搜索"strongloop"或者直接进入[https://aws.amazon.com/marketplace/pp/B00PG9I0M0/](https://aws.amazon.com/marketplace/pp/B00PG9I0M0/ "https://aws.amazon.com/marketplace/pp/B00PG9I0M0/").

## 连接到AWS实例
一旦启动你的AWS实例,你能用ssh登录:
```shell
ssh -i /full/path/private-key.pem ec2-user@01.23.45.67
```
- /full/path/private-key.pem指定的私钥文件的路径
- 01.23.45.67是你实例的IP地址
- 确保用的用户名是`ec2-user`

当你登录进入,设置目录权限:
```shell
$ sudo chown -R $USER /usr/local
```
然后,确保你的stroopLoop是最新的:
```shell
$ slc update
```
注意:当命令行打印http://0.0.0.0:3000/访问的时候,你需要用你AWS的IP地址来代替.