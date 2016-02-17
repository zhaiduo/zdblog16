---
title: 谷歌彻底被墙，该怎么办？
id: 1933
categories:
  - Google与Idea
date: 2014-06-08 13:09:11
tags:
---

作为谷歌的重度用户，最常用的谷歌服务包括：search、gmail和各种API。一旦谷歌被墙，会让人觉得手足无措。解决的办法应该有：

1.  购买[国外服务器](https://www.digitalocean.com/?refcode=71e301756cba)，自己搭建SSH通道 ()
1\. 首先需要一个[VPS](https://www.digitalocean.com/?refcode=71e301756cba)或者ssh帐号，把公钥复制到VPS上省去每次登陆都需要输入密码:
把本地~/.ssh/id_rsa.pub 或者id_dsa.pub的内容写入到远程服务器所需要登陆的账户的家目录下(如/root)~/.ssh/authorized_keys.

    也可以自己生成：$ ssh-keygen -t rsa -C "email@example.com"

    2\. 利用ssh通道实现端口转发（详见http://www.ibm.com/developerworks/cn/linux/l-cn-sshforward/ ）
ssh -qTfnN -D 7001 root@YOUR_SERVER

3\. 此时已经建立了通道，用firefox浏览器的autoproxy插件就可以实现翻gfw墙。

    4\. 上面的只适用于firefox，要想使每一个软件都能利用ssh通道，可以借助proxychains软件,ubuntu下：
sudo apt-get install proxychains
编辑配置文件/etc/proxychains.conf：
加上我们自己的proxy：
socks5  127.0.0.1 7001

这是用proxychains YOURAPP &就可以让任何软件翻gfw墙了，如使chrome能够访问twitter：
proxychains chromium-browser

2.  购买国外服务器，自己写代码，搭桥
比如用PHP通过imap协议，获取/管理Gmail。

3.  使用代理服务器
即使用第三方提供的IP、端口，来访问谷歌。如前面的SSH通道，也可以自己搭建。

    首先在VPS上安装Squid

    # yum install -y squid
然后简单地配置一下squid

    # vim /etc/squid/squid.conf

    ## 找到 http_access deny all，改为http_access allow all ##
## 默认端口为3128，如需修改，找到 http_port修改即可 ##
接着启动squid即可

    # /etc/init.d/squid start

    设置putty

    打开putty，到Connection->SSH->Tunnels，填入Source port：3128，选择Dynamic，并点击add。

    点击左边菜单”Session”,输入Host Name,填入Saved Sessions，并保存，点击“open”，输入用户名和密码之后SSH通道就建立好了。

    在这里推荐使用Firefox浏览器

    我们设置一下firefox浏览器就可以用了

    打开火狐浏览器，到“工具->选项->高级->网络“，点击设置

    选择“手动配置代理:(M)”，在“SOCKS主机:”一栏填写：localhost，“端口:(T)”：3128，其它的默认，确定即可。

    基本上是设置完毕了，不过我们还得防DNS劫持啊，所以要修改一下本地的DNS服务器，可以用GOOGLE的：8.8.8.8 8.8.4.4。

4.  购买VPN
虚拟专用网络 (VPN) 是跨专用网络或公用网络（例如 Internet）的点对点连接。远程访问 VPN 连接使在家中或路上工作的用户可以使用公用网络（例如 Internet）提供的基础结构来访问专用网络上的服务器。站点间 VPN 连接（也称为路由器间 VPN 连接）使组织可以在各个独立办公室之间或与其他组织之间通过公用网络建立路由的连接，同时帮助保证通信的安全。

5.  使用别的可以替代谷歌的，可信赖类似服务。如：[微软的免费存储空间](https://onedrive.live.com/?invref=d2a684c77e563243&invsrc=90)和邮箱，还有Bing搜索。
6.  肉身翻墙