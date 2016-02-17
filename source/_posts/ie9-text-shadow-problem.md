---
title: IE9下文字阴影问题
id: 1226
categories:
  - CSS
  - 网站技术
date: 2010-12-19 23:35:35
tags:
---

今天在Win7下用IE9 beta看博客的时候发现文字阴影效果很难看，和以前IE8修正CSS阴影效果前一样。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219213647.jpg "20101219213647")](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219213647.jpg)[![](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219170407.jpg "20101219170407")](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219170407.jpg)

检查发现FILTER: Shadow是罪魁祸首，去掉好看很多，透明png也正常，但是阴影效果没有了，因为IE对text-shadow都不给力。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219210952.jpg "20101219210952")](http://www.zhaiduo.com/wp-content/uploads/2010/12/20101219210952.jpg)

值得注意的一个细节是中文的阴影看起来没有问题，只是字母的阴影效果很难看。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/12/bad_shadow.jpg "bad_shadow")](http://www.zhaiduo.com/wp-content/uploads/2010/12/bad_shadow.jpg)

可惜的是没有找到完美的解决办法，介于IE下难看的字体阴影，我决定加大颜色为#666的字体颜色对比度，改为#b0b0b0，看起来好了一些。