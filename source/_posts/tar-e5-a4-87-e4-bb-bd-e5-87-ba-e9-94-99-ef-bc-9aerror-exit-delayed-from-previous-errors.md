---
title: tar备份出错：Error exit delayed from previous errors
tags:
  - 出错
  - 备份
id: 1624
categories:
  - Linux/Unix
  - 网站维护
date: 2012-06-20 20:45:18
---

用tar备份网站出现错误：
tar: Error exit delayed from previous errors
记录tar输出：
tar -zcvf zhaiduo.com.tar.gz zhaiduo.com/ > temp.log
出现提示错误：
tar: public_html/some.html: Cannot open: Permission denied
tar: Error exit delayed from previous errors

chmod后问题解决。