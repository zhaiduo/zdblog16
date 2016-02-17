---
title: git常用命令
tags:
  - git
id: 1600
categories:
  - 版本控制
---

在Git 内都只有三种状态：已提交（committed），已修改（modified）和已暂存（staged）。

要检查已有的配置信息，可以使用git config --list 命令
git个人配置文件放在个人用户根目录下：.gitconfig
[push]
default = matching

warning: You can specify what action you want to take in this case, and
warning: avoid seeing this message again, by configuring 'push.default' to:
warning: 'nothing' : Do not push anything
warning: 'matching' : Push all matching branches (default)
warning: 'tracking' : Push the current branch to whatever it is tracking
warning: 'current' : Push the current branch

通过如下修改：
git config push.default matching
或者：
git config --global push.default matching

文件.gitignore 的格式规范如下：
• 所有空行或者以注释符号＃ 开头的行都会被Git 忽略。
• 可以使用标准的glob 模式匹配。
• 匹配模式最后跟反斜杠（/）说明要忽略的是目录。
• 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。

若要看已经暂存起来的文件和上次提交时的快照之间的差异，可以用git diff --cached
命令。（Git 1.6.1 及更高版本还允许使用git diff --staged，效果是相同的，但更好记
些。）

给git commit 加上-a 选项，Git
就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过git add 步骤：
$ git commit -a -m 'added new benchmarks'
[master 83e38c7] added new benchmarks
1 files changed, 5 insertions(+), 0 deletions(-)

想回顾下提交历史，可以使用git log命令查看
$ git log --pretty=oneline
$ git log --pretty=format:"%h - %an, %ar : %s"
%H 提交对象（commit）的完整哈希字串
%h 提交对象的简短哈希字串
%T 树对象（tree）的完整哈希字串
%t 树对象的简短哈希字串
%P 父对象（parent）的完整哈希字串
%p 父对象的简短哈希字串
%an 作者（author）的名字
%ae 作者的电子邮件地址
%ad 作者修订日期（可以用-date= 选项定制格式）
%ar 作者修订日期，按多久以前的方式显示
%cn 提交者(committer)的名字
%ce 提交者的电子邮件地址
%cd 提交日期
%cr 提交日期，按多久以前的方式显示
%s 提交说明
$ git log --pretty=format:"%h %s" --graph
-p 按补丁格式显示每个更新之间的差异。
--stat 显示每次更新的文件修改统计信息。
--shortstat 只显示--stat 中最后的行数修改添加移除统计。
--name-only 仅在提交信息后显示已修改的文件清单。
--name-status 显示新增、修改、删除的文件清单。
--abbrev-commit 仅显示SHA-1 的前几个字符，而非所有的40 个字符。
--relative-date 使用较短的相对时间显示（比如，“2 weeks ago”）。
$ git log --since=2.weeks
-(n) 仅显示最近的n 条提交
--since, --after 仅显示指定时间之后的提交。
--until, --before 仅显示指定时间之前的提交。
--author 仅显示指定作者相关的提交。
--committer 仅显示指定提交者相关的提交。
来看一个实际的例子，如果要查看Git 仓库中，2008 年10 月期间，Junio Hamano 提
交的但未合并的测试脚本（位于项目的t/ 目录下的文件），可以用下面的查询命令：
$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01"
--before="2008-11-01" --no-merges -- t/

想要撤消刚才的提交操作，可以使用--amend 选项重新提交：
$ git commit --amend
可以使用git reset HEAD... 的方式取消暂存。

该如何取消修改 $ git checkout --

要查看当前配置有哪些远程仓库，可以用git remote 命令，它会列出每个远程库的简短名字。
要添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用，运行git remote add [shortname] [url]：
从远程仓库抓取数据到本地：
$ git fetch [remote-name]
实际上，默认情况下git clone 命令本质上就是自动创建了本地的master 分支用于跟踪远程仓库中的master 分支（假设远程仓库确实有master 分支）。所以一般我们运行git pull，目的都是要从原始克隆的远端仓库中抓取数据后，合并到工作目录中的当前分支。
git push [remote-name] [branch-name]。如果要把本地的master 分支推送到origin 服务器上（再次说明下，克隆操作会自动使用默认的master 和origin 名字）
以通过命令git remote show [remote-name] 查看某个远程仓库的详细信息，比如要看所克隆的origin 仓库
列出现有标签的命令非常简单，直接运行git tag
创建一个含附注类型的标签非常简单，用-a （译注：取annotated 的首字母）指定标签名字即可：
$ git tag -a v1.4 -m 'my version 1.4'
可以使用git show 命令查看相应标签的版本信息
如果你有自己的私钥，还可以用GPG 来签署标签，只需要把之前的-a 改为-s （译注：取signed 的首字母）即可：
$ git tag -s v1.5 -m 'my signed 1.5 tag'
轻量级标签:$ git tag v1.4-lw
git push 并不会把标签传送到远端服务器上，运行git push origin [tagname] 即可
如果要一次推送所有本地新增的标签上去，可以使用--tags 选项
可以用git config 为命令设置别名。来看看下面的例子：
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
$ git unstage fileA
$ git reset HEAD fileA
$ git config --global alias.last 'log -1 HEAD'

新建一个testing 分支，可以使用git branch 命令：
$ git branch testing
要切换到其他分支，可以执行git checkout 命令
$ git checkout testing
$ git checkout -b 'hotfix'
Switched to a new branch "hotfix"
$ git checkout master
$ git merge hotfix
$ git branch -d hotfix
Deleted branch hotfix (3a0874c).

&nbsp;

Git Gui新建本地项目：

1\. add remote

2.本地合并

3.add. commit.push