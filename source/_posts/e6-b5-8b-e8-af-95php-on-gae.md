---
title: 测试PHP on GAE
tags:
  - GAE
id: 1832
categories:
  - PHP
  - 云时代
date: 2013-09-24 21:43:03
---

考虑到未来对PHP代码的保存和测试、开发的方便，我决定使用Mac版。

安装指导看这里：[https://developers.google.com/appengine/docs/php/gettingstarted/installing](https://developers.google.com/appengine/docs/php/gettingstarted/installing)

Mac版的安装，需要先安装[macports](https://www.macports.org/install.php)。 我用的是lion版的pkg文件。

最后启动PHP SDK：
./dev_appserver.py --php_executable_path=/opt/local/bin/php-cgi54 helloworld/

浏览localhost:8080成功。

在申请到PHP的High Replication应用后，

提交到GAE：appcfg.py update helloworld/

测试成功！