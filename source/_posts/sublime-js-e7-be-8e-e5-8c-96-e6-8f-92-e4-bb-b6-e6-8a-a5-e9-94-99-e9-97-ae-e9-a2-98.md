---
title: Sublime JS美化插件报错问题
tags:
  - sublime
id: 2399
comment: false
categories:
  - 前端
date: 2015-12-30 23:35:35
---

报错信息如下：

`ImportError: No module named 'six'`

根据[这里](https://github.com/enginespot/js-beautify-sublime/issues/39)的办法，问题搞定：

Full steps to fix (incorporates 2 separate comments above):

Select Package Control and then Add Repository
Copy/Paste/Enter the URL: https://github.com/fyelles/js-beautify-sublime and hit enter
Select Package Control and Remove Package: Javascript beautify
Select Package Control and Install Package (Note Different Name): js-beautify-sublime