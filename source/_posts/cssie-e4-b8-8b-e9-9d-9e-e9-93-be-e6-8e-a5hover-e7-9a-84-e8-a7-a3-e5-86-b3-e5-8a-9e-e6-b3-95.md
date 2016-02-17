---
title: 'CSS:IE下非链接HOVER的解决办法'
id: 206
categories:
  - CSS
date: 2007-09-12 16:50:52
tags:
---

IE下CSS样式表只支持A的HOVER效果，这里有一个解决办法让IE和其他浏览器一起痛快地HOVER：
[code lang="css"]
<style type="text/css">
span.collapse {
padding:8px;background:url(icon.png) no-repeat 0 -200px;
m: expression(this.onmouseover =  new Function("this.className = 'collapse-hover';"));
}

span.collapse:hover,
span.collapse-hover {
padding:8px;background:url(icon.png) no-repeat 0 -150px;
m: expression(this.onmouseout = new Function("this.className = 'collapse';"));
}

</style>
<span class="collapse">None A Hover Test</span>
[/code]