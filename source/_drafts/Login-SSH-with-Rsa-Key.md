---
title: Login SSH with Rsa Key
tags:
  - putty
  - rsa
  - ssh
id: 2326
comment: false
categories:
  - Linux/Unix
---

出现问题：key server refused our key
检查.ssh目录下是否有authorized_keys文件，authorized_keys文件内容为：
ssh-keygen -t rsa
cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys

download mykey download PuTTYgen from http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
start puttygen go to conversion > import key select downloaded mykey Then [Save private key], you can change key comment if needed