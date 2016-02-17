---
title: Windows7下面为Apache2.2增加OpenSSL支持
tags:
  - Apache
  - OpenSSL
id: 1247
categories:
  - 安装
date: 2010-12-28 13:39:10
---

今天需要在https下测试程序，发现现在给本地Apache2.2增加OpenSSL支持已经变得非常容易，安装过程如下：

1.  下载安装[Win32OpenSSL](http://www.slproweb.com/products/Win32OpenSSL.html)
包括：Win32 OpenSSL v1.0.0c和Visual C++ 2008 Redistributables，安装在C:/OpenSSL-Win32/目录
2.  复制C:/OpenSSL-Win32/bin下libeay32.dll和ssleay32.dll到C:/WINDOWS/system32
3.  进入命令行模式，生成crt证书
C:OpenSSL-Win32bin&gt;openssl req -config openssl.cfg -new -out zhaiduo.csr -keyout zhaiduo.pem
C:OpenSSL-Win32bin&gt;openssl rsa -in zhaiduo.pem -out zhaiduo.key
C:OpenSSL-Win32bin&gt;openssl x509 -in zhaiduo.csr -out zhaiduo.crt -req -signkey zhaiduo.key -days 3650
4.  给Apache增加mod_ssl
打开LoadModule ssl_module modules/mod_ssl.so
打开Include conf/extra/httpd-ssl.conf
5.  修改http-ssl.conf配置
SSLCertificateFile "C:/OpenSSL-Win32/bin/server.crt"
SSLCertificateKeyFile "C:/OpenSSL-Win32/bin/server.key"
6.  然后重启apache，打开[https://localhost/](https://localhost/)，Firefox会提示是否接受不安全的证书，导入即可。简单吧～
另外如果出现403 FOrbidden的错误，你可以查看一下error.log，如果是
client denied by server configuration 你需要给< VirtualHost _default_:443 >增加一个Directory
> < Directory "https_dir" >
> AllowOverride None
> Order allow,deny
> allow from all
> < /Directory >

如果是rsa server certificate commonname does not match server name，可以检查一下证书里面的certificate commonname是否与VirtualHost的ServerName一致。