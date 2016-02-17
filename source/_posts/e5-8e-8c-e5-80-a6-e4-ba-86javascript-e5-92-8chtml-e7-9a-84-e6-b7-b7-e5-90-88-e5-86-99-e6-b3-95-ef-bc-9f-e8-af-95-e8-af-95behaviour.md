---
title: 厌倦了Javascript和HTML的混合写法？试试Behaviour
tags:
  - Ajax
id: 218
categories:
  - Uncategorized
date: 2007-11-22 18:37:15
---

[![behaviour.gif](http://www.zhaiduo.com/wp-content/data/behaviour.gif)](http://bennolan.com/behaviour/)
我们都知道PHP程序最好做到前后台的分离，尽量避免PHP加插到HTML中的做法。其实同样的,我们也可以做到Javascript与HTML的分离。 [Behaviour](http://bennolan.com/behaviour/)就是这样一个基于Ajax的js功能原型。现在我们来看看对比：

比如我们想给一个连接添加JS功能。常规的写法如下：
> [code lang="html"]**[My action](/view/120#)**
> 
> [/code]
有了Behaviour，我们可以这样写：
> [code lang="html"] <script type="text/javascript">
> var myrules = {
> '#myaction' : function(element){
> element.onclick = function(){
> ....
> }
> }
> };
> Behaviour.register(myrules);
> </script>
> **[My action](/view/120#)** [/code]
HTML干净了很多吧！非常感谢[Ben Nolan](http://bennolan.com/)!