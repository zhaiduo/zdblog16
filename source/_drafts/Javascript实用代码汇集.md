---
title: Javascript实用代码汇集
id: 189
categories:
  - javascript
  - 窄多废话
tags:
---

**Window Resize**

[code lang="javascript"]
var i=0;
function resize() {
if (navigator.appName == 'Netscape') i=40;
window.resizeTo(402 +30, 582 + 60-i);
self.focus();
}
[/code]