---
title: 'Corrupt JPEG Error: extraneous bytes before marker 0xd9'
tags:
  - Corrupt JPEG
  - GD
  - 出错
id: 579
categories:
  - PHP
date: 2010-07-08 14:12:03
---

一个Flash项目，一直以来被一个PHP GD模块的问题所困扰，遭到很多用户投诉，无法通过Flash上传图片。我研究过，发现有些图片在Windows下，Photoshop下都可以看见，但是一通过PHP的GD模块来处理，就出现如下错误(例如[这张图片](http://bugs.libgd.org/?getfile=262))：
> imagecreatefromjpeg() [function.imagecreatefromjpeg]: gd-jpeg, libjpeg: recoverable error: Corrupt JPEG data: 91 extraneous bytes before marker 0xd9
其中91和0xd9会因为图片的不同而不同，例如Corrupt JPEG data: 4 extraneous bytes before marker 0xd9。

**寻找解决方法：**

1.  究其原因应该是gd-jpeg, libjpeg有问题，最快的解决办法就是重新编译libjpeg，但是这对使用虚拟主机的网站来说不太靠谱。
2.  通过PHP分析有问题的图片头，标记0xd9的错误，但是每张图片的错误标记不同，所以不成立。
具体原因是由于[JPG图片头](http://www.media.mit.edu/pia/Research/deepview/exif.html)中EOI marker (0xFF 0xD9) 前的自定义数据部分，PHP GD2无法识别.
3.  由于虚拟主机的限制，这个也不靠谱
ini_set('gd.jpeg_ignore_warning', 1);
imagecreatefromjpeg($file);
4.  替代工具：[ImageMagick](http://us3.php.net/manual/en/book.imagick.php),但是空间限制，也只有放弃。
目前暂时没有针对PHP自身的解决方案，另外建议不要使用ImageCreateFromString，也会有这个问题，可以用getimagesize。

困扰的是：老板不管这个是否是BUG，他只要完美，而我却没有答案。