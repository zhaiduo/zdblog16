---
title: Mysql查询错误：Illegal mix of collations
tags:
  - 出错
  - 问题
id: 1737
categories:
  - Mysql
  - PHP
date: 2012-11-28 09:39:58
---

UTF编码的Query like查询latin1的数据表时会出现如下错误：

Mysql Errors:

Illegal mix of collations (latin1_swedish_ci,IMPLICIT) and (utf8_general_ci,COERCIBLE) for operation 'like'

解决办法是加上set names latin1。