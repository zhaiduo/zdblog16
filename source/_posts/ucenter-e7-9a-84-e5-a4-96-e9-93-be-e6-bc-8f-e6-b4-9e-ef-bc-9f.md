---
title: Ucenter的外链漏洞？
tags:
  - Ucenter
  - discuz
  - 漏洞
  - 链接
id: 667
categories:
  - 杂项
date: 2010-07-05 14:14:47
---

最近常在[zaccode](http://www.zaccode.com/space-3603.html)晃悠，zaccode用的是Discuz开发的Ucenter社区程序，在Ucenter里面发布日志话题的时候，在里面的链接，如果是链向外部网站的，通常都会加上转向功能：
> http://www.zhaiduo.com => /link.php?url=http://www.zhaiduo.com
但是在无意间，我注意到某些日志的外部链接并没有被转向，而是直链的。经过自己的测试证实Ucenter确实有这个问题，可以通过某些手段绕过URL转向。
这是我在zaccode的测试页面：[Ucenter外链测试](http://www.zaccode.com/space-3603-do-blog-id-3998.html)。

根据测试结果，在Ucenter里面添加链接的时候，只要使用类似这种格式(注意href前面的title):
&lt;a title="" href="http://www.zhaiduo.com/" target="_blank"&gt; zhaiduo.com &lt;/a&gt;
都可以添加成直链。估计是Ucenter在preg_replace的时候，匹配规则的漏洞所至。

至于有URL转向的链接和直链有什么区别，我就不用废话了。嘿嘿～