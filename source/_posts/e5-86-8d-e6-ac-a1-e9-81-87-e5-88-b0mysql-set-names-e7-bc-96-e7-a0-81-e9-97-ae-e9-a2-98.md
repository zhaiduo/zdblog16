---
title: 再次遇到Mysql set names编码问题
tags:
  - 编码
  - 问题
id: 1450
categories:
  - Mysql
  - PHP
date: 2011-12-11 03:52:50
---

最近和编码挺有缘的，升级Mysql数据库又遇到set names编码问题。老的数据库是latin1，数据是GB2312，新的数据库是utf8，数据表也是utf8。通过PHPMYADMIN导入新数据库后，set names utf8后，数据仍为乱码。

后来发现因为老的数据库是latin1，所以应该是set names latin1，而数据表是utf8，但是数据仍为GB2312，所以网页应该是GBK编码。问题解决。

[![](http://www.zhaiduo.com/wp-content/uploads/2011/12/luanma.jpg "luanma")](http://www.zhaiduo.com/wp-content/uploads/2011/12/luanma.jpg)