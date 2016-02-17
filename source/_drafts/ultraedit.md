---
title: UltraEdit模式匹配功能教程
id: 1239
categories:
  - PHP
tags:
---

举例说明如何利用UE的匹配功能将PHP程序快速升级到5.3的要求。

首先下面的直接替换掉：
session_resgister =&gt; 去掉
split=&gt; explode
ereg_replace =&gt;preg_replace

正则替换PHP简化模式，

替换：&lt;?=$zhaiduo?&gt;  =&gt; &lt;?php echo $zhaiduo; ?&gt;
&lt;?=^([0-9a-zA-Z_]+^)?&gt;
=》
&lt;?php echo ^1; ?&gt;

更复杂： &lt;?=$sda['dsa']?&gt;  =&gt; &lt;?php echo $sda['dsa']; ?&gt;
&lt;?=^([~ ?&gt;&lt;]+^)?&gt;
=》
&lt;?php echo ^1; ?&gt;

补充： &lt;? =&gt; &lt;?php
=&gt;
&lt;?^p =&gt; &lt;?php^p

下面附上语法参考，以供查询。参考语法我主要是用的是**语法一**，注意不要和语法二混淆。

**语法一：UE的正则表达式**

符号  功能
%     匹配行的开始 - 显示搜索字符串必须在行的开始，但是在所选择的结果字符串中不包括任何行终止字符。
$     匹配行尾 - 显示搜索字符串必须在行尾，但是在所选择的结果字符串中不包括任何行终止字符。
?     除了换行符以外匹配任何单个的字符
*     除了换行符匹配任何数量的字符和数字
+     前一字符匹配一个或多个，但至少要出现一个
++    前一字符匹配零个或多个，但至少要出现一个
^b    匹配一个分页
^p    匹配一个换行符(CR/LF)(段)(DOS文件)
^r    匹配一个换行符(CR 仅仅)(段)(MAC 文件)
^n    匹配一个换行符 ( LF 仅仅 )( 段 )( UNIX 文件 )
^t    匹配一个标签字符TAB
[]    匹配任何单个的字符，或在方括号中的范围
^{A^}^{ B^} 匹配表达式A或 B
^     重载其后的正规表达式字符
^(^)  括或标注为用于替换命令的表达式。

一个正则表达式最多可以有9个标注表达式, 按正规表达式的需要而定。
相应的替换表达式是 ^x , 替换范围x是1-9。例如：
If ^(h*o^) ^(f*s^) matches “hello folks”,
^2 ^1 would replace it with “folks hello”.

（hello folks 将被替换成 folks hello。）

注： ^ 是实际字符 ^不是Ctl + 键值。

例如：
m?n 匹配 “man”,”men”,”min” 但不匹配 “moon”.
t*t 匹配 “test”,”tonight” 和 “tea time” (the “tea t” portion) 但不匹配 “tea
time” (newline between “tea ” and “time”).
Te+st 匹配 “test”,”teest”,” teeeest “等等。但是不匹配 “tst”。
[aeiou] 匹配每个小写元音。
[,.?] 匹配一文字的 “,”，”.”或 “?”。
[0-9, a-z] 匹配任何数位，或小写字母。
[~0-9] 除了数字以外匹配任何字符 (~ 意味着”不”)

你按如下方式可以查找一个表达式A或 B ：

“^{John^}^{Tom^}”

这将在找John或Tom的出现。应该在 2 个表达式之间没有任何东西。

你可以在同一搜索中按如下方式组合A or B and C or D：

“^{John^}^{Tom^}^{Smith^}^{Jones^}”

这将在John or Tom 后面找 Smith or Jones。

**语法二：”Unix”句法类型的正则表达式**

符号        功能
          标记下一个字符作为一个特殊的字符。
"n"         匹配字符"n"。"n" 一个换行符或换行符字符。
^           匹配/定位行的开始。
$           匹配/定位行的尾。
*           匹配前面的字符零次或多次。例
+           匹配前面的字符一次或多次。例
.           匹配除了一个换行符字符匹配任何单个的字符。
(expression)标注用于替换命令的表达式。一个正则表达式根据需要，最多可以有9个标注表达式。相应的代替表达式是 x , x的范围是 1-9 。
例如：
If (h.*o) (f.*s) matches "hello folks",
2 1 would replace it with "folks hello".
（hello folks 将被替换成 folks hello。）

[xyz]       一个字符集。匹配在方括号之间的任何字符。
[^xyz]      一个否定的字符集。不匹配在方括号之间的任何字符。
d          匹配一个数字字符。等价于[0-9]。
D          匹配一个非数字字符。等价于[^0-9]。
f          匹配一个换页字符。
n          匹配一个换行字符。
r          匹配一个回车符字符。
s          匹配任何空白的空格, 标签, 换页, 包括空格等等，但不匹配换行符。
S          匹配任何非空白的字符，但不匹配换行符。
t          匹配一个标签TAB字符。
v          匹配一个垂直的标签字符。
w          匹配任何词语字符包括下划线。
W          匹配任何非词语字符字符。
注： ^ 是实际字符 ^不是Ctl + 键值。

例如：
m.n 匹配 “man”,”men”,”min” 但不匹配 “moon”.
t+t 匹配 “test”,”tonight” 和 “tea time” (the “tea t” portion) 但不匹配 “tea
time” (newline between “tea ” and “time”).
Te*st 匹配 “test”,”teest”,” teeeest “等等。但是不匹配 “tst”。
[aeiou] 匹配每个小写元音。
[,.?] 匹配一文字的 “,”，”.”或 “?”。
[0-9,a-z] 匹配任何数位，或小写字母。
[^0-9] 除了数字以外匹配任何字符 (~ 意味着”不”)

你按如下方式可以查找一个表达式A或 B ：

“(John)|(Tom)”

这将在找John或Tom的出现。应该在 2 个表达式之间没有任何东西。

你可以在同一搜索中按如下方式组合A or B and C or D：

“(John|Tom) (Smith|Jones)”

这将在John or Tom 后面找 Smith or Jones。

另外：

p 匹配 CR/LF ( 作为 rn 的一样 ) 作为DOS行结束符匹配

如果查找/替换功能中正则表达式没有选用，则替换字段中下列字符也是有效的：

符号 功能

^^ 匹配一个 “^” 字符
^s 替换为被选择 ( 加亮 ) 活跃的文件窗口的文章。
^c 替换为剪贴板的内容
^b 匹配一个页裂缝
^p 匹配一个换行符 ( CR/LF )( 段 )( DOS 文件)
^r 匹配一个换行符 ( CR 仅仅 )( 段 )( MAC 文件)
^n 匹配一个换行符 ( LF 仅仅 )( 段 )( UNIX 文件)
^t regexpp(匹配一个标签TAB字符