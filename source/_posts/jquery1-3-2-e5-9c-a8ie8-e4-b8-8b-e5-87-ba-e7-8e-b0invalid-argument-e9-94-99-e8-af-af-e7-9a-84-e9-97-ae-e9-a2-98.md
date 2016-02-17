---
title: jQuery1.3.2在IE8下出现“Invalid Argument”错误的问题
tags:
  - Jquery
  - 出错
  - 办法
id: 807
categories:
  - javascript
date: 2009-05-08 15:47:00
---

今天给博客页头加了一个动画效果（鼠标点击会更换页头背景），用的是jQuery1.3.2，FireFox下一切正常，但是IE8出现"line: 4166 Invalid Argument"的错误：
![](http://zhaiduo.googlepages.com/MWSnap288.jpg)

原因不详，临时解决办法如下：
> fx.elem.style[ fx.prop ] = fx.now + fx.unit;
改为:
> if(fx.prop &amp;&amp; fx.unit &amp;&amp; fx.elem &amp;&amp; fx.now){
> fx.elem.style[ fx.prop ] = fx.now + fx.unit;
> }