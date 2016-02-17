---
title: 安装Molehill和Away3D
tags:
  - AS3
  - Away3D
  - molehill
id: 1312
categories:
  - 3D
  - Flash
date: 2011-03-10 00:52:06
---

今天终于有空配置Flash Pro CS5下的Molehill和Away3D环境，准备开始玩玩Molehill 3D. 我参考的教程有下面两个：

*   [http://johnlindquist.com/2011/02/28/quickstart-for-molehill-and-away3d/](http://johnlindquist.com/2011/02/28/quickstart-for-molehill-and-away3d/)
*   [http://blog.kaourantin.net/?p=104](http://blog.kaourantin.net/?p=104)
首先是安装(参考johnlindquist.com)，包括Flash player11.0 Incubator，Flex SDK 4.5.0.19786，flashplayer_inc_playerglobal_022711.swc和molehill_away3d_patch.zip。

然后是设置，在CS5的SET-&gt;PREFERENCES选择Actionscript，点击3.0的设置，修改SDK Path为flex_sdk_4.5.0.17689的安装目录，library path里面增加$(FlexSDK)/frameworks/libs。

接着从blog.kaourantin.net下载teapot.zip，里面有个目录叫Copy Files Inside Folder To Your Adobe Flash CS5 installation，就是复制里面的文件和目录到Flash Pro CS5的安装配置目录下，如：C:Program FilesAdobeAdobe Flash CS5CommonConfiguration。

最后，在CS5里面打开teapot.fla，在publish setting里面的flash板块选择Flash Player 11，编译即可。

注意：编译后出现如下错误：VerifyError: Error #1014: 无法找到类 flash.display3D::Context3D。
不用惊慌，其实编译已经完成，只不过预览的player版本不够。用装好Incubator的浏览器即正常打开～慢慢享受吧~

[![](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110310003258.jpg "20110310003258")](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110310003258.jpg)

[![](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110310003333.jpg "20110310003333")](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110310003333.jpg)