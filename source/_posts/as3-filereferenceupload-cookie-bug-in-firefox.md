---
title: as3 FileReference.upload cookie bug in firefox
tags:
  - AS3
  - bug
id: 340
categories:
  - Flash
date: 2008-09-12 16:02:35
---

I use PHP to detect [as3] FileReference.upload by cookie in Firefox2, there are all cookies missing except $_COOKIE['PHPSESSIONID']. But it works in IE8 beta.

References:
1\. [under Firefox, FileReference loose cookies during upload](http://bugs.adobe.com/jira/browse/FP-78)
2\. [Firefox, Flex URLRequest, and Sessions Issue](http://thanksmister.com/?p=59)