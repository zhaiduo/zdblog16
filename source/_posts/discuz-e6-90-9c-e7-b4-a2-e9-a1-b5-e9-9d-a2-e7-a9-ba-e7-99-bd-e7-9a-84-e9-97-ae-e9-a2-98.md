---
title: Discuz搜索页面空白的问题
tags:
  - discuz
id: 1134
categories:
  - PHP
date: 2010-11-02 13:20:31
---

Discuz论坛换服务器后，客户报告搜索页面不法使用，一片空白。由于其他服务一切正常，没有明显错误迹象也没有任何改动。也没有任何错误提示，于是不得不从global.func.php和template.func.php进行追踪，发现最后问题出在function parse_template的preg_replace上，这才恍然大悟原来是[曾经遇到过的问题](http://www.zhaiduo.com/2010/07/preg-replace-error-regular-expression-is-too-large/)，也就是preg_replace被pcre.backtrack_limit限制的问题，直接修改php.ini里面pcre.backtrack_limit，增大数额，重启服务器，删除旧的缓存文件1_search.tpl.php，问题解决。