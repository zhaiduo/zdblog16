---
title: WP升级测试
tags:
  - CHARACTER SET
  - COLLATION
  - WP升级
  - 测试
id: 222
categories:
  - Mysql
date: 2007-12-11 22:57:51
---

这是一个升级测试！
今天有空把WordPress从2.04升级到2.3.1，默认的数据库字符是latin1，升级后出现乱码，因为wp-config.php里面多了
define('DB_CHARSET', 'utf-8');
define('DB_COLLATE', '');
这两行，按照网上的办法，把utf-8去掉，问题解决。具体原因尚不清楚，有空再看看。

更新：关于[Character Set和Collation](http://dev.mysql.com/doc/refman/5.1/zh/charset.html) (Collation是“整理”的意思，用于不同字符的比较，排序等，如按字母或汉语拼音排序)

*   一个Character Set都可以对应多个Collation，并且有默认的Collation
*   以_ci结尾的Collation，是不区分大小写(Case- Insensitive)的
*   以_cs结尾的Collation，是区分大小写(Case-Sensitive)的
*   以_bin结尾的 Collation，是二进制(Binary)的。
关于如何修改Collation

对于新建Column:

ALTER TABLE tbl_name
[DEFAULT CHARACTER SET character_set_name] [COLLATE collation_name]

对于所有新建table
mysqld --default-character-set=gbk --default-collation=gbk_chinese_ci

这是常用的Character Set和Collation
`mysql&gt; SHOW CHARACTER SET;
+----------+-----------------------------+---------------------+--------+
| Charset  | Description                 | Default collation   | Maxlen |
+----------+-----------------------------+---------------------+--------+
| big5     | Big5 Traditional Chinese    | big5_chinese_ci     |      2 |
| latin1   | cp1252 West European        | latin1_swedish_ci   |      1 |
| latin2   | ISO 8859-2 Central European | latin2_general_ci   |      1 |
| ascii    | US ASCII                    | ascii_general_ci    |      1 |
| ujis     | EUC-JP Japanese             | ujis_japanese_ci    |      3 |
| sjis     | Shift-JIS Japanese          | sjis_japanese_ci    |      2 |
| gb2312   | GB2312 Simplified Chinese   | gb2312_chinese_ci   |      2 |
| gbk      | GBK Simplified Chinese      | gbk_chinese_ci      |      2 |
+----------+-----------------------------+---------------------+--------+
你可以使用mysql&gt; SHOW COLLATION LIKE 'latin1%';查看更多的latin1的COLLATION`