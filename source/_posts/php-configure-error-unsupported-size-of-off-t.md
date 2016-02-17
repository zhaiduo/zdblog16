---
title: php configure error unsupported size of off_t
id: 2340
comment: false
categories:
  - PHP
date: 2015-04-18 18:48:32
tags:
---

系统环境：macos 10.10.2 vbox4.3.20 centos7 php5.6
--enable-opcache出错，取消后
PHP编译时zip_add.c报错：error unsupported size of off_t

但是有意思的事，我把 --with-zilb 和 －－enable-zip单独放一行的时候，编译通过。