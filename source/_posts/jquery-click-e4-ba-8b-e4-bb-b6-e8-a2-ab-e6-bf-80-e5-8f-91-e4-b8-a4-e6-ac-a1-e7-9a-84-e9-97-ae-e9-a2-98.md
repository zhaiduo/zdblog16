---
title: Jquery Click事件被激发两次的问题
tags:
  - Jquery
  - 问题
id: 1436
categories:
  - javascript
date: 2011-11-11 03:24:15
---

今天遇到Jquery Click事件被激发两次的奇怪的现象，HTML代码很简单：

&lt;a href="javascript:void(0);" id="add"&gt;&lt;img src="add.png" border=0"&gt; Add&lt;/a&gt;

在Javascript中使用click事件

$(document).ready(function() {

$('#add').click(function() {alert('ok');});

});

点击后发现alert了两次。寻思了很久，不得其所。网上搜索暂时有如下解决办法：

$('#add').unbind('click').click(function() {});

难道今天是两个1，alert也要闹节吗？囧～