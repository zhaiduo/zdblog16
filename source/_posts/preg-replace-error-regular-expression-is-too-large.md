---
title: 'preg-replace error: regular expression is too large'
tags:
  - 出错
id: 754
categories:
  - PHP
date: 2010-07-22 15:33:55
---

进行模板替换的时候出现如下错误：
> Error msg: preg_replace() [function.preg-replace]: Compilation failed: regular expression is too large at offset 62894
根据[PHP.net](http://www.php.net/manual/en/pcre.configuration.php#ini.pcre.backtrack-limit)的解释：
这个错误是由PCRE的倒带(backtracking)和递归(recursion)限制造成，可以通过修改ini解决。
> print_r(ini_get_all("pcre"));
> [pcre.backtrack_limit] =&gt; Array
> (
> [global_value] =&gt; 100000
> [local_value] =&gt; 100000
> [access] =&gt; 7
> )
> [pcre.recursion_limit] =&gt; Array
> (
> [global_value] =&gt; 100000
> [local_value] =&gt; 100000
> [access] =&gt; 7
> )
> ini_set('pcre.backtrack_limit', '300000');
如果使用的虚拟主机，也只有重新修改程序，换一种替换方式了。

究其原因在于我用的模板里面把loop嵌套在if里面，导致if语块的字符串太长造成的，所以应该尽量避免把loop嵌套在if里面。

另外一种常见的错误是：fopen() [function.fopen]: URL file-access is disabled in the server configuration
虚拟主机禁止了fopen非本地文件的访问，解决办法可以用：[fsockopen](http://www.php.net/manual/en/function.fsockopen.php)。