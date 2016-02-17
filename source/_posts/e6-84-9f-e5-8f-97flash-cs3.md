---
title: 感受FLASH CS3
id: 204
categories:
  - Flash
date: 2007-08-31 22:19:13
tags:
---

这两天终于有时间感受了一下[FLASH9 CS3](http://www.adobe.com/products/flash/features/allfeatures/)，感觉FLASH确实有了质的飞跃，记得04年的时候选择做Java Applet，是由于FLASH无法实现音频振幅的实时提取，一些三维效果的效率过低等等。如今已经今非昔比，特别是[<font size="-1">**Papervision 3D**</font>](http://www.papervision3d.org/)在三维实时效果上的运用几乎让人叹为观止。做了一个基于[AS3的MP3播放器](/sample/mp31.swf?mp3url=loop.mp3)玩玩，FLASH实在太好玩。

这里有一些AS3常用到的东东：

**HTML内嵌变量与SWF的传递**

HTML代码: < param name="FlashVars" value="url=file.mp3">

AS3:  var url:String=loaderInfo.parameters.url;

**禁止SWF放大缩小：**

[code lang="actionscript"]import flash.display.Stage;
import flash.display.StageAlign;
import flash.display.StageScaleMode;
import flash.events.Event;

var swfStage:Stage = this.stage;
swfStage.scaleMode = StageScaleMode.NO_SCALE;
swfStage.align = StageAlign.TOP_LEFT;[/code]

自定义菜单：

[code lang="actionscript"]
var mycd:ContextMenu=new ContextMenu();
var item:ContextMenuItem=new ContextMenuItem("zhaiduo's Menu");
mycd.hideBuiltInItems();
mycd.customItems.push(item);
item.addEventListener(ContextMenuEvent.MENU_ITEM_SELECT,openurl);
this.contextMenu=mycd;
[/code]