---
title: PostgreSql常见问题
id: 2223
comment: false
categories:
  - Uncategorized
tags:
---

PHP远程连接出错：

pg_connect(): Unable to connect to PostgreSQL server: could not connect to server: Connection refused (0x0000274D/10061)
Is the server running on host &amp;quot;localhost&amp;quot; and accepting
TCP/IP connections on port 5432?

PHP远程连接超时出错：

Connection failed: SQLSTATE[08006] [7] server closed the connection unexpectedly This probably means the server terminated abnormally before or while processing the request.

建议修改postgresql.conf, set  log_statement='all'，查看日志。

tail pgsql.log
tail pgsql/data/pg_log/postgresql-Fri.log

默认postgresql是本地连接,要把listener和port设好.然后换要修改pg_hba.conf,设置认证方式,这样才可以通过tcp/ip远程连接数据库.

关闭selinux
setenforce 0
关闭iptables -F

try {
            $db = new PDO('pgsql:dbname=test;port=5432;host=127.0.0.1;', 'zhaiduo','www');
            $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
            debug($db);
        } catch (PDOException $e) {
            echo 'Connection failed: ' . $e->getMessage();
        }

///////////////////

Connection failed: SQLSTATE[08006] [7] could not receive data from server: Software caused connection abort (0x00002745/10053)

&nbsp;

监听所有地址：
修改/Data/apps/pgsql/data/postgresql.conf，listen on '*'。
/Data/apps/pgsql/data/pg_hba.conf   all 0.0.0.0/0

修改用户密码：ALTER USER techonthenet WITH PASSWORD 'newpasswd';

#su -c '/usr/pgsql-9.4/bin/pg_ctl -D /Data/apps/pgsql/data -l logfile start|stop|restart' postgres
#su -c '/usr/pgsql-9.4/bin/createdb test' postgres
#su -c '/usr/pgsql-9.4/bin/createuser adam -P' postgres

#su -c '/usr/pgsql-9.4/bin/psql -U dbuser -d exampledb -h 127.0.0.1 -p 5432' postgres

su postgres -c "/usr/pgsql-9.4/bin/pg_ctl stop -m fast" //强行关机

&nbsp;

#除了前面已经用到的\password命令（设置密码）和\q命令（退出）以外，控制台还提供一系列其他命令。
#\h：查看SQL命令的解释，比如\h select。
#\?：查看psql命令列表。\l：列出所有数据库。
#\c [database_name]：连接其他数据库。
#\d：列出当前数据库的所有表格。
#\d [table_name]：列出某一张表格的结构。
#\du：列出所有用户。
#\e：打开文本编辑器。
#\conninfo：列出当前数据库和连接的信息。

#基本的数据库操作，就是使用一般的SQL语言。
## 创建新表
#CREATE TABLE usertbl(name VARCHAR(20), signupdate DATE);
## 插入数据
#INSERT INTO usertbl(name, signupdate) VALUES('张三', '2013-12-22');
## 选择记录
#SELECT * FROM user_tbl;
## 更新数据
#UPDATE user_tbl set name = '李四' WHERE name = '张三';
## 删除记录
#DELETE FROM user_tbl WHERE name = '李四' ;
## 添加栏位
#ALTER TABLE user_tbl ADD email VARCHAR(40);
## 更新结构
#ALTER TABLE usertbl ALTER COLUMN signupdate SET NOT NULL;
## 更名栏位
#ALTER TABLE usertbl RENAME COLUMN signupdate TO signup;
## 删除栏位
#ALTER TABLE user_tbl DROP COLUMN email;
## 表格更名
#ALTER TABLE usertbl RENAME TO backuptbl;
## 删除表格
#DROP TABLE IF EXISTS backup_tbl;

&nbsp;

&nbsp;