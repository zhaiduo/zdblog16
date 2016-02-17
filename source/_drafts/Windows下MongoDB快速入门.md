---
title: Windows下MongoDB快速入门
tags:
  - mongodb
id: 1568
categories:
  - NoSQL
---

**数据保存**
MongoDB默认将数据存储在 安装目录所在盘的/data/db 目录下

**常用管理命令**
DOS CMD窗口里启动：C:my_mongo_dirbin &gt; mongod
安全启动：mongod --auth
切换数据库：use videos
显示管理员：db.system.users.find()
登录：db.auth('zhaiduo', 'password')
添加管理员：db.addUser('zhaiduo', 'password')

**[常用数据库操作命令](http://www.mongodb.org/display/DOCS/SQL+to+Mongo+Mapping+Chart):
**建表：db.createCollection("mytable")
插入：db.users.insert({a:3,b:4})
查询指定字段：db.users.find({}, {a:1,b:1}) =》 SELECT a,b FROM users
返回所有行：db.users.find()
搜索：db.users.find({age:34})
排序：db.users.find({age:34}).sort({name:1})
条件选择：db.users.find({age:{$gt:34}})
匹配搜索：db.users.find({name:/^Zhaiduo/})
有限返回：db.users.find().limit(10).skip(20)
排序：db.bios.find().sort( { name: 1 } )
返回一个记录：db.users.findOne()
过滤重复：db.users.distinct('last_name')
计数：db.users.count()
添加索引：db.users.ensureIndex({name:1})
更新：db.users.update({b:'q'}, {$set:{a:1}}, false, true)
删除：db.users.remove({z:'abc'});

**数据备份**
A simple approach is just to stop the database, back up the data files, and resume.
[导入](http://www.mongodb.org/display/DOCS/Import+Export+Tools)：mongoimport -d test -c foo importfile.json
导出：mongodump --host prod.example.com, mongodump --db blog --collection posts,
mongodump --db blog --collection posts --out - &gt; blogposts.bson

**与Mysql[对比](http://docs.mongodb.org/manual/reference/sql-comparison/)：**

table     collection
row     BSON document
column     BSON field
join     embedding and linking
primary key     _id field
group by     aggregation

**技巧：**
分页：
var min_page = NUMBER_OF_ITEMS * (PAGE_NUMBER - 1)
var max_page = min_page + NUMBER_OF_ITEMS
db.companies.find().min({_id:min_page}).max({_id:max_page})
分页二：
var skip = NUMBER_OF_ITEMS * (PAGE_NUMBER - 1)
db.companies.find({}, {$slice:[skip, NUMBER_OF_ITEMS]})

故障：
如果启动服务器出现错误：
**************
Unclean shutdown detected.
Please visit http://dochub.mongodb.org/core/repair for recovery instructions.
*************
看看/data/db 目录下是否有mongod.lock，删除即可。