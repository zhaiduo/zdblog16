---
title: PHP上传GIF文件的安全溢出问题
id: 185
categories:
  - PHP
date: 2007-07-18 22:21:01
tags:
---

今天看到[PHP Classes](http://www.phpclasses.org)博客上提到的[PHP上传GIF文件的安全溢出漏洞](http://www.phpclasses.org/blog/post/67-PHP-security-exploit-with-GIF-images.html)，觉得这是一个很严重的问题。就算我们验证了GIF文件的类型和通过getimagesize()验证了GIF文件大小，PHP代码仍有可能被嵌入GIF文件中，就像〈?php readfile('/etc/passwd'); ?〉，很有可能被黑客利用。

这是他们提供的解决办法：

1\. 利用.htaccess或httpd.conf限制上传文件所在目录执行PHP的权限。

< FilesMatch ".php$" >
deny from all
< /FilesMatch>

2\. 避免直接调用上传的GIF文件。如：src="image.php?uploaded.gif" mce_src="image.php?uploaded.gif"。

3\. 利用GD模块复制上传的GIF文件。

我的办法是可以设置 Apache，限定refer来自本站的才能调用GIF，就是常规的网站防盗链的办法[ Allow from env=local_ref ]。
总的感觉解决办法让上传GIF文件变得有些碍手碍脚。不知道还有什么其他解决办法。