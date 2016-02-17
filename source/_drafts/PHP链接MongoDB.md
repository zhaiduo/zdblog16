---
title: PHP链接MongoDB
tags:
  - mongodb
id: 2162
categories:
  - PHP
---

版本PHP5.4.35，windows7 64位

先安装mongoDB，可以把mongo bin的路径加入环境变量
再下载php_mongo.dll
https://s3.amazonaws.com/drivers.mongodb.org/php/index.html
推荐下载：php_mongo-1.5.7-5.4-vc9.dll ，放入ext目录。
ini增加 extension=php_mongo-1.5.7-5.4-vc9.dll.

启动服务器：
新建目录mongod, cd mongd

mongod --auth --dbpath e:mongod
允许本地无账号密码，可以访问数据库，安全模式会有一个admin特殊的数据库

--config e:mongodmongodb.conf YAML格式 不支持utf格式

链接服务器：
输入命令：mongo
use admin //添加系统管理员
db.addUser("admin", "admin新密码");//添加用户admin
db.auth("admin", "admin新密码");//授权用户admin为管理员

use test//添加数据库管理员
db.addUser("adam", "adam新密码2");//添加用户adam
db.auth("adam", "adam新密码2");//授权用户adam为管理员

然后安全连接数据库：
mongo test -u adam -p adam新密码2 --host localhost --port 27017
////test数据管理员adam:linry    系统:admin:adam