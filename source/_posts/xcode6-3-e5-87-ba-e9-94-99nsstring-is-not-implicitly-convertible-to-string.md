---
title: Xcode6.3出错NSString is not implicitly convertible to String
tags:
  - iOS
  - swift
id: 2335
comment: false
categories:
  - MAC
date: 2015-04-14 22:37:47
---

Xcode6.3最近更新后，swift出错：NSString is not implicitly convertible to String

直接用as String或者String()转型即可。

比如：

> pathForResource(shaderName, ofType: "glsl")
> ＝》
> pathForResource(shaderName as String, ofType: String("glsl"))