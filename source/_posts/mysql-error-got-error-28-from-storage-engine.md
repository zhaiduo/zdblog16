---
title: 'mysql error: Got error 28 from storage engine'
tags:
  - 出错
id: 1815
categories:
  - Mysql
date: 2013-06-14 19:16:59
---

平时的程序都没问题，突然无法打开，提示mysql error: Got error 28 from storage engine。根据[stackoverflow的解答](http://stackoverflow.com/questions/10513887/mysql-database-got-error-28-from-storage-engine-while-accessing-from-webmin)，是系统盘的空间不够啦，一看确实只有10M。清理磁盘后，问题解决。