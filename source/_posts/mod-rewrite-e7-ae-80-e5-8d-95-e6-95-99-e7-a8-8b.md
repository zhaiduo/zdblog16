---
title: mod_rewrite简单教程
tags:
  - Apache
  - 教程
id: 257
categories:
  - Linux/Unix
date: 2008-04-22 10:44:18
---

**mod_rewrite**是Apache模块中非常有用的一个模块，用于URL的重写与简洁化。
Version 1.2-1.3 [来源](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html)：
RewriteEngine on|off: 激活或者进制重写规则
RewriteBase /subcat 指定重写规则适用的根路径
RewriteCond TestString CondPattern  ：TestString是规则对象，CondPattern是匹配的具体规则；用于定义重写规则的条件；和RewriteRule一块使用。
常用的TestString包括以下服务器变量：
HTTP headers:HTTP_USER_AGENT, HTTP_REFERER, HTTP_COOKIE, HTTP_HOST, HTTP_ACCEPT
connection &amp; request: REMOTE_ADDR, QUERY_STRING
server internals: DOCUMENT_ROOT, SERVER_PORT, SERVER_PROTOCOL
system stuff: TIME_YEAR, TIME_MON, TIME_DAY
RewriteRule Pattern Substitution: Pattern是规则表达式，Substitution是重写替换的对象。
下面是规则表达式的一些说明：
> .           匹配任何单字符
> [chars]     匹配字符串:chars
> [^chars]    不匹配字符串:chars
> text1|text2 可选择的字符串:text1或text2
> ?           匹配0到1个字符
> *           匹配0到多个字符
> +           匹配1到多个字符
> ^           字符串开始标志
> $           字符串结束标志
> n         转义符标志
反向引用 $N 用于 RewriteRule 中匹配的变量调用(0 &lt;= N &lt;= 9)
反向引用 %N 用于 RewriteCond 中最后一个匹配的变量调用(1 &lt;= N &lt;= 9)

RewriteCond适用的标志符
'nocase|NC' (no case)忽略大小
'ornext|OR' (or next condition)逻辑或，可以同时匹配多个RewriteCond条件

RewriteRule适用的标志符
'redirect|R  [=code]' (force redirect)强迫重写为基于http开头的外部转向(注意URL的变化) 如：[R=301,L]
'forbidden|F' (force URL to be forbidden)重写为禁止访问
'proxy|P' (force proxy)重写为通过代理访问的http路径
'last|L' (last rule)最后的重写规则标志，如果匹配，不再执行以后的规则
'next|N' (next round)循环同一个规则，直到不能满足匹配
'chain|C' (chained with next rule)如果匹配该规则，则继续下面的有Chain标志的规则。
'type|T=MIME-type' (force MIME type)指定MIME类型
'nosubreq|NS' (used only if no internal sub-request)如果是内部子请求则跳过
'nocase|NC' (no case)忽略大小
'qsappend|QSA' (query string append)附加查询字符串
'noescape|NE' (no URI escaping of output)禁止URL中的字符自动转义成%[0-9]+的形式。
'passthrough|PT' (pass through to next handler)将重写结果运用于mod_alias
'skip|S=num' (skip next rule(s))跳过下面几个规则
'env|E=VAR:VAL' (set environment variable)添加环境变量

Version 2.0 [来源](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)：

注意：
.htaccess或conf文件中需要设置 RewriteEngine On
并且确认所在目录支持 Options FollowSymLinks
> 例子：
> RewriteEngine on
> RewriteCond %{HTTP_USER_AGENT} ^MSIE [NC,OR]
> RewriteCond %{HTTP_USER_AGENT} ^Opera [NC]
> RewriteRule ^.* - [F,L] 这里"-"表示没有替换，浏览器为IE和Opera的访客将被禁止访问。
更多事例可以参考：[http://httpd.apache.org/docs/2.0/rewrite/rewrite_guide.html](http://httpd.apache.org/docs/2.0/rewrite/rewrite_guide.html)。
> 例子：
> RewriteEngine On
> RewriteBase /test
> RewriteCond %{REQUEST_FILENAME}.php -f
> RewriteRule ([^/]+)$ /test/$1.php
> #for example: /test/admin =&gt; /test/admin.php
> RewriteRule ([^/]+).html$ /test/$1.php [L]
> #for example: /test/admin.html =&gt; /test/admin.php
> 限制目录只能显示图片
> &lt; IfModule mod_rewrite.c&gt;
> RewriteEngine on
> RewriteCond %{REQUEST_FILENAME} !^.*.(gif|jpg|jpeg|png|swf)$
> RewriteRule .*$ - [F,L]
> &lt; /IfModule&gt;

> TAG标签重写
> #/tag+me.html => /tag/me/
> RewriteRule zhaiduo/tag/([0-9a-zA-Z]+)/$  zhaiduo/tag+$1.html [L]
> #/tag+me_2.html => /tag/me/2/
> RewriteRule zhaiduo/tag/([0-9a-zA-Z]+)/([0-9]+)/$  zhaiduo/tag+$1_$2.html [L]