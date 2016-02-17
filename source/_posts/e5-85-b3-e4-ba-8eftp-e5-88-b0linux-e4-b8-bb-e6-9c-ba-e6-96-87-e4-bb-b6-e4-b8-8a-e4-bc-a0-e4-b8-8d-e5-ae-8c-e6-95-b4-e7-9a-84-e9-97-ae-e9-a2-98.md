---
title: 关于FTP到Linux主机文件上传不完整的问题
tags:
  - FTP
  - 问题
id: 1426
categories:
  - Linux/Unix
  - PHP
date: 2011-10-16 18:59:59
---

遇到个有趣的情况，从XP使用FTP上传文件到vsftpd的linux系统，PHP显示源代码，而wget的PHP则可以运行。发现 所有文件的第一个字符都会丢失。例如PHP就会变成&lt;?php -&gt; ?php。同一款FTP软件也上传文件到别的Linux系统，却都没有任何问题。可以肯定的是，不关short_tag的问题，PHP解析和配置都是正常，要不wget的PHP是无法正常运行的。那就只能先假设Linux的vsftpd有问题，换成Linux系统下的FTP来mget XP的PHP文件，还是显示源代码。难道是binary，没有用二进制上传的问题？用dos2unix测试问题依旧，换成FTP binary 下载XP的PHP的文件后，发现终于可以正常运行。

&nbsp;