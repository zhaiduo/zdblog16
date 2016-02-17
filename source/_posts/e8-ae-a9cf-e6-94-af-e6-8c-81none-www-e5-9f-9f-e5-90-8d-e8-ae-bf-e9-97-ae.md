---
title: 让CF支持none-www域名访问
tags:
  - CDN
  - DNS
  - 反向代理
id: 1545
categories:
  - 主机
date: 2012-04-17 23:27:06
---

我们都知道CF的CDN很棒，但是CF的缺点是整个域名都要使用它的DNS SERVER，而且不支持裸域名的访问。

我的解决办法是：

在第三方做一个反向代理，

然后把已经转到CF的裸域名的A记录指向第三方的IP地址。

经测试，确实有效。