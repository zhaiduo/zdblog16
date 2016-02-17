---
title: Javascript开发需要namespace和错误调试
id: 1037
categories:
  - javascript
date: 2010-09-01 15:45:25
tags:
---

做Javascript开发我想最头痛的就是这两方面了：变量的冲突和错误的调试问题。
为了避免在不同js脚本中的变量相互冲突，我们需要用到namespace。下面是一简单的例子：
> var ZED = new function() {
> //私有内部变量和函数，无法调用
> var privateFunction = function() {
> alert('privateFunction');
> };
> //公有内部变量和函数，可以调用
> this.publicFunction = function() {
> alert('publicFunction');
> };
> };
变量不冲突了，还要确保错误信息的正常反馈，有利于程序的调试，这样才能让Javascript开发做到游刃有余。
常用的错误调试有两种：window.onerror和try{}catch(e){}模块
下面是简单的例子：
onerror的好处在于容易找到错误的地方，但是不兼容主流的浏览器，除了IE和FireFox
> var arrErrors = new Array();
> window.onerror = function (strErr, strURL, strLineNumber){
> var strMess = "URL: " + strURL +
> "nline number: " + strLineNumber +
> "nError Message: " + strErr;
> arrErrors.push(strMess);
> alert(arrErrors.join("n__________nn"));
> return true;
> }
try.catch的好处在于兼容主流的浏览器，但是错误的信息不足，造成调试困难
> try{
> with(ZED){
> privateFunction();
> }
> }catch(e){
> alert("Name: " + e.name + "nDesc: " + e.description + "nMsg: " + e.msg);
> }
参考调式工具： [Javascript Stacktrace](http://github.com/emwendelin/javascript-stacktrace)
> var lastError;
> try {
> ZED.privateFunction();
> } catch(e) {
> lastError = e;
> }
> alert(printStackTrace().join('nn'));