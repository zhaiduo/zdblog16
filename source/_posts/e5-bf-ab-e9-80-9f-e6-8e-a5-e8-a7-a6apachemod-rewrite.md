---
title: '快速接触apache:mod_rewrite'
id: 329
categories:
  - 安装
  - 技术研究
date: 2006-11-03 08:55:39
tags:
---

试验[mod_rewrite](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)环境：windowsXP Pro + apache2.0.59 + php5.1.6
修改httpd.conf:

LoadModule rewrite_module modules/mod_rewrite.so

修改 AllowOverride All
在root目录创建.htaccess
> RewriteEngine on
> RewriteRule ^([0-9a-z-]+).html$ $1.php [L]  //所有0-9a-z包含-字母的html映射到php文件。
测试OK。