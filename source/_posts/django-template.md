---
title: Django模板有特色的几个地方
tags:
  - python
id: 1084
categories:
  - 网站技术
date: 2010-09-22 01:10:58
---

过去写过简单的模板引擎，以追求模板语法的简洁化为目标。主要分为三大部分：简单变量、条件判断和数组循环。条件判断和数组循环还各自支持嵌套语法。最近了解[Django的模板引擎](http://www.djangoproject.com/documentation/0.96/templates/)比较多，觉得这么几个地方很喜欢和值得思考：

*   模板的继承
帮助减少模板的重复内容，将模板对象化，程序化。只需要<tt>extends</tt>列出集成的模板，根据不同情况替换block的内容即可。而我以前的办法是嵌套的include其他模板。
*   模板变量的过滤、排序功能
模板语法支持字符串处理、列表排序，减轻了程序的负担，增加了模板的灵活性。
*   通过[load](http://docs.djangoproject.com/en/dev/howto/custom-template-tags/)在模板里面引用外部程序内容，而以前主要是通过公共变量来处理。
可以减少无用的公共变量定义，如果有需要直接在模板里引用。