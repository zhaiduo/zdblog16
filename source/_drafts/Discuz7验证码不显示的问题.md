---
title: Discuz7验证码不显示的问题
id: 595
categories:
  - 杂项
tags:
---

config.inc.php的EFBBBF问题。

另外发现seccode.php里面有些问题：

Error msg: date_default_timezone_set() [function.date-default-timezone-set]: Timezone ID 'Etc/GMT-8.025' is invalid
Line mum: 199
Date time: 2010-05-15 10:34:57 (CST)
Error num: 8
Error type: Notice
Script name: common.inc.php

include/common.inc.php
date_default_timezone_set('Asia/Hong_Kong');
//@date_default_timezone_set('Etc/GMT'.($timeoffset > 0 ? '-' : '+').(abs($timeoffset)));