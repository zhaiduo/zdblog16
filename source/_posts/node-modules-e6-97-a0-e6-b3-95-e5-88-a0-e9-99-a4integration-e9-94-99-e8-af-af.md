---
title: node_modules无法删除integration错误
tags:
  - npm
id: 2010
categories:
  - webapp
date: 2014-08-06 23:55:07
---

windows下删除web app的node_modules目录，可能出现无法删除integration错误的提示，[根据这里的解释](https://github.com/joyent/node/issues/6960)，源自windows路径长度的限制，造成这个bug。

This is the maximum length of a path according to the Windows API, defined as 260 characters.

解决办法：
http://support.microsoft.com/?kbid=320081

you can delete a file named "lpt1" if you specify the full path of the file by using the following special syntax:
del \?c:path_to_filelpt1

或者直接把太深的目录拖到浅一点的目录。