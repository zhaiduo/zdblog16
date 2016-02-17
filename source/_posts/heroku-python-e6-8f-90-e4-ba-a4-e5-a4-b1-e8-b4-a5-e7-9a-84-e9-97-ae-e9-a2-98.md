---
title: Heroku Python提交失败的问题
tags:
  - Heroku
  - python
  - 出错
id: 1872
categories:
  - 云时代
date: 2014-01-21 00:16:31
---

本以为nodejs搞定，在Heroku上提交python应该易如反掌，哪知又出问题：
提交时出错提示：“Push rejected, no Cedar-supported app detected”。
出现这个错误是heroku无法判断app的类型，通常python需要在app根目录下有requirements.txt这个文件。
后来发现是我的用户目录下的.gitignore里屏蔽了所有text文件，增加一行!requirements.txt后问题解决。