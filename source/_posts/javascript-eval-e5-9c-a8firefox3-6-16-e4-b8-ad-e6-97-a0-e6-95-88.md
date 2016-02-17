---
title: Javascript Eval在Firefox3.6.16中无效
tags:
  - FireFox
id: 1336
categories:
  - javascript
date: 2011-03-26 16:01:01
---

最近重装系统，也升级Firefox3.6.16，到刚发现Javascript调用 eval居然出错l，找不到eval返回的对象。

例如：obj=eval("document.form.item_"+i);

使用DOM对象则一切正常：document.form[i]

在网上搜索了一下，发现只有Firefox有这个问题。但是没有找到官方的说明。Mozilla确实鼓励大家[不要使用Eval](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/eval)，特别是在[json](https://developer.mozilla.org/en/json#Quick_Warning)的使用中。

但是不清楚，Firefox是什么时候禁用eval的。