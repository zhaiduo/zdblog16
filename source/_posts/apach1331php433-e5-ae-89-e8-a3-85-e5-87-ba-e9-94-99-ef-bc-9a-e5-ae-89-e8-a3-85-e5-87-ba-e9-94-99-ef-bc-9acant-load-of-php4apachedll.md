---
title: "Apach1.3.31+PHP4.3.3安装出错：can't load of php4apache.dll"
id: 308
categories:
  - 安装
  - 技术研究
date: 2006-09-06 00:12:32
tags:
---

复制php.ini到系统盘windows目录下，httpdconf配置文件中增加:
> LoadModule php4_module "C:/php/sapi/php4apache.dll"
> 
> #AddModule mod_php4.c // 不用填加这一行
> 
> AddType application/x-httpd-php .php
解决办法：复制php安装目录下php4ts.dll到系统盘windows目录下。

听说apach2.2.3+php4.4也有这个问题，不过好像用这种办法无法解决。

**Update: PHP5.0.1安装(目录**C:/php5**)
**

1\. copy php.exe, php.ini 到 windows目录
2\. copy 所有DLL到system32目录
3\. 编辑httpd.conf，增加：
> AddType application/x-httpd-php .php
> LoadModule php5_module "c:/php5/php5apache.dll"
> SetEnv PHPRC C:/php5