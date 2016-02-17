---
title: 为什么PHP做网站要使用框架？
tags:
  - framework
id: 1889
categories:
  - PHP
date: 2014-03-03 21:09:23
---

如果用PHP做网站不用框架，下面问题如何解决？
* 相应代码缺少注释，文档化麻烦
* 前后台没有框架机制，不利维护和敏捷开发
* 没有缓存机制，无法快速切换各种缓存模块
* 没有错误处理机制，无法系统排错，无法准确定位错误点
* 缺少模板机制，代码HTML混杂，降低安全性

PHP做网站使用框架framework的好处

* 面向对象，扩展性好
* 模块化，可重用性高
* 底层封装，更少的代码量，更快速度开发
* 代码管理，文档化方便，也利于Unit test

目前流行的PHP框架：

* http://framework.zend.com/
* http://ellislab.com/codeigniter
* http://cakephp.org/
* http://yiiframework.com/
* http://laravel.com/
* http://symfony.com/

CakePHP 开发框架
如果你仍然需要编写面向PHP4兼容的代码，CakePHP 将是一个非常不错的选择， 在PHP 4 & 5的MVC式框架列表里面，CakePHP都曾经是最流行的。

Zend Framework框架
Zend Framework 是面对一些较有经验的开发者和从底层构建一些企业级应用程序而设计的。

CodeIgniter
CodeIgniter 是一个PHP5.2+ 的MVC框架，它体积小巧切具有丰富的文档资源。通常被称为“初学者框架”。

Symfony
Symfony 是最古老的PHP框架之一，他同样也是转为企业级Web应用程序而设计的。Symfony使用命令行代码生成工具来为项目快速生成所需的代码。
Symfony的网站上手机了大量的教程和范例代码，来帮助你熟悉掌握他们。

Yii Framework
Yii 是一个高度模块化，高性能的PHP5框架，专门为了Web应用程序而开发。Yii是其最主要一大特性，运行起来比Codeigniter和Zend框架要快。