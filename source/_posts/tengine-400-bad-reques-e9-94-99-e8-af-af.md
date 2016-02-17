---
title: Tengine 400 Bad Reques错误
tags:
  - Nginx
  - tengine
  - web server
id: 2344
comment: false
categories:
  - Linux/Unix
date: 2015-04-22 16:30:30
---

tengine在合并javascript文件时，nginx返回400错误，百思不得其解。
原来是tengine：
默认只有text/css application/x-javascript

增加concat_types "application/javascript";即可。...