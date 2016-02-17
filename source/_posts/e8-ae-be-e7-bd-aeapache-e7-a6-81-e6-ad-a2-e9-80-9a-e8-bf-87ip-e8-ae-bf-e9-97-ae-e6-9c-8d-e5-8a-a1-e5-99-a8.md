---
title: 设置Apache禁止通过IP访问服务器
tags:
  - Apache
  - 备案
id: 587
categories:
  - Linux/Unix
date: 2010-05-12 12:55:18
---

最近一台RHEL4服务器刚备案了一个域名，可是始终无法访问。询问托管商后得知还有一个未知域名尚未备案，网站所以被屏蔽。分析原因可能是服务器IP旧的使用者。因为域名没有备案，也没有更改指向，所以连诛到我们。为了防止服务器这样无辜的被再次连诛，我们可以修改Apache的httpd.conf，禁止通过IP来访问网站。
在httpd.conf末加上：
> &lt; VirtualHost 服务器IP &gt;
> ServerName 服务器IP
> &lt; Location / &gt;
> Order Allow, Deny
> Deny from all
> &lt; /Location &gt;
> &lt; /VirtualHost &gt;

另外IIS下的设置：需要删除默认网站，然后设置主机头，在网站站点属性，IP右边的高级里添加域名。