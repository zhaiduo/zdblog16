---
title: Js版WMA的media player播放器插件
id: 98
categories:
  - javascript
  - 窄多废话
date: 2007-01-02 14:19:46
tags:
---

在网页中快速插入音乐播放器，可以很方便的在博客中引用好听的wma音乐。主要javascript代码如下：
> var url="";
> var url_string=document.location.href;var re = new RegExp("url=(.+)","ig");
> var arr = re.exec(url_string);var mString=RegExp.$1;
> if(mString.match(/^http:///i) && mString.match(/.wma$/i)){url=mString;}
> var width=350;var height=68;
> 
> 然后write media player播放器的code...你可以自行替换wma，从而可以播放其他格式的音乐文件，如：mp3。
点击查看wmaplayer.html的内容：[wmaplayer.html](http://www.zhaiduo.com/wp-content/data/mediaplayer.html)
<iframe width="350" height="68" frameborder="0" marginwidth="0" marginheight="0" src="http://www.zhaiduo.com/wp-content/data/mediaplayer.html?url=http://fs9.139.com/0/438/andy258/share/200651921811230.wma"> </iframe>

引用方法: <font color="red">
《iframe width="350" height="68" frameborder="0" marginwidth="0" marginheight="0" xsrc="http://www.zhaiduo.com/wp-content/data/mediaplayer.html?url=wma文件地址"》 《/iframe》</font>