---
title: 通过Google查询网络用户地理位置
tags:
  - Ajax
  - geolocation
id: 332
categories:
  - Google与Idea
date: 2008-08-28 09:57:34
---

<p class="entry-body">
<p class="item-body">Google的[Ajax API](http://code.google.com/apis/ajax/documentation/#ClientLocation)运用中有一个google.loader.ClientLocation对象,可以方便我们实时高速地查询网络用户的真实地理位置，这给不方便使用数据库的站长带来了极大的方便，同时减少了网站负担，也省去了自己不断更新IP地理位置数据库的麻烦。
> ClientLocation对象返回属性包括
> # ClientLocation.latitude
> # ClientLocation.longitude
> # ClientLocation.address.city
> # ClientLocation.address.country
> # ClientLocation.address.country_code
> # ClientLocation.address.region
> 测试结果如下: ([查看例子](http://www.zhaiduo.com/wp-content/data/mylocation.html))
> 纬度:23.117
> 经度:113.25
> 城市:Guangzhou
> 国家:China
> 国家代码:CN
> 地区:Guangdong