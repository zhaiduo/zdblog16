---
title: Linux基本管道命令
id: 2298
comment: false
categories:
  - Linux/Unix
tags:
---

基本的管线命令指令介绍

run > log 2>&1 把所有错误写入log(重定向仅影响 stdout，不影响 stderr，stderr 被重定向到 stdout 的当前位置，即 log)

run 2>&1 >log 把所有错误写入log(可能会保存不成功)

• cut
语法：[root @test /root ]# cut -d "分隔字符" [-cf] fields
参数说明：
-d ：后面接的是用来分隔的字符，预设是『空格符』
-c ：后面接的是『第几个字符』
-f ：后面接的是第几个区块？
范例：[root @test /root]# cat /etc/passwd | cut -d ":" -f 1
将 passwd 这个文件里面，每一行里头的 : 用来作为分隔号，而列出第一个区块！也就是姓名所在啦！
[root @test /root]# last | cut -c1-20
将 last 之后的数据，每一行的 1-20 个字符取出来！
• sort
语法：[root @test /root ]# sort [-t 分隔符] [(+起始)(-结束)] [-nru]
参数说明：
-t 分隔符：使用分隔符来隔开不同区间，预设是 tab
+start -end：由第 start 区间排序到 end 区间
-n ：使用『纯数字』排序（否则就会以文字型态来排序）
-r ：反向排序
-u ：相同出现的一行，只列出一次！
范例：[root @test /root]# cat /etc/passwd | sort将列出来的个人账号排序！
[root @test /root]# cat /etc/passwd | sort -t: +2n将个人账号中，以使用者 ID 来排序（以 : 来分隔，第三个为 ID ，但第一个代号为 0 之故）
[root @test /root]# cat /etc/passwd | sort -t: +2nr反相排序啰！
• wc
语法：[root @test /root ]# wc [-lmw]
参数说明：
-l ：多少行
-m ：多少字符
-w ：多少字
范例：[root @test /root]# cat /etc/passwd | wc -l这个文件里头有多少行？
[root @test /root]# cat /etc/passwd | wc -w这个文件里头有多少字！？
• uniq这个指令用来将『重复的行删除掉只显示一个』
语法：[root @test /root ]# uniq
范例：[root @test /root]# last | cut -d" " -f1 | sort | uniq
• tee命令重定向到文件的同时将数据显示在屏幕上
语法：[root @test /root ]# last | tee last.list | cut -d " " -f1
范例：[root @test /root]# last | tee last.list | cut -d " " -f1
• tr
语法：[root @test /root ]# tr [-ds] SET1
参数说明：
-d ：删除 SET1 这个字符串
-s ：取代掉重复的字符！
范例：[root @test /root]# last | tr '[a-z]' '[A-Z]' <==将小写改成大写
[root @test /root]# cat /etc/passwd | tr -d : <== : 这个符号在 /etc/passwd 中不见了！
[root @test /root]# cat /home/test/dostxt | tr -d '\r' > dostxt-noM
• split
语法：[root @test /root ]# split [-bl] 输入文件 输出文件前导字符
参数说明：
-b ：以文件 size 来分
-l ：以行数来分
范例：[root @test /root]# split -l 5 /etc/passwd test <==会产生 testaa, testab, testac... 等等的文件
说明：在 Linux 底下就简单的多了！你要将文件分割的话，那么就使用 -b size 来将一个分割的文件限制其大小，如果是行数的话，那么就使用 -l line 来分割！
管线命令在 bash 的连续的处理程序中是相当重要的！另外，在 log file 的分析当中也是相当重要的一环。
管道输送到一个命令的标准输入可以使用标准输入参数”-“ 进行更仔细的控制.如cat命令的示例
eg:  sort mylist | more
sort mylist | cat –n | lpr
pwd | cat – mylist | lpr

More:
http://www.ibm.com/developerworks/cn/linux/l-lpic1-v3-103-4/index.html