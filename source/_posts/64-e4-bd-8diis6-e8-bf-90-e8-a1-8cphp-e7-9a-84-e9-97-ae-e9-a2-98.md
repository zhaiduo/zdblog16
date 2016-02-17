---
title: 64位iis6运行PHP的问题
tags:
  - IIS6
id: 1781
categories:
  - PHP
  - windows
  - 安装
date: 2013-03-26 22:45:32
---

配置好PHP+iis6环境出现如下错误：%1 is not a valid Win32 application
解决办法是运行：cscript %SYSTEMDRIVE%inetpubadminscriptsadsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1
目的让iis6支持32位运行。

如果需要支持mcrypt, mbstring组件，需要把类似libmcrypt.dll, php_mcrypt.dll的文件复制到SysWOW64文件夹下。

搞笑的是复制后，重启iis6，居然还是找不到php_mcrypt.dll。重启系统后，问题解决。