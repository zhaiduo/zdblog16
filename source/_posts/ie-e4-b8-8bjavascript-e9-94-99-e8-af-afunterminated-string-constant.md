---
title: 'IE下Javascript错误:Unterminated string constant'
tags:
  - 出错
id: 344
categories:
  - javascript
date: 2008-10-24 01:48:25
---

最近总是出现很多灵异事件，快被逼疯了。一段很简单的Javascript代码
> href=”javascript:void(0);” onclick=”window.open(’http://stumbleupon.com/newurl.php?url=’+document.location.href+’&amp;
> title=’+escape(document.title));”
在IE下提示出错：Unterminated string constant
Firfox下没问题，查看IE下源文件，复制出来看，很简单，也应该不会有问题啊。有一个细节很搞笑，document.location.href+’&amp;在源文件里看后面是有换行的，可复制出来却没有。问题的根源也当然就是这个换行符罗~！