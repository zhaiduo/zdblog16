---
title: 神秘的lightbox.js错误
tags:
  - 出错
id: 797
categories:
  - javascript
date: 2009-02-20 01:04:00
---

今天网站页面用IE(7&amp;8)突然都无法访问，弹出这样的错误窗口:
![](http://zhaiduo.googlepages.com/19320090220003846.jpg)
网页跟本无法打开，点击确定关闭错误窗口后，页面自动跳到空白页面。

用FireFox看，页面可以打开，但是Error Console里面有这样一个错误：
> Error: uncaught exception: Permission denied to call method Location.toString
经过对网页源代码的排查发现是lightbox代码的问题:
> script type="text/javascript" src="/css/prototype.js"
> script type="text/javascript" src="/css/scriptaculous.js?load=effects,builder"
> script type="text/javascript" src="/css/lightbox.js"
奇怪的是今天没有对lightbox代码进行过修改，真是很灵异的事件。