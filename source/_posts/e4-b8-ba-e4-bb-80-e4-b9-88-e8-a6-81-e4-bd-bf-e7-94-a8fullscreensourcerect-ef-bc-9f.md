---
title: 为什么要使用fullScreenSourceRect？
id: 1586
categories:
  - AS3
  - Flash
date: 2012-05-25 03:47:56
tags:
---

用as3制作FLash播放器时，使用fullScreenSourceRect来做硬件缩放，效率上比软件缩放高，adobe官方文档如是说([Hardware scaling in full-screen mode](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7e31.html))。可是根据我自己使用情况来看，视频播放并没有特别明显的快慢，反倒是视频画面质量模糊下降很多。那就奇怪了，为什么官方还要介绍这种用法？就连退出全屏模式的文字也那么的不堪入目。
[![](http://www.zhaiduo.com/wp-content/uploads/2012/05/17720120525002351-300x141.jpg "17720120525002351")](http://www.zhaiduo.com/2012/05/%e4%b8%ba%e4%bb%80%e4%b9%88%e8%a6%81%e4%bd%bf%e7%94%a8fullscreensourcerect%ef%bc%9f/attachment/17720120525002351/)

反倒是不用fullScreenSourceRect，全屏效果更清晰一些，字体也不会模糊。
[![](http://www.zhaiduo.com/wp-content/uploads/2012/05/17820120525013908-300x170.jpg "17820120525013908")](http://www.zhaiduo.com/2012/05/%e4%b8%ba%e4%bb%80%e4%b9%88%e8%a6%81%e4%bd%bf%e7%94%a8fullscreensourcerect%ef%bc%9f/attachment/17820120525013908/)

那么是不是可以说fullScreenSourceRect对全屏播放视频没有帮助？

我想[这个旧帖子](http://forums.adobe.com/message/889544)也是这个意思。难道这么多年了还是没改进？