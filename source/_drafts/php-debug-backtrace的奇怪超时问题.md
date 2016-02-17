---
title: php debug_backtrace的奇怪超时问题
id: 2368
comment: false
categories:
  - PHP
tags:
---

php debug_backtrace Fatal error: Maximum execution time
原来是SQLDependency的时候，getTableType里面又使用了qArr缓存sql查询，变成死循环....