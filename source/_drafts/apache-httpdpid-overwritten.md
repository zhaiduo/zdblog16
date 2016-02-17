---
title: Apache出错：httpd.pid overwritten - Unclean shutdown
tags:
  - Apache
id: 1265
categories:
  - 网站维护
---

windows7下Apache2.2重启的时候，切换PHP5.2.1.7到5.3.1出现如下错误：

httpd.pid overwritten -- Unclean shutdown of previous Apache run?

重启系统错误依旧，原来系统环境变量PATH里面还有5.2.1.7的路径。