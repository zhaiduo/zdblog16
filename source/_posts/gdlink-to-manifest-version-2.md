---
title: '终于把Chrome Extension: GDLink升级到manifest_version 2'
tags:
  - Chrome
  - Extension
id: 1826
categories:
  - 浏览器
date: 2013-09-06 07:21:10
---

前段时间发现Chrome Extension: GDLink无法使用，但是一直没空查找原因。原来是Chrome Extension要求把manifest_version升级到2。相应的chrome.tabs.create也做了些变化，onclick 事件被要求chrome.contextMenus.onClicked.addListener来调用，所以旧的chrome.tabs.create里是调用onclick事件已经无效。