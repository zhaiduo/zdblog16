---
title: Red Hat Enterprise Linux (RHEL)5相关版本介绍
id: 198
categories:
  - Linux/Unix
date: 2007-08-12 12:56:37
tags:
---

**rhel5/ Red Hat Enterprise Linux (RHEL) 5 **
Red Hat于2007年3月14日正式发布了RHEL5.
1\. 完整集成新的服务器和存储虚拟技术, 能很好与红帽集群技术工作.

Red Hat实现了让你可以在本地服务器上、你的存储区区域网络SAN、跨群集上管理大量存储数据的需求。RHEL 5还支持iSCSI磁盘阵列，以及具有“以太网远程直接内存存取(RDMA)”功能的InfiniBand。对于那些喜欢在一个文件系统进行大数据量存储的用户，RHEL 5的Ext3文件系统现在将支持16T的文件系统——这已经不小了。

2\. 容错性方面, 提供了红帽集群套件, 红帽Global File System(Global文件系统)和集群逻辑卷管理器. 这项技术能使任何系统上匿名用户能安全访问和共享应用数据.
3\. 内核从2.6.9升级到2.6.18\. 加强了系统的内核: 比如程序移植, 网络和输入/输出子系统, 另外也加强了系统的性能和扩展性. 另外还包括加强的安全性, 比如包含全局安全配置(Comprehensive Security Profiles)和增强的编译器和运行缓冲管理技术.
4\. 虚拟技术支持x86和x86-64平台. 提供了基于Itanium 2的预览Xen技术, 它的虚拟管理器能方便管理安装任务和管理Xen虚拟主机.

Red Hat在RHEL 5里增加了虚拟化管理功能，这样就使任何用户都可以在Linux平台上安装虚拟机（Vrtual Machine，VM）——最起码他们可以尝试去安装。为了成功安装一个虚拟机。使用RHEL 5，任何相当有经验的系统管理员都能够毫不费劲地创建一个虚拟机。而且一旦安装成功，还可以很方便地对虚拟机进行管理。

基于Linux内核(Kernel-based)的虚拟机(Virtual Machine)——即KVM——是最新的Linux内核（2.6.20）中的最热点功能。另外，一些开源项目中也加入了对虚拟化技术的研究和研发，比如 OpenVZ、SWSoft、Parallels项目.

5\. 测试版发行仅有两个不同版本: RHEL 5 Server 和RHEL 5 Client (aka Desktop). 客户版本只能运行在x86和x86-64平台上.
6\. 红帽将在RHEL 5桌面投入更多的时间.

**rhel5 Client**
Client版,也就是桌面版(Desktop),Desktop版包含的办公软件比较多.

**rhel5 x86 64**
for 64位操作系统

**CentOS4.5**
是 RHEL4 U5（Red Hat Enterprise Linux）源代码再编译的产物，而且在 RHEL 的基础上修正了不少已知的 Bug ，相对于其他 Linux 发行版，其稳定性值得信赖。

**CentOS 5.0**
CentOS5是用RedHat Enterprise 5源码重新编译的版本，CentOS5的核心就是 RHEL5。CentOS是Red Hat Enterprise Linux的100%兼容的重新组建,并完全符合Red Hat的再发行要求. CentOS面向那些需要企业级操作系统稳定性的人们,而且并不涉及认证和支持方面的开销.

CentOS5新添加的功能简介：

1、Xen虚拟功能(亮点)

该功能允许一台计算机在“不同独立部分”(虚拟计算机)运行多款操作系统，同是还允许四台虚拟计算机运行RHEL&nbsp5&nbspServer。
不过，它还增加了一个名为RHEL&nbspAdvanced&nbspPlatform功能，去支持无限多的虚拟机运行，另外，还加入了Global&nbspFile&nbspSystem。

2、支持四核处理器

基于AIGLX和Compiz软件，&nbspRHEL&nbsp5具有奇妙的3D图像界面，桌面用户具有更好的系统挂起与恢复的能力。

3、提高文件系统管理数据容量

最高可以管理16TB字节，而RHEL&nbsp4仅为8TB。

4、新增Stateless&nbspLinux技术

**RHEL5****下载地址**：[http://books.lxgcn.com/linuxiso/](http://books.lxgcn.com/linuxiso/)