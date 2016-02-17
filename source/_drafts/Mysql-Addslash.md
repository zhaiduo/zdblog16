---
title: Mysql Addslash
id: 567
categories:
  - Mysql
tags:
---

select * from data where title='zhaiduo's test';

结果不同：
MySQL server version: 5.0.90-community: 没有匹配
MySQL server version: 4.1.20: 有找到

$mysql_version=substr(mysql_get_server_info(),0,1);
>5 escape twice