---
title: Ruby常见问题
id: 2138
categories:
  - Coding
tags:
---

gem install rails出错：
ERROR:  Error installing json:
        The 'json' native gem requires installed build tools.

先下载安装：DevKit http://github.com/oneclick/rubyinstaller/wiki/Development-Kit

然后：
Run cd C:Ruby193DevKit
Run ruby dk.rb init
Run ruby dk.rb review
Run ruby dk.rb install

gem install json --platform=ruby
ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"