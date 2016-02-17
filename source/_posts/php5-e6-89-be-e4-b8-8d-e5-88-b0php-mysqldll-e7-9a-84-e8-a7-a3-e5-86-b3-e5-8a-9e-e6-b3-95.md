---
title: PHP5找不到php_mysql.dll的解决办法
id: 323
comment: false
categories:
  - 安装
date: 2006-10-17 13:45:46
tags:
---

Windows下安装Apache2.0.59+PHP5.1.6成功后，log.error中出现下面的错误：
> php_mysql.dll the specified module could not be found
原因是PHP5不再支持默认的mysql.dll, 而是mysqli.dll，解决办法就是复制libmysql.dll(在php安装根目录)和php_mysql.dll(在ext目录里面)到系统目录的system32下面。