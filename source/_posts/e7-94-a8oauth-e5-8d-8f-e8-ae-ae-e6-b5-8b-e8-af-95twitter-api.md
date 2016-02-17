---
title: 用OAuth协议测试Twitter API
tags:
  - OAuth
  - Twitter
id: 868
categories:
  - PHP
date: 2010-07-25 23:46:21
---

去年用Basic Auth做的Twitter API测试已经无法使用，早就看到Twitter推荐OAuth的提示，今天有空用OAuth[重写了一下](http://lab.zhaiduo.com/test/)。

OAuth的主要目的是尽量减少用户密码在第三方授权过程中的暴露，增强第三方授权的安全性。我使用的是Twitter推荐的[twitteroauth](http://github.com/abraham/twitteroauth)，也看了看[oauth-php](http://code.google.com/p/oauth-php/)，觉得太复杂。twitteroauth内容少一些，代码看得不会太晕。由于之前写过Blogger的OAuth，所以改起来不是太难；但是不太理解的是user_timeline调用起来太过复杂，本来简单一个网址的调用，现在还要KEY和SECRET，加上用户名和密码才能获取。我的测试只是简单获取Tweets列表以及获取相关的followers，来来去去的token验证显得多此一举。

于是我又索性把connect, redirect和callback集成到了一起，方便我进行简单调用。有意思的是旧的Basic Auth还可以用来更新Twitter，虽然返回的是403。不过，话又说回来，OAuth的应用在越来越多的地方可以看到，掌握它还是很有必要的。