---
title: Mysql主要版本特征
id: 326
categories:
  - 安装
  - 技术研究
date: 2006-10-26 15:12:07
tags:
---

mysql 3.23 (过时，如果你还在用，推荐升级，以提高性能)

*   首次推出innodb类型的数据表
*   inner joins和的outer joins部分支持
*   不支持union
mysql 4.0

*   完全支持union用法
*   完全支持inner和outer joins
*   升级myisam表，代替了旧的isam表
*   增加查询缓存。
mysql 4.1

*   改善password hashing
*   Unicode(UTF8)多国语言支持
*   支持子查询
*   新功能：CREATE TABLE table LIKE table 快速复制一个table
*   OpenSSL支持
[ mysql 5.0](http://dev.mysql.com/doc/refman/5.0/en/mysql-5-0-nutshell.html)

*   database, table, and column的名称支持多国语言
*   支持存储过程
*   事件触发
*   视图
*   `VARCHAR长度可以超过255限制到`65,532字节`
`
*   增加Bit数据类型
*   服务器端指针，用于存储过程和函数。
*   INFORMATION_SCHEMA方便查询数据库，表格，字段，类型权限等资料。
mysql 5.1 (beta版)

*   [分区](http://www.mysqlpress.com/doc/refman/5.1/zh/partitioning.html)
*   事件安排，类似crontab
*   Pluggable Storage Engine  				API
*   Row-Based Replication