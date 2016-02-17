---
title: 关于GBK通过UTF8保存到Mysql的搜索问题
tags:
  - 搜索
  - 问题
id: 1440
categories:
  - Mysql
  - PHP
date: 2011-11-24 02:02:05
---

Mysql的全局字符是latin1，数据源是GBK，通过UTF8客户端存入Mysql的UTF8编码表中。

在PHP中用GBK的UTF8数据源作为关键字，搜索latin1编码的UTF8表的时候，发现无法匹配关键字。

解决办法是set names gbk获得关键字，然后用set names latin1来进行utf8搜索。