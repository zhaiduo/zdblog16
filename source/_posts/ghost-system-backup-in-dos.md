---
title: Dos下的ghost备份
tags:
  - dos
  - ghost
  - 备份
id: 1185
categories:
  - 电脑
date: 2010-11-19 12:08:55
---

虽然dos已经很少人用，但是并不多余；虽然ghost已经有了14.0的版本，但是很不爽它在系统长期驻存。虽然现在有很多高级备份方法，但是还是被巨大的备份文件所吓到。最终还是比较恋旧，而且不是我一个人喜欢～执着于dos来ghost备份系统的方案。存档记录一下，看看这种系统备份方法还能用多久。
这种系统方案需要以下两个条件：

*   一个20G的FAT32分区
如果要备份的C盘超过30G，超过FAT32分区支持的最大空间，也可以把备份空间转成NTFS格式。dos下运行dos4ntfs即可访问NTFS分区。
*   两个软件HS-GHOST v8.2和vFloppy，前者是dos下ghost系统用，后者虚拟软驱用于启动系统进入DOS。
当然XP的光盘版WIN PE也很好用，也可以用它进入PE，直接用它里面的ghost还原系统。
备份系统过程：

创建20G的FAT32分区-&gt;把HS-GHOST v8.2和vFloppy复制到fat32分区，安装vfloopy，重启系统-&gt;选择vFloopy进入dos-&gt;进入ghost.exe-&gt;

local-&gt;partition-&gt;to image

还原系统过程差不多，只是在ghost的时候选择local-&gt;partition-&gt;from image就可以了。