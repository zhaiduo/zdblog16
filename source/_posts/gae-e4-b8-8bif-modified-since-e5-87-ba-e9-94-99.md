---
title: GAE下If-Modified-Since出错的问题
tags:
  - GAE
  - IE
  - 问题
id: 1559
categories:
  - Python
date: 2012-05-18 14:39:55
---

最近发现IE8下GAE显示图片的时候会出现如下错误：

python代码如下：
datetime.datetime.strptime(self.request.headers['If-Modified-Since'],HTTP_DATE_FMT)

出错为：
File "E:Pythonlib_strptime.py", line 328, in _strptime
    data_string[found.end():])
ValueError: unconverted data remains: ; length=37269

FireFox却没有这个问题。原因在于self.request.headers['If-Modified-Since']在IE8下多了length：
IE8: Thu, 17 May 2012 17:13:07 GMT; length=37269

解决办法很简单，过滤掉分号及之后的部分即可。