---
title: 'PHP Error: Permission denied in Unknown on line 0'
id: 122
categories:
  - PHP
  - 窄多废话
date: 2007-03-01 16:19:35
tags:
---

今天上传一个脚本到新的服务器，可是却莫名其妙的出现这样的出错：
> PHP Warning: Unknown(/*****/***.php): failed to open stream: Permission denied in Unknown on line 0
经过检查，确认没有程序错误。根据错误的提示“Permission denied”，可能是文件权限的问题，于是修改权限为644，问题解决。事后想想，虽然是权限问题，可是这个错误提示也太模糊啦，初的一看，真让人一头雾水，不知道从何下手。很少对PHP提示的出错有些不知所措。