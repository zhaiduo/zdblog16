---
title: css
id: 71
categories:
  - 窄多废话
tags:
---

input[type=text] {
width: 300px;
background-color: cyan;
}

<title>CSS Style Change Script</title>   <script type="text/javascript">  var mycss=getCookie("mycss"); if(mycss != "" &amp;&amp; mycss != undefined ){ 	document.write('
<link rel="stylesheet" xhref="css-test/css'+mycss+'.css" mce_href="css-test/css'+mycss+'.css" type="text/css" id="cssstyle">'); }else{ 	document.write('
<link rel="stylesheet" xhref="css-test/css1.css" mce_href="css-test/css1.css" type="text/css" id="cssstyle">'); }  function chg(t){ 	document.getElementById('cssstyle').href = 'css-test/css'+t+'.css'; 	 	var today = new Date();     var expires = new Date();     expires.setTime(today.getTime() + 1000*3600*24*365);   	setCookie('mycss',t,expires); 	 } function setCookie(name, value, expire) { 	document.cookie = name + "=" + escape(value)+ ((expire == null) ? "" : ("; expires=" + expire.toGMTString())); }  function getCookie(Name) { 	var search = Name + "="; 	if (document.cookie.length > 0) { 	        offset = document.cookie.indexOf(search); 	        if (offset != -1) { 	                offset += search.length; 	                end = document.cookie.indexOf(";", offset); 	                if (end == -1) 	        	        end = document.cookie.length; 	                return unescape(document.cookie.substring(offset, end)); 	        } 	} } </script>  [css1](javascript:void(0);) | [css2](javascript:void(0);)
<div id="box">BOx, Yes, I'm here.</div>