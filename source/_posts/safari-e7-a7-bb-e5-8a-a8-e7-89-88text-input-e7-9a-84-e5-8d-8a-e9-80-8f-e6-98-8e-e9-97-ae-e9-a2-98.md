---
title: Safari移动版Text Input的半透明问题
tags:
  - iPhone
  - iPod
  - 前端技术
id: 1656
categories:
  - MAC
  - 浏览器
date: 2012-07-15 23:42:10
---

[![](http://www.zhaiduo.com/wp-content/uploads/2012/07/safari_disabled_problem.jpg "safari_disabled_problem")](http://www.zhaiduo.com/2012/07/safari%e7%a7%bb%e5%8a%a8%e7%89%88text-input%e7%9a%84%e5%8d%8a%e9%80%8f%e6%98%8e%e9%97%ae%e9%a2%98/safari_disabled_problem/)
在测试给搜索加上下拉菜单的时候，发现移动版的Safari浏览器(iPad和iPod)对disabled的Text input显示为半透明，而Mac版和Win版的Safari均无问题，而且其它浏览器也显示正常。经测试，取消掉disabled="disabled"，Text input恢复正常。