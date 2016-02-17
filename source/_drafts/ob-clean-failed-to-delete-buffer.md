---
title: ob_clean的failed to delete buffer错误
tags:
  - 出错
id: 1458
categories:
  - PHP
---

使用ob_clean出项如下错误：
ob_clean() failed to delete buffer. No buffer to delete.
解决办法：
if (count(ob_list_handlers()) > 0) {
    ob_clean();
}