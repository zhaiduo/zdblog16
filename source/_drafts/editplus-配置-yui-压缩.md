---
title: editplus 配置 yui 压缩
tags:
  - 前端
id: 1916
categories:
  - javascript
---

配置工具栏
命令：java
参数：-jar "F:/yui/yuicompressor-2.4.8.jar" --type $(FileExt) --charset utf-8 "$(FileName)" -o "$(FileNameNoExt)-min.$(FileExt)"
初始目录：$(FileDir)