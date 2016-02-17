---
title: Nginx + php-fpm 504 Gateway Time-out
tags:
  - Nginx
  - time-out
id: 1910
categories:
  - Linux/Unix
date: 2014-04-07 00:25:21
---

Nginx log error like the following:
2014/04/06 23:54:32 [error] 13340#0: *25756 upstream timed out (110: Connection timed out) while reading response header from upstream

Add three timeouts, the problem is resolved.

nginx.conf:
http{
    fastcgi_connect_timeout 300s;
    fastcgi_send_timeout 300s;
    fastcgi_read_timeout 300s;
    #fastcgi_buffer_size 128k;
    #fastcgi_buffers 8 128k;
    #fastcgi_busy_buffers_size 256k;
    #fastcgi_temp_file_write_size 256k;
    #fastcgi_intercept_errors on;
}