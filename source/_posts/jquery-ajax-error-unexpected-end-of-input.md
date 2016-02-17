---
title: 'Jquery Ajax Parsererror: Unexpected end of input'
tags:
  - Ajax
  - 出错
id: 2329
comment: false
categories:
  - 前端
date: 2015-04-10 13:43:22
---

![](http://ww3.sinaimg.cn/mw690/67efa17fjw1er0g4lzdftj20np0a6acx.jpg)
使用jquery-1.9.1进行ajax提交 Error 报错：
parsererror
Unexpected end of input

根据[这里](http://bugs.jquery.com/ticket/13459)的解释：
> "parsererror", SyntaxError: {message: "Unexpected end of input"}
> 
> jQuery 1.8.3 did report a success, 1.9.1 reports a failure.

根据[这里](https://github.com/jquery/jquery-migrate/blob/master/warnings.md#jqmigrate-jqueryparsejson-requires-a-valid-json-string)的解释，解决办法是：
var json = $.parseJSON(jsonString || "null");
或者
dataType: "text"