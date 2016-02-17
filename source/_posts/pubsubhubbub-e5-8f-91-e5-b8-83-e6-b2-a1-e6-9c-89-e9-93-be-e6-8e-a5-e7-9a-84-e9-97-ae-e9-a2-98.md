---
title: pubsubhubbub发布没有链接的问题
tags:
  - Atom
  - RSS
  - Wordpress
  - pubsubhubbub
  - 博客同步
id: 946
categories:
  - 互联网
  - 网站技术
date: 2010-08-11 23:17:02
---

[pubsubhubbub](http://code.google.com/p/pubsubhubbub/)是一个开源免费的服务器端Atom和RSS订阅系统。我们一般理解的RSS是读者去主动订阅博客的RSS内容，而pubsubhubbub却是让服务器成为读者去订阅RSS内容。只要注册了一个运行的pubsubhubbub服务，当博客更新的时候，博客就会发个消息给pubsubhubbub服务器（publish），然后pubsubhubbub服务器便会主动的来抓取博客的更新内容（subscribe）。Atom和RSS里面的一个主题被称称作Hub，所以pubsubhubbub=publish+subscribe+hub。

通过pubsubhubbub协议，我可以让自己的博客内容发布到[新浪微博](http://t.sina.com.cn/zhaiduo)上。只要发布(publish）窄多博客的Atom内容到[月光博客](http://www.williamlong.info)的[BuzzSync](http://buzzsync.appspot.com/)(比较懒，直接用别人写好的程序)，每当我有新的博客发布的时候，BuzzSync会自动转发我的博客内容到新浪微博。

可是有个问题，就是发布到微博的内容只要标题，没有链接，我试着改了改Wordpress的WP-include/feed-atom.php，看看现在问题是否解决。

在title里面修改如下内容：

&lt;title type="&lt;?php html_type_rss(); ?&gt;"&gt;&lt;![CDATA[&lt;?php the_title_rss() ?&gt; &lt;?php the_permalink_rss() ?&gt; ]]&gt;&lt;/title&gt;

更新：测试失败，继续测试...