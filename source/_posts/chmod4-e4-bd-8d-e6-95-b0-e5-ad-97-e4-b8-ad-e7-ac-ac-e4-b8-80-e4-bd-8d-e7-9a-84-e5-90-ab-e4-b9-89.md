---
title: chmod4位数字中第一位的含义
id: 116
categories:
  - Linux/Unix
  - 窄多废话
date: 2007-02-02 21:25:48
tags:
---

Linux/Unix 的系统命令chmod可以用来修改目标的访问权限。权限可以分为三级 : 拥有者(U)、群组(G)、其他(O)。

如果filename的拥有者是root，那么使用chmod 4755 filename可使此程式具有root的权限来执行这个文件 ，

ls -l filename 表现为：-rwsr-xr-x

同理2代表同组。