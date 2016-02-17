---
title: 关于selinux
id: 2232
comment: false
categories:
  - Uncategorized
tags:
---

SELinux全称是Security Enhanced Linux，由美国国家安全部(National Security Agency)领导开发的GPL项目，它拥有一个灵活而强制性的访问控制结构，旨在提高Linux系统的安全性，提供强健的安全保证，可防御未知攻击，据称相当于B1级的军事安全性能。比MS NT所谓的C2等高得多。

应用SELinux后，可以减轻恶意攻击或恶意软件带来的灾难，并提供对机密性和完整性有很高要求的信息很高的安全保障。 SELinux vs Linux 普通Linux安全和传统Unix系统一样，基于自主存取控制方法，即DAC，只要符合规定的权限，如规定的所有者和文件属性等，就可存取资源。在传统的安全机制下，一些通过setuid/setgid的程序就产生了严重安全隐患，甚至一些错误的配置就可引发巨大的漏洞，被轻易攻击。

1 vi /etc/sysconfig/selinux
2 #SELINUX=enforcing #注释掉
3 #SELINUXTYPE=targeted #注释掉
4 SELINUX=disabled #增加
5 :wq #保存，关闭。
6 shutdown -r now #重启系统

查看SELinux的状态：

getenforce

临时关闭
setenforce 0

关闭SELinux的方法：
修改/etc/selinux/config文件中的SELINUX="" 为 disabled ，然后重启。
如果不想重启系统，使用命令setenforce 0
注：
setenforce 1 设置SELinux 成为enforcing模式
setenforce 0 设置SELinux 成为permissive模式
在lilo或者grub的启动参数中增加：selinux=0,也可以关闭selinux

#---------------------------------------------------------------
查看selinux状态：
/usr/bin/setstatus -v
如下：
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   permissive
Mode from config file:          enforcing
Policy version:                 21
Policy from config file:        targeted

getenforce/setenforce查看和设置SELinux的当前工作模式
#-----------------------------------------------------------------------
   发现服务一启动，马上停止，在网上查找资料，找到安装时要先禁用SELinux，再安装MySQL，步骤是：

1\. 关闭SELinux，重启系统；
2\. 安装MySQL（MySQL server应该可以启动了）；
3\. 启用SELinux，重启系统，之后MySQL server就可以正常启动了。

   启用禁用SELinux的方法是：

   vi /etc/selinux/config（也有人说是/etc/sysconfig/selinux文件，其实两个之间是链接关系，随便改其中一个，另一个也改了）

   SELINUX=disable 禁用SeLinux

   SELINUX=enforcing 启用SeLinux

/////////////////////////////////

We also need to allow Postgres database traffic to pass though the firewall. CentOS 7 implements a dynamic firewall through the firewalld daemon; the service doesn't need to restart for changes to take effect. The firewalld service should start automatically at system boot time, but it's always good to check.

sudo firewall-cmd --state
The default state should be running, but if it is not running start it with:

sudo systemctl start firewalld
Next, add the rules for port 5432\. This is the port for PostgreSQL database traffic.

sudo firewall-cmd --permanent --zone=public --add-port=5432/tcp
Then reload the firewall.

sudo firewall-cmd --reload

In this step, we will configure the firewall to allow Nginx traffic, and customize some Nginx configurations.

We need to allow HTTP/HTTPS traffic to pass though the firewall. Like before, check that the firewalld service is running.

sudo firewall-cmd --state
The default state should be running, but if it's not running, start it:

sudo systemctl start firewalld
Now add the firewall rule for port 80 (HTTP):

sudo firewall-cmd --permanent --zone=public --add-port=80/tcp
Add another for port 443 (HTTPS):

sudo firewall-cmd --permanent --zone=public --add-port=443/tcp
Then, reload the firewall.

sudo firewall-cmd --reload
Next, start Nginx.

sudo systemctl start nginx.service
And enable it.

sudo systemctl enable nginx.service