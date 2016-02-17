---
title: 奇怪的Discuz论坛错误：Current template file not found or have no access
tags:
  - discuz
id: 1410
categories:
  - PHP
date: 2011-10-09 03:29:10
---

Discuz!论坛换到新的服务器出现一个令人诡异的错误：
> Current template file '././templates/default/discuz.htm' not found or have no access!
经过细密排查，发现并非文件权限和文件是否存在的问题。而是DISCUZ_ROOT出现了一个怪怪的问题：

在include/template.func.php里面的函数function parse_template($tplfile, $templateid, $tpldir)，里面有两句：
> if(!@$fp = fopen($tplfile, 'r')) {
> dexit("Current template file './$tpldir/$file.htm' not found or have no access!");
> }
发现DISCUZ_ROOT的路径是E://...，此为正确路径，而$tplfile的路径竟然变成了D://，服务器D盘是光驱，自然会找不到。

至于这个$tplfile什么时候跳成D的，很是诡异，暂时没有发现源头。难道是万圣节快到？^_^!

解决办法可以加个preg_match匹配替换错误的D路径，论坛一切正常。