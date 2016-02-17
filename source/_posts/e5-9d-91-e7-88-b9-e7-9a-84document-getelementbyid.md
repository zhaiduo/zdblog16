---
title: 坑爹的document.getElementById
id: 1413
categories:
  - javascript
date: 2011-10-10 05:32:53
tags:
---

document.[getElementById](https://developer.mozilla.org/en/DOM/document.getElementById)作为返回DOM元素对象的快速方法给大家带来很多方便。而且当DOM元素不存在的时候，getElementById就不会返回该元素对象的引用而是NULL。如果不自己进行返回的检查，NULL后面的语句将无法执行。

有趣的是getElementById返回的NULL在for循环下将自动退出，类似于break的效果。不得不说这是一个hack for break。而且Javascript错误控制台也不会有任何错误和警告。这就坑爹啦，一旦出现问题，将很难被发现。