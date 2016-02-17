---
title: Linux Tips
tags:
  - Mysql
id: 551
categories:
  - Linux/Unix
---

Red Hat Enterprise Linux AS release 4

**lost mysql password?**
# service mysqld stop
# /usr/bin/mysqld_safe --skip-grant-tables &
# mysql -u root mysql
 mysql> UPDATE user SET Password=PASSWORD('new_password') WHERE user='root';
 mysql> FLUSH PRIVILEGES;
 mysql> exit;
# service mysqld stop
# service mysqld start