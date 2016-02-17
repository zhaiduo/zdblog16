---
title: git常见问题
tags:
  - git
id: 2214
categories:
  - 版本控制
---

http://www.git-scm.com/book/en/v2/Getting-Started-About-Version-Control

## windows下git clone fatal错误: could not read Password

git config --global core.askpass "C:Program Filesgitlibexe cgit-coregit-gui--askpass"

##服务器上初始化repo

mkdir /home/adam/repo #create directory for new repository
cd /home/adam/repo
git init
touch firstfile
git add .
git commit

cd /home/adam
git clone –bare ./repo repo.git
touch repo.git/git-daemon-export-ok

客户端：
git clone ssh://adam@localhost:2222/home/adam/repo.git

## git如何再次添加ignore的文件?

注:如果要忽略的文件已被git管理,需要先移除,命令如下:

e.g.:

git rm -r --cached  WebRoot/WEB-INF/classes/**/*

-r:递归

git commit

查看远程URL
git remote -v

修改remote

git remote set-url origin URL

git remote set-branches [--add] <name> <branch>...
git remote set-url [--push] <name> <newurl> [<oldurl>]
git remote set-url --add <name> <newurl>
git remote set-url --delete <name> <url>

/////////////brnach
git checkout -b newbranch
=
git brnach newbranch
git checkoutnewbranch

改名：git branch -M oldbranch newbranch
/////////////////
git push local branch to remote:
git checkout -b user
//make/commit some changes
git push origin user

//////////////////stage
git stage .