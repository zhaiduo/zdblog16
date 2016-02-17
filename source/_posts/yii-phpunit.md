---
title: Yii PHPUnit
tags:
  - phpunit
  - yii
id: 2015
categories:
  - 单元测试
date: 2014-08-11 12:07:44
---

在yii protected/tests/目录下运行:phpunit unit进行单元测试，出现各种错误：
比如pear install phpunit/DbUnit或者PHP_Invoker找不到，这个需要PHP支持pcntl模块，windows下不支持。

如果出现如下错误：
PHPUnit_Extensions_Story_TestCase.php failed to open  yiiframeworkYiiBase.php
可以尝试安装：
pear install phpunit/PHPUnit_Story
注意：phpunit的pear库已经移到phpunit.de，并且在2014年底，安装方式会有变化。

You have installed PHPUnit via PEAR. This installation method is no longer
supported and [http://pear.phpunit.de/](http://pear.phpunit.de/) will be shut down no later than
December, 31 2014.

一般常见找不到问题，可以通过下面来安装，找不到可以pear search试试。

pear install phpunit/PHPUnit
pear install phpunit/PHPUnit_Selenium
pear install phpunit/PHP_Invoker
pear install phpunit/PHPUnit_Story
pear install phpunit/DbUnit

具体测试过程中，Yii include的错误，可以直接注释，或者[disable掉](https://github.com/yiisoft/yii/issues/1907)。

//////////////// yiiframeworktestCTestCase.php
//require_once('PHPUnit/Runner/Version.php');
//require_once('PHPUnit/Util/Filesystem.php'); // workaround for PHPUnit <= 3.6.11

spl_autoload_unregister(array('YiiBase','autoload'));
//require_once('PHPUnit/Autoload.php');
spl_autoload_register(array('YiiBase','autoload')); // put yii's autoloader at the end
////////////////

Failed opening PHPUnit_Extensions_Story_TestCase.php   yiiframeworkYiiBase.php
disable include path:
YiiBase::$enableIncludePath=false;