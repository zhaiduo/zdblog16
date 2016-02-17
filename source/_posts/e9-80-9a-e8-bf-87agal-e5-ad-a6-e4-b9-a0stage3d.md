---
title: 通过AGAL学习Stage3D
tags:
  - AGAL
id: 1463
categories:
  - 3D
  - Flash
  - 三维时代
date: 2012-01-16 03:03:49
---

好久没有玩玩Flash 3D，[官方的Stage3D AGAL教程](http://www.adobe.com/devnet/flashplayer/articles/hello-triangle.html)已经放出。相对于[Away3D的Molehill教程](http://www.zhaiduo.com/2011/03/%e5%ae%89%e8%a3%85molehill%e5%92%8caway3d/)，变化不大，而是多了perspective和camera的教程。主要亮点在于AGAL的学习，对于OpenGL和WebGL的Vertex和Fragement学习都是很好的补充。

首先是安装环境，我使用FLalsh CS5测试，下载最新的Flex SDK，和11.0的playerglobal11_0.swc和flash player 11，以及com.adobe.utils.AGALMiniAssembler。
然后在Setting-&gt;preference-&gt;actionscript下的actioscript3.0 setting里面修改Flex SDK Path为你的解压路径/flex_sdk_4.5.1.21328A。
最后，安装FP11Publish_cs5.mxp让flash piblish setting里面支持flash player 11.0。直接上官方代码，享受AGAL的快感吧～

同样编译错误不用惊慌：VerifyError: Error #1014: 无法找到类 flash.display3D::Context3D。

打开这里publish preview-&gt;html才是王道。

另外，发现之前的incubator看flv视频很容易让Firefox崩溃，现在毫无压力。

[![](http://www.zhaiduo.com/wp-content/uploads/2012/01/15820120116040305.jpg "15820120116040305")](http://www.zhaiduo.com/2012/01/%e9%80%9a%e8%bf%87agal%e5%ad%a6%e4%b9%a0stage3d/attachment/15820120116040305/)