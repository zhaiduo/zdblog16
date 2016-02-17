---
title: "PHP post error: Forbidden - You don't have permission to access"
tags:
  - 出错
id: 102
comment: false
categories:
  - PHP
date: 2007-01-08 12:16:16
---

When we post a form with PHP, some errors maybe return, such as: 500 SERVER Error, or:
> <p align="left">Forbidden
> You don't have permission to access /post.php on this server.Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.
Here are some explains may help:
> We had installed a software to block attack against the web-server which caused the trouble for you.We have tweaked that to allow the URL format.
A similar reason same as the above explain, they will redirect your post, when your post includes some "security" words, such as: "inc","curl".

Further more optional reasons:
> In the control panel of hosting, the PHP scripts doesn't need special permissions, but mod_php is configured in safe mode, so if I need PHP-CGI scripts or applications that install something, You need permissions (770). Besides, need to create a .htaccess file with the command: Options ExecCGI.
> mod_security:
> ModSecurityTM is an open source intrusion detection and prevention engine for web applications (or a web application firewall). Operating as an Apache Web server module or standalone, the purpose of ModSecurity is to increase web application security, protecting web applications from known and unknown attacks.
> 
> While mod_security can be a very powerful tool, misconfigured or overly strict rule sets can interfere with vBulletins Operation. Below for Apache users you can use an htaccess file and add a specific rule to disable mod_security.
> 
> Make or edit your forum .htaccess file and add the following code
> Code:
> 
> &lt; IfModule mod_security.c &gt;
> SecFilterEngine Off
> SecFilterScanPOST Off
> &lt; /IfModule&gt;
or
> < IfModule mod_security.c>
> SecFilterInheritance Off
> < /IfModule>

place this file in your problem directory.
----------------------------------------