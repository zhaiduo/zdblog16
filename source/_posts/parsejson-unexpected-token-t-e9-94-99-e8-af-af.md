---
title: $.parseJSON Unexpected token t错误
tags:
  - Jquery
id: 2064
categories:
  - javascript
date: 2014-09-12 11:53:26
---

常见的原因是：双引号内的引号需要双重释义。例如："description":"Created for \"zhaiduo.com\""

验证json格式是否有问题，可以看这里：http://jsonlint.com/