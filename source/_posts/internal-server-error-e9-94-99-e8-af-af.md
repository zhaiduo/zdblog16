---
title: Internal Server Error错误
tags:
  - cms
  - 出错
id: 1505
categories:
  - PHP
date: 2012-03-28 23:07:49
---

今天客户的网站突然出现莫名的Internal Server Error错误，经过分析，排除了服务器和rewrite的配置错误。最后在检查CMS的缓存系统时发现是缓存id出了问题，出现貌似1.0E+19的id号，从而导致系统获取缓存失败。经过var_dump确认系统可以接受的最大整数就是1.0E+19-1，而我自己的本地服务器则更小，只有1.0E+14-1，但是却没有这个问题。

看来在整数的检查和随机整数的生成上，CMS系统还存在不足，需要及时修补。这个问题曾经出现过3-4次，却不是所有的系统问题。本地机是WAMP环境(Apache/2.2.14 (Win32))，服务器是Linux php-clustre-testing-2 2.6.32-5-amd64环境。PHP版本均为PHP Version 5.2.17。