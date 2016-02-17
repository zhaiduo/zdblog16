---
title: mysql_real_escape_string在PHP5.2.9上的问题
tags:
  - 问题
id: 1320
categories:
  - PHP
date: 2011-03-17 00:42:04
---

按理说，mysql_escape_string和mysql_real_escape_string一样，除了mysql_real_escape_string接受的是一个连接句柄并根据当前字符集转移字符串。mysql_escape_string() 并不接受连接参数，也不管当前字符集设定。

可是今天却被我发现了问题，测试环境如下：
* Apache/2.0.63 (Unix)
* MySQL 客户端版本: 5.0.77
* PHP5.2.9
* MySQL 字符集:  UTF-8 Unicode (utf8)
在转义一个中文单词“碧桂园”的时候发现被转义成乱码，倒数第二节字符后被插入5c，成了著名的5c漏洞(单引号转义漏洞：0xbf27 addslashes 转换后变为 0xbf5c2)。连接句柄和数据库都是utf8码，看不出有任何问题。换个环境PHP5.2.17并没有发现问题。
[![碧桂园](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110316235704.jpg "20110316235704")](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110316235704.jpg)
有趣的是PHP5.2.9的时候用mysql_escape_string却没有出现问题。看来要注意检测中文字符后的5c转义问题。