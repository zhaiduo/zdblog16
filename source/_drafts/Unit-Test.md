---
title: Unit Test
id: 1898
categories:
  - 杂项
tags:
---

TDD

TDD要求在每个方法定义编写前，去考虑方法的各种可能情况，并且直到测试通过，才开始编写下一个方法。它是你在编写最小单元功能的时候，确保每一个功能单元是更加健壮的，因此称作单元测试。

http://phpunit.de/getting-started.html
http://docs.seleniumhq.org/download/
http://yiiframework.ru/doc/guide/en/test.overview
http://www.yiiframework.com/doc/guide/1.1/en/test.unit

http://pear.php.net/package/PHPUnit2/download
http://lodar.net/install-pear-phpunit-and-phpdoc2-for-php-5-4-on-windows/

install pear

http://pear.php.net/
php go-pear.phar

假定PHP安装在C:php):

PHP_PEAR_BIN_DIR=C:php
PHP_PEAR_DATA_DIR=C:phpdata
PHP_PEAR_DOC_DIR=C:phpdocs
PHP_PEAR_INSTALL_DIR=C:phppear
PHP_PEAR_PHP_BIN=C:phpphp.exe
PHP_PEAR_SYSCONF_DIR=C:php
PHP_PEAR_TEST_DIR=C:phptests

http://www.phpunit.de/
#pear config-set auto_discover 1
#pear install pear.phpunit.de/PHPUnit

Registering the channel:
pear channel-discover pear.phpunit.de

Listing available packages:
pear remote-list -c phpunit

Installing a package:
pear install phpunit/package_name

Installing a specific version/stability:
pear install phpunit/package_name-1.0.0

pear install phpunit/package_name-beta
Receiving updates via a feed:

http://pear.phpunit.de/feed.xml

Error: No releases available for package "pear.phpunit.de/PHPUnit"
#pear update-channels
pear clear-cache

use pear.symfony-project.com
sudo pear channel-discover pear.phpunit.de
sudo pear channel-discover pear.symfony-project.com
sudo pear install --alldeps phpunit/PHPUnit

pear install phpunit

cd e:Adam_workunit_test
phpunit --bootstrap src/autoload.php teststest.php

http://phpunit.de/manual/3.7/zh_cn/phpunit-book.html#writing-tests-for-phpunit
http://phpunit.de/manual/3.7/zh_cn/automating-tests.html

Error:
require_once(PHPUnit/Extensions/SeleniumTestCase.php): failed to open
Try:
pear install --force phpunit/PHPUnit_Selenium
或者直接去github下载PHPUnit/Extensions/SeleniumTestCase.php