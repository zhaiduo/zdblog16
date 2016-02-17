---
title: MySQL优化技巧
id: 328
categories:
  - Mysql
  - 技术研究
date: 2006-11-02 20:57:17
tags:
---

1、key_reads / key_read_requests应该尽可能的低，至少是1:100，1:1000更好（上述状态值可以使用SHOW STATUS LIKE ‘key_read%’获得）

2、使用查询缓冲最多可以达到238%的效率。Qcache_lowmem_prunes的值非常大，则表明经常出现缓冲不够的情况,同时Qcache_hits的值非常大，则表明查询缓冲使用 非常频繁，此时需要增加缓冲大小Qcache_hits的值不大，则表明你的查询重复率很低，这种情况下使用查询缓冲反而会影响效率，那么可以考虑不用查 询缓冲。此外，在SELECT语句中加入SQL_NO_CACHE可以明确表示不使用查询缓冲。Qcache_free_blocks，如果该值非常大，则表明缓冲区中碎片很多query_cache_type指定是否使用查询缓冲。如：1G内存设置:
> query_cache_size = 32M
> 
> query_cache_type= 1  (缓存所有的结果，除了 SELECT SQL_NO_CACHE 查询)
3、table_cache指定表高速缓存的大小。每当MySQL访问一个表时，如果在表缓冲区中还有空间，该表就被打开并放入其中，这样可以更快地访问表内容。通过检查峰值时间的状态值Open_tables和Opened_tables，可以决定是否需要增加table_cache的值。如果你发现 open_tables等于table_cache，并且opened_tables在不断增长，那么你就需要增加table_cache的值了（上述状态值可以使用SHOW STATUS LIKE ‘Open%tables’获得）。注意，不能盲目地把table_cache设置成很大的值。如果设置得太高，可能会造成文件描述符不足，从而造成性能不稳定或者连接失败。对于有1G内存的机器，推荐值是128－256。