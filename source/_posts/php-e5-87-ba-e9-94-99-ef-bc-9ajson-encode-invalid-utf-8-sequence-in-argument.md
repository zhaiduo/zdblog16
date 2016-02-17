---
title: 'PHP出错：json_encode: Invalid UTF-8 sequence in argument'
id: 2263
comment: false
categories:
  - PHP
date: 2015-03-19 23:55:52
tags:
---

json打包出错：

json_encode(): Invalid UTF-8 sequence in argument

解决办法：检测非法UTF8

mb_check_encoding($strs,'UTF-8')

然后

mb_convert_encoding($strs,'UTF-8','UTF-8');

即可保证不会出现Invalid UTF-8的错误，但是可能结果字符串中会有问号等乱码。