---
title: "关于UnicodeDecodeError: 'ascii' codec can't decode的错误"
tags:
  - GAE
  - Jinjia2
  - mongodb
  - openshift
  - python
id: 1770
categories:
  - NoSQL
  - Python
date: 2013-01-26 02:40:55
---

由于[GAE博客](http://www.wancp.info/)使用的是Master/Slave datastore，被要求更换为[High Replication Datastore Migration](https://developers.google.com/appengine/docs/adminconsole/migration)，考虑到暂时不想重写程序，所以试着把[GAE博客](http://www.wancp.info/)迁移到Openshift。可是没想到在迁移的过程中被UnicodeDecodeError这个错误拖延了一个多月，看来Python 2.7的[unicode encode/decode](http://docs.python.org/2/library/codecs.html#standard-encodings)是挺折腾人的。

GAE datastore 的备份数据是[sqlite3](http://www.sqlite.org/pragma.html)格式，转换到mongoDB都还顺利，可是在用jinjia2显示的时候总是出现UnicodeDecodeError或者UnicodeEncodeError。开始以为错误在于数据库存储过程中的转码错误，[sqlite3](http://docs.python.org/2/library/sqlite3.html)出来的数据是latin_1，存入mongodb要encode成utf-8，提取出来用decode，然后encode latin_1就行。可是依然出现类似这样的错误：“UnicodeDecodeError: 'ascii' codec can't decode”。

我尝试了is_ascii(blog), isinstance(blog, unicode), from django.utils.encoding import smart_str, unicode(blog_nr.strip(codecs.BOM_UTF8), 'utf-8')等等，最后repr测试发现mongodb数据的存储/获取是没有问题的，问题出在[jinjia2](http://jinja.pocoo.org/docs/api/)的模板采用unicode编码，
> Jinja2 is using Unicode internally which means that you have to pass Unicode objects to the render function or bytestrings that only consist of ASCII characters.
答案很简单，mongoDB出来的数据再加上unicode(blog, "utf8")就完美了。