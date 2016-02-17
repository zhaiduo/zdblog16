---
title: IIS6返回Bad Request (Invalid Hostname)的问题
tags:
  - IIS6
  - 问题
id: 1406
categories:
  - windows
  - 网站维护
date: 2011-10-08 21:27:31
---

一款新的云主机系统需要安装IIS6+PHP+Mysql的环境。可以一切准备就绪后发现打开网页是：Bad Request (Invalid Hostname)。

IIS6和系统配置IP并没有不同，也确定域名没有解析错误。后来用netstat -an发现IP居然是10.0开头，看来是主机没有绑定系统配置的IP。

打开网络链接属性查看，果然IP段是自动选择，设定IP段后，问题解决。

发现一个有趣的现象：这款国内公司提供的所谓的云主机，CPU有2.4G，内存1G。可用起来的感觉和1.8G CPU/512内存的VPS差不多，真是开眼界。

另外如果在Mysql 安装向导设置过程中出现如下错误：
> 终结点映射器中没有更多的终结点可用 error code $00800706D9
最好不要勾选Firewall对端口3306的忽略。