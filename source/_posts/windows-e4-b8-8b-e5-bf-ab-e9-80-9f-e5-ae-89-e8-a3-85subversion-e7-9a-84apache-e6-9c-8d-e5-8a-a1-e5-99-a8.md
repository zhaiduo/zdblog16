---
title: Windows下快速安装Subversion的Apache服务器
tags:
  - Apache
  - SVN
  - VC++
id: 812
categories:
  - PHP
  - 安装
date: 2009-07-24 00:07:00
---

PHP宣布使用[Subversion](http://subversion.tigris.org/faq.zh.html)作为新的版本控制系统。
相对于CVS而言，它主要有如下特点：
1.支持目录的版本化，复制、删除和改名操作。
2.仓库基于BerkleyDB数据库，具有更快的操作速度。
3.更加方便高效地存储任何文件，包括二进制和Unicode文件。
4.非常容易维护，和其它语言的互操作性很强。
也可以说Subversion是基于CVS的新一代版本控制系统。

Windows下快速安装Subversion的Apache服务器步骤如下：

下载Subversion 1.5.6
http://subversion.tigris.org/servlets/ProjectDocumentList?folderID=91
http://subversion.tigris.org/files/documents/15/45937/Setup-Subversion-1.5.6.msi

下载Tortoisesvn 1.6.3
http://tortoisesvn.net/downloads
http://downloads.sourceforge.net/tortoisesvn/TortoiseSVN-1.6.3.16613-win32-svn-1.6.3.msi?download

下载Apache HTTP Server 2.2.11
http://httpd.apache.org/download.cgi

分别在服务器端安装好Subversion和在客户端安装Tortoisesvn，然后在服务器端编辑Apache配置文件：
httpd.conf

取消注释
LoadModule dav_module modules/mod_dav.so
LoadModule dav_fs_module modules/mod_dav_fs.so

在Subversion的bin目录下复制mod_dav_svn.so和mod_authz_svn.so到Apache的modules目录，在模块配置后面增加
LoadModule dav_svn_module modules/mod_dav_svn.so
LoadModule authz_svn_module modules/mod_authz_svn.so

最后在文件末增加
《Location /svn》
DAV svn
#SVN仓库父目录
SVNParentPath c:/SVN/
#风格样式控制文件
SVNIndexXSLT "/SVN/svnindex.xsl"
#访问控制，需要在Apache的bin目录下，用htpasswd为指定用户生成密码。
#htpasswd -cm c:SVNsvn-auth-file 用户名
AuthType Basic
AuthName "Subversion Repository"
AuthUserFile c:SVNsvn-auth-file
Require valid-user
《/Location》

启动Apache即可。

SVN简要操作

在客户端创建仓库:
打开资源管理器，c:/SVN/下添加目录zhaiduo，点击鼠标右键，在Tortoisesvn选项中点击Create Repository.
Import导入文件 推荐仓库布局/Trunk, /Branches, /Tags
checkout复制文件到在客户端本地
Commit提交修改文件
Updat更新客户端复制文件
Export导出干净文件

Tortoisesvn选项中编辑config文件，用于设置svn:keywords:Id.