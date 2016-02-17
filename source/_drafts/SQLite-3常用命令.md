---
title: SQLite 3常用命令
tags:
  - SQLite
id: 1751
categories:
  - 技术研究
---

# SQLite 3 http://www.sqlite.org/pragma.html#schema and http://docs.python.org/2/library/sqlite3.html

SQLite natively supports the following types: NULL, INTEGER, REAL, TEXT, BLOB.

import sqlite3

persons = [
    ("Hugo", "Boss"),
    ("Calvin", "Klein")
    ]

con = sqlite3.connect(":memory:")

# 建表
con.execute("create table person(firstname, lastname)")

# 一次插入多行
con.executemany("insert into person(firstname, lastname) values (?, ?)", persons)

#多语句执行
cur.executescript(""" ....; ....; """)

# 按行读取
for row in con.execute("select firstname, lastname from person"):
    print row

call the cursor’s fetchone() method to retrieve a single matching row,
or call fetchall() to get a list of the matching rows.

# 删除
print "I just deleted", con.execute("delete from person").rowcount, "rows"

# Save (commit) the changes 提交
conn.commit()

con.execute("create table person (id integer primary key, firstname varchar unique)")

# Successful, con.commit() is called automatically afterwards
with con:
    con.execute("insert into person(firstname) values (?)", ("Joe",))

# con.rollback() is called after the with block finishes with an exception, the
# exception is still raised and must be caught
try:
    with con:
        con.execute("insert into person(firstname) values (?)", ("Joe",))
except sqlite3.IntegrityError:
    print "couldn't add Joe twice"

安全性：

# Never do this -- insecure!
symbol = 'RHAT'
c.execute("SELECT * FROM stocks WHERE symbol = '%s'" % symbol)

# Do this instead
t = ('RHAT',)
c.execute('SELECT * FROM stocks WHERE symbol=?', t)
print c.fetchone()

技巧：

# dict arr
def dict_factory(cursor, row):
    d = {}
    for idx, col in enumerate(cursor.description):
        d[col[0]] = row[idx]
    return d
con.row_factory = dict_factory

# Convert file existing_db.db to SQL dump file dump.sql
import sqlite3, os

con = sqlite3.connect('existing_db.db')
with open('dump.sql', 'w') as f:
    for line in con.iterdump():
        f.write('%sn' % line)

class Point(object):
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __repr__(self):
        return "(%f;%f)" % (self.x, self.y)

def adapt_point(point):
    return "%f;%f" % (point.x, point.y)

def convert_point(s):
    x, y = map(float, s.split(";"))
    return Point(x, y)

# Register the adapter
sqlite3.register_adapter(Point, adapt_point)

# Register the converter
sqlite3.register_converter("point", convert_point)

##########################################
语法：
 Table names that begin with "sqlite_" are reserved for internal use.