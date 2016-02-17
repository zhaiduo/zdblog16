---
title: Falcon测试
tags:
  - git
  - 出错
id: 2174
categories:
  - Python
---

[falcon](http://falcon.readthedocs.org/en/latest/user/install.html)是个高性能的python框架。

/////////////先来安装
$ pip install --upgrade cython falcon
安装出错：
cython error: Unable to find vcvarsall.bat

set DISTUTILS_USE_SDK=1
set MSSdk=1
pip install cython

再次出错：
error: command 'cl.exe' failed: No such file or directory

 try to install the Microsoft Visual C++ 2008 Redistributable Package

重启后，安装装成功（虽然有些小的warning提示）：
set DISTUTILS_USE_SDK=1
set MSSdk=1
pip install cython

cython -v

然后安装falcon出错: pip install falcon

ValueError: [u'path']

根据这里的[issue](http://bugs.python.org/issue7511)，下载[新的msvc9compiler.py](https://bitbucket.org/jurko/cpython/src/b0962aec201e7d4b4f1ac32dbc130379ec6d943a/Lib/distutils/msvc9compiler.py?at=jurko/distutils_msvc_express_fix)到C:Python27libdistutilsmsvc9compiler.py，问题解决，安装成功。

再运行一下 pip install --upgrade cython falcon

/////////测试

pip install uwsgi
出错:uwsgi 'module' object has no attribute 'uname'
因为：No uWSGI does not run on windows

falcon example: http://www.giantflyingsaucer.com/blog/?p=4342

try:
pip install gunicorn
example:https://pypi.python.org/pypi/falcon/0.2.0b2

Error:
ImportError: No module named fcntl
ImportError: No module named resource

看来windows下没法玩...

重新玩centos7:(记得yum install gcc epel-release -y)
yum install python-pip -y
pip install cython
Error: pyconfig.h not found
try: yum install python-devel -y

pip install falcon

/////////安装完成

//安装git server
yum install git -y

mkdir /home/adam/repo #create directory for new repository
cd /home/adam/repo
git init
touch firstfile
git add .
git commit

cd /home/adam
git clone --bare ./repo repo.git
touch repo.git/git-daemon-export-ok

客户端：
git clone ssh://adam@localhost:2222/home/adam/repo.git

Now we want to submit the changes back to the git server:
git push

git push出错：
remote: error: insufficient permission for adding an object to repository database ./objects
remote: fatal: failed to write object
error: unpack failed: unpack-objects abnormal exit
try: chown -R adam:adam repo.git

//测试代码

服务器端：cd /home/adam/
git clone ./repo.git adamrepo
就把客户端提交的代码放入服务器端。

服务器端修改后，也可以git push到repo.git。

客户端刷新服务器端修改的代码：
git clone ssh://adam@localhost:2222/home/adam/repo.git adamrepo
或者用：
git pull 从远程获取最新版本并merge到本地
git fetch origin (更新后不是最新的，还需要git merge origin) 从远程获取最新版本到本地，不会自动merge

客户端修改后:
git stage .
git commit -m ""

git push origin

//测试falcon

pip install uwsgi