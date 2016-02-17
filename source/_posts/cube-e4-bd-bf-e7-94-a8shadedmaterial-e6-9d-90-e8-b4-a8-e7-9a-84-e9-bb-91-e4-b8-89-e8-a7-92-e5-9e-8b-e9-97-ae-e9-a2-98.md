---
title: Cube使用ShadedMaterial材质的黑三角型问题
tags:
  - papervision3d
  - 问题
id: 793
categories:
  - 3D
  - AS3
date: 2009-02-03 16:33:00
---

![](http://zhaiduo.googlepages.com/MWSnap253.jpg)
在PV3d里面立方体原型Cube中使用ShadedMaterial材质的时候，如果立方体所有面都使用同一shader，渲染结果的时候，每个面会出现单个黑色三角形的问题。
> myShader = new PhongShader(light);
> myShadedMaterial = new ShadedMaterial(myBitmapMaterial,myShader);
> mlist = new MaterialsList();
> mlist.addMaterial(myShadedMaterial, "all");
根据[nabble上的解释](http://www.nabble.com/ShadedMaterial-problem-td17353753.html)：解决办法只能给每个面指定单独的Shader。经测试问题解决。

另外，要解决两平面相对垂直时，视角中出现的三角形突起，如下图：
![](http://zhaiduo.googlepages.com/18720090203235441.jpg)
可以修改小平面useOwnContainer属性来解决。
> plane.useOwnContainer=true;
但是发现如果有多个平行平面垂直于一平面的时候，useOwnContainer会导致平行平面之间视角失真的问题，看来还得找其他办法。如图，注意深蓝色平面。

![](http://zhaiduo.googlepages.com/18820090204001444.jpg)
正常情况

![](http://zhaiduo.googlepages.com/18920090204001500.jpg)
失真情况

更新：是Z-fighting的问题，用ViewportLayer和[QuadrantRenderEngine](http://blog.zupko.info/?p=177)来解决。具体如下
> import org.papervision3d.render.QuadrantRenderEngine;
> import org.papervision3d.view.layer.util.ViewportLayerSortMode;
> ...
> viewport.containerSprite.sortMode = ViewportLayerSortMode.INDEX_SORT;
> renderer = new QuadrantRenderEngine(QuadrantRenderEngine.ALL_FILTERS);
> ...
> viewport.getChildLayer(target).layerIndex = 1;
> viewport.getChildLayer(floor).layerIndex = -100;