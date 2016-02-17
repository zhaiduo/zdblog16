---
title: Windows下还原Plesk系统备份文件
tags:
  - Plesk
  - 备份
  - 控制台
id: 779
categories:
  - 网站维护
date: 2008-12-10 23:51:00
---

[Plesk](http://www.parallels.com/products/plesk/)是国外虚拟主机最常见的几种虚拟主机控制台(Hosting Control Panel)之一，前面提到我的博客丢失前曾经在9月份有这中备份，但是由于备份文件下载下来没有后缀名，不知道如何解压。今天终于解决问题。根据[Plesk官方论坛的解释](http://forum.swsoft.com/showthread.php?t=53402)，我是这样做的（文件名为zhaiduo.com_2008.09.18_10.56）：

1、首先将zhaiduo.com_2008.09.18_10.56改名为zhaiduo.com_2008.09.18_10.56.zip。用Rar解压后发现，61M的文件变成了124M的zhaiduo.com_2008.09.18_10.56。

2、将文件zhaiduo.com_2008.09.18_10.56改名为zhaiduo，打开Windows自带的Outlook Express，然后直接将zhaiduo用鼠标拖拽到Outlook的收件箱，如果文件导入成功（可以多试几次），
[![](http://3.bp.blogspot.com/_qn1iksfCdto/ST_qrqJbzAI/AAAAAAAAGjA/iuqqjQBaBDc/s400/17220081210231231.jpg)](http://3.bp.blogspot.com/_qn1iksfCdto/ST_qrqJbzAI/AAAAAAAAGjA/iuqqjQBaBDc/s1600-h/17220081210231231.jpg)
会弹出下面的对话框（这封邮件进行解码时出错，邮件标头中含有无效数据），不用理会按确定。你会发现收件箱里多了一封新邮件。

3.新邮件里面可以看见附件的标志，点击就出现了所有附件的下拉菜单。
[![](http://2.bp.blogspot.com/_qn1iksfCdto/ST_qr6Q5FoI/AAAAAAAAGjI/EmHMB9sXGms/s400/17320081210231722.jpg)](http://2.bp.blogspot.com/_qn1iksfCdto/ST_qr6Q5FoI/AAAAAAAAGjI/EmHMB9sXGms/s1600-h/17320081210231722.jpg)
直接全部保存就可以了。

4.最后，附件里面可以看到类似zhaiduo.com.httpdocs的文件，不用惊慌，
[![](http://2.bp.blogspot.com/_qn1iksfCdto/ST_qsI_4sTI/AAAAAAAAGjQ/W8f5uhvxds8/s400/17520081210234254.jpg)](http://2.bp.blogspot.com/_qn1iksfCdto/ST_qsI_4sTI/AAAAAAAAGjQ/W8f5uhvxds8/s1600-h/17520081210234254.jpg)
把这些文件名加一个.tar的后缀，用RAR解压，所有文件就都看见了。^_^