---
title: Red Hat Enterprise AS 4安装DirectAdmin
tags:
  - RHEL 4
  - control panel
  - 出错
  - 系统安装
  - 虚拟主机
id: 553
categories:
  - Linux/Unix
date: 2010-04-14 12:00:47
---

[DirectAdmin](http://www.directadmin.com)是一款和Cpanel、Pleask类似的虚拟主机管理系统。其主要优点是功能相对较前，价格优势明显。本来想找人自己写个虚拟主机管理系统，但是考虑到成本和时间，最后还是决定在Red Hat Enterprise AS 4上安装DirectAdmin。

**安装步骤：**

纯净系统安装：查看一下[install.html](http://www.directadmin.com/install.html)，看你的操作系统是否在支持之列
-至少要有一个公网IP地址（在NAT和基于局域网的系统下无法工作）
-安装有ssh和gcc、gcc-c++编译环境

如果登录用户不是admin或root（使用su获取root访问权限的情况）：
在你退出root账户之前，你必须添加AllowUsers到 /etc/ssh/sshd_config 文件中
AllowUsers 用户名

使用 root 权限并下载 setup.sh文件 wget http://www.directadmin.com/setup.sh
修改setup.sh的文件读写权限755, 运行setup脚本

安装脚本提示输入：客户ID、许可ID和主机名
重点：主机名必须和主域名相同，例如：zhaiduo.com是不符合要求的主机名，server.zhaiduo.com才是符合的。
如果主机名和主域名相同将会导致e-mail和FTP出错，并且需要你保证DNS的设置能够解析到主机名。

然后,会提示"Is eth0 your network adaptor with the license IP?"意思是要输入网卡别名,

如果你在VPS中安装,有可能要你输入网卡的别名,如果你用的是星外的centos的VHD文件,默认的网卡是:seth0
注意是数字零,不是字母o

如果输入错了,会造成的安装后2222端口无法访问.(当然,如果防火墙中没有允许2222端口也是无法访问的)

访问DA控制面板可以通过链接http://server.ip.address:2222访问DA控制面板

如下命令列出的Admin 用户名/密码：
/usr/local/directadmin/directadmin i

清理系统：
手工卸载Apache, Mysql, VsFTP, PHP, Zend:
service stop
vi /etc/rc.local
cd /etc/init.d
rm httpd, mysqld, vsftd
cd /usr/local
rm -rf apache
rm -rf php
rm -rf Zend
rm -rf mysql

安装过程基本顺利，主要遇到以下几个问题：
1\. glibc-2.5 not found
解决办法：升级gcc和gcc-c++
> //gcc-2.34 to gcc-4.1.2
> 710  rpm -qa|grep glibc
> 711  rpm -e glibc-headers
> 713  rpm -e glibc-devel
> 717  rpm -e libtool
> 718  rpm -e systemtap
> 723  rpm -e tog-pegasus-devel
> 724  rpm -e gcc-c++
> 733  rpm -e java-1.4.2-gcj-compat-1.4.2.0-27jpp.noarch
> 734  rpm -e gcc-java
> 735  rpm -e gcc
> 737  rpm -ivh gcc*.rpm
> 
> //update binutils-2.17.50.0.6-6.el5.i386.rpm, glibc-2.5-24.i386.rpm
> 742  rpm -e binutils
> 743  rpm -Uvh glibc*.i386.rpm binutils-2*.rpm
> 
> //update libstdc++-4.1.2-42.el5.i386.rpm libgcc-4.1.2-42.el5.i386.rpm
> //update libgomp-4.1.2-42.el5.i386.rpm cpp-4.1.2-42.el5.i386.rpm
> 767  rpm -Uvh gcc*.rpm
> 768  rpm -Uvh libstdc++*.rpm
> 773  rpm -Uvh libgcc*.rpm
> 776  rpm -Uvh cpp*.rpm
> 781  rpm -Uvh libgomp*.rpm
> 782  rpm -Uvh gcc-4*.rpm
> 783  rpm -e libgomp
> 784  rpm -ivh libgomp*.rpm
> 788  rpm -Uvh gcc-4*.rpm
> 789  rpm -Uvh gcc-c++*.rpm

2\. "ips.conf not found" and "./directadmin: error while loading shared libraries: libssl.so.6: cannot open shared object file: No such file or directory"
> cd /usr/local/directadmin
> ldd directadmin
> #libssl.so.6 => not found
> #libcrypto.so.6 => not found
> #ln -s libssl.so.4 libssl.so.6
> #ln -s libcrypto.so.4 libcrypto.so.6
> #/sbin/service httpd restart
> #./directadmin p    //permission set