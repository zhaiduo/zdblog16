---
title: 关于prototype中$相关Function的说明
id: 314
categories:
  - javascript
  - 技术研究
date: 2006-09-16 12:01:37
tags:
---

> **$() 替代简写document.getElementById()，可以同时返回多个id。**
> 
> var zhaiduo = $('DivA');
> 
> var zhaiduos = $('DivA','DivB');
> 
> **$F() 返回表单中任何元素的值，如text, button, select, texarea等。**
> 
> $F('Form_text')
> 
> // &lt;input type="text" id="Form_text" value="zhai duo"&gt;
> 
> **$A() 把相关的字符串列表转成数组对象。**
> 
> var zhaiduo = $A('AA BB CC DD');
> 
> zhaiduo.each(function(iteme){}
> 
> **$H() 将对象转成Hash数组对象。**
> 
> var zhaiduo = { X: 32, Y: 24, Z: 32 };
> 
> var myhash = $H(zhaiduo);
> 
> **$R() 创建一个有起始和结束范围的对象。**
> 
> var my_range = $R(1970, 2008, false);
> 
> my_range.each(function(value, index){}