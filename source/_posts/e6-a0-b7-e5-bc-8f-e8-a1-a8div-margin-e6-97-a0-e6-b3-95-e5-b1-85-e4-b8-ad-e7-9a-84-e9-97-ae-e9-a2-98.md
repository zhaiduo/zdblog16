---
title: 样式表DIV Margin无法居中的问题
tags:
  - bootstrap
  - 问题
id: 1685
categories:
  - CSS
date: 2012-07-31 00:48:42
---

最近在为客户把PSD文件转成网页，可是基本样式已经确定了后，客户又要求加入Bootstrap框架，提供bootstrap.css，网页样式需要包括新旧三方CSS样式，在新旧样式夹杂的情况下，状况百出，有些哭笑不得。

旧的网页还在用xhtml1-transitional，却又偏偏夹杂着洋气的bootstrap。姑且我们不看Firefox13下bootstrap.css里面造成的密密麻麻的CSS样式警告。仅仅是在DIV居中的定义上，已经让我大跌眼镜。有个独立的DIV，作为container容器，需要固定宽度居中显示，懂点CSS的人都知道用margin:0 auto;就可以搞定。可就在新旧样式的夹杂下，Firefox、Chrome、IE8却偏偏不是固定宽度居中，而是100%显示。搞笑的是IE6和IE7却很配合，乖乖得居中。最后不得不在DIV前多加一个clear:both才解决了问题。

关于：bootstrap.css里面造成的密密麻麻的CSS样式。我发现大部分是“未知属性 '-moz-border-radius'。  声明被丢弃。”错误。
根据[这里](http://forums.mozillazine.org/viewtopic.php?f=9&t=2485853)的解释：Freifox4以后Firefox支持直接border-radius和box-shadow的定义，而不再需要使用“-moz”。

Bootstrap是个很好的前端框架，美观、规范，可以让人学习到前端制作需要掌握和注意的方方面面。但是就这样草草率率的将Bootstrap揉进现有的网页，确实有欠考虑。用它之前还是多去[了解它](https://github.com/twitter/bootstrap/)。