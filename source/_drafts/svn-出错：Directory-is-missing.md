---
title: svn 出错：Directory is missing
tags:
  - SVN
id: 1908
categories:
  - 版本控制
---

SVN服务器上有目录xxx，可以是网站目录下不见了，svn up出现出错：Directory xxx is missing。

svn revert xxx
mkdir xxx
svn add xxx
svn up