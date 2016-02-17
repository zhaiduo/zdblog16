---
title: Bash技巧
id: 199
categories:
  - Linux/Unix
tags:
---

令服务器崩溃的代码：<font class="headline">fork bomb</font>

[code lang="bash"]

: () { : | : &amp; } ; :

[/code]