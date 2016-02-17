---
title: ImageMagic把pdf转成jpg出现黑色块的问题
id: 2040
categories:
  - Linux/Unix
date: 2014-08-28 19:27:36
tags:
---

今天发现有些pdf转成img后出现黑色块，根据这里的[解释](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642098)，很有可能是pdf用的是透明背景，而不是白色背景。所以，解决办法就是：

命令行增加： -background white -alpha remove

问题解决。