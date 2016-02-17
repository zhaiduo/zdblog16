---
title: CSS Hack for ALL IE
id: 318
categories:
  - CSS
  - 技术研究
  - 窄多废话
date: 2006-09-30 11:27:18
tags:
---

> /*目的：除了IE(包括IE7)背景为红色，其他均为绿色*/
> #item {
> width: 200px;
> height: 200px;
> background: red;
> }
> 
> /*IE7不支持:lang，可以利用这个属性*/
> *:lang(en) #item{
> background:green !important;
> }
> 
> /*增加对Safari的支持*/
> #item:empty {  /*[CSS3](http://www.w3.org/TR/css3-selectors/) `:empty` pseudo-class => no children*/
> background: green !important
> }
> <div id="item">some text here</div>