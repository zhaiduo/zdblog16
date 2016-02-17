---
title: Google starter kit前端开发工具
tags:
  - google
id: 2036
categories:
  - webapp
---

安装
web-starter-kit/npm install

编译
gulp

实时效果检视
gulp serve

编译前操作
编辑样式：web-starter-kit/apps/styles
脚本：web-starter-kit/app/scripts

速度测试：gulp pagespeed

更多参考：
https://developers.google.com/web/fundamentals/principles/

=========================================
发布流程：
gulp
make deploy

=========================================
Makefile：
@cp "dist/index.html" "dist/index.php"
@rm -rf "dist/index.html"
@xcopy "dist" "目标目录" /s
=========================================
遇到的问题
Can't get Gulp to run: cannot find module 'gulp-util'
需要在本地再次安装
try npm install gulp-util --save-dev
其他模块包括： module 'through2', 'object-assign', 'pretty-bytes', 'chalk', 'imagemin'