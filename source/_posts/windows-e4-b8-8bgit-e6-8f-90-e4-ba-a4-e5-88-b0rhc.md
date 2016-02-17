---
title: Windows下git提交到rhc
tags:
  - git
  - putty
  - rhc
id: 1593
categories:
  - 云时代
date: 2012-05-26 13:14:13
---

[Redhat的云平台](https://openshift.redhat.com/)支持PHP、Python和Node.js，还有Perl和Java，有免费3G的空间，可以好好利用。不过windows客户端教程写的是Cygwin, 觉得Cygwin太臃肿，所以试试用putty加git提交。

首先安装好[git windows版](http://code.google.com/p/msysgit/downloads/list)([参考](http://help.github.com/win-set-up-git/)：git选择run from windows command promt和与putty结合)和[putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)，然后用puttygen.exe生成公匙(putty.pub)和私匙(putty.ppk)，由于putty的公匙格式和rhc接受的公匙格式不同，所以需要把putty.pub:

---- BEGIN SSH2 PUBLIC KEY ----
Comment: "zhaiduo@gmail.com"
AAAAB3NzaC1yc2EAAAABJQAAA...
p/P0MpTSxpvUt7e7bEK5GKz7s...
bvEk/0c7uA4Q38e5day2COHt/....
NdvnbQ==
---- END SSH2 PUBLIC KEY ----

改成:

ssh-rsa AAAAB3NzaC1yc2EAAA... zhaiduo@gmail.com

保存为authorized_keys，如果使用windows版的ssh，可以放到自己的windows用户下的.ssh目录(.ssh目录可以在dos下mkdir生成：mkdir ".ssh")

然后提交到rhc。看到页面提示“Your public key has been created”，才说明提交的公匙合格。

然后打开pageant.exe，在里面add key，添加刚才生成的putty.ppk私匙。

接着打开git GUI([参考](http://nathanj.github.com/gitguide/tour.html))，在菜单的remote里添加:
名字：zhaiduo
locatoin: ssh://db...31@zhaiduo-zd.rhcloud.com/~/git/zhaiduo.git/

选择一个目录作为项目，git init here即可。

在git bash里面下载代码到本地：git pull zhaiduo master
修改好后提交：
git add .
git commit -m "new update"
git push zhaiduo

Counting objects: 7, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 630 bytes, done.
Total 4 (delta 3), reused 0 (delta 0)
remote: Stopping application...
...
remote: Running .openshift/action_hooks/pre_build
remote: Running .openshift/action_hooks/build
remote: Running .openshift/action_hooks/deploy
remote: Starting application...
remote: MongoDB already running
remote: MySQL already running
remote: Done
remote: Running .openshift/action_hooks/post_deploy

如果是GUI提交成功能看到绿色的"成功"条。

**更新：**
重启电脑后，发现git push的时候出错：putty fatal error: Network error: Cannot assign requested address.
又尝试了很多办法，但是还是错误，于是决定放弃putty，直接使用git自带的ssh.exe。

首先，在系统环境变量修改GIT_SSH值为：git安装目录binssh.exe
然后在自己的用户目录下：C:Documents and SettingsZhaiduo
参考[这里](http://help.github.com/win-set-up-git/)重新ssh-keygen,把新的id_rsa复制到rhc网上和当前目录的authorized_keys。
重启后，在git GUI里远端删除remove remote，重新添加remote，显示git GUI(zhaiduo)：获取(fetch)成功。