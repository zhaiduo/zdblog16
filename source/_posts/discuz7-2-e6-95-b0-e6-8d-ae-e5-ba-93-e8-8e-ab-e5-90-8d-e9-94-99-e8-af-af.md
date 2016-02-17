---
title: Discuz7.2数据库莫名错误
tags:
  - discuz
id: 1111
categories:
  - PHP
date: 2010-10-14 00:46:57
---

客户反映Discuz论坛无法打开，经查看发现多个表格损坏和丢失
> #29 - File './cdb_adminsessions.MYD' not found (Errcode: 2)
> #1017 - Can't find file: 'cdb_bbcodes' (errno: 2)
> #29 - File './cdb_threadtypes.MYD' not found (Errcode: 2)
> cdb_forumfields,cdb_tasks,cdb_threadtags and cdb_typeoptions dosn't exist
按理说论坛访问量不大，也没有发生异常的事件，数据库表格损坏和丢失的可能性极低，目前尚不清楚是黑客原因还是空间的问题。
根据upgrade13.php升级程序的内容找回丢失和损坏的表格，一切恢复正常，好在主要的表格没有丢失和顺坏。