---
title: Windows下Mysql的Lost connection问题
id: 1387
categories:
  - Mysql
date: 2011-08-03 13:20:54
tags:
---

VPS的Windows下AMP环境，Mysql出现如下错误:

Error: Lost connection to MySQL server at 'reading initial communication packet', system error: 0

发现Mysql服务无法停止和启动，重新配置也无效。本以为网站打不开，后来发现网站打开很慢，但是ping正常。

最后发现C盘空间不足，一检查，原来是logfiles满了，清除后，一切正常。