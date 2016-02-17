---
title: Virtualbox安装window10的64位预览版错误
tags:
  - window10
id: 2170
categories:
  - windows
date: 2014-12-26 12:47:24
---

错误代码如下：
error code 0x0000005d

根据[这里](http://answers.microsoft.com/en-us/windows/forum/windows_tp-windows_install/error-code-0x0000005d-in-virtualbox/775902f2-1d6e-48fd-9609-789f7337333f)的解释：

我升级了VB，然后下载VT-x support check，

http://www.intel.com/support/processors/tools/piu/sb/cs-014921.htm

并且运行了：

"C:Program FilesOracleVirtualBoxVBoxManage.exe" setextradata global VBoxInternal/CPUM/CMPXCHG16B 1

问题解决。