---
title: AS3
tags:
  - AS3
id: 286
categories:
  - Flash
---

Shapeshifter - The Online Animation Tool
http://www.aniboom.com/ShapeshifterMain/

Google Maps API for Flash
http://code.google.com/apis/maps/documentation/flash/basics.html

var validUrlRE = new RegExp("^(http|https|ftp|file)://.+");
var titleRE = new RegExp("");
var allAlphaNumericRE = new RegExp("^\w+$");

//#include "util/regular_expressions.as"
if (validUrlRE.test(this.urlInput.getValue()))
{
// urlInput contains a mostly valid URL.
}

if (allAlphaNumericRE.test(this.nameInput.getValue()))
{
// this.nameInput contains alpha numeric characters
}

var title = titleRE.match(htmlSource);
trace(title[1]); // This contains the HTML file's title.

essential actionscript 3.0 examples
http://moock.org/eas3/examples/