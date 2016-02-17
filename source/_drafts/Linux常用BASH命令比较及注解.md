---
title: Linux常用BASH命令比较及注解
id: 184
categories:
  - Linux/Unix
tags:
---

LESS比MORE更好用，LESS更能来回翻页。

cat 文件名   一屏查看文件内容
rm -rf 非空目录名   递归删除一个非空目录下的一切
find 路经 -name “字符串”   查找路经所在范围内满足字符串匹配的文件和目录
ln 源文件 链接名   创建当前目录源文件的硬链接
ln -s a b   创建当前目录下a的符号链接b
df   用于报告文件系统的总容量，使用量，剩余容量。
du -b /home   查看目前/HOME目录的容量(k)及子目录的容量(k)。
fdisk -l   查看系统分区信息
挂载光驱   mount –t iso9660 /dev/cdrom /mnt/cdrom
rpm –qa 查询已安装RPM
rpm –e 软件包名称   删除具体的软件包
rpm -ivh   rpm –ivh 软件包全名   安装软件包并显示过程
tar –zcvf zhaiduo.tar.gz /mnt   把目录打包并压缩
tar –zxvf zhaiduo.tar.gz   压缩包的文件解压恢复
tar –jxvf zhaiduo.tar.bz2
kill -9 PID  强行终止某个PID进程

more 参考：

[Alphabetical Directory of Linux Commands](http://www.oreillynet.com/linux/cmd/)