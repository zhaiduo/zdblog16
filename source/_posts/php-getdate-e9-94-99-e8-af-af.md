---
title: 'PHP: getdate()错误'
id: 327
categories:
  - PHP
  - 技术研究
date: 2006-10-31 22:50:13
tags:
---

PHP5中当在ini中指定错误级别为E_STRICT时，可能导致getdate出现如下错误：
> getdate() [[function.getdate](function.getdate)]: It is not safe to rely on the system's timezone settings. Please use the date.timezone setting, the TZ environment variable or the [date_default_timezone_set](http://us2.php.net/manual/en/function.date-default-timezone-set.php)() function. In case you used any of those methods and you are still getting this warning, you most likely misspelled the timezone identifier.
解决办法可以在 getdate() 前面加上：
> date_default_timezone_set('时区名');
时区名如：Asia/Hong_Kong，时区列表可以[参看这里](http://us2.php.net/manual/en/timezones.php)。