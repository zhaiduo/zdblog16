---
title: Papervision3D的正反两面材质测试
tags:
  - papervision3d
id: 791
categories:
  - 3D
  - AS3
date: 2009-01-08 13:19:00
---

![](http://zhaiduo.googlepages.com/MWSnap249.jpg)
要做到[Papervision3D](http://docs.pv3d.org/)的Plane实现正反两面材质，现在主要有两个方法：
一是利用DisplayObject3D两个Plane放到一起，贴图做到一正一反就可以实现：[[wave2.swf](http://zhaiduo.googlepages.com/wave2.html)]
> p = new Plane(bitmapMaterial,829, 389,10,10);
> planeGroup.addChild(p);
> p2 = new Plane(bitmapMaterial2,829, 389,10,10);
> p2.rotationY = 180;
> planeGroup.addChild(p2);
> scene.addChild(planeGroup);
波动效果利用Plane的segments分段特性，控制每个geometry.vertices来实现。

二是利用Cube，把高度设为零，上下两面做贴图：[[As3dModPerlin.swf](http://zhaiduo.googlepages.com/As3dModPerlin.html)]
> var materialsList:MaterialsList = new MaterialsList() ;
> materialsList.addMaterial(bitmapMaterial, "top" ) ;
> materialsList.addMaterial(bitmapMaterial2, "bottom" ) ;
> var cube:Cube = new Cube(materialsList, 829, 389 , 1,10,10,10 ) ;
> planeGroup.addChild(cube) ;
> scene.addChild(planeGroup);
波动效果采用[everydayflash](http://www.everydayflash.com/)的[AS3Dmod库](http://code.google.com/p/as3dmod/wiki/AS3Dmod_Tutorial)来实现。