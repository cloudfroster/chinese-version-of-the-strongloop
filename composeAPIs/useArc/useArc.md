# 使用Arc
注意:你可以使用Arc来构建或者发布,监控任何Node应用程序,但是创建api只能适用于loopback应用程序.

## 启动Arc
在项目的根目录运行下面的命令:
```shell
$ slc arc
```

## 登录Arc
Arc功能需要注册才能使用(免费的),所以你将会看见登录框:
![https://docs.strongloop.com/download/attachments/5308533/arc-login.png?version=1&modificationDate=1433453826000&api=v2](https://docs.strongloop.com/download/attachments/5308533/arc-login.png?version=1&modificationDate=1433453826000&api=v2 "https://docs.strongloop.com/download/attachments/5308533/arc-login.png?version=1&modificationDate=1433453826000&api=v2")
如果你已经有了strongloop账号,登录即可,如果没有,点击`register`按钮注册一个账号.

登录strongloop后,你将会看见下面的页面:
![https://docs.strongloop.com/download/attachments/5308533/arc-splash-tracing.png?version=2&modificationDate=1432768173000&api=v2](https://docs.strongloop.com/download/attachments/5308533/arc-splash-tracing.png?version=2&modificationDate=1432768173000&api=v2 "https://docs.strongloop.com/download/attachments/5308533/arc-splash-tracing.png?version=2&modificationDate=1432768173000&api=v2")
试着点击下每个模块.

## 退出Arc
在你启动strongLoop的命令行,键入`Ctrl-C`即可.

## Arc创作器一览
点击`composer`就能登录composer面板:![https://docs.strongloop.com/download/attachments/5308533/arc_atlas.png?version=1&modificationDate=1433454665000&api=v2](https://docs.strongloop.com/download/attachments/5308533/arc_atlas.png?version=1&modificationDate=1433454665000&api=v2 "https://docs.strongloop.com/download/attachments/5308533/arc_atlas.png?version=1&modificationDate=1433454665000&api=v2")

## 离线使用Arc
Arc以一个单页应用程序运行,但是它需要一些网络连接的功能,比如登录认证.Arc在你每次登录的时候,会把cookies存入你的浏览器,目前cookies有效期是两周.

所以,一旦你有一个有效的cookie,你就能离线使用Arc.Arc还会记录你退出时候的页面,下次进来就能看见了.