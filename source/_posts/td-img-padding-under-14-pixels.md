---
title: 表格TD内高度14像素以下图片的空白问题
tags:
  - 问题
id: 1445
categories:
  - CSS
date: 2011-11-29 20:48:49
---

在做网页的时候发现表格的TD内如果只放高度比较小的图片，网页上td图片上方将出现一行多余的空白。用FF3和IE8均发现这个问题。经测试高度小于14像素的图片才会出现空白。在TD上和CSS定义TD的高度和图片一致，均不能解决问题。

[![](http://www.zhaiduo.com/wp-content/uploads/2011/11/13620111129203320.jpg "13620111129203320")](http://www.zhaiduo.com/wp-content/uploads/2011/11/13620111129203320.jpg)

一般认为问题应该是处在行距上，但是line-height和font-size为0，还是不能解决问题。既然图片高度变化可以影响这个空白，问题应该在图片身上。经测试display:block给图片，问题解决。

更新：发现排队的DIV也有这个问题，不过只是在IE下，float:left可以解决。