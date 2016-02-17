---
title: console.log加图片加样式的办法
id: 1902
categories:
  - javascript
date: 2014-03-30 23:35:22
tags:
---

现在流行技术流，有些东西只给搞技术的人看。
前端网页console.log也可以加图片加样式，chrome浏览器支持。
`

//寻觅前端
var isChrome = /webkit/.test(navigator.userAgent.toLowerCase()) &amp;&amp; /chrome/.test(navigator.userAgent.toLowerCase());
if(isChrome){
console.log("%cn ","font-size:60px;background:url('http://sae..../console.gif?v="+$SAE.version+"') left top no-repeat;");
console.log('发现了SAE的什么BUG？n还是对我们有什么好的建议？n如果你也对技术充满热情。n期待你的加入。http://sae....tId=177');
console.log("如有意加入，请在邮件标题中注明:%c["+$SAE.version+"]","color:#FF8A0B;font-weight:bold;");

}

`
[![24020140330232657](http://www.zhaiduo.com/wp-content/uploads/2014/03/24020140330232657-300x140.jpg)](http://www.zhaiduo.com/wp-content/uploads/2014/03/24020140330232657.jpg)