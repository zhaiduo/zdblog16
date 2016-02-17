---
title: RewriteRule里正则表达式减号字符的顺序问题
tags:
  - Trouble
  - 正则表达式
id: 489
categories:
  - 杂项
date: 2010-01-20 18:17:40
---

在用URLRewrite的时候，PHP正则匹配(preg_match)的时候，常常有一个容易忽略的小问题：
> <span style="color: #008000;">有效：</span>RewriteRule ([0-9a-zA-Z+_.-]{3,})/$  /article-$1.html [L]
> <span style="color: #ff0000;">无效：</span>RewriteRule ([0-9a-zA-Z-+_.]{3,})/$  /article-$1.html [L]
仅仅是因为方括号内减号（-）字符顺序的不同，让正则匹配失效。
但这又不是普遍的问题，只是在个别虚拟主机上出现。

下面的解释可以帮我们释疑：
> 正则表达式通过使用元字符来编码在模式中，元字符不代表其自身，它们用一些特殊的方式来解析。
> 减号（-）字符可以在字符类中指定一个字符范围。例如，[d-m] 匹配了 d 和 m 之间的任何字符，包括两者。<span style="color: #afd42a;">如果字符类中需要减号本身，则必须用反斜线转义或者放到一个不能被解释为指定范围的位置，典型的位置是字符类中的第一个或最后一个字符。</span>