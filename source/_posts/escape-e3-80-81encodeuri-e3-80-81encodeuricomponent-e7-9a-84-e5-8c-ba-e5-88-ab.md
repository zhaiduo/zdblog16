---
title: escape、encodeURI、encodeURIComponent的区别
id: 759
categories:
  - javascript
date: 2010-08-17 11:22:59
tags:
---

escape、encodeURI、encodeURIComponent的区别主要在于编码的字符不同：
> 原始字符串：09az~!@#$%^&amp;*()_+}{":|&lt;&gt;?`-=[];',./ 好的
> escape字符串：09az%7E%21@%23%24%25%5E%26*%28%29_+%7D%7B%22%3A%7C%3C%3E%3F%60-%3D%5B%5D%3B%27%2C./%20%u597D%u7684
> encodeURI字符串：09az~!@#$%25%5E&amp;*()_+%7D%7B%22:%7C%3C%3E?%60-=%5B%5D;',./%20%E5%A5%BD%E7%9A%84
> encodeURIComponent字符串：09az~!%40%23%24%25%5E%26*()_%2B%7D%7B%22%3A%7C%3C%3E%3F%60-%3D%5B%5D%3B'%2C.%2F%20%E5%A5%BD%E7%9A%84
escape() 不会转码 **0到9a到z@*/_+.-** 其他会被转码成%20的形式，中文则是%u597D的形式，属于ISO Latin字符集编码。

escape() 更加适合于QueryString中等号后面的英文数据的转码,例如：action=eacape('wo&amp;ta')&amp;list=1;

encodeURI() 不会转码 **~!@#$&amp;*()_+:?-=;',./** 其他会被转码成%20的形式，属于UTF-8编码。

escape() 更加适合于GBK到UTF8页面的转码，同样页面编码的用escape就可以

encodeURIComponent() 不会转码  **~!*()_-'. **把采用UTF-8编码格式的字符串用escape的Latin字符编码。

encodeURIComponent()适合于URL不会被#字符截断，URL被当作URI字段的编码，因为/可以被转码。

URL里常用的字符：?=&amp;#    所以encodeURI适合保持URL合法性，但是要转码URL的情况。空白在escape()被转成+，其它都是%20。