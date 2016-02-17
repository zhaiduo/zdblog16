---
title: Blender导出Dae文件到Papervision3D的方法
tags:
  - Blender
  - papervision3d
id: 800
categories:
  - 3D
  - Flash
date: 2009-03-05 10:03:00
---

这里有三个把Blender里面材质映射（UV Mapping）好的三维物件导入Flash（通过Papervision3D渲染）的方法。
方法一：[ActionScript 3.0 exporter](http://www.rozengain.com/blog/2008/01/02/export-your-blender-objects-straight-to-away3d-papervision3d-and-sandy/) from rozengain.com (除了pv3d,还支持Sandy3D和Away3D)
步骤：
1\. [下载](http://www.rozengain.com/files/blog/blender-export/AS3Export.rar)到Windows下的这个目录: (Blender .2.48: C:Documents and Settings<username>Application DataBlender FoundationBlender.blenderscripts)
2\. [Blender](http://www.blender.org/)里面选中要导出的物件，确定是在编辑模式下，Ctrl+T让物件三角形化（triangulated）。
3\. 菜单File  -> Export -> ActionScript 3.0 Class
4\. 装入pv3d: var BlenderBox:TriangleMesh3D=new BlenderBoxClass(material...);

方法二：[XMLExporter/XMLPrimitive](http://professionalpapervision.wordpress.com/2008/12/09/new-blender-xml-exporterpv3d-xml-primitive/) from professionalpapervision.wordpress.com （应该是方法一的改良版）
步骤：
1\. [下载](http://flex3cookbook2.googlecode.com/files/exporter-primitive.zip)让后复制Python XMLExporter到和方法一一样的目录
2\. 和方法一一样的，把XML导出。利用XMLPrimitive这个Class装载。zhaiduoText = new XMLPrimitive("BlenderBox.xml",Material...);

方法三：Blender .2.48里面内置的Collada 1.4导出工具：
步骤：
1\. 菜单： File -> Export -> Collada 1.4 (.dae)
2\. 利用org.papervision3d.objects.parsers.dae导入