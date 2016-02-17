---
title: WP里面tag cloud的中文显示问题
tags:
  - Wordpress
  - 出错
id: 264
categories:
  - PHP
date: 2008-04-12 00:03:00
---

Wordpress2推出的[tag cloud功能](http://codex.wordpress.org/Template_Tags/wp_tag_cloud)确实不错，不过最热门的tag显示字体大的太过难看。

![tag_clouds.jpg](http://www.zhaiduo.com/wp-content/data/tag_clouds.jpg)

修改办法：编辑PHP源文件：[wp-includes/category-template.php](http://trac.wordpress.org/browser/trunk/wp-includes/category-template.php?rev=6824)

找到function: wp_generate_tag_cloud里面的这么一项：
`( $smallest + ( ( $count - $min_count ) * $font_step ) )`
修改为：
`( $smallest + ( ( $count - $min_count ) * $font_step ) * 0.3 )`
其中的0.3是为了缩小最大的TAG尺寸，大家可以根据自己喜好设定比例。