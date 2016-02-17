---
title: Docker下安装PHP+Nginx环境
tags:
  - docker
id: 2119
categories:
  - Linux/Unix
---

service docker start
docker run --name ngxtest -t -i -p 8000:8000 centos /bin/bash
docker attach ngxtest

yum install -y net-tools wget
http://nginx.org/en/linux_packages.html#stable
获取Nginx rpm: http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum install -y nginx php

vi /etc/nginx/conf.d/default.conf