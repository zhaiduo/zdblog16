---
title: '关于win7下virtualbox5的RC:REGDB_E_CLASSNOTREG错误'
id: 2377
comment: false
categories:
  - 虚拟时代
date: 2015-08-07 13:42:42
tags:
---

win7 64位下安装virtualbox5后，也会报这个错"创建 VirtualBoxClient COM 对象失败."，解决办法：

#virtualboxclient com 对象失败
管理员身份DOS执行：
VBoxSVC.exe /ReRegServer
regsvr32.exe VBoxC.dll
后右键点击属性，在兼容性处勾选已Windows Server 2008，以及下面的 以管理员身份运行此程序。即可。

建立centos7的虚拟机后，启动又报同样的错误"并且提示不能为centos7打开一个新任务":

The virtual machine 'centos7' has terminated unexpectedly during startup with exit code 1 (0x1). 