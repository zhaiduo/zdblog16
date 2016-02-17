---
title: CentOs6.5测试Hadoop
tags:
  - hadoop
  - java
  - 大数据
id: 1971
comment: false
categories:
  - 云时代
date: 2014-07-30 23:15:19
---

References:
http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/
http://wiki.apache.org/hadoop/GettingStartedWithHadoop
http://blog.csdn.net/fuwencaho/article/details/37727873

/////////////////////////////////////////////////////////////

=======
Test Single-node-cluster Hadoop on CentOS6.5
=======

wget http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.i686.rpm
yum remove java-1.5.0-*
yum install java-1.6.0-openjdk.i686
export JAVA_HOME=/usr/lib/jvm/jre-1.6.0-openjdk
java -version

sudo groupadd hadoop
sudo useradd -g hadoop hduser

ssh-keygen -t rsa
cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys

/etc/sysctl.conf
# disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

cd /usr/local
http://mirrors.hust.edu.cn/apache/hadoop/core/hadoop-2.4.1/hadoop-2.4.1.tar.gz

cd /usr/local
$ sudo tar xzf hadoop-1.0.3.tar.gz
$ sudo mv hadoop-1.0.3 hadoop
$ sudo chown -R hduser:hadoop hadoop

//////////////////////////////

vi $HOME/.bashrc
=====================================
# Set Hadoop-related environment variables
export HADOOP_HOME=/usr/local/hadoop

# Set JAVA_HOME (we will also configure JAVA_HOME directly for Hadoop later on)
export JAVA_HOME=/usr/lib/jvm/jre-1.6.0-openjdk

# Some convenient aliases and functions for running Hadoop-related commands
unalias fs &> /dev/null
alias fs="hadoop fs"
unalias hls &> /dev/null
alias hls="fs -ls"

# If you have LZO compression enabled in your Hadoop cluster and
# compress job outputs with LZOP (not covered in this tutorial):
# Conveniently inspect an LZOP compressed file from the command
# line; run via:
#
# $ lzohead /hdfs/path/to/lzop/compressed/file.lzo
#
# Requires installed 'lzop' command.
#
lzohead () {
    hadoop fs -cat $1 | lzop -dc | head -1000 | less
}

# Add Hadoop bin/ directory to PATH
export PATH=$PATH:$HADOOP_HOME/bin
===================================

/////////////////

$ sudo mkdir -p /app/hadoop/tmp
$ sudo chown hduser:hadoop /app/hadoop/tmp
# ...and if you want to tighten up security, chmod from 755 to 750...
$ sudo chmod 750 /app/hadoop/tmp

/usr/local/hadoop/bin/hadoop namenode -format

echo "foo foo quux labs foo bar quux" | python ./mapper.py
echo "foo foo quux labs foo bar quux" | python ./mapper.py | sort -k1,1 | /home/hduser/reducer.py

if Error:
hadoop ssh: Could not resolve hostname
try:
sbin/start-dfs.sh

if Error:
cat: /usr/local/hadoop/conf/slaves: No such file or directory
try:
cp /hadoop/etc/hadoop/slaves /hadoop/conf/

if Error:
-copyFromLocal: /home/hduser  No such file or directory
try:
/usr/local/hadoop$ hdfs dfs -mkdir -p /user/hduser

Test with 332KB text:
/usr/local/hadoop/bin/hadoop dfs -copyFromLocal /home/hduser/tmp/*.txt /user/hduser/adam/
/usr/local/hadoop/bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.4.1.jar wordcount /user/hduser/adam/*.txt /user/hduser/adam-out
 /usr/local/hadoop/bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.4.1.jar wordcount -D mapred.reduce.tasks=16 /user/hduser/adam/*.txt /user/hduser/adam-out2

Result:
# /usr/local/hadoop/bin/hadoop dfs -cat /user/hduser/adam-out/part-r-00000 > words-count.txt
sort -n -k 2 -t t words-count.txt

重复次数最多的单词如下：
development     11
element 11
effect  12
left    12
That    12
amount  13
heat    13
planet  13
vast    13
went    13
bright  14
get     14
last    14
Mount   14
put     14
against 15
right   15
ancient 16
just    16
present 16
yet     16
might   19
fact    21
almost  25
part    28
point   29
What    29
cannot  33
different       39
what    62
first   65
most    66
But     67
must    67
out     80
about   83
light   98
great   114
but     131
It      161
not     200
at      226
it      385