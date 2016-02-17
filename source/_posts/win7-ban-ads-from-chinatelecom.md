---
title: 如何用Windows7防火墙屏蔽中国电信广告
tags:
  - Window 7
  - 垃圾广告
  - 屏蔽
  - 防火墙
id: 760
categories:
  - 窄多废话
date: 2010-07-23 01:14:39
---

用中国电信的ADSL上网，我们常常能看到网页里莫名其妙的出现中国电信的广告。
这种下三滥插入广告的手段让人鄙视、唾弃，对于只会上网的朋友，要想解除这个烦恼还是挺头痛的。
[![](../wp-content/uploads/2010/07/20100722233009.jpg "20100722233009")](../wp-content/uploads/2010/07/20100722233009.jpg)[![](../wp-content/uploads/2010/07/20100722233120.jpg "20100722233120")](../wp-content/uploads/2010/07/20100722233120.jpg)

下面介绍一下在Windows 7中如何通过防火墙的设置屏蔽中国电信广告。

首先选择控制面板-&gt;系统和安全-&gt;Windows防火墙

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234440.jpg "20100722234440")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234440.jpg)

然后点击高级设置-&gt;入站规则-&gt;新建规则-&gt;自定义

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234531.jpg "20100722234531")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234531.jpg)

然后选择 作用域，本地选择任何IP，远程选择你想要屏蔽的IP，IP可以查看有电信广告的网页源代码获得。例如上面的图片中的源代码：
http://121.32.136.21
var base_url="http://218.16.103.69:1010/";
var stat_path="http://121.32.136.11:81
121.32.136.21，218.16.103.69和121.32.136.11就是我们要屏蔽的IP。或者屏蔽121.32.136.*这个IP段。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234636.jpg "20100722234636")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234636.jpg)

接着选择的操作是阻止连接。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234655.jpg "20100722234655")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234655.jpg)

配置文件全选。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234708.jpg "20100722234708")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234708.jpg)

然后给规则加个名字。

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234750.jpg "20100722234750")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234750.jpg)

一切OK，可以和垃圾广告说拜拜啦~

[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234816.jpg "20100722234816")](http://www.zhaiduo.com/wp-content/uploads/2010/07/20100722234816.jpg)

最后，总结一下屏蔽中国电信垃圾广告的办法：

方法一、通过带有防火墙功能的ADSL Modem设置防火墙IP、域名过滤。
[![](http://www.zhaiduo.com/wp-content/uploads/2010/07/p20100729182833.jpg "p20100729182833")](http://www.zhaiduo.com/wp-content/uploads/2010/07/p20100729182833.jpg)
方法二、使用防火墙软件过滤，如天网防火墙个人版、Norton个人防火墙。

方法三、Windows自带防火墙过滤，如Window 7下通过防火墙屏蔽中国电信广告。