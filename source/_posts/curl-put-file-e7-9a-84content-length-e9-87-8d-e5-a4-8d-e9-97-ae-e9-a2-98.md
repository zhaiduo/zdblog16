---
title: Curl PUT FILE的content-length重复问题
tags:
  - API
  - Dropbox
  - OAuth
id: 1682
categories:
  - PHP
date: 2012-07-28 00:39:42
---

昨天用Dropbox OAuth API写PHP接口的时候遇到十分诡异的问题。Curl的request header里居然有两个重复一样的content-length：
> Content-length: 4288
> Content-Length: 4288
API返回了错误:
> Error (4xx)
> We can't find the page you're looking for. Check out our Help Center and forums for help, or head back to home.
我很确定header数组里面只有一个Content-length，第二个Content-Length的L是大写，貌似是系统自动加上的。
如果不用Content-length，API会返回"HTTP Error 411 Length required"的错误。

由于找不到合理的解释，只能用个trick，删除一个Content-length了事：
> curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Length: '));