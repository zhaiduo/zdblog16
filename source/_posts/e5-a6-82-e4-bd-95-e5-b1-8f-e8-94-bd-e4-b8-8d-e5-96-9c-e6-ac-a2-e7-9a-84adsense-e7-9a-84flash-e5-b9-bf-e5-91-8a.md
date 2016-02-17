---
title: 如何屏蔽不喜欢的Adsense的Flash版广告
tags:
  - adsense
  - 广告
id: 710
categories:
  - Google与Idea
date: 2010-08-03 16:54:34
---

比如王通的SEO广告-Flash版每次都看见有点视觉疲劳，但是Flash广告上看不到广告网址，我又不想点击广告进去送钱给他。那我该如何屏蔽这种广告呢？

我记得Google使用doubleclick之前的flash广告是可以看到广告商的网址的。但是新版已经没有了。

分析Flash广告的代码：
> iframe allowtransparency="true" hspace="0" id="google_ads_frame3" marginheight="0" marginwidth="0" name="google_ads_frame" src="http://googleads.g.doubleclick.net......
我们可以看到当前网页的URL，但是却没有广告商的网址。
[![](http://www.zhaiduo.com/wp-content/uploads/2010/08/p20100803164530.jpg "p20100803164530")](http://www.zhaiduo.com/wp-content/uploads/2010/08/p20100803164530.jpg)

我们再仔细看广告的右下角，有一个感叹号，鼠标移过去出现“Google提供的广告”。用fireFox浏览器点击鼠标右键复制目标网址可以看到：
> http://www.google.com/url?ct=abg&amp;q=https://www.google.com/adsense/support/bin/request.py%3Fcontact%3Dabg_afc%26url%3Dhttp://......%3Dwww.boloni.cn%26.....
**www.boloni.cn**这个就是广告商的网址。登录Adsense帐号，在帐号设置里面的广告过滤加入这个网址，就可以屏蔽它的Flash广告啦。