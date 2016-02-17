---
title: 好用的Google图表插件
tags:
  - 图像技术
  - 教程
id: 258
categories:
  - Google与Idea
date: 2008-03-26 14:15:10
---

[Google Chart API](http://code.google.com/apis/chart/)提供一个很好的接口帮助我们快速生成各种统计图表。从常见的条状、线条、馅饼图表到维恩图（用于显示元素间的重迭关系），甚至用地图的方式来显示统计图表，种类繁多，应用灵活，给我们带来了很多方便，而且这个API可以不受限制的调用，我们可以很方便的在博客或其他网页上调用。感觉不足之处是不支持中文和和缺少动态的展示方式。

例如我们看看2008年台湾大选的得票比较图：
![](http://chart.apis.google.com/chart?chf=bg,s,FFA928&amp;chco=0000ff,008000,ffffff&amp;chtt=TaiWan%202008%20%2813,000,000%29&amp;chs=300x120&amp;chd=t:51.7,36.5,11.8&amp;cht=p3&amp;chl=Ma%286,720,000%29%7CXie%284,750,000%29%7COthers)

调用说明：
http://chart.apis.google.com/chart? 调用路径
chs=250x100&amp; 调用变量chs：指定图表尺寸大小
chd=t:51.7,36.5,11.8&amp; 调用变量chd：用逗号分割的数据组，可以用|分隔多组；不确定数据可用-1表示。t: 表示数据类型为数字 s:表示数据类型为单字母，如（chd=s:ATb19,Mn5t）e:表示数据类型为双字母，如（chd=e:AA,AZ,Aa）
cht=p3 调用变量cht：表示地图类型：
> lc:线条 lxy:点线图 ls:火花线 bhs:水平对比条 bvs:垂直对比条
> bhg:水平条 bvg:垂直条 chbh:指定条的宽度 p:饼状图 p3:三维饼状图
> v: 重迭图 s:散点图 r:雷达图
> t:地图 chtm指定地图区域
&amp;chl=Ma|Xie|Others 调用变量chl：用逗号分割的对映数据的文字说明
**更多用法:**
chco: 指定颜色
chm: 区域颜色填充
chtt: 指定图表标题

![](http://chart.apis.google.com/chart?chs=380x200&amp;cht=t&amp;chtm=asia&amp;chld=JPINCNTWKR&amp;chd=s:p0AfT&amp;chf=bg,s,EAF7FE)