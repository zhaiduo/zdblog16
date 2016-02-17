---
title: setInterval的问题
tags:
  - 出错
id: 271
categories:
  - javascript
date: 2008-05-05 17:27:03
---

[setInterval](http://developer.mozilla.org/en/docs/DOM:window.setInterval)作为定时触发某一个函数是很有用的工具，可是当我们要调用的函数带有变量的时候，常常出现如下的错误:
> Error: parentnode.removechild is not a function
> Error: useless setInterval call (missing quotes around argument?)
根据[这里](http://bytes.com/forum/thread94459.html)的解释，问题出在setInterval里用引号处理变量名的时候，例如：
> codeSnippet = "clockUpdate(" + fieldId + ")";
fieldId会被当作是一个字符串变量被函数clockUpdate引用，如果fieldId不是字符串，而是对象，照样会被解析成字符串变量。所以在这里有一个技巧，帮助我们引用非字符串变量：
> codeSnippet = "clockUpdate(""+fieldId+"");";
虽然mozilla定义的setInterval语法可以帮助我们轻松调用参数：
> intervalID = window.setInterval(func, delay[, param1, param2, ...]);
但是这个方法用IE7不管用，它会提示未定义参数的错误。
结合上面提到的，我想setInterval最好还是调用用字符串变量作为参数的函数。