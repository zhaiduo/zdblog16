---
title: Google统计信息对网页优化的建议
tags:
  - 网页优化
  - 网页设计
id: 686
categories:
  - Google与Idea
  - 搜索引擎优化
date: 2010-07-12 23:22:07
---

Google Spider每天都在读取不计其数的网页，互联网上的网页有什么特点，有什么问题，当然是Google最清楚了。这里Google公布了一些对Spider抓取的[网页各项数据的统计结果](http://code.google.com/speed/articles/web-metrics.html)，其中比较有意思的是：

*   平均网页大小是320KB
*   三分之一的网页没有使用压缩技术
*   80%的网页包含10种以上的来自同一个主机的资源，例如：image, css, javascript,video等等。
*   访问人气高的网站，每打开一个网页，平均会消耗8次HTTP请求，前提是网页脚本和样式表都放在同一个主机。
*   网页的内容都是通过Googlebot抓取，有的网站使用robots.txt阻止了Googlebot抓取CSS和Javascript文件。所以建议不要这样做。
*   Google建议网页内增加专门给Googlebot提供的内容，例如Google自己的服务器就是提供给Googlebot未经压缩过的CSS和Javascript文件的内容，方便他们读取，而提供给访客浏览器的则是压缩过的，以提高访问速度。
*   网页内容的兼容性要强，如果这是针对IE或者FIreFox浏览器的内容，或者说是和WebKit(WebKit是一种开源的浏览器内核引擎)不兼容的网页内容，Google只会把它当作看不见。
*   网页取样并不是随机的，而是有侧重点的，例如PageRank高的网页拥有更多的机会获得取样。
结果后面还列举了排名高的网站和所有网站的平均数据间的对比，这有助于我们了解什么样的特性帮助网站获得高的排名。

从SEO，网页优化的角度来看，上面这些结果和建议对于我们设计搜索引擎喜欢的网页来说是很有启发的，对我们设计网页、了解搜索引擎、了解Googlebot很有帮助。可以总结为以下几点：

1.  网页文件大小最好不要超过320KB
2.  尽量压缩让除了二进制格式以外的所有网页元素
3.  不要随便阻止Googlebot对网站的抓取
4.  提高网站的多浏览器兼容性，标准可以向WebKit内核看齐
5.  尽量提高网站的Pagerank，以增加网站内容被抓取的机会