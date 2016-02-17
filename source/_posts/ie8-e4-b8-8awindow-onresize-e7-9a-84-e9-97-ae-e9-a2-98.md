---
title: IE8上window.onresize的问题
tags:
  - IE8
  - Javascript
id: 455
categories:
  - Uncategorized
date: 2010-01-05 13:43:21
---

今天发现IE8下window.onresize会作用于< select >上， 或者其他Form元素变形的时候.
本来有个脚本用于替换背景，
window.onresize = resize;
function resize() {
	window.location.reload();
}
可是选择select或者其他Form元素变形的时候，resize会被触发。

如果去掉
< !DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/REC-html40/transitional.dtd" >
发现没有这个问题，window.onresize没有被触发。

考虑用检测window的宽度是否发生变化，来替代window.onresize。