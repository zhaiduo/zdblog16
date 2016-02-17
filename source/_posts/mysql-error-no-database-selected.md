---
title: 'Mysql Error: No database selected'
tags:
  - 出错
id: 267
categories:
  - Mysql
date: 2008-04-22 12:46:25
---

一个网站的mysql数据库(Server version: 4.1.22-standard; MySQL client version: 4.1.22)的负担太重被空间商临时关闭了账号。恢复后出现了一个令人啼笑皆非的错误：Mysql Error: No database selected。检查数据库的用户名和密码以及数据库名称并没有异常。联系空间商，他们也说没有暂停mysql账号。再检查所有文件的完整性，也一切正常。这就奇了怪了哦！根据[webdeveloper论坛](http://www.webdeveloper.com/forum/archive/index.php/t-98090.html)上的解释：
> the database was not selected because the user did not have permission to select it. 应该是mysql账号的权限无法读取数据库。
郁闷的是为什么mysql账号没有权限会出现“No database selected”的错误，给人错误的指引和误导。而不是提示“No permissions for that database”。或者是有什么没有遇见过的特殊情况，继续跟进中。。。

更新：暂时解决办法：放弃旧账号，创建新账号，问题解决。