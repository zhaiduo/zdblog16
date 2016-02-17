---
title: WordPress3升级导致博客scheduled maintenance
tags:
  - Wordpress
  - 问题
id: 880
categories:
  - 网站维护
date: 2010-07-27 23:47:46
---

今天升级WordPress3的一个插件，其间升级到一半网页就没有响应，刷新一下，网页变成了下面的提示：

Briefly unavailable for scheduled maintenance. Check back in a minute.

根据[WP的解决办法](http://wordpress.org/support/topic/349036)，问题出在插件更新没有完成，程序自动在根目录下生成.maintenance而没被删除，所以导致wp-settings.php里面的

// Check if we're in maintenance mode.
wp_maintenance();

生效，整个博客都无法打开，出现维护中的字样。

解决办法是直接删除.maintenance文件或者注释掉wp-settings.php里面的wp_maintenance();