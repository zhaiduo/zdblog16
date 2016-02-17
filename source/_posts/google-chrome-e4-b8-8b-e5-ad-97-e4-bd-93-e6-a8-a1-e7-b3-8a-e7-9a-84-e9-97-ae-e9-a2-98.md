---
title: Google Chrome下字体模糊的问题
tags:
  - CSS-hack
  - Chrome
  - text-shadow
id: 911
categories:
  - CSS
  - 网站技术
date: 2010-08-01 16:46:04
---

今天用Google Chrome5.0看了一下自己的博客，发现很是难看：
[![](http://www.zhaiduo.com/wp-content/uploads/2010/08/20100801010417.jpg "20100801010417")](http://www.zhaiduo.com/wp-content/uploads/2010/08/20100801010417.jpg)
我用FireFox，IE8，Safrari和Opera看过，只有Google Chrome的字体最难看，很是模糊。
起初以为是字体的问题，换成宋体、雅黑都没反应。后来分析CSS样式表文件，发现是text-shadow文字阴影效果的问题。
> text-shadow: 0px 1px 1px #000;
> FILTER: Shadow(Color=#000000, strength=1, Direction=135);
考虑到只是针对Chrome的问题，现在还找不到满意的排除Chrome的CSS Hack，只有先放弃字体阴影的效果。
取消阴影效果以后，Chrome页面中文字体显示正常。
[![](http://www.zhaiduo.com/wp-content/uploads/2010/08/20100801164345.jpg "20100801164345")](http://www.zhaiduo.com/wp-content/uploads/2010/08/20100801164345.jpg)

解决办法：
试过
text-shadow: 0px 1px 1px #000;
和
text-shadow:rgba(0,0,0,0.01) 0 0 1px;
都不行，
最后
text-shadow: #000 0 1px 0;
问题解决。