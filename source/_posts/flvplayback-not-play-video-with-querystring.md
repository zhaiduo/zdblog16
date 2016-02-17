---
title: Flvplayback无法播放包含参数的视频网址的问题
tags:
  - 出错
id: 1565
categories:
  - AS3
  - Flash
date: 2012-05-21 02:01:48
---

最近常看Flash视频，发现视频可以正常下载，但是无法正常播放。原来是视频网址包含问号参数，出现如下错误：
> VideoError: 1005: Invalid xml: URL: "http://domain/zhaiduo.flv?sid=as92Ft32&amp;FLVPlaybackVersion=2.1" No root node found; if url is for an flv it must have .flv extension and take no parameters
> at fl.video::SMILManager/http://www.adobe.com/2007/flash/flvplayback/internal::xmlLoadEventHandler()
> at flash.events::EventDispatcher/dispatchEventFunction()
> at flash.events::EventDispatcher/dispatchEvent()
> at flash.net::URLLoader/onComplete()
网上解决办法有三个：

*   直接修改FLVPlayback的源文件 ([来源](http://www.actionscript.org/resources/articles/995/1/Writing-a-Custom-YouTube-Player-for-a-Google-Gadget/Page1.html))，在665行：
if ( name.indexOf("?") &lt; 0 &amp;&amp;
to
if ( name.indexOf(".flv") &gt; 0 &amp;&amp;

    失败：修改ncmanager.as后出现更多错误，例如：DynamicStream.as, Line 368    1020: Method marked override must override another method，貌似是FLVPlayback的版本不对。
*   用URL重写，把?和参数伪静态：
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_URI} ^/video/(.*)$
RewriteRule ^video/(.*)$ http://$1 [R=301,L]
虽然重写成功，但是得到的视频是403 forbidden，貌似视频网址有安全防范。
*   重写FLVPlayback
我都尝试了，最后用[NetConnection](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/NetConnection.html)和[NetStream](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/NetStream.html)重新定制了一个简单的Flv player才把问题解决。