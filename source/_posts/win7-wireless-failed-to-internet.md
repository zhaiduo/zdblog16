---
title: 再次出现Win7无法无线上网的问题
tags:
  - windows7
  - 无法上网
  - 无线上网
  - 问题
id: 1343
categories:
  - 互联网
date: 2011-04-05 16:52:44
---

今天老婆的笔记本突然无法无线上网，无线网卡显示有限的访问权限，这让我想起了[上次遇到的问题](http://www.zhaiduo.com/2010/09/windows7_wireless_limit_access/)。登录到路由器EchoLife HG520s的无线MAC过滤，把出了我和老婆的MAC地址保留外，其它都拒绝。问题解决。
具体操作如下：
1、先到DOS界面下，用Ipconfig -all|more查询本机的MAC地址(Physical Address)。
[![](http://www.zhaiduo.com/wp-content/uploads/2011/04/01620110405164306.jpg "01620110405164306")](http://www.zhaiduo.com/wp-content/uploads/2011/04/01620110405164306.jpg)
2、登录路由器无线MAC过滤页面，设置只允许通过的MAC地址。
[![](http://www.zhaiduo.com/wp-content/uploads/2011/04/01820110405164331.jpg "01820110405164331")](http://www.zhaiduo.com/wp-content/uploads/2011/04/01820110405164331.jpg)