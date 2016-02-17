---
title: Ucenter的终极通信失败
tags:
  - discuz
  - 出错
id: 1261
categories:
  - PHP
date: 2011-01-07 05:22:39
---

今天帮客户整合ShopEx和Ecshop到discuz x1.5，发现全新的discuz x1.5安装后，Ucenter仍然出现通信失败的错误。经过排查，排除掉IP和UC_KEY不吻合的问题。分析uc_server的function dfopen发现问题来自fsockopen，返回的是“HTTP 错误 403 - 禁止访问”。原来客户的虚拟主机不支持socke绑定，所以会出现host与实际ip不一致的情况。这可以说是uc_server和uc_client的终极BUG，这种认证方式在无法绑定socket或fsockopen被禁止的主机下完全无效。

如果你还在为你的通信失败伤透脑筋，奉劝你换个hosting试一试。否则只有泪奔的命！