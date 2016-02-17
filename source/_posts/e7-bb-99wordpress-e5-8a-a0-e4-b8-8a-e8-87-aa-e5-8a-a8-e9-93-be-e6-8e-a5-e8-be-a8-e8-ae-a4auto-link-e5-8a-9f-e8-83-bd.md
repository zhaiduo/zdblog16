---
title: '给WordPress加上自动链接辨认[Auto-Link]功能'
tags:
  - Wordpress
  - 链接
id: 269
categories:
  - PHP
date: 2008-04-29 10:28:40
---

虽然WordPress已经发展到[Version 2.5.1](http://wordpress.org/download/)，但是我认为WP仍然缺少一个我们需要的一个十分常用而又简单的功能：自动链接辨认[Auto-Link]。很多朋友喜欢在博客里面添加很多链接，但是烦于不停的给URL路径加上链接，WP里面也暂时没有这方面的设置。我们可以自己手动做个简单修改达到这个功能：

在wp-includes目录里面找到post-template.php这个文件：

打开编辑，找到 **function get_the_content()**这个函数

在它的最后面作如下修改：

[code lang="php"]return $output;[/code]

增加为

[code lang="php"]$pattern = "/[s]http://([^s"]+)/ism";

$replacement = " [http://$1](http://$1)";

$output=preg_replace($pattern, $replacement, $output);

return $output;[/code]