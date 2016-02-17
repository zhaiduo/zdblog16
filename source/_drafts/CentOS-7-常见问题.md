---
title: CentOS 7 常见问题
tags:
  - centos 7
id: 2095
categories:
  - Linux/Unix
---

Error:
最小安装出现：centos failed to start lsb.
try:
edit: vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
ONBOOT=yes
sudo chkconfig network on
or
service network start

yum install net-tools
yum upgrade

Mac airbook error:
mac could not load the host usb proxy service VERR_GENERAL_FAILURE
try: install extension pack
https://www.virtualbox.org/wiki/Downloads
///////////////////////////////intro

Installing Docker - CentOS-7

Docker is included by default in the CentOS-Extras repository. To install simply run the following command.

$ sudo yum install docker
Manual installation of latest version

While using a package is the recommended way of installing Docker, the above package might not be the latest version. If you need the latest version, you can install the binary directly.

When installing the binary without a package, you may want to integrate Docker with systemd. For this, simply install the two unit files (service and socket) from the github repository to /etc/systemd/system.

FirewallD

CentOS-7 introduced firewalld, which is a wrapper around iptables and can conflict with Docker.

When firewalld is started or restarted it will remove the DOCKER chain from iptables, preventing Docker from working properly.

When using systemd, firewalld is started before Docker, but if you start or restart firewalld after Docker, you will have to restart the Docker daemon.

Next, let's install the docker-io package which will install Docker on our host.

$ sudo yum install docker-io
Using Docker

Once Docker is installed, you will need to start the docker daemon.

$ sudo service docker start
If we want Docker to start at boot, we should also:

$ sudo chkconfig docker on
Now let's verify that Docker is working. First we'll need to get the latest centos image.

$ sudo docker pull centos
Next we'll make sure that we can see the image by running:

$ sudo docker images centos
This should generate some output similar to:

$ sudo docker images centos
REPOSITORY      TAG             IMAGE ID          CREATED             VIRTUAL SIZE
centos          latest          0b443ba03958      2 hours ago         297.6 MB
Run a simple bash shell to test the image:

$ sudo docker run -i -t centos /bin/bash
If everything is working properly, you'll get a simple bash prompt. Type exit to continue.

A Daemonized Hello world
sudo docker run -d centos:centos7 /bin/sh -c "while true; do echo hello world; sleep 1; done"

$ sudo docker ps
CONTAINER ID  IMAGE         COMMAND               CREATED        STATUS       PORTS NAMES
1e5535038e28  ubuntu:14.04  /bin/sh -c 'while tr  2 minutes ago  Up 1 minute        insane_babbage
$ sudo docker logs insane_babbage
$ sudo docker logs 1e5535038e28
$ sudo docker stop insane_babbage

 http://docs.docker.com/userguide/usingdocker

获取新image
$ sudo docker pull centos
搜索
$ sudo docker search sinatra

https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-nginx-as-a-proxy

/etc/rc.d/rc.local编辑后，需要chmod 755

iptables添加端口：
http://www.cyberciti.biz/tips/linux-iptables-examples.html
iptables -A INPUT -m state --state NEW -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -m state --state NEW -p tcp --dport 443 -j ACCEPT

yum install iptables-servies
systemctl restart iptables.service