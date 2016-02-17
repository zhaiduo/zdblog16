---
title: Android Studio开发测试
tags:
  - java
  - 安卓
id: 2025
categories:
  - APP
---

登记成为安卓开发者需预授权扣款25美元，在Google play下载Android Studio。之前还需安装jdk7开发包，记得设置JAVA_HOME环境变量。

sdk包下载推荐用镜像mirrors.neusoft.edu.cn 80，并且修改镜像文件：
http://mirrors.neusoft.edu.cn/android/repository/addon-6.xml
http://mirrors.neusoft.edu.cn/android/repository/addon.xml
http://mirrors.neusoft.edu.cn/android/repository/addons_list-2.xml
http://mirrors.neusoft.edu.cn/android/repository/extras/intel/addon.xml
http://mirrors.neusoft.edu.cn/android/repository/repository-10.xml
http://mirrors.neusoft.edu.cn/android/repository/sys-img/android-tv/sys-img.xml
http://mirrors.neusoft.edu.cn/android/repository/sys-img/android-wear/sys-img.xml
http://mirrors.neusoft.edu.cn/android/repository/sys-img/android/sys-img.xml
http://mirrors.neusoft.edu.cn/android/repository/sys-img/google_apis/sys-img.xml
http://mirrors.neusoft.edu.cn/android/repository/sys-img/x86/addon-x86.xml

教程可参考 - 前端之Android入门：http://isux.tencent.com/?s=%E5%89%8D%E7%AB%AF%E4%B9%8BAndroid%E5%85%A5%E9%97%A8

编译webkit.WebView时，出错提示是乱码方括号：
setting-》appearance->override default fonts改成simsun即可。