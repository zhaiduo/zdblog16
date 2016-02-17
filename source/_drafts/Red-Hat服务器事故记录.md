---
title: Red Hat服务器事故记录
id: 1150
categories:
  - Linux/Unix
  - 网站维护
tags:
---

系统：Linux version 2.6.18-53.1.14.el5  (gcc version 4.1.2 20070626 (Red Hat 4.1.2-14)) 四核CPU + 2G内存

最初症状：mysql 太多链接，php无法连接数据库。
接着：调高mysql配置，max connection=500, 其它配置调高。Apache当掉2次。
[![](http://www.zhaiduo.com/wp-content/uploads/2010/11/20101109134856.jpg "20101109134856")](http://www.zhaiduo.com/wp-content/uploads/2010/11/20101109134856.jpg)
再接着：继续调高mysql配置，几个buffer_size到8M，调高key_buffer和table_cache，mysql当掉。
然后：恢复中等mysql配置，还原key_buffer和table_cache到256M，调高thread concurrency=8，
sysctl -p:
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 1
早上，mysql再次当掉，论坛先耗尽内存。把connection限制到300。
晚上，mysql再次当掉，Handler_read_rnd_next超过3G，几个buffer_size到2M，还原thread concurrency=4。
把cache时间调到八个小时，给get_event加上缓存。给user表的uid,vid增加索引。
早上，暂时没有大问题，但是Handler_read_rnd_next超过1.5G，考虑优化增加更多索引。性能测试。
早上，Handler_read_rnd_next还是超过1.5G

下午决定再次重启，增加tmp_table_size,table_cache,sort_buffer_size.
两天后Handler_read_rnd_next还是超过1.9G，决定加大key_buffer_size到384M

第二天不到两天，Handler_read_rnd_next超过2G，由于没有FLUSH QUERY CACHE权限，设置cron job:
30  	5  	*/2  	*  	*  	 /etc/init.d/mysql restart
两天一次于清晨5点半。

第二天下午发现table_cache小了，tmp table已经到1700，还原table_cache到2500

第二天，Handler_read_rnd_next超过2.3G，公司没有采纳我的建议，优化程序，唯有加crontab，每两天重启一次mysql
30  	5  	*/2  	*  	*  	 /etc/init.d/mysql restart

继续观察。。。

主要mysql问题参数：
Slow_queries             2
Innodb_buffer_pool_reads  	13
Handler_read_rnd  	37 k
Handler_read_rnd_next  	1,365 M
Created_tmp_disk_tables  	28
Select_full_join  	6
Opened_tables  	182
Table_locks_waited  	16
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 549px; width: 1px; height: 1px; overflow: hidden;">
<table id="cron_jobs_table" class="dynamic_table" cellspacing="0" cellpadding="0">
<tbody>
<tr id="info_row_1" class="dt_info_row info-odd">
<td><span id="minute_info_1">30</span></td>
<td><span id="hour_info_1">5</span></td>
<td><span id="day_info_1">*/2</span></td>
<td><span id="month_info_1">*</span></td>
<td><span id="weekday_info_1">*</span></td>
<td>`/etc/init.d/mysql restart`</td>
</tr>
</tbody>
</table>
</div>