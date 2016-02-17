---
title: 火狐登录问题：Forbidden (403) CSRF verification failed
tags:
  - FireFox
  - 问题
id: 1538
categories:
  - 浏览器
date: 2012-04-16 18:56:27
---

用火狐浏览器登录http://instagr.am发现出现无法登录的情况：
Forbidden (403) CSRF verification failed
[![](http://www.zhaiduo.com/wp-content/uploads/2012/04/17020120416184701-300x200.jpg "17020120416184701")](http://www.zhaiduo.com/2012/04/%e7%81%ab%e7%8b%90%e7%99%bb%e5%bd%95%e9%97%ae%e9%a2%98%ef%bc%9aforbidden-403-csrf-verification-failed/attachment/17020120416184701/)
根据[官方的帮助](http://support.mozilla.org/zh-CN/questions/864750)，进入火狐about:config配置页面，
搜索network.http.sendRefererHeader，设置值为1即可。果然，登录成功。

另外，火狐表单里面会记住很多曾经登录过的用户名，可以把鼠标选中表单项，当用户名列表出现时移到相应的用户名上，按Ctrl+Del即可删除所记住的用户名。