---
title: Redis使用小结
tags:
  - redis
id: 2256
comment: false
categories:
  - NoSQL
---

Redis功能强大，足以完全替换Mysql+Memcache。
主要数据类型包括：字符、List、Set、有序Set、Hash。

有序Set、Hash比较常用，配合sort命令可以秒杀Mysql的常规展示功能。

充分利用管道一次执行多行命令，set集合不允许重复内容的特性，可以打造高效快速计数器。

`$list[]=array('sadd',array($prefix,$keyName));
//初始化API计数器值为0
$list[]=array('setnx',array($keyName,0));
//自增
$list[]=array('incr',array($keyName));`

常用Mysql命令转换成redis：

总数：

分页：

标签：

类别：