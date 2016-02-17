---
title: 保护页面内容的好办法
id: 317
categories:
  - javascript
  - 技术研究
date: 2006-09-29 13:24:32
tags:
---

[Yahoo! Hack Day](http://hackday.org/)首页有一段有趣的Javascript代码：
> function tick()
> {
> if(document.getElementById('d0'))
> {
> var pp=[];
> for(var i=0;i<4;i++)
> {
> var d='d'+i;
> if (document.getElementById(d))
> {
> pp[i]=parseInt(document.getElementById(d).innerHTML);
> }
> }
> pp[0]--;
> if (pp[0]<0){
> pp[0]=59;
> {
> pp[1]--;
> if (pp[1]<0)
> {
> pp[1]=59;
> pp[2]--;
> if (pp[2]<0)
> {
> pp[2]=23;
> pp[3]--;
> if (pp[3]<0)
> {
> document.location.reload();
> }
> }
> }
> }
> }
> document.getElementById('d0').innerHTML = pp[0];
> document.getElementById('d1').innerHTML = pp[1];
> document.getElementById('d2').innerHTML = pp[2];
> document.getElementById('d3').innerHTML = pp[3];
> }
> }
> 
> window.onload = function() {
> setInterval("tick()", 1000);
> };
将一段打乱的文字在一秒后自动恢复原貌。觉得这是一个很好的防止搜索引擎收录的好办法，页面上存放的是杂乱的无序的hack后的文字，搜索引擎收录的是毫无意义的杂乱文字，从而保护了页面中的真实内容。当页面装载完全，再由javascript还原本来刻度的面目。不错！好好研究研究。