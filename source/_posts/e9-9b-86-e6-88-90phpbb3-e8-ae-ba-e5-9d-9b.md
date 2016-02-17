---
title: 集成phpBB3论坛
tags:
  - phpBB
  - 问题
id: 794
categories:
  - PHP
date: 2009-02-06 18:05:00
---

[phpBB3](http://www.phpbb.com/downloads)从功能和界面上都是很不错的免费论坛程序。要把它和自己的系统结合起来其实也没有想象的那么复杂。这里有个简单的方案：
<span style="font-weight: bold;">主要目标</span>

*   做到原有系统用户可以自动登录论坛
如果用户已经登录原有系统，检查该用户是否在论坛有同名帐号，否则自动生成和用户同名的帐号，然后自动论坛。
*   从论坛注册和登录都会自动到转到原有系统的注册和登录页面。
屏蔽原论坛的注册登录功能，以及修改密码功能。
修改时遇到如下错误：
> Strict Standards: Non-static method utf_normalizer::nfkc() should not be called statically
还不清楚原因何在，临时解决办法：先屏蔽utf8_clean_string函数。修改如下：
> Edit: includes/auth.php
> 885 function login($username, $password, $autologin = false, $viewonline = 1, $admin = 0, $noclean = 0)
> 908 user_add($login['user_row'], (isset($login['cp_data'])) ? $login['cp_data'] : false);
> if($noclean == 1){
> $clean_name=$username;
> }else{
> $clean_name=utf8_clean_string($username);
> }
> $sql = 'SELECT user_id, username, user_password, user_passchg, user_email, user_type
> FROM ' . USERS_TABLE . "
> WHERE username_clean = '" . $db-&gt;sql_escape($clean_name) . "'";
> Edit: includes/auth/auth_db.php
> 27 function login_db(&amp;$username, &amp;$password, $noclean=0)
> if($noclean == 1){
> $clean_name=$username;
> }else{
> $clean_name=utf8_clean_string($username);
> }