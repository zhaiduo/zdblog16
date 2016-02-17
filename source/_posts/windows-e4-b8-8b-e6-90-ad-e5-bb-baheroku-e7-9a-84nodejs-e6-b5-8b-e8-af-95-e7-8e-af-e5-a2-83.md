---
title: Windows下搭建Heroku的nodejs测试环境
tags:
  - Heroku
  - Nodejs
  - npm
  - 出错
  - 办法
  - 环境搭建
id: 1865
categories:
  - 云时代
date: 2014-01-16 19:42:44
---

在Heroku上新建App: twittest-njs，下载heroku-toolbelt.exe，安装后在本地dos下heroku login登录。
然后步骤如下：
#add web.js 添加[测试代码](https://github.com/zhaiduo/twittest-njs/blob/master/web.js)

本地git init一个目录：twittest-njs，打开dos进入该目录
运行#npm init
运行#npm install express logfmt --save

dos下提示registry.npmjs.org访问出错：
npm ERR! Error: SSL Error: CERT_UNTRUSTED
wayout: npm config set strict-ssl false

npm ERR! error rolling back express@3.4.4 Error: ENOTEMPTY
npm ERR! Unsupported
npm ERR! Not compatible with your version of node/npm: connect@2.11.0
npm ERR! Required: {"node":">= 0.8.0"}
npm ERR! Actual:   {"npm":"1.1.12","node":"0.6.14"}

wayout: upgrade [http://nodejs.org/download/](http://nodejs.org/download/) [http://nodejs.org/dist/npm/](http://nodejs.org/dist/npm/) to Program Filesnodejs
解决办法，升级node和npm到最新版。

#add Procfile 创建Procfile文件到当前目录，内容如下：
web: node web.js

在目录 D:Program FilesHerokuruby-1.9.2bin> 下运行#foreman start出错，提示：
foreman start(0.63)
Bad file descriptor

wayout: gem uninstall foreman;gem install foreman -v 0.61
原因是0.63版本的foreman有问题，换到0.61即可。

复制 copy foreman和foreman.bat 从D:Program FilesHerokuruby-1.9.2bin> 到 to herokutwittest-njs
编辑foreman.bat edit: ruby.exe前增加路径："D:/Program Files/Heroku/ruby-1.9.2/bin/"
当前目录herokutwittest-njs下运行：#foreman start

结果显示如下：
19:08:07 web.1  | started with pid 5880
19:08:09 web.1  | Listening on 5000

打开浏览器访问：http://localhost:5000/，网页显示：Hello JS World!

至此，Windows下搭建Heroku的nodejs测试环境成功。

**补充：如果部署到Heroku出现如下错误：**
Fatal: Could not read from remote repository.
或者：
PuTTY Fatal Error: Disconnected: No supported authentication methods available

强烈建议[重新安装git](http://git-scm.com/downloads)，安装时选择openssh，而不是putty。