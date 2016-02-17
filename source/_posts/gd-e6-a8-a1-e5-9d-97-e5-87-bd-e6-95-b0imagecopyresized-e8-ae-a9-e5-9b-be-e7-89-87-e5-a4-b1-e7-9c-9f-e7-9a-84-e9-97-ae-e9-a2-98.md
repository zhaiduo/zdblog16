---
title: GD模块函数imagecopyresized让图片失真的问题
tags:
  - 问题
id: 1384
categories:
  - PHP
date: 2011-07-20 18:07:14
---

今天遇到PHP的GD模块函数缩小图片，让图片失真的问题，后来发现是imagecopyresized这个函数的问题。而用imagecreatetruecolor和
imagecopyresampled却没有这个问题。
[![](http://www.zhaiduo.com/wp-content/uploads/2011/07/gd_shizhen.jpg "gd_shizhen")](http://www.zhaiduo.com/wp-content/uploads/2011/07/gd_shizhen.jpg)

系统环境：PHP Version 5.2.6-1+lenny9
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.3.7
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled