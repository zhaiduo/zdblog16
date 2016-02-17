---
title: URL Rewrite的VBscript解决办法
tags:
  - 办法
id: 790
categories:
  - Uncategorized
date: 2009-01-07 22:29:00
---

比如要实现这样的URL转向：
> http://www.zhaiduo.com/page/3/
> =>
> http://zhaiduo.googlepages.com/search3.htm
如果服务器没有URLRewrite功能可用这个代码在Windows下生成目录和文件。然后用FTP上传即可。保存下面内容为：create.vbs
> Option Explicit
> Dim objFSO, objFolder, strDirectory, strDirectory2
> strDirectory = "D:zhaiduo.compage"
> Set objFSO = CreateObject("Scripting.FileSystemObject")
> 
> Dim I
> For I = 1 To 55
>    strDirectory2=strDirectory &amp; "" &amp; I
>    Set objFolder = objFSO.CreateFolder(strDirectory2)
>    WScript.Echo "Just created " &amp; strDirectory2
>    CreateIndexFile strDirectory2, I
>    WScript.Echo "Just created " &amp; strDirectory2 &amp; "index.php"
> Next
> 
> WScript.Quit
> 'end
> 
> Sub CreateIndexFile(Folder,I)
>   Dim TextStream
>   Set TextStream = objFSO.CreateTextFile(Folder &amp; "index.php")
>   TextStream.WriteLine("")
>   TextStream.Close
> End Sub
双击运行即可。