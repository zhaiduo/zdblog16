---
title: JSON.parse是多余的
tags:
  - Json
  - python
id: 1100
categories:
  - javascript
date: 2010-09-27 00:42:16
---

前段时间有同事问是不是浏览器自带Json解析器的问题，没太留意，今天发现确实有这个情况。先是调用JSON.parse的时候提示JSON.parse错误，在追查错误缘由的时候发现ajax返回的msg是个object，我直接用python dump json格式：
> print 'Content-type: text/x-jsonnn'
> print json.dumps([{'title': arr['title']}])
然后用Javascript可以直接引用：
> $ajax(
> success: function(msg){
> if(msg[0].title) alert(msg[0].title);
> }
> )
试了FF,IE8,Chrome均没有问题，觉得不是浏览器自带Json解析器的问题，而是Jquery自动解析了json数据。留下存档，以备考究。

另外，Appengine本地调试支持import json, 但是deploy后，会出现ImportError: No module named json错误，
所以还是用from django.utils import simplejson。如果dumps数据中包含unicode字符，记得指定ensure_ascii = False，否则会是乱码。