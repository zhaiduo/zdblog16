---
title: Mongodb 错误：Connection refused
tags:
  - mongodb
  - openshift
id: 1743
categories:
  - NoSQL
  - Python
date: 2012-12-11 21:35:34
---

今天调试webapp2，Mongodb出现如下错误：
AutoReconnect: could not connect to x.x.x.x:27017: [Errno 111] Connection refused

根据网上的解释：需要删除mongod.lock，通常在/var/lib/mongodb下。然后重启sudo service mongodb start。

我用的是openshift，所以可以通过puttygen生成一个新的key，保存好私匙，并在账户管理里面添加Public Keys。然后在putty输入host name: 231..93cde98d@zhaiduo.rhcloud.com，在putty connection->ssh->auth下指定刚才生成的ppk私匙。点击Open即可连接，别忘了输入自己指定的Passprhase哦～

最后在提示行输入：killall -9 mongod;ctl_all restart重启即可。

rhc命令行工具可以用这个命令 : rhc app cartridge restart -a {appName} -t mongo