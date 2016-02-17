---
title: 网页在GreenBrowser下的兼容问题
tags:
  - CSS
  - 兼容性
id: 592
categories:
  - 杂项
date: 2010-05-26 23:16:48
---

从没用过GreenBrowser，但是没想到它有这么烦人。
没办法，客户要求用GreenBrowser浏览网站没问题，但是偏偏遇到只有它才有的问题：
1\. 页面右边多出一页的空白：最外层table不要用align="left"
2\. 恼人的空白：一对td标签内部最好不要有换行

[![](http://www.zhaiduo.com/wp-content/uploads/2010/05/greenbrowser_sucks.jpg "greenbrowser_sucks")](http://www.zhaiduo.com/wp-content/uploads/2010/05/greenbrowser_sucks.jpg)

3\. 页面右边多出一页的空白：Body标签内最好包上一个DIV，并设置width:100%;overflow:hidden;