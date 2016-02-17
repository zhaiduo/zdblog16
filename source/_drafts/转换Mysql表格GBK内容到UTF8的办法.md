---
title: 转换Mysql表格GBK内容到UTF8的办法
tags:
  - GBK
  - UTF8
id: 1731
categories:
  - Mysql
  - PHP
---

Mysql数据表内包含大量GBK编码的乱码数据，如何快速批量的转换成UTF8编码，而且可以正常显示中文？我想到的办法如下：

1.  先用PHP导出iconv转码成UTF8编码生成SQL文件，再导入。但是缺点是不适合数据量大的转换，比如超过100万的数据量。
2.  借用改变浏览器编码的方式复制正常显示中文。不过也不适合大量数据。
3.  队列处理一个个的转码处理。
最后办法：

用程序output.php导出生成正常显示中文的sql文件，再用Editplus另存为utf8格式，鼠标全选复制到phpmyadmin的sql运行框，最后展示程序需要：set names utf8。