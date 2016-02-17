---
title: AS3中利用EventDispatcher定义自己的事件驱动类
tags:
  - AS3
id: 338
categories:
  - Flash
date: 2008-09-11 17:46:08
---

flash.events.EventDispatcher已经给我们很好例子如果定义自己的事件驱动，那么我们在什么时候可以用得上呢？这里有一个例子：当我们装载XML的时候，XmlLoaded函数响应Event.COMPLETE事件，
> obj.addEventListener(Event.COMPLETE, XmlLoaded);
但这还不够，仅仅是表明XML装载完成，如果要通知其他实例，我们还需要设定一个自定义的事件响应。

我以前的做法是：
设置一个变量isLoad来探测XML装载完成，如果isLoad为true,函数GetXml()返回XML字符串内容
> var test:LoadXml=new LoadXml(me,"zhaiduo.xml");
> test.obj.addEventListener(Event.COMPLETE, XmlLoaded2);
> function XmlLoaded2(event:Event):void{
> trace(test.GetXml());
> }

现在可以改为：
先自定义FinishLoadingEvent类，然后在XmlLoaded函数中提交新的FinishLoadingEvent事件，
> dispatchEvent(new FinishLoadingEvent(FinishLoadingEvent.FINISH_EVENT, myXML.toXMLString()));
这样，XML装载完后，我们会得到自定义的事件，加上对这个事件的侦测，我们就可以轻易让其他实例获得XML字符串。
> test.addEventListener(FinishLoadingEvent.FINISH_EVENT, XmlLoaded3);
> function XmlLoaded3(event:FinishLoadingEvent):void{
> trace(event.source);
> }