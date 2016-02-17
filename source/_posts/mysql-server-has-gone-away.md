---
title: MySQL server has gone away
id: 125
categories:
  - Mysql
  - 窄多废话
date: 2007-03-06 21:37:29
tags:
---

有个客户的记录特别长，在导入database的时候出现如下错误：
> >> mysql -u root -p target_db < target.sql
> >> MySQL server has gone away
问题出在单个记录长度超过mysql默认设定的长度1024，max_allowed_packet = 1M，加大长度，修改my.cnf问题得以解决：
> set-variable=max_allowed_packet=32M