---
title: 用Curl登录Plesk后台备份文件
id: 474
categories:
  - PHP
date: 2010-01-11 12:23:46
tags:
---

Plesk很不厚道，备份文件不能轻易用压缩软件解压，很不方便。之前我也用过[outlook的办法解压plesk备份文件](http://www.zhaiduo.com/2008/12/windowsplesk.html)，不过这个方法在系统升级后已经失效。

我们可以用PHP的Curl模块备份网站文件。
其主要思想是通过Curl直接抓取https后台下，file manager中的文件。
备份环境：Apache/2.2.11 (Win32) SVN/1.5.6 PHP/5.3.0 DAV/2
主要Curl代码如下
> $ch = curl_init();
> 
> //https支持
> curl_setopt($curl, CURLOPT_HTTPAUTH, CURLAUTH_ANY);
> curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
> curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 2);
> 
> curl_setopt($ch, CURLOPT_URL, $url); //plesk 后台路径
> curl_setopt($ch, CURLOPT_USERPWD, USERNAME.':'.PASSWORD); //plesk 后台用户名，密码
> 
> curl_setopt($ch, CURLOPT_HEADER, 1); //输出header部分
> curl_setopt($ch, CURLINFO_HEADER_OUT, 1);
> curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
> 
> if ($method == 'POST') {
> curl_setopt($ch, CURLOPT_POST, 3);
> curl_setopt($ch, CURLOPT_POSTFIELDS, $vars); //post提交的urlencode数据
> }
> $data = curl_exec($ch);
> curl_close($ch);