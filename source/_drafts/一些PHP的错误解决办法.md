---
title: 一些PHP的错误解决办法
tags:
  - 出错
id: 1881
categories:
  - PHP
---

函数 mcrypt_create_iv($length, MCRYPT_DEV_URANDOM) 提示 Cannot open source device 错误：原因在于在Windows下该函数只适用于PHP版本大于等于5.3的时候。之前只能用MCRYPT_RAND。