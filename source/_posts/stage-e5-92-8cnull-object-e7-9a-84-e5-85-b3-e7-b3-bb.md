---
title: Stage和null object的关系
tags:
  - AS3
  - 出错
id: 334
categories:
  - Flash
date: 2008-09-04 16:38:49
---

最近接触flash CS3比较多，但是由于基础不好，常常被一些简单的问题搞得晕头转向。虽然从flash8和MX2004一直都有接触，但是CS3的不同到这两天才开始有所领悟。以前习惯直接在actions frame里面coding，这给之后直接用as3来coding带来了很多不习惯。

AS3里代码和源文件的分离，一段很简单的代码
> package com.zhaiduo{
> 
>   import flash.display.Sprite;
>   import flash.display.StageAlign;
>   import flash.display.StageScaleMode;
> 
>   public class Example extends Sprite {
> 
>     public function Example() {
>       stage.align = StageAlign.TOP_LEFT;
>       stage.scaleMode = StageScaleMode.NO_SCALE;
>     }
>   }
> }
就会出现如下错误：
> TypeError: Error #1009: Cannot access a property or method of a null object reference.
> 	at com.zhaiduo::Example$iinit()
> 	at learn_fla::MainTimeline/learn_fla::frame1()

后来发现这和Stage有着密切关系，新建的fla文件如果直接在actions frame里面coding，stage是[object Stage]。但是我们写在as文件里面，如果不和一个实例linkage，stage就是null。所以会出现上面的错误。
![mwsnap171.jpg](http://www.zhaiduo.com/wp-content/data/mwsnap171.jpg)