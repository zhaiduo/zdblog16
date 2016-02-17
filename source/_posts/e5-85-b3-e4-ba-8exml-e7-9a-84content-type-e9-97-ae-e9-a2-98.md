---
title: 关于XML的content-type问题
tags:
  - XML
id: 301
categories:
  - 技术研究
date: 2006-08-15 16:24:46
---

我们一般用content-type: text/xml来作为XML文件作为header输出，不过可能有些浏览器无法正常下载。**Pete向我们建议：**

if the user agent contains Mozilla.
So for IE, Firefox, and Safari 1.x my feed will be served in **text/xml**

other clients will get the proper **application/rss+xml** MIME type.
Here's the PHP code:
> if(preg_match('/mozilla/i',$_SERVER['USER_AGENT'])){
> header('content-type: text/xml');
> }else{
> header('content-type: application/rss+xml');
> }
**好像有问题，WP里面没办法加入带有"<和>"的代码？也不能加颜色，怎么办？<font color="red">更新：已解决</font>**