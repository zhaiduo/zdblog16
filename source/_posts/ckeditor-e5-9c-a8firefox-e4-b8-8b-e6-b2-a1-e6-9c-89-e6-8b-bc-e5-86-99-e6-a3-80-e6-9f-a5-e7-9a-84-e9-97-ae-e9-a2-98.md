---
title: Ckeditor在Firefox下没有拼写检查的问题
tags:
  - CKEditor
id: 1361
categories:
  - javascript
date: 2011-05-30 09:58:59
---

根据文档解释，Ckeditor在Firefox下的拼写检查是被禁止掉的，可以通过在ckeditor.config.js配置文件里面增加

`config.[disableNativeSpellChecker](http://docs.cksource.com/ckeditor_api/symbols/CKEDITOR.config.html#.disableNativeSpellChecker) = false;`

来重新激活Firefox下的拼写检查。