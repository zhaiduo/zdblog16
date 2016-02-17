---
title: "Js Err: 'button[].type' is null or not an object"
tags:
  - Ajax
id: 209
categories:
  - Uncategorized
date: 2007-09-14 18:19:36
---

今天作一个ajax的project遇到一个有趣的问题，由于用惯了PHP，我喜欢在array的最后一项后面加上逗号，而且一直也没出现什么差错。写javascript的时候我还是按照这样的习惯，FireFox也没提示任何的JS运行错误。不料终于在IE上遇到了问题，出现了下面的错误：
![](http://www.zhaiduo.com/wp-content/data/mwsnap098.jpg)
试着把逗号去掉，问题解决。看来IE还是很死板的来解析javascript。不过这也可以看作是Javascript在IE和基于Mozilla的浏览器之间的一点[区别](http://developer.mozilla.org/en/docs/Migrate_apps_from_Internet_Explorer_to_Mozilla#JavaScript_differences)。回想起来，别看这个问题很小，还真花了我2个小时的时间，有些时候还真让人歇斯底里，觉得好像是老天爷故意在和你作对一样，挠破头皮也没辙。不过也应该是自己的水平还有待提高。^_^!