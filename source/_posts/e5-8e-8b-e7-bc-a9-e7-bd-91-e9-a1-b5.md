---
title: 压缩网页
tags:
  - 网页压缩
id: 672
categories:
  - 网站技术
date: 2010-07-15 13:05:09
---

前面[Google统计信息对 网页优化的建议](/2010/07/google%e7%bb%9f%e8%ae%a1%e4%bf%a1%e6%81%af%e5%af%b9%e7%bd%91%e9%a1%b5%e4%bc%98%e5%8c%96%e7%9a%84%e5%bb%ba%e8%ae%ae/ "Permanent link to Google统计信息对网页优化的建议")提到网页压缩技术，有朋友[mimicangel](http://zuoge.520zone.com/)不是很明白，下面我就对网页压缩技术进行一下详细的介绍。

网页压缩指的是网页以及网页包含的所有文本文件及二进制文件的压缩，文本文件主要包括网页本身、CSS、Javascript、XML等文件，而二进制文件主要包括图片文件、图标文件、Flash等视频文件。根据压缩方法不同，我们可以把网页压缩分为三类：

1.  图片等二进制文件的压缩
图片的压缩一般可以通过Photoshop等图片处理工具进行压缩，视频的压缩可以可以根据不同的视频格式搜索视频压缩工具，例如大部分视频网站使用的FLV格式可以用Adobe Flash Media Encoder 来进行压缩生成，这些都是属于软件的使用问题，就不再详述。
2.  HTML、XML、CSS、JS文件的[Gzip压缩](http://www.gnu.org/software/gzip/manual/gzip.html)
我们浏览器看到的网页等其它文本文件都是通过服务器生成的，有些服务器是直接保存的服务器上面的，服务器只需要读给我们，我们就可以称之为静态页面；相反文件在服务器上不存在，而是经过程序生成的网页，我们称之为动态网页。不管是静态还是动态，这些文本的网页文件都可以用Gzip这种技术来压缩，如果我们的浏览器同时支持Gzip压缩的格式，那么我的访问网页的速度将得到较大提升。可以放心的是目前的主流浏览器均支持这种压缩技术，为了更加保险，我们可以用程序检测浏览器是否支持Gzip压缩，然后根据结果判断是否压缩网页、CSS以及JS等文件。
3.  CSS和Javascript等语法的压缩
熟悉CSS和Javascript的朋友应该知道，在语法上，我们是有很大余地去简化语法和删除多余的空格和换行符的。例如：
font-size:12px; line-height:17px; font-family: Arial, Helvetica, sans-serif;
我们可以简化为：
font:12px/17px Arial, Helvetica, sans-serif;
这样我们可以通过精简文字达到压缩文本文件的目的。所以说Web2.0推崇的DIV+CSS的网页设计模式也可以理解为一种压缩网页的方法。
方法说完了，下面我推荐一些CSS和Javascript文件压缩工具给不熟悉HTML和程序的朋友，需要说明的是：压缩工具主要适用于CSS和Javascript文件，HTML网页的简化和压缩还是需要专业人士的参与。

**CSS**

*   [http://compressor.ebiene.de/](http://compressor.ebiene.de/) CSS和Js都可以压缩
*   [CSS Drive  CSS Compressor](http://www.cssdrive.com/index.php/main/csscompressor/)
*   [http://www.cssoptimiser.com/](http://www.cssoptimiser.com/)
*   [http://flumpcakes.co.uk/css/optimiser/](http://flumpcakes.co.uk/css/optimiser/)
*   [CSS Formatter and Optimiser](http://www.cleancss.com/)
**Javscript**

*   [http://compressorrater.thruhere.net/](http://compressorrater.thruhere.net/)
*   [http://dean.edwards.name/packer/](http://dean.edwards.name/packer/)
*   [http://jscompress.com/](http://jscompress.com/)
*   [http://javascriptcompressor.com/](http://javascriptcompressor.com/)