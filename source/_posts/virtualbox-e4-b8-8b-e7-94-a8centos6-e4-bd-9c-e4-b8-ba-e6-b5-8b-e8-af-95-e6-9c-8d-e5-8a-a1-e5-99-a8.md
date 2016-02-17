---
title: Virtualbox下用CentOS6作为测试服务器
tags:
  - CentOS6
  - VirtualBox
id: 1417
categories:
  - Linux/Unix
  - 安装
date: 2011-10-13 21:59:43
---

网络方式用NAT，系统是XP，所以Host是XP，Guest是CentOS6

1.  Virtualbox下用CentOS6 Live CD ISO 创建CentOS6系统，安装Mysql+PHP+Nginx环境。
2.  安装ftp用于Guest从Host传输数据。
3.  要做到Host可以访问Guest，从Guest传输数据，需要[Vboxmanage](http://www.virtualbox.org/manual/ch08.html)的帮忙。找到Virtualbox安装目录，开通SSH、FTP和HTTP端口映射。例如：
VBoxManage setextradata "zhaiduo_centos6_NPM" "VBoxInternal/Devices/e1000/0/LUN#0/Config/http/Protocol" TCP
VBoxManage setextradata "zhaiduo_centos6_NPM" "VBoxInternal/Devices/e1000/0/LUN#0/Config/http/GuestPort" 80
VBoxManage setextradata "zhaiduo_centos6_NPM" "VBoxInternal/Devices/e1000/0/LUN#0/Config/http/HostPort" 8008
就是把Guest的TCP 80端口映射到Host的8008端口。这样，我们就可以通过host ip:8008访问guest。其中"zhaiduo_centos6_NPM"是虚拟机名称，e1000是Guest使用的Intel的网卡，有些是pcnet。可以通过dmesg | grep eth查到。http是服务名称。然后修改虚拟机的配置，在NAT网络连接下的port forwarding rules添加相应的端口映射rule。如果觉得麻烦可以直接修改Documents and SettingsZhaiduoVirtualBox VMszhaiduo_centos6_NPM下面的zhaiduo_centos6_NPM.vbox。
4.  设置完后重启VirtualBox，发现Guest仍然不能访问，应该是[iptables](http://wiki.centos.org/HowTos/Network/IPTables)的问题，简单一点iptables -F清空，然后/etc/init.d/iptables save、restart即可。复杂一点可以这样：
iptables -L -n --line-number
iptables -D INPUT input里面reject的那一行的行号
iptable -A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
iptable -A INPUT -j REJECT --reject-with icmp-host-prohibited
最后保存、重启。
5.  关于vsFTPd的安装很简单，yum install成功后，设置/etc/vsftpd/vsftpd.conf，enable chroot_list_enable和指定chroot_list_file。如果启动后登录FTP出现如下错误：
500 OOPS: cannot change directory
解决办法：
setsebool ftp_home_dir 1
setsebool allow_ftpd_full_access 1
service vsftpd restart
6.  最后say hello to Nginx.