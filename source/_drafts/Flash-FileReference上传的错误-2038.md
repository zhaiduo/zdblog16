---
title: 'Flash FileReference上传的错误#2038'
tags:
  - 出错
id: 405
categories:
  - Flash
---

Flash FileReference上传的时候出现如下错误
ioErrorHandler: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2038"]
httpStatusHandler: [HTTPStatusEvent type="httpStatus" bubbles=false cancelable=false eventPhase=2 status=406]

分别在两个不同的网站测试，一个可以，一个不行。究其原因，怀疑是.htaccess造成。
里面有这么一段：
< Limit GET POST >
order deny,allow
deny from all
allow from all
< /Limit >
< Limit PUT DELETE >
order deny,allow
deny from all
< /Limit >