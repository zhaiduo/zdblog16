---
title: 二个Mysql错误
tags:
  - 出错
id: 778
categories:
  - Mysql
date: 2008-12-10 13:48:00
---

第一个错误：
> Database Error!
> You have an error in your SQL syntax near '; ' at line 1,
MySQL server version: 3.23.58 | PHP version: 4.3.2
原因：SQL语句最后";"分号后面多了一个空格：
> where id='$id'; ";
第二个错误：
> Error msg: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 104
> Mysql Errors:
> Lost connection to MySQL server at 'reading initial communication packet', system error: 104
系统自动恢复，原因不明。