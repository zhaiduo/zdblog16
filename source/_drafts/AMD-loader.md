---
title: AMD loader
id: 1804
categories:
  - javascript
tags:
---

//Calling define with module ID, dependency array, and factory function
define('myModule', ['dep1', 'dep2'], function (dep1, dep2) {

    //Define the module value by returning a value.
    return function () {};
});

Why?

* Sync is bad, use Async
* hard to debug
* cross-domain requests
* load them before executing

Link: http://requirejs.org/docs/whyamd.html