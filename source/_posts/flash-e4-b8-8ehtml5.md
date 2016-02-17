---
title: FLash与HTML5
tags:
  - Apple
  - Canvas
  - SVG
  - 三维
  - 图形化
id: 506
categories:
  - Flash
  - javascript
  - 互联网
date: 2010-02-05 16:28:02
---

苹果新发布的平板电脑iPad不支持Flash(也不支持USB, 扩展内存和蓝牙)，乔布斯做了解释（因为Flash buggy，常常和苹果的宕机有关），
> Apple does not support Flash because it is so buggy. Whenever a Mac crashes more often than not it’s because of Flash. No one will be using Flash. The world is moving to HTML5.
与此同时以降低浏览器对插件的依赖程度为主要目的的[HMLT5](http://www.whatwg.org/specs/web-apps/current-work/multipage/)推出了大量的HTML新特性，其中用以替代Flash的[Canvas](https://developer.mozilla.org/en/Canvas_tutorial)和[SVG](https://developer.mozilla.org/en/SVG_In_HTML_Introduction)图形功能(通过Javascript进行二维/三维绘图，其中二维绘图已经被主流浏览器所支持)让人刮目相看。以前只能用Flash做到的效果，现在不用装插件就可以通过Javascript来实现。我们可以看看下面简单的Canvas/SVG例子
[![](http://www.zhaiduo.com/wp-content/uploads/2010/02/p20100205160125.jpg "p20100205160125")](http://www.zhaiduo.com/wp-content/uploads/2010/02/p20100205160125.jpg)

*   [Canvas Particle System](http://www.mrspeaker.net/dev/parcycle/)
*   [Highcharts](http://highcharts.com/)
*   [Space Invaders game](http://croczilla.com/bits_and_pieces/svg/samples/invaders/invaders.svg)
*   [Some Adventure-y Guy](http://www.mrspeaker.net/dev/platform/)
*   [JS WARS](http://29a.ch/jswars/)
*   [nifty game](http://www.paulbrunt.co.uk/2009/09/20/berts-breakdown/)
*   [Canvascape - "3D Walker"](http://www.benjoffe.com/code/demos/canvascape/)
*   [Paint.Web - painting              demo, open-source](http://code.google.com/p/paintweb)
*   [Star-field              flight](http://arapehlivanian.com/wp-content/uploads/2007/02/canvas.html)
Flash未来可谓是凶多吉少。虽然目前看来，和HTML5相比，Flash确实有着明显优势

1.  安装方便
2.  性能流畅
3.  巨大的用户基数
4.  领先的视频/音频播放技术
特别是高性能三维网页动画(但是这种优势很快即将不再，OpenGL已经瞄准三维网页市场，推出[WebGL](http://www.khronos.org/webgl/))：

*   [Milkyball, a further extension of my Triangle3D experimentation](http://www.unitzeroone.com/blog/2010/01/20/pixelbender-raytracer-milkyball/)
*   [PV3D light rays](http://kode80.com/2009/11/19/pv3d-light-rays/)
*   [Multi-pass Lantern](http://www.derschmale.com/demo/away3d/multipassLantern/)
但是Flash仍然有不少隐忧：

1.  始终需要插件安装
2.  三维复杂动画的性能瓶颈
3.  众多竞争对手：苹果公司, Sliverlight, HTML5, WebGL

如果有那么一天，Flash将不再是插件，而成为主要浏览器默认的一部分，我想这才是我对Flash的期望。无论如何，对我来说Flash的确是个很棒的玩具和工具，我会继续支持和使用它！至于它能否占领市场，一统天下，乔布斯和HTML5最终能否成为Flash的终结者，我们拭目以待吧。

另外，你准备好[HTML5](http://www.alistapart.com/articles/get-ready-for-html-5/)了吗？