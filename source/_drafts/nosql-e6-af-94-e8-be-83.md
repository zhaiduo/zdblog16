---
title: Nosql比较
id: 2109
categories:
  - NoSQL
tags:
---

http://nosql-database.org/
http://www.slideshare.net/thobe/choosing-the-right-nosql-database

//////////////////graph database

Neo4j

//////////////////Document database

MongoDB
https://s3.amazonaws.com/drivers.mongodb.org/php/index.html
http://docs.mongodb.org/ecosystem/drivers/php/

CouchDB
http://guide.couchdb.org/
http://kore-nordmann.de/blog/phpillow_php_couchdb_wrapper.html

//////////////////ColumnFamily database
cassandra
https://cassandra.apache.org/

BigTable-Google

Hbase

///////////////////////////////

When to use Document database
what data is collections of simillar entities
but semi structured rather than tabular
when fields in entries have multiple values

When to use ColumnFamily database
when scalability is the main issue
both scaling size and scaling load
in particulat scaling write load
Linear scalability both in read and write
low level to duplicate data

When to use graph database
deep traversals
for complex and domains
when how entities relate is an important aspect of the domain