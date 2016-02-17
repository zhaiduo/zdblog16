---
title: 'PHP5: Non-static method should not be called statically'
tags:
  - PHP5
  - 出错
id: 292
categories:
  - PHP
date: 2008-06-25 12:53:04
---

今天发现PHP5调用静态方法的时候出现如下的错误:
> Error message: Non-static method My_Class::mystatic() should not be called statically
根据网上搜索的结果:
> These messages are generated in compile time, all the functions are
> executed AFTER that, so error_reporting(0); does not have any effect and
> this is expected behaviour. - [来源](http://bugs.php.net/bug.php?id=40244)
这个错误只是一个E_STRICT错误(Runtime Notice)，不会影响其后的程序执行。解决办法可以隐藏E_STRICT的报告。

另外：关于File_PDF找不到File/PDF/fonts/courierb.php的问题。
[File_PDF](http://pear.php.net/package/File_PDF/)最新源文件里面也没有这个courierb.php文件，先暂时复制courier.php为courierb.php。