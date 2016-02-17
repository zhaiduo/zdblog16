---
title: Javascript与swf对象交互的问题
tags:
  - swf
id: 795
categories:
  - AS3
  - javascript
date: 2009-02-10 16:51:00
---

在网页中通过flash来登录页面的时候，会涉及到Javascript与swf对象的交互问题。主要考虑的问题在于做到网页上的登录状况需要与swf里面的登录状况同步一致。AS里面的ExternalInterface包帮助我们解决这个问题，主要用法包括：

从Javascript发送数据到AS中的公开函数：
ExternalInterface.addCallback("JsFunc", AsFunc);

在AS中向Javascript函数传递数据。
ExternalInterface.call("JsFunc", AsData);

假设swf对象的id为zhaiduo,则可以这样来调用AS中的公开函数：
> mc('zhaiduo').JsFunc(blahs...);
> function mc(movieName) {
> if (navigator.appName.indexOf("Microsoft") != -1) {
> return window[movieName];
> } else {
> return document[movieName];
> }
> }
交互过程中意外遇到一个有趣的Javascript现象：
> if (navigator.appName.indexOf("Microsoft") != -1) {
> document.location.href="http://www.zhaiduo.com";  //IE8用reload无效
> }else{
> document.location.reload(); //FF2用href无效
> }