---
title: Windows下面php5找不到php_curl.dll的问题
id: 210
categories:
  - PHP
  - windows
date: 2007-09-27 10:30:07
tags:
---

由于要用到Curl，所以设置的时候提示这样的错误：
> unable to load dynamic library '....php_curl.dll'
我的环境是Apache/2.0.59 (Win32) PHP/5.2.3，按理说php5的安装是很简单的，直接指定extension_dir = "c:/php523/ext/"就可以了，像gd2, mysqli和mysql_dll都没问题，唯独 php_curl.dll总是提示出错。试着修改PATH路径，把DLL复制到/windows/system32/，还是提示找不到php_curl.dll。

最后，终于在php.net上找到这么一句话： Note to Win32 Users: In order to enable this module on a Windows environment, libeay32.dll and ssleay32.dll must be present in your PATH.

在php根目录找到这两个文件，复制 libeay32.dll 和 ssleay32.dll到/windows/system32/，终于搞定，phpinfo出现如下信息：
> cURL support     enabled
> cURL Information     libcurl/7.16.0 OpenSSL/0.9.8e zlib/1.2.3