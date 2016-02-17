---
title: 两个FLash问题
tags:
  - flv
  - 问题
id: 785
categories:
  - AS3
  - Flash
date: 2008-12-24 16:15:00
---

1\. Flash CS3里面无法向FLex一样调用文件的问题
下面这种方式在CS3里面无效,
> [Embed(source="zhaiduo.jpg")] private var zhaiduo:Class;
我们可以把文件导入库library, 通过linkage ID调用。如:linkage ID为"Zhaiduo"。
> var zd:Zhaiduo=new Zhaiduo(100,100);
> var myBitmap:Bitmap = new Bitmap(zd);
2\. NetStream无法播放非本地FLV视频文件的问题
NetStream只允许本地bitmapData.draw。所以只有声音看不见影像。例子可以[看里](http://zhaiduo.googlepages.com/first2.html)。
[Nabble](http://www.nabble.com/run-flv-from-video-Website-in-papervision3d--td15306962.html)上有这样一段解释：
> The only way around this is to deliver your video via a custom
> configured flashCom server.  (Open source solutions include red5 and
> haXeVideo).  These flashCom servers have to send a flag with the
> NetStream that allows bitmapData.draw for your domain.  Regardless,
> you aren't going to get this from a remote server.