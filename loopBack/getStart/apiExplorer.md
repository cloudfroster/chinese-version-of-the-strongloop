# 使用API Explorer
## 先决条件
- 安装了strongloop
- 阅读了loopback核心概念

你可能并不是唯一一个使用你刚才创建api的人.这意味着,你将需要为你的API写文档,Loopback生成器将为你提供API explorer.

提示:如果你是从创建简单API阅读过来的,保持程序运行并跳读到运行API explorer.如果你是跳读到这里的,跟随下面的操作步骤:
```shell
$ git clone https://github.com/strongloop/loopback-getting-started.git
$ cd loopback-getting-started
$ git checkout step1
$ npm install
```

## 运行API Explorer
运行程序
```shell
$ node .
```
现在进入 http://localhost:3000/explorer. 你将看见StrongLoop API Explorer显示的2个模式: Users 和 CoffeeShops:
![https://docs.strongloop.com/download/attachments/3836324/API%20Explorer.png?version=1&modificationDate=1418940635000&api=v2](https://docs.strongloop.com/download/attachments/3836324/API%20Explorer.png?version=1&modificationDate=1418940635000&api=v2)

CoffeeShop模型是你定义的,User模型是loopback默认生成的.

## 关于Loopback内置模型
实际上,Loopback创建了几个其他的内置模型:
- Application模型
- User模型 注册和验证你的程序或第三方服务
- Access control模型 ACL AccessToken,Scope,Role和RoleMapping模型
- Email模型 用SMTP或者第三方服务来为用户发送电子邮件

内置模型(除了Email)继承自PersistedModel,所有他们自动拥有全套增加,更新和删除操作(CRUD).

提示:默认只有User模型通过REST暴露.为了暴露其他的模型,改变模型的public属性为true在server/model-config.json文件里.使用小心,暴露公有API可能会有安全风险.

## 探索CoffeeShop模型
现在,仔细深入的探索下CoffeeShop模型,点击CoffeeShop来显示所有API接口.
![https://docs.strongloop.com/download/attachments/3836324/gs-first-api-explorer.png?version=1&modificationDate=1418940676000&api=v2](https://docs.strongloop.com/download/attachments/3836324/gs-first-api-explorer.png?version=1&modificationDate=1418940676000&api=v2)

初看api接口,你将看见他们包含了一些通过创建,读,更新,删除操作(CRUD)和一些其他的.

点击第一行, POST /CoffeeShops Create a new instance of the model and persist it into the data source来展开这些操作:
![https://docs.strongloop.com/download/attachments/3836324/gs%20api%20exp%20use1.png?version=1&modificationDate=1418940748000&api=v2](https://docs.strongloop.com/download/attachments/3836324/gs%20api%20exp%20use1.png?version=1&modificationDate=1418940748000&api=v2)

遵循上图中的步骤.

点击模型Schema来得到JSON数据模板,你可以在data文本框中编辑.

增加一些文字到name属性.你不需要添加id属性.因为loopback将自动管理它来确保这将一直是唯一的ID对于每个模型实例.
```shell
{
  "name": "My Coffee Shop",
  "id": 0
}
```
然后点击try it out按钮.

你将看见REST请求和相应(例如):
![https://docs.strongloop.com/download/attachments/3836324/gs%20api%20exp%20response.png?version=1&modificationDate=1418940788000&api=v2](https://docs.strongloop.com/download/attachments/3836324/gs%20api%20exp%20response.png?version=1&modificationDate=1418940788000&api=v2)

这个Response Body字段将显示你刚刚键入的数据来确保数据已经增加到了数据源.

现在点击GET /CoffeeShop来展开接口.点击try it out!来得到你键入的CoffeeShop模型.你将看见你通过POST接口创建的数据.

如果你有这份心思,试试其他的请求:你能通过Query data来过滤特殊的数据.

提示:你可能已经注意到了accessToken字段和Set Access Token按钮在API Explorer窗口的右上角.使用这些对用户进行身份验证,并“登录”应用程序来执行需要身份验证操作.