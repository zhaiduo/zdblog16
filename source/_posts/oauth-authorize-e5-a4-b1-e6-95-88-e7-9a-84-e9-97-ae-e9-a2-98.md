---
title: Oauth authorize失效的问题
tags:
  - OAuth
  - Twitter
id: 1093
categories:
  - PHP
date: 2010-09-22 11:51:00
---

前段时间测试[Oauth链接Twitter](http://www.zhaiduo.com/2010/07/%e7%94%a8oauth%e5%8d%8f%e8%ae%ae%e6%b5%8b%e8%af%95twitter-api/)没什么问题，昨天发现[链接失效了](http://lab.zhaiduo.com/test/)，根据[这里的解释](http://developer.linkedin.com/message/5948?tstart=0#5948)：
> Scripting the login process or impersonating users is strictly forbidden.
貌似是Twitter禁止脚本通过Oauth自动登录，仔细看看Twitter OAuth class，发现是post的时候Twitter返回的格式发生了变化，Twitter OAuth默认采用json格式，所以json_decode返回就变成了空，造成授权无法继续。修改返回HTML后，程序正常。