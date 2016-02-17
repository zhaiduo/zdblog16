---
title: SQL Server管理小技巧
tags:
  - sql server
id: 234
categories:
  - windows
date: 2008-01-18 15:25:14
---

1\. 批量修改table所有者为'dbo'
> EXEC sp_MSforeachtable 'exec sp_changeobjectowner ''?'',''dbo'' '
2\. 快速导入导出image类型字段的方法: TEXTCOPY.exe
在企业管理启里面类似image等这样的Binary字段无法直接查看，TEXTCOPY.exe可以帮助我们轻松解决这个问题。SQL Server会将大于8k的二进制数据分段保存，所以用程序获取image字段的时候需要注意将分段的合并，所以在处理大量图片的时候，会出现效率上的问题。TEXTCOPY.exe是一个很好的快速高效工具，它可以帮助你快速存储和获取image字段，进行跨数据库的操作，而且免去了频繁使用用户名密码登录的麻烦和安全问题。你可以在SQL server的安装目录/MSSQL/Binn下找到它，其用法如下：
> TEXTCOPY [/S [sqlserver] ] [/U [login] ] [/P [password] ] [/D [database] ] [/T table] [/C column] [/W "where clause"] [/F file] [{/I /O}] [/K chunksize] [/Z] [/?]
> /S sqlserver : SQL Server 服务器，通常用(local)
> /U login : 用户名
> /P password
> /D database : 数据库名
> /T table : 数据表名
> /C column : 字段为text或image的列名
> /W "where clause" : 条件判断语句
> /F file : 要存储或是导入源的文件名
> /I : 表示插入数据
> /O : 表示输出数据
> /K : 分块数据段的大小，最小1024字节数，默认4096
> /Z : 现实调试信息
> /? : 帮助