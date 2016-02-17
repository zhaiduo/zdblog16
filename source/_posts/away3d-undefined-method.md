---
title: 郁闷的Away3D未定义linestyle问题
tags:
  - Apple App
  - Away3D
  - Box2D
  - 出错
id: 1219
categories:
  - AS3
  - Flash
date: 2010-12-16 00:14:47
---

好久没有玩过[Away3D](http://away3d.com/downloads)，今天下载了3.6 for FP10，最简单的代码在Flash CS4中却总是提示未定义方法linestyle这样的错误：

Error 1061:  call to a possibly undefined method linestyle through a reference with static type graphics

[![](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101215232942-300x73.jpg "20101215232942")](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101215232942.jpg)

貌似是找不到flash.display.Graphics的问题，我又换了FP9的版本一样的错误，用低版本2.4也是一样的错误。有些无语了。

最后试着用了用Away3D.swc，居然问题解决。具体原因还是不明，看来我的Flash丢生啦......

事情的起因是源于看到[苹果的App应用Angry Birds](http://itunes.apple.com/us/app/angry-birds/id343200656?mt=8)红透移动互联网，让我又重新燃起了对[Box2D](http://box2dflash.sourceforge.net/)的好奇。甚至也想试试用Away3D来测试Box2D，参考的是[clockmaker](http://clockmaker.jp/blog-en/2009/04/3d-ball-simulation/)的作品。

唉，年纪大了，脑力有些不给力啊。