---
title: 'session_start(): Cannot send session cache limiter'
tags:
  - 出错
id: 342
categories:
  - PHP
date: 2008-09-22 01:51:33
---

PHP生成XML文件，莫名其妙的生成如下的错误：
> session_start(): Cannot send session cache limiter - headers already sent
检查了一下代码，确认
> header(’Content-type: text/xml’);
前面确实没有echo任何东西。
session_start()也看不出什么问题。只是提示出错的位置位于这个PHP文件的第一个字符，
(output started at xml.php:1)

试着重新将全部php代码复制到一个新文件，保存。问题解决。