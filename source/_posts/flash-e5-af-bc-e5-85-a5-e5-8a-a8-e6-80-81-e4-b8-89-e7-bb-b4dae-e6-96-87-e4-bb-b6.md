---
title: Flash导入动态三维DAE文件
tags:
  - 3D
  - AS3
  - animation
  - dae
  - javascript
id: 51
categories:
  - Flash
date: 2009-08-27 13:37:59
---

Flash导入DAE文件制作三维动画的一些参考网址：
**Papervision3D GreatWhite : MD2 Animation**
[http://sleepydesign.blogspot.com/2008/01/papervision3d-greatwhite-md2-animation.html](http://sleepydesign.blogspot.com/2008/01/papervision3d-greatwhite-md2-animation.html)

**DAEMC**
[http://tracehello.wordpress.com/2009/04/](http://tracehello.wordpress.com/2009/04/)

**DAE &amp; MD2 Example**
[http://techblog.floorplanner.com/2009/05/](http://techblog.floorplanner.com/2009/05/)

**Cast3D**
[http://cast3d.org/demos:lwalkfig](http://cast3d.org/demos:lwalkfig)

我偏向使用[Blender](http://www.blender.org/)+DAEMC来导入dae模型，如果出现形如“Couldn't find the joint id = Bone_...”的错误，通常都是dae文件文件的问题。特别注意骨骼(armature bones)间的父子关系。
model = new DAEMC(true, null, 0);
model.load("soldier.dae", new MaterialsList( { soldier_flat_png: new BitmapFileMaterial("soldier_flat.png",true) } ));
model.scale=250;
scene.addChild(model);
startRendering();

剩下的就是如何用Blender建模、贴图、[骨骼和动画](http://wiki.blender.org/index.php/Doc:Tutorials/Animation/BSoD/Character_Animation)，最后输出格式标准的dae文件。
![p20090827132317](http://www.zhaiduo.com/wp-content/uploads/2009/08/p20090827132317.jpg "p20090827132317")
![p20090827133140](http://www.zhaiduo.com/wp-content/uploads/2009/08/p20090827133140.jpg "p20090827133140")

另外感谢[http://www.tomtallian.com/](http://www.tomtallian.com/)提供的3D人物模型。^^骨骼和动画需要自己加。

PS: javascript控制所有iframe显示内容
window.onload=function(){
for(i = 0; i &lt; document.all.length; i++){
if(document.all(i).tagName=="IFRAME"){
document.all(i).src="about:blank";
}
}
}