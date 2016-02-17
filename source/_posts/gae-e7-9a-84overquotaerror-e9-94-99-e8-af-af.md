---
title: GAE的OverQuotaError错误
tags:
  - GoogleAppEngine
id: 1607
categories:
  - Python
  - 云时代
date: 2012-06-15 13:06:15
---

在GAE的应用中OverQuota是常见的错误：
OverQuotaError: The API call datastore_v3.RunQuery() required more quota than is available.

我测试的数据有三万多条，仅仅一个db.GqlQuery（6个查询条件）就可以OverQuota：Datastore Small Operations  100% 	0.05 of 0.05 Million Ops,换做db.Key.from_path后，Datastore Small Operations为0%。

给所有数据缓存后，Frontend Instance Hours可以控制在10%左右。

另外发现三万多条数据导出后文件居然有100多M，格式应该是sqllite。