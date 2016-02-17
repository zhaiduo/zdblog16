---
title: 打造自己的FireFox插件(Add-ons)
tags:
  - FireFox
  - 插件
id: 422
categories:
  - javascript
date: 2009-10-15 00:07:36
---

根据最新的[FF官方插件教程](https://developer.mozilla.org/En/Firefox_addons_developer_guide/Let%27s_build_a_Firefox_extension)，再加上[7zip](http://www.7-zip.org/)的帮助，我们可以轻松打造自己的FireFox插件。
先准备生成xpi的所有文件，目录结构如下：（假设插件名为zhaiduo）

*   插件目录zhaiduo

    *   文件install.rdf
    *   文件chrome.manifest
    *   目录chrome

            *   目录content

                    *   文件overlay.xul
            *   文件overlay.js

                *   目录locale

                    *   目录en-US

                            *   文件zhaiduo.dtd

                *   目录skin

                    *   文件overlay.css
            *   文件icon.png
根据教程准备好文件后，安装好7zip，然后利用下面的bat脚本调用7-zip自动生成xpi文件即可：
> set x=%cd%
> md buildchrome
> cd chrome
> 7z a -tzip "%x%.jar" * -r -mx=0
> move "%x%.jar" ..buildchrome
> cd ..
> copy install.* build
> copy chrome.manifest build
> cd build
> 7z a -tzip "%x%.xpi" * -r -mx=9
> move "%x%.xpi" ..
> cd ..
> rd build /s/q