---
title: seajs开发环境搭建
id: 2021
categories:
  - webapp
date: 2014-08-15 01:42:26
tags:
---

seajs是基于[CMD规范](https://github.com/seajs/seajs/issues/242)的前端开发工具，和基于AMD的requireJs不同，seajs有着更适合国人使用习惯的使用方法。搭建好Python, nodeJs, npm, grunt开发环境后, 安装好spm2：
$ npm install spm@2.x -g
$ npm install spm-build -g

spm基于[gruntjs](http://gruntjs.com/)构建，使用更简单，复杂应用可自行配置gruntfile.js，进行编译。

windows下需要安装GNU win32的make工具, 包括make和coreutils包。（记得设置环境变量）
测试用例采用qunit环境，测试文件放入testssuites目录下，需要在seajs.use中测试。

更多参考：
seajs配置：https://github.com/seajs/seajs/issues/262