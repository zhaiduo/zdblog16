---
title: 'Javascript错误：Expected identifier, string or number'
tags:
  - 出错
  - 断网
id: 921
categories:
  - javascript
date: 2010-08-02 23:04:50
---

一段Jquery调用
$.get("tag.php",{act:'list',class:'id'},function{});
在IE8下出现如下错误：
Error Message: Expected identifier, string or number
原因是class被看作是IE的保留字，修改一下即可。

另外一个问题：
安装[Zenmap](http://nmap.org/zenmap/)扫外网时电脑突然断线无法上网，并且无法访问网关192.168.1.1，不过内网一切正常，症状很像arp病毒，但是在网关重新绑定静态mac地址后，一切正常。
[![](http://www.zhaiduo.com/wp-content/uploads/2010/08/p20100729183335.jpg "p20100729183335")](http://www.zhaiduo.com/wp-content/uploads/2010/08/p20100729183335.jpg)