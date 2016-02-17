---
title: Nodejs错误：
SyntaxError: 'Unexpected identifier""'
tags:
  - Expressjs
  - Jade
  - Nodejs
id: 1502
categories:
  - javascript
date: 2012-03-28 19:56:39
---

最近初学Nodejs，采用[Nodejs+Express+Jade建站](http://zdvps.zhaiduo.com/)。res.render的时候，出现如下错误：
> SyntaxError: Unexpected identifier" Object.Function (unknown source)
仅从字面意思，很难判断是哪里出问题。不得不一个部分一个部分的排查，最后确认是Jade模板的问题。
原来是jade语法不对：
> title= This is Jade Example => title This is Jade Example
多了一个等号，看来样板程序也不是十分可靠，初学东西前，掌握好基础知识为好。

由于自己最开始接触的编程语言就是javascript，所以一直对它有好感。在感叹javascript已经可以作为服务器后端开发高效的程序时，我又不由得纳闷：“虽然编程语言在进步，可是做为网站编程，换种语言是否意味着只是在重复造车轮？” - 我不确定，我只是好奇，尽力去找寻用不同语言开发网站的不同乐趣～