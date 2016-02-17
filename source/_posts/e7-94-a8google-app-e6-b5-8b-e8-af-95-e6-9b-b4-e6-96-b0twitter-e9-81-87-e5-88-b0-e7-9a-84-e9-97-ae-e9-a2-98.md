---
title: 用Google App测试更新twitter遇到的问题
tags:
  - Python
  - 无奈
id: 789
categories:
  - Uncategorized
date: 2009-01-06 14:08:00
---

本来打算用PHP写一个Twitter的更新程序。主要问题在于通过Basic Authentication来通过授权。最简单的办法就是用Curl。这里有个很好的[CLASS](http://twitter.slawcup.com/twitter.class.phps)可以借鉴，但是无奈服务器对curl的限制，只好放弃。最近接触Google App，用的是Python。于是打算用[Python](http://docs.python.org/dev/index.html)试试。

Python中关于Http的[Basic Authentication的教程](http://www.voidspace.org.uk/python/articles/authentication.shtml)已经很详细，大概的方法包括使用urllib、urllib2和httplib。无奈这些方法在google_app下都出现这样的错误：
> AttributeError: 'module' object has no attribute 'error'
解决办法只有使用[URL Fetch API](http://code.google.com/appengine/docs/urlfetch/)，通过给header增加Authorization字段，达到通过Twitter API授权的问题。

代码如下：
> base64string = base64.encodestring('%s:%s' % (username, password))[:-1]
>   result = urlfetch.fetch(url=update_url,
>                           payload=form_data,
>                           method=urlfetch.POST,
>                           headers={
>                             'Content-Type': 'application/x-www-form-urlencoded',
>                             'Authorization': 'Basic '+ base64string
>                           })