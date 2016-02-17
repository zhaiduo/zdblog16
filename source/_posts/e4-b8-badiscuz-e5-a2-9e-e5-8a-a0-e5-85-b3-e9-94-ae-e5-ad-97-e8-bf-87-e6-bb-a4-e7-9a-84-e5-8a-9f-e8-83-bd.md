---
title: 为Discuz增加关键字过滤的功能
id: 207
categories:
  - PHP
date: 2007-09-13 21:00:31
tags:
---

最近一个朋友的[discuz](http://www.discuz.net/)论坛上的某些页面由于含有某些敏感词语而被和谐掉了，用户访问这些页面就会自动跳转到含有这样一个提示的页面：“页面含有不当的词语-XXX，请尽快删除。”，估计是空间提供商做了关键字的过滤。朋友可就麻烦了，因为想要登录到论坛后台修改那些含有被和谐内容都不行，只要页面含有那些关键字，任何网页都无法打开。我的解决办法是只有用程序自动替换被和谐的内容。

根据discuz显示内容的特点，它是通过include模板文件来生成网页，所以我们可以在include template前后做手脚，利用ob_start来控制缓存，替换点相关词语后再flush缓存的内容。

曾经想过两个比较复杂的方案，让被和谐的内容进行urlencode编码，然后用javascript来对网页上的urlencode编码进行解码。后来卡壳在javascript的解码问题上，希望以后能够解决这个问题。 另外一种办法是用图片来显示，程序自动将相关内容转成图片来显示。这两种办法应该都是可行的，碍于时间问题就先搁置一下。不知道还有其他什么好办法。