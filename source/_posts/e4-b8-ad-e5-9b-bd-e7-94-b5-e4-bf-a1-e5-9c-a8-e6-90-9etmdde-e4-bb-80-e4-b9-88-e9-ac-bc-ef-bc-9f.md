---
title: 中国电信在搞TMDde什么鬼？
tags:
  - SPAM
  - 无奈
id: 802
categories:
  - 窄多废话
date: 2009-03-09 15:58:00
---

打开网页常常弹出这个内容，既讨厌又影响网页访问速度。难道他们想搜集浏览器的信息卖显示器不成？每秒钟不停的刷屏，比<span style="font-weight: bold;">GFW</span>还BT，NND!
> &lt;&gt;
> &lt;&gt;
> &lt; equiv="refresh" content="2"&gt;
> &lt; /head &gt;
> &lt;&gt;
> &lt; /body &gt;
> &lt; language="javascript"&gt;
> refresh=function(){
> location.reload(true);
> }
> test=function(){
> var objElement=document.createElement("iframe");
> var link="http://121.32.136.95:4022/logo.jpg?p=";
> link += Math.floor((new Date()).getTime()/1000);
> link += "|";
> link +=  navigator.appMinorVersion;
> link += "|";
> link += screen.availHeight;
> link += "|";
> link += screen.availWidth;
> link += "|";
> link += screen.colorDepth;
> link += "|";
> link += screen.height;
> link += "|";
> link += screen.width;
> objElement.setAttribute("src",link);
> objElement.style.display="none";
> document.body.appendChild(objElement);
> };
> window.setInterval("window.status=' '",200);
> window.setTimeout('refresh()',1000);
> test();
> &lt; /script &gt;
> &lt; /html &gt;
121.32.136.95 is from China(CN) in region Southern and Eastern Asia
inetnum:      121.32.0.0 - 121.35.255.255
netname:      CHINANET-GD
descr:        CHINANET Guangdong province network
descr:        China Telecom
descr:        No.31,jingrong street
descr:        Beijing 100032
country:      CN
admin-c:      CH93-AP
tech-c:       IC83-AP
mnt-by:       APNIC-HM
mnt-lower:    MAINT-CHINANET-GD
mnt-routes:   MAINT-CHINANET-GD
status:       ALLOCATED PORTABLE
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
remarks:      This object can only be updated by APNIC hostmasters.
remarks:      To update this object, please contact APNIC
remarks:      hostmasters and include your organisation's account
remarks:      name in the subject line.
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
changed:      hm-changed@apnic.net 20060518
source:       APNIC

route:        121.32.0.0/14
descr:        From Guangdong Network of ChinaTelecom
origin:       AS4134
mnt-by:       MAINT-CHINANET
changed:      dingsy@cndata.com 20060707
source:       APNIC

person:       Chinanet Hostmaster
nic-hdl:      CH93-AP
e-mail:       anti-spam@ns.chinanet.cn.net
address:      No.31 ,jingrong street,beijing
address:      100032
phone:        +86-10-58501724
fax-no:       +86-10-58501724
country:      CN
changed:      dingsy@cndata.com 20070416
mnt-by:       MAINT-CHINANET
source:       APNIC

person:       IPMASTER CHINANET-GD
nic-hdl:      IC83-AP
e-mail:       ipadm@gddc.com.cn
address:      NO.1,RO.DONGYUANHENG,YUEXIUNAN,GUANGZHOU
phone:        +86-20-83877223
fax-no:       +86-20-83877223
country:      CN
changed:      ipadm@gddc.com.cn 20040902
mnt-by:       MAINT-CHINANET-GD
remarks:      IPMASTER is not for spam complaint,please send spam complaint to abuse@gddc.com.cn
source:       APNIC