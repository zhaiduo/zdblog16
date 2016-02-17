---
title: 把博客换到云主机
tags:
  - 云主机
  - 网站搬家
id: 1461
categories:
  - 网站维护
date: 2011-12-29 09:16:04
---

最近博客慢得要死，正愁没办法。惊喜地发现[Godaddy推出云主机服务](http://affiliate.godaddy.com/redirect/EA4455117A5CB5FB5E33DA3674C9E989EDD6872BAB9614FF663843297F08EDD6EE680DBB8BFB7F20CBEEAA91E9764C84 "Cloud hosting")，因为最近有看到一个博客也用的最新的[Godaddy云主机](http://affiliate.godaddy.com/redirect/EA4455117A5CB5FB5E33DA3674C9E989EDD6872BAB9614FF663843297F08EDD6EE680DBB8BFB7F20CBEEAA91E9764C84 "Cloud hosting")做博客，速度很快，所以毫不犹豫的下了单，一个月最便宜只要$3.74/mo，服务器是AP，亚洲太平洋地区。

但是云主机配置好后，使用FTP却让我有些失望，家里ADSL的4M，FTP上传只有可怜的2K/s左右，还好云主机支持SSH，本来打算用scp或者sftp来转移博客，不过都被connection refused。最后只有tar打包，使用wget下载。终于看到满意的1.2M/s。

博客转移完毕发现速度并没有想象的快，不过比原来好很多，期待云主机给我更多的惊喜～