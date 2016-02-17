---
title: YUM介绍
tags:
  - 教程
id: 268
categories:
  - Linux/Unix
date: 2008-04-25 23:51:02
---

一台新服务器上用的是Redhat Enterprise 5.1的操作系统(RHEL5)，用up2date却说找不到这个命令，原来它用的是Yum 3.0来自动升级。Yum这东东我第一次接触，看看到到底是何来历。
[Yum (Yellow dog Updater Modified) ](http://linux.duke.edu/projects/yum/)是一中在LInux下与RPM兼容的软件包管理和自动升级软件，通过命令行来操作。用于Red Hat系统的更新和管理。已经被Fedora, centos和许多其他与RPM兼容的基于Linux发行版所运用，包括[黄狗Linux](http://www.yellowdoglinux.com/)的本身[难怪它叫Yellow dog Updater Modified B-)]，用来取代原来的YUP(Yellowdog Updater)，所以，可以说Yum是YUP与RPM的孩子。
> 主要命令如下：
> 安装： yum install package name
> 安装RPM： yum install my_package.RPM
> 组安装：yum groupinstall "MySQL Database"
> 升级：yum update package name
> 更新组：yum groupupdate "MySQL Database"
> 删除：yum remove package name
> 删除组：yum groupremove "MySQL Database"
> 搜索：yum list package name
> 高级搜索：yum search package name
> 更新系统：yum update
> 激活每天自动更新: /sbin/chkconfig --level 345 yum on; /sbin/service yum start
> **软件包名称说明：**
> 例如：tsclient-0.132-6.i386.rpm
>     *软件包名称：tsclient
>     *带有版本号和发行版本的软件包名称：tsclient-0.132-6
>     *带有硬件架构的软件包名称：tsclient.i386
> 
> yum 以 名称.架构 的格式来列出软件包。仓库通常也将软件包存储在以架构区分的目录中。每次为软件包指定架构的时候，实际指定的是此软件对机器架构的 最低 要求。
> i386 - 适于任何现有的 Intel 兼容计算机
> noarch -  适于所有架构
> ppc - 适于 PowerPC 系统，例如 Apple Power Macintosh
> x86_64 - 适于 64 位 Intel 处理器，例如 Opterons