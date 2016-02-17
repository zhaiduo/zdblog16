---
title: Github快速入门
tags:
  - Cloud
  - git
  - 版本控制
id: 1210
categories:
  - 技术研究
---

install http://msysgit.googlecode.com/files/Git-1.7.0.2-preview20100309.exe

Global setup:

 Download and install Git
  git config --global user.name "Adam"
  git config --global user.email zhaiduo@gmail.com

Next steps:

  mkdir PlaywithAppEngine
  cd PlaywithAppEngine
  git init
  touch README
  git add README
  git commit -m 'first commit'
  git remote add origin git@github.com:zhaiduo/PlaywithAppEngine.git

  git push origin master

Existing Git Repo?

  cd existing_git_repo
  git remote add origin git@github.com:zhaiduo/PlaywithAppEngine.git
  git push origin master

Importing a Subversion Repo?

  Click here

When you're done:

  Continue

    1  git config --global user.name "Adam"
    2  git config --global user.email zhaiduo@gmail.com
    3  mkdir PlaywithAppEngine
    4  cd PlaywithAppEngine
    5  git init
    6  touch README
    7  git add README
    8  git commit -m 'first commit'
    9  git remote add origin git@github.com:zhaiduo/PlaywithAppEngine.git
   10  git push origin master
   11  git push origin master
   12  cd ~/.ssh
   13  ls
   14  ssh-keygen -t rsa -C "zhaiduo@gmail.com"
   15  ls
   16  mkdir key_backup
   17  cp id_rsa* key_backup
   18  ls
   19  cd -
   20  git push origin master
   21  cd -
   22  ls id_rsa
   23  ls
   24  cat id_rsa.pub
   25  cd -
   26  git push origin master
   27  cd -
   28  rm id_rsa*
   29  ls
   30  ssh-keygen -t rsa -C "zhaiduo@gmail.com"
   31  cd -
   32  git push origin master
   33  history > his.data

########################
AdamL_2@CHENGDU ~/PlaywithAppEngine (master)
$ git commit -m 'first test'
[master 3564bcf] first test
 12 files changed, 184 insertions(+), 0 deletions(-)
 create mode 100644 app.yaml
 create mode 100644 css/index.css
 create mode 100644 footer.html
 create mode 100644 header.html
 create mode 100644 images/88e082938947ff54d2a4ba8d6425c48027444754.gif
 create mode 100644 index.html
 create mode 100644 index.py
 create mode 100644 index.yaml
 create mode 100644 zd_db.py
 create mode 100644 zd_db.pyc
 create mode 100644 zd_html.py
 create mode 100644 zd_html.pyc

AdamL_2@CHENGDU ~/PlaywithAppEngine (master)
$ git remote add origin git@github.com:zhaiduo/PlaywithAppEngine.git
fatal: remote origin already exists.

AdamL_2@CHENGDU ~/PlaywithAppEngine (master)
$ git push origin master
Enter passphrase for key '/c/Documents and Settings/AdamL_2/.ssh/id_rsa':
Counting objects: 17, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (13/13), done.
Writing objects: 100% (16/16), 7.39 KiB, done.
Total 16 (delta 0), reused 0 (delta 0)
To git@github.com:zhaiduo/PlaywithAppEngine.git
   5084ad7..3564bcf  master -> master
######################################################

常用命令：

git add README
git commit -m 'first commit'
git push origin master

提交分支到服务器
roy@ubuntu:~/workspace/test$ git push origin your_branch_name
“origin”是固定的

获得最新的项目文件（从服务器下载）
roy@ubuntu:~/workspace/test$ git pull git://github.com/royzhu/test.git

建立自己的分支
$ git branch your_branch_name

再看看有哪些分支
$ git show-branch
! [your_branch_name] a new branch
--
*+ [master] a new branch

查看现在使用的分支
$ git branch
* master
your_branch_name
加*号表示当前使用的分支

进入自己的分支
$ git checkout your_branch_name

#检查当前修改、新增的文件
git status

#新增分支，对于大范围的修改，应先使用此命令创建分支
git checkout -b 分支名

#显示所有分支列表，前面有星号的为当前分支
git branch

#切换至另一个分支
git checkout 分支名

#将新增的文件加入版本控制
git add .

#提交。也可以使用git commit -a -m '描述'，此命令包含了git add .
git commit -m '修改内容的描述'

#使用commit提交本地后，在保证所有测试用例通过的情况下，可以上传至远程版本服务器
git push
#注意，如果别人已经有上传了新的改动至服务器，则应将远程版本同步下来

git pull
#执行后，git会进行自动合并操作，失败的会提示用户手动合并(直接修改文件，并去掉git<<====等冲突标记)
#将修改过的文件重新commit后上传
git push

#查看某个文件的修改历史
git log -p app/controllers/grids_controller.rb

#获取以前版本的文件
git checkout 0d7371d574 public/open-flash-chart.swf

#0d7371d574为commit号前的n位数值，此值可以通过查看文件的修改历史获取到

/////////

修改后提交到github
git add.
git commit -m 'some update'

应该在每次运行checkout之前执行commit或reset。

$ git reset --hard  如果你的文件编辑乱了，运行
$ git log 显示最近提交列表，以及他们的SHA1哈希值
$ git reset --hard SHA1_HASH 恢复到一个指定的提交状态，并从记录里永久抹掉所有比该记录更新的提交
$ git checkout SHA1_HASH 简单地跳到一个旧状态
$ git checkout master 会把你带到当下来

$ git checkout "@{10 minutes ago}" 选择只恢复特定文件或子目录，把这些加到该命令后面就可以了。
$ git checkout "@{5}" 你可以要求倒数第五次保存状态：