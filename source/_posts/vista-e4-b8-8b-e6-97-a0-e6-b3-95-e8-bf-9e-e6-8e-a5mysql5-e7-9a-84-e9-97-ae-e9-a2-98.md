---
title: Vista下无法连接Mysql5的问题
tags:
  - Mysql
  - PHP
  - vista
id: 434
categories:
  - Mysql
  - PHP
date: 2009-12-13 09:54:15
---

没想到在Vista SP2 下安装Mysql5会遇到麻烦，安装过程都很顺利，Dos下访问mysql也完全没问题。可是通过Apache访问phpmyadmin就是不行，提示如下错误：
A connection attempt failed because the connected party did not (trying to connect via tcp://localhost:3306)

开始以为是mysql的版本问题，我先装的是5.1, 然后是5.43、5.0，均出现同样的问题。也根据网上流传的Vista下Mysql5.0无法运行的帖子，试过用ResHacker.exe修改MySQLInstanceConfig.exe，还是没能解决。

后来检查过VIsta的防火墙设置，3306端口已经打开，没有发现问题。开始估计问题出在 PHP脚本上，根据[mysql_connect](http://www.php.net/function.mysql-connect)的官方解释：
Note: Whenever you specify "localhost" or "localhost:port" as server, the MySQL client library will override this and try to connect to a local socket (named pipe on Windows). If you want to use TCP/IP, use "127.0.0.1" instead of "localhost". If the MySQL client library tries to connect to the wrong local socket, you should set the correct path as Runtime Configuration in your PHP configuration and leave the server field blank.

把localhost改为127.0.0.1，一起正常～