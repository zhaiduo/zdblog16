---
title: Mysql5.7 start mysqld.service失败的问题
id: 2147
categories:
  - Mysql
date: 2014-12-18 01:30:17
tags:
---

根据日志的错误提示：
innoDB pthread_create returned 13

这里给出了mysqld无法启动的相似描述：
http://community.sitepoint.com/t/cannot-set-up-innodb-support-in-mysql-due-to-pthread-create-returned-11-error/44560

系统是centos7。