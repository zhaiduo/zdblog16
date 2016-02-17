---
title: 网站被墙在国外的Mysql数据库备份方案
tags:
  - 备份
  - 打不开
id: 786
categories:
  - Mysql
date: 2008-12-27 01:20:00
---

不知道大家有没有这样的经历：刚买的国外虚拟主机，网站做好还没有来得及备份就被GFW"墙"了起来。但是没有备份数据的网站是很不稳妥的。辛苦做好的网站如何花最少的钱、或者不用装软件就可以轻松备份呢？

这里有一个有个办法，步骤如下：
1、找一个可以通过FTP访问被墙网站W的服务器A
2、在服务器A上编写PHP的FTP脚本B，任务是把Mysql备份脚本C上传到被墙网站W，
3、在服务器A上编写PHP的FTP脚本C，任务是执行Mysql备份脚本C
> $backup=exec("/usr/bin/mysqldump --opt --host=localhost --user=dbuser --password=dbpasswd dbname > backup.sql");4、在服务器A上编写PHP的FTP脚本D，任务是把备份文件(backup.sql)下载到服务器A。

当然这些都可以全部用PHP来实现。简单运行脚本就可以轻松完成备份操作。