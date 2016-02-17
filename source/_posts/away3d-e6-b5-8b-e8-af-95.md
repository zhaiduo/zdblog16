---
title: Away3D测试
tags:
  - Away3D
id: 805
categories:
  - 3D
  - AS3
  - Flash
date: 2009-03-19 17:25:00
---

[![](http://zhaiduo.googlepages.com/MWSnap268.jpg)](http://zhaiduo.googlepages.com/helloaway3d.html)
测试[Away3D](http://away3d.com/)用了[2.3.3](http://away3d.com/downloads)flash9版本中的样例来测试。很喜欢这个水下的光影效果。Away3D的学习资料没有PV3D多，但是和Alternative3D比较还是好很多，可以看看Away3D核心开发人员:[Fabrice Closier](http://www.closier.nl/blog/)的博客，能学到[很多东西](http://www.closier.nl/blog/?cat=6)。

另外有个地方要注意的是：从Blender导出dae文件到Away3D，必须添加UV Mapping，否则Collada.load装载材质的时候会出现这样的错误：
> TypeError: Error #1009: Cannot access a property or method of a null object reference.
注意dae中的路径问题。