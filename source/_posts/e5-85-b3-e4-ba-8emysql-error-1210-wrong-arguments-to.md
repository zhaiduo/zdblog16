---
title: '关于Mysql Error “#1210 - Wrong arguments to”'
id: 177
categories:
  - Mysql
date: 2007-06-27 21:17:48
tags:
---

今天有个朋友把discuz从4.0升级到5.5，不料还没装好，运行正常的旧论坛竟然出现了下面的错误：

_SQL: UPDATE tb_stats SET count=count+1 WHERE (type='total' AND variable='hits') ...
Error: Wrong arguments to =
Errno.: 1210 _

初以为是安装新的table覆盖了旧的，吓出一身冷汗。通过分析counter.inc.php，发现注释掉那一行SQL后，论坛可以看见了，但是是乱码。进数据库看看，发现旧论坛的table是lantin1的编码，而新论坛是gbk，难道安装新论坛修改了数据库默认的字符设置？现在还不敢肯定。

Mysql.com也对 **#1210 - Wrong arguments to** [错误作出了解释](http://bugs.mysql.com/bug.php?id=321)，看来的确是编码的问题。

_**1\. Specify that the string is in latin1 too:
SELECT * FROM test WHERE name=_latin1'bla';**_

_**2\. Convert the string from utf8 to latin1:
SELECT * FROM test WHERE name=CONVERT('bla' USING latin1);**_目前还不清楚旧论坛该怎么处理。再看看有什么解决办法。
问题已解决：很简单：

ALTER DATABASE `yourdatabase` DEFAULT CHARACTER SET latin1;

另外: discuz安装程序没有考虑到向下的兼容，这是不足。 造成在4.0的mysql中安装时出现很多问题。之所以数据库默认字符被修改，就是因为下面在install.php中的这一句：

CREATE DATABASE IF NOT EXISTS `$dbname` DEFAULT CHARACTER SET $dbcharset

哪怕数据库已存在， DEFAULT CHARACTER SET 仍然有效执行。