---
title: SGML、XML和HTML的关系
tags:
  - HTML5
id: 956
categories:
  - 互联网
date: 2010-08-09 01:00:20
---

我们知道现在整个互联网的基石都是由HTML这种标记化语言来构成的。当我们通过浏览器查看网页源文件的时候，我们通常可以看到类似于这样的代码：
> &lt;html&gt;
>       &lt;head&gt;
>         &lt;title&gt;Zhaiduo's Document&lt;/title&gt;
>       &lt;/head&gt;
>       &lt;body&gt;
>         &lt;p&gt;My Paragraph&lt;/p&gt;
>       &lt;/body&gt;
>     &lt;/html&gt;
这是一个最简单的HTML标记语言的例子，但是随着互联网的发展，HTML也在随着时代一起变迁，出现了不同的版本和格式。随着HTML5带领我们跨入新的互联网时代，我们很有必要来了解一下HTML的历史和将来，了解一下由HTML变种出来的XHTML，以及HTML和XML、SGML的关系。

按照时间顺序，我们先来看看什么是SGML？SGML是上世纪八十年代为了方便把书面的媒体文档转化到电子媒体文档而推出的一个标准，这个标准规范了标记语言，可以更加清晰地描述电子文档的内容、结构进行标记。SGML使用文件类型定义DTDs来描述文档的逻辑结构，方便分析文档内部的不同内容。但是由于SGML的标记方法太多太复杂，从而使得富媒体的文档解析器设计起来也很复杂，很难解析的完美。所以，接着随着互联网的快速发展，只是用于方便简单地展示文字和图像的HTML语言应运而生，但是由于HTML的语法太过自由，缺乏标准化和结构化的标记语言导致了HTML文档内容难以被程序解析。由于HTML的这个弱点，XML诞生了，规范化了文档的内容和结构。所以可以说XML是SGML的一个简化版本，一个结合HTML特色方便展示文字内容和图像的HTML版本。而HTML本身的文件类型定义DTD是固定的，如果加上XML的DTD定义和规范，这就成为了我们常说的XHTML(XML+HTML4)。HTML也就可以说是拥有固定DTD的一类 SGML语言。而XML则是SGML的一个子集。

早在1997年，HTML4就作为HTML网页的核心特征，然而它也渐渐无法满足我们日益膨胀的富媒体互联网的对网页是在语法、速度、交互性和扩展性上的需要。2004年，HTML5的起草正式提上日程。

说明：以上文字翻译自以下部分参考网址，纯属个人理解，以防误解。若想了解更多，请访问以下网址。

*   [XML and SGML](http://www.students.tut.fi/~leppane7/leppanen.html)
*   [SGML and HTML](http://www.w3.org/TR/html4/intro/sgmltut.html)
*   [HTML5 differences from HTML4](http://www.w3.org/TR/html5-diff/)
*   [X/HTML 5 Versus XHTML 2](http://xhtml.com/en/future/x-html-5-versus-xhtml-2/)
*   [HTML 5 versus XHTML 1.0 Transitional?](http://stackoverflow.com/questions/256953/html-5-versus-xhtml-1-0-transitional)