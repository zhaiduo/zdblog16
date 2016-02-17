---
title: UTF8的BOM让FirFox一片空白
tags:
  - utf-8
  - 问题
id: 801
categories:
  - PHP
date: 2009-03-08 02:57:00
---

今天遇到在FirFox/IE下，网页都是一片空白的问题，以为和IE的META Content-Type问题类似。可是毫无效果。在二进制下看到网页尾部多了EF BB BF三个字节，原来是[UTF8的BOM](http://en.wikipedia.org/wiki/Byte-order_mark)(Byte Order Mark)在搞鬼。 将这三个字节过滤掉，问题解决。呼～三点了,觉去。。。