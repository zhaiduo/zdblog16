---
title: 'PHP5.3.0==deprecated ^_^!'
tags:
  - 升级
id: 813
categories:
  - PHP
date: 2009-07-24 16:53:00
---

今天把内容管理系统升级,PHP升到5.3.0-windows-VC6版本，Apache升到2.2.11，Mysql升到5.1。安装过程很顺利，可是装好后，通过浏览器访问就一片混乱了，真是抓狂！

主要原因是5.3放弃了一些常用的函数：

ereg_replace() is deprecated
 All ereg*-functions will be deprecated
split() is deprecated
 All POSIX Regex function will be deprecated in PHP 5.3\. 
set_magic_quotes_runtime() is deprecated
mysql_escape_string() is deprecated
session_register(), session_unregister(), and session_is_registered() are now deprecated. 
 Use the $_SESSION superglobal array instead.

更多放弃和更新可以看这里：[http://cvs.php.net/viewvc.cgi/php-src/UPGRADING?revision=PHP_5_3](http://cvs.php.net/viewvc.cgi/php-src/UPGRADING?revision=PHP_5_3)