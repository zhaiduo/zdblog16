---
title: 开发ShopEx Widget版块
tags:
  - shopex
  - 商城开发
  - 模板定制
id: 1282
categories:
  - PHP
  - 网站技术
date: 2011-01-19 02:17:36
---

根据客户的要求，需要给ShopEx商城定制一个产品展示橱窗的版块，这是我第一次做ShopEx的Widget版块开发，感觉费了点周章。不过总算开发成功，说说我的感受。
[![](http://www.zhaiduo.com/wp-content/uploads/2011/01/20110119002035.jpg "20110119002035")](http://www.zhaiduo.com/wp-content/uploads/2011/01/20110119002035.jpg)

首先要进行ShopEx的二次开发，需要掌握一些额外的技术：

1.  [MooTools](http://mootools.net/docs/core) Javascript脚本库
2.  PHP [Smarty](http://www.smarty.net/docs/en/index.tpl)模板技术
3.  ShopEx的Widget和Theme的架构原理、目录结构
Widget文件：_config.html default.html widgest.php widget_cfg_yourwidget.php widget_cfg_yourwidget.php
Theme文件：index.html theme.xml info.xml
系统模板：core/shop/view和controller
其次需要认识ShopEx模板和Widget版块之间的关系。ShopEx模板有个主要特点是模板文件主要勾勒网页框架，而大部分细节的模板部分都放到Widget内部，这就是所谓的版块。

另外再加上一些小窍门，Widget版块的开发可以说是得心应手，水到渠成啦～
例如：

快速连接数据库：$db = &amp;$this-&gt;system-&gt;database();

Mootools：
$$('.class').addEvent('click', function(){})
$(this).getParent().getStyle('height').toInt()
$(this).getFirst("div")
$(this).innerHTML=""
$$('.link').each(function(e){})

不过在我开发的过程中，调试模板花了一些时间，没有错误提示很难追踪错误源头。把}&gt;漏掉了一个&gt;还真不好找。

还有一个兼容性问题，Mootools在Ie9 Beta下，return document.id(this.createElement(a)).set(b)出现这样的错误“script5022: exception thrown and not caught”，但是在IE9的兼容模式下一切正常。