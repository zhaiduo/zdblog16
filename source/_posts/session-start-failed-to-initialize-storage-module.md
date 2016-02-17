---
title: 'session_start(): Failed to initialize storage module'
tags:
  - 出错
id: 282
categories:
  - PHP
date: 2008-06-05 09:06:57
---

很多空间经常出现session_start的初始化错误，出错信息：
> Fatal error: session_start(): Failed to initialize storage module: user (path: /tmp) in /home/***.php on line 1
从错误看来是系统临时目录/tmp无法保存session文件的问题，
原则上我们可以直接修改php.ini中的session.save_handler值从'user'到'files'。但是在虚拟空间里通常都没有修改权限。这是我的解决办法：
> if(!is_dir('./tmp/'))mkdir ('./tmp/', 0700);
> session_save_path('./tmp/');
> session_start();
直接在session_start前面增加上面的内容。