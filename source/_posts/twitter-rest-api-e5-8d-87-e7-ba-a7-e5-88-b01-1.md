---
title: Twitter REST API升级到1.1
tags:
  - REST API
id: 1823
categories:
  - PHP
date: 2013-09-04 23:24:51
---

好久没看Twitter，发现API无法返回内容，原来是升级啦，v1已经停止使用。
The Twitter REST API v1 is no longer active. Please migrate to API v1.1\. https://dev.twitter.com/docs/api/1.1/overview.

解决办法，把旧的API地址换成

 var $twt_url='https://api.twitter.com/1.1/';

即可。

另外search的调整，从/search.json?到/search/tweets.json?，返回的results也变成了statuses。这不是折腾吗？