---
title: 'PHP5成员重载错误: Indirect modification of overloaded property has no effect'
tags:
  - PHP5
id: 483
categories:
  - PHP
date: 2010-01-14 13:56:26
---

PHP5成员重载的时候
> Class Foo{
> private $arr;
> public function __get($key) {
> if(isset($this-&gt;arr[$key])){
> return $this-&gt;arr[$key];
> }
> }
> 
> public function __set($key, $val) {
> if(isset($this-&gt;arr[$key])){
> $this-&gt;arr[$key] = $val;
> }
> }
> }
> $f = new Foo;
> $f-&gt;test = 1;
出现如下错误：
> Notice: Indirect modification of overloaded property Foo::$arr has no effect
根据Google结果：
[[27 Sep 2007 8:16pm UTC] brjann at gmail dot com](http://bugs.php.net/bug.php?id=41641)
> It seems that declaring the getter as "public function &amp;__get(){...}" does the trick. However, it took some googling to find.
[php magic __set and __get](http://dev.iordanov.net/archives/6)
> this one works as expected. Actually php interpreter seems to do same thing. Trying to get value if exists and change it. Problem is that when it takes this value there is no place to store it and rise this error. Trying to modify property in not existing array. Solution is to make this array available. Returning values by reference seems to work.
解决办法是给__get()加上引用传递&amp;__get，
> public function &amp;__get($key) {
> return $this-&gt;arr[$key];
> }
> $f-&gt;array['test'] = 1;
试图帮助函数找到引用被绑定的不存在的变量arr。但是这里存在没有调用__set的问题。
我的办法是$arr转为公有化，放弃__set。
> public $arr;
> $f-&gt;arr['test'] = 1;