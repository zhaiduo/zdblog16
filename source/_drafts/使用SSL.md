---
title: 使用SSL
tags:
  - SSL
id: 2221
comment: false
categories:
  - 网站维护
---

CloudFlare的免费SSL不应该浪费：

openssl genrsa -des3 -out zhaiduo.com.key 1024
openssl req -new -key zhaiduo.com.key -out zhaiduo.com.csr
openssl rsa -in zhaiduo.com.key -out zhaiduo.com.rsa
openssl x509 -req -days 3650 -in zhaiduo.com.csr -signkey zhaiduo.com.rsa -out zhaiduo.com.crt

修改nginx.conf

server {
listen 443;
server_name www.zhaiduo.com zhaiduo.com;
ssl on;
ssl_certificate ./cert/zhaiduo.com.crt;
ssl_certificate_key ./cert/zhaiduo.com.rsa;
access_log /zhaiduo.com/logs/access_ssl.log;
error_log /zhaiduo.com/logs/error_ssl.log;
...
}

&nbsp;