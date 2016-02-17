---
title: UTF格式下字符串的比较
id: 1488
categories:
  - PHP
date: 2012-02-24 17:28:17
tags:
---

有两个UTF8的文本文件，前5个字符都是"uid"，可是用PHP来比较，==和strcmp都不对。十六进制下看，确实是有不同：
[![](http://www.zhaiduo.com/wp-content/uploads/2012/02/strcompare_wired-300x83.jpg "strcompare_wired")](http://www.zhaiduo.com/2012/02/utf%e6%a0%bc%e5%bc%8f%e4%b8%8b%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%9a%84%e6%af%94%e8%be%83/strcompare_wired/)
肉眼完全无法辨别。0xFFFE2200后面多了“0xFFFE”这个字符串。原来是有名的[U+FEFF. BOM](http://en.wikipedia.org/wiki/Byte_order_mark)。

根据维基的解释，多了FFFE的这个文件实际上是个UTF-16格式。
> In [UTF-16](http://en.wikipedia.org/wiki/UTF-16 "UTF-16"), a BOM (`U+FEFF`) may be <span style="text-decoration: underline;">placed as the first character of a fil</span>e or character stream to indicate the endianness (byte order) of all the 16-bit code units of the file or stream.
英文倒是好办，用匹配模式清楚杂物即可。中文的话难道要不断检测“0xFFFE”这个字符串。特别是对于不懂技术的客户来说，这可真是伤脑筋。