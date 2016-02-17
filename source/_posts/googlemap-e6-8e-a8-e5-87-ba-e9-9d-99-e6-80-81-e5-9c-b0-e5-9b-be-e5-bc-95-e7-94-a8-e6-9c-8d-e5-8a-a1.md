---
title: GoogleMap推出静态地图引用服务
id: 240
categories:
  - Google与Idea
date: 2008-02-22 13:39:50
tags:
---

曾经想过通过javascript调用Google Map的麻烦性，因为考虑到调用地图无非就是想显示相关地图而已，不需要太多的动态脚本功能，Google的动作还真快，[静态地图的引用服务](http://code.google.com/apis/maps/documentation/staticmaps/)已经推出。

http://maps.google.com/staticmap?center=23.137913,113.321185&amp;zoom=9&amp;size=200x200&amp;/
maptype=roadmap&amp;markers=23.137913,113.321185,reda|23.167913,113.361185,greenb&amp;/
key=API-KEY
![staticmap.gif](http://www.zhaiduo.com/wp-content/data/staticmap.gif)

通过指定经纬度，放大尺度，图片大小，地图类型，锚点标识以及调用需要的API KEY，我们很容易轻松的调用你所需要的地图，不足的地方是地图不能显示卫星地图，并且有调用限制（每人每天限制1000张地图调用），另外就是中国的地图没什么内容哦。看看纽约的地图，真是不同哦：
![staticmap2.gif](http://www.zhaiduo.com/wp-content/data/staticmap2.gif)