# 从数据库映射模型
####先决条件:
1. 安装了strongLoop
2. 会使用Arc

StrongLoop Composer的discovery特性能让你简单从存在的数据库中创建模型.跟随这些步骤:
1. 创建一个连接你数据库的数据源,提供数据库服务器认证信息(用户名,密码等).
2. 用Test Connection来测试能连接到你的数据库.
3. 在导航面板点击下拉菜单,然后点击discover models.
![https://docs.strongloop.com/download/attachments/4557562/discovery1.png?version=1&modificationDate=1415753534000&api=v2](https://docs.strongloop.com/download/attachments/4557562/discovery1.png?version=1&modificationDate=1415753534000&api=v2)
4. composer将列出数据库,像下面展示的一员,你想创建的模型,或者选择Select All来创建模型,然后点击Next.
![https://docs.strongloop.com/download/attachments/4557562/discovery2.png?version=1&modificationDate=1415753534000&api=v2](https://docs.strongloop.com/download/attachments/4557562/discovery2.png?version=1&modificationDate=1415753534000&api=v2)
5. composer将列出每个你选择的表格的列,取消你不想要的列,然后点击Next.
![https://docs.strongloop.com/download/attachments/4557562/discovery3.png?version=1&modificationDate=1415753534000&api=v2](https://docs.strongloop.com/download/attachments/4557562/discovery3.png?version=1&modificationDate=1415753534000&api=v2)
注意:一般来说,不取消主键唯一地标识表中的行.loopback中的每个模型需要一个具有独特的价值的ID属性.

Composer将根据数据库的表和列创建相应的模型和属性.然后在模型编辑器中展示他们,例如:
![https://docs.strongloop.com/download/attachments/4557562/discovery4.png?version=2&modificationDate=1433894005000&api=v2](https://docs.strongloop.com/download/attachments/4557562/discovery4.png?version=2&modificationDate=1433894005000&api=v2)