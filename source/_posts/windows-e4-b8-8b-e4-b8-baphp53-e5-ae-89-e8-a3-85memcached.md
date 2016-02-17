---
title: Windows下为PHP53安装memcached
tags:
  - memcached
id: 1885
categories:
  - PHP
date: 2014-02-25 00:31:08
---

我的环境是XP，apache2.2，php5.3.28。
先下载windows版的mamcached server: http://code.jellycan.com/files/memcached-1.2.6-win32-bin.zip

然后下载5.3.27版的php_memcache.dll：http://windows.php.net/downloads/pecl/snaps/memcache/3.0.9/php_memcache-3.0.9-5.3-ts-vc9-x86.zip

把php_memcache.dll解压，放入ext目录。把memcached.exe放在C盘memcached目录下。

以管理员身份运行DOS，安装memcached server: c:windwosmemcached -d install 然后memcached -d start。打开服务列表，能看到mamcached server已启动。

重启apache，即可测试memcached php程序。