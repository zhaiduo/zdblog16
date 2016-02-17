---
title: spmjs运行构建命令出错
tags:
  - seajs
  - spm
id: 2249
comment: false
categories:
  - 前端
date: 2015-03-06 15:35:56
---

npm update以后，运行spm build提示：
spm Deprecated: buildArgs.include is deprecated, using sea, standalone and umd instead.:

构建失败。貌似spm不小心被升级为3的版本。

试着重装spm@2.x
cnpm cache clean 清理缓存
cnpm uninstall spm -g 卸载模块
cnpm uninstall spm@2.x -g 卸载模块

cnpm install spm@2.x -g
cnpm install spm-build@0.x -g

spm build
//////////////
....
Done: without errors.

问题解决。

更多参考：
迁移 spm2 的模块到 spm3
https://github.com/spmjs/spm/wiki/%E8%BF%81%E7%A7%BB-spm2-%E7%9A%84%E6%A8%A1%E5%9D%97%E5%88%B0-spm3