---
title: CSS样式表常用技巧
tags:
  - 浏览器
id: 256
categories:
  - CSS
date: 2008-03-20 14:01:43
---

全局通配符 *
通配符可以涵盖定义页面上所有的CSS对象,例如:
> * {padding:0;margin:0px;border:0px;}
overflow可以不显示超过对象尺寸的内容,也可以用于清除周围(floated)浮动的元素。
> .anyclass {overflow:hidden;}
同时指定多个class样式
> &lt; div class="class1 class2 class3"&gt;
class内包含对象的css定义（用空格分隔）：
> .div subelement {width:100px;}
同级对象的css定义（用逗号分隔）：
> .class1, .class2, #myid {color:#000;}

这里[有篇Eric写的文章](http://meyerweb.com/eric/thoughts/2007/05/01/reset-reloaded/)，推荐给网页定义默认的CSS样式，这样可以避免不同浏览器之间默认样式表设置给页面风格带来的干扰，让我们的网页做到真正的所有浏览器都一个模样，真正的标准化．
> html, body, div, span, applet, object, iframe,
> h1, h2, h3, h4, h5, h6, p, blockquote, pre,
> a, abbr, acronym, address, big, cite, code,
> del, dfn, em, font, img, ins, kbd, q, s, samp,
> small, strike, strong, sub, sup, tt, var,
> dl, dt, dd, ol, ul, li,
> fieldset, form, label, legend,
> table, caption, tbody, tfoot, thead, tr, th, td {
> 	margin: 0;
> 	padding: 0;
> 	border: 0;
> 	outline: 0;
> 	font-weight: inherit;
> 	font-style: inherit;
> 	font-size: 100%;
> 	font-family: inherit;
> 	vertical-align: baseline;
> }
> /* remember to define focus styles! */
> :focus {
> 	outline: 0;
> }
> body {
> 	line-height: 1;
> 	color: black;
> 	background: white;
> }
> ol, ul {
> 	list-style: none;
> }
> /* tables still need 'cellspacing="0"' in the markup */
> table {
> 	border-collapse: separate;
> 	border-spacing: 0;
> }
> caption, th, td {
> 	text-align: left;
> 	font-weight: normal;
> }
> blockquote:before, blockquote:after,
> q:before, q:after {
> 	content: "";
> }
> blockquote, q {
> 	quotes: "" "";
> }