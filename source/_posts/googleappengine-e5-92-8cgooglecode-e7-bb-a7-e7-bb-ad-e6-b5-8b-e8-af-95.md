---
title: GoogleAppEngine和GoogleCode继续测试
tags:
  - GoogleAppEngine
  - GoogleCode
  - SVN
  - python
id: 357
categories:
  - 杂项
date: 2009-09-03 13:44:26
---

**GoogleAppEngine测试**
从[去年申请GoogleAppEngine帐号](http://www.zhaiduo.com/2008/12/google-app-engine.html)，用Python写了个简单的TwitterUpdate到现在，已经有段时间了。现在希望那个有时间把它完善一下，也正好满足Twitter被墙后的需要。
GoogleAppEngine主要命令：
devserver.py yourapp/ 启动运行环境
appcfg.py --email=zhaiduo@gmail.com update yourapp/ 提交

**出现的问题：**
AppConfigNotFoundError - 注意文件名不要错误： devserver.py yourapp/
&lt; type 'exceptions.SyntaxError' &gt;: Non-ASCII character ......, but no encoding declared; - 中文编码问题
> 办法：添加到Python文件头：# -*- coding:utf-8 -*- ＃必须在第一行或者第二行
**[GoogleCode](http://code.google.com/)测试**
我[选用Subversion作为更新方式](http://www.zhaiduo.com/2009/07/windowssubversionapache.html)，工具用的是[Tortoisesvn](http://tortoisesvn.net/downloads)

为什么要测试GoogleAppEngine和GoogleCode这两种Google提供服务？
1\. 了解Google开发项目的程序和过程，以提高自己的项目维护、管理和开发能力。
2\. 熟悉GoogleAppEngine，SVN和Python。
3\. 可以当作免费存储空间。（[AppEngine是限制流量](http://code.google.com/appengine/docs/quotas.html#Free_Changes)：每天下载量可以到50G； GoogleCode：单个文件最大: 100 MB. 共2G空间 ）