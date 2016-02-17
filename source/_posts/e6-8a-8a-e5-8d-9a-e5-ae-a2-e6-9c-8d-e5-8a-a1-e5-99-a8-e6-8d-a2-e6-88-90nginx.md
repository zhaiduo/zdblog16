---
title: 把博客服务器换成Nginx
tags:
  - Nginx
  - Wordpress
id: 1630
categories:
  - Linux/Unix
  - 云时代
  - 网站维护
date: 2012-06-25 03:30:18
---

最近博客所在服务器不太稳定，常常出现打不开的情况。考虑到Nginx在性能上的巨大优势。我把博客从Apache服务器已到了Nginx的服务器。
由于Nginx不支持.htaccess，所以需要在conf里面用Nginx的语法配置重写规则。

主要添加修改如下部分：
> location / {
>         index index.php;
>         if (!-e $request_filename) {
>           rewrite ^.* /index.php break;
>           fastcgi_pass 127.0.0.1:9991;
>         }
>         include fcgi.conf;
>     }

之前忘了加入fastcgi_pass，打开Wordpress内页会提示下载index.php。如果忘了include fcgi.conf，缺少fastcgi_param SCRIPT_FILENAME $document_root/index.php。则Nginx服务器找不到网站目录，会提示“No input file specified. ”的错误。

目前，服务器一切正常，感觉速度提升很明显。再观察几天看看是否出现新的问题。另外，更多关于wordpress在Nginx下的安全配置，可以[参考这里](http://codex.wordpress.org/Nginx)。