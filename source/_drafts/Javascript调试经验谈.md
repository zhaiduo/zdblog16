---
title: Javascript调试经验谈
tags:
  - 调试
id: 379
categories:
  - javascript
---

无论是下面哪个错误：
javascript Object expected Line: 1 Char:1
javascript Invalid property value. code:0
请先检查程序运行的逻辑性有否缺漏，确定是否是程序设计缺陷造成。

Discuz关于$()函数的冲突，jQuery中给出了解决方法，jQuery.noConflict()
用法：
var jq = jQuery.noConflict();
jq(document).ready(function() {
jq('.hvtb').hover(function() {
jq(this).addClass('pretty-hover');
}, function() {
jq(this).removeClass('pretty-hover');
});
});

IE中出现错误: Invalid argument. Code: 0
可以试试
try
{
//whatever
} catch (ex) {
ShowError(ex.description);
}

数组和对象无法通过等号赋值来克隆，可以用下面的技巧：
var oldArray = ["mip", "map", "mop"];
var newArray = oldArray.slice();

function cloneObject(source) {
for (i in source) {
if (typeof source[i] == 'source') {
this[i] = new cloneObject(source[i]);
}
else{
this[i] = source[i];
}
}
}
var obj1= {bla:'blabla',foo:'foofoo',etc:'etc'};
var obj2= new cloneObject(obj2);

href="javascript:void(0);" onclick="javascript:go();"可能在IE7/8下失效。推荐用getElementById来listen事件。

**Error: "Invalid character Line: 1"**
Usually, when I get messages like that, it is becuase I have odd ASCII
charaters in the page (which you cannot see) usually from cut & paste and
usually at the end of the line.