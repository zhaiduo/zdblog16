---
title: 用VC++测试OpenGL和DirectX9
tags:
  - DirectX
  - OpenGL
  - VC++
  - 出错
  - 测试
  - 问题
id: 375
categories:
  - 3D
  - 三维时代
date: 2009-09-11 00:18:43
---

测试环境WinXP专业版SP3:

[Microsoft Visual C++ 2008 Express Edition](http://www.microsoft.com/express/vc/)
[Microsoft DirectX SDK (March 2009)](http://www.microsoft.com/DOWNLOADS/details.aspx?FamilyID=24a541d6-0486-4453-8641-1eee9e21b282&amp;displaylang=en)

**测试[DirectX9](http://msdn.microsoft.com/zh-cn/library/bb219838(en-us,VS.85).aspx)遇到的问题：**

# 错误：[Cannot convert from 'const char [..]' to 'LPCTSTR'](http://social.msdn.microsoft.com/Forums/en-US/vclanguage/thread/c1b08c0a-a803-41c3-ac8c-84eba3be1ddb)

**Problem**

This error message means that you are trying to pass a multi-byte string (const char [12]) to a function which expects a unicode string (LPCTSTR). The LPCTSTR type extends to const TCHAR*, where TCHAR is **char** when you compile for multi-byte and **wchar_t** for unicode. Since the compiler doesn't accept the char array, we can safely assume that the actual type of TCHAR, in this compilation, is wchar_t.

**解决办法**
Change your project configuration to use **multibyte** strings. Press **ALT+F7** to open the properties, and navigate to** Configuration Properties &gt; General. Switch Character Set** to "<span style="color: #ff0000;">**Use Multi-Byte Character Set**</span>".

错误：<span style="font-family: Courier New;"><span style="font-size: medium;">**Error LNK2019: unresolved external symbol _Direct3DCreate@4 referenced in function “long_cdecl InitD3D(struct HWND__*)”(?InitD3D@@YAJPAUHHWD__@@@Z)**</span></span>

**解决办法
**确保DirectX SDK安装正确，检查下列路径：
Tools-&gt;Options-&gt;Projects and Solutions-&gt;VC++ Directories.
Under the selection box "Show Directories For", select "Library Files" and check the directory "C:/DXSDK/Lib";
then the same for "Include Files" and check "C:/DXSDK/Include".

然后

Those are linker errors, not compiler errors, so they don't involve missing headers.
You need to link to the appropriate DirectX import libraries.
when you make a project, select **Project-&gt;Properties-&gt;Linker-&gt;Input**, and under **Additional Dependencies**, enter these items separated by a space: **"<span style="color: #ff0000;">d3d9.lib d3dx9.lib</span>";**

或者可以直接在源文件里加入<span style="font-family: Courier New;">
#pragma comment(lib, "d3d9.lib")
#pragma comment(lib, "d3dx9.lib")
#pragma comment(lib, "dxerr9.lib")</span>

**测试[OpenGL](http://www.opengl.org/documentation/)遇到的问题：**

Problem:

# error LNK2019: unresolved external_ Help me please

<span style="color: #ff0000;">LNK2019: unresolved external symbol _gluPerspective@32 referenced in function</span>

<span style="font-family: Arial; font-size: x-small;">Add "**opengl32.lib glu32.lib glaux.lib**" to **Project Properties-&gt;Configuration Properties-&gt;Linker-&gt;Input-&gt;Additional Dependencies.**</span>

<span style="color: #ff0000;">LNK1104: cannot open file 'glaux.lib'</span>

r u running VS2008?
if so, just remove glaux.lib from the link inputs.