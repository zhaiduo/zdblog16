---
title: RTML使用技巧
tags:
  - RTML
id: 66
categories:
  - Uncategorized
date: 2006-11-28 13:04:07
---

[RTML](http://developer.yahoo.com/stores/V1/rtml.html)某些语句会大量增加导入内存的对象，造成缓存溢出，影响硬盘读取速度，从而导致生成模板速度降低，我们应该尽量避免使用他们的次数：
> * WITH-OBJECT
> * FOR-EACH-OBJECT
> * GET-PATH-TO
> * GET-ALL-PATHS-TO
另外注意结构上的调整，防止生成过于复杂或是过多的Paths，影响发布速度。
快速删除多个items，可以把要删除的items的Path指到一个新建的临时section，直接删除section就可以了。

关于分页，一般有两种解决办法，一种是使用javascript伪装分页，但是这种方法对搜索引擎不太有好，模板编辑太复杂。另外就是通过脚本控制生成分页的CSV，直接上传就可以了。

另外，困惑的是，yahoo有自带有一个自动分页的模板，可惜不能直接修改。不知道升级账户会不会开放自己订制这个分页模板。

附：[Yahoo的RTML Help](http://help.yahoo.com/l/us/yahoo/smallbusiness/store/edit/advanced/advanced-37.html)