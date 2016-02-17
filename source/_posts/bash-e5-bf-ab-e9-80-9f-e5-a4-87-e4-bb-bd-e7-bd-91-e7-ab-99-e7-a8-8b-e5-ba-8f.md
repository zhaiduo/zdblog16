---
title: Bash快速备份网站程序
tags:
  - 备份
id: 1055
categories:
  - 网站维护
date: 2010-09-07 18:21:41
---

有个网站用的是国外的服务器，上面很多图片和页面，通过Cpanel下载网站备份超过一个G，下载下来要大半天，很没有效率。考虑到图片和程序的分离备份。用Bash写个脚本是最简单的。主要目的是打包过滤只想下载备份的文件。

脚本参考如下：
find ./public_html/ -type f ! -name  '*.jpg' ! -name '*.png' ! -name '*.gif' ! -name '*.cache' &gt; list.txt
tar -czvf backup-20100907.tar.gz --files-from list.txt

这样取出图片部分，备份文件才20多M，这才是效率～