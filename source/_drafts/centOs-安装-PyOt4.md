---
title: centOs 安装 PyOt4
id: 1957
categories:
  - 杂项
tags:
---

yum install python
yum install python-devel
yum install qt4 qt-devel qt-config

PyQt4 Download
http://www.riverbankcomputing.co.uk/software/pyqt/download

http://pyqt.sourceforge.net/Docs/PyQt4/installation.html

http://sourceforge.net/projects/pyqt/files/sip/sip-4.16.2.zip

sip/python configure.py --incdir=/usr/inc/python2.6

make & make install

python configure-ng.py -q /usr/lib64/qt4/bin/qmake --static

make & make install

phython scripts/webkit2png -h

wget http://dl.fedoraproject.org/pub/epel/6/i386/PyQt4-webkit-4.6.2-8.el6.i686.rpm
wget http://dl.fedoraproject.org/pub/epel/6/i386/PyQt4-webkit-devel-4.6.2-8.el6.i686.rpm
rpm -ivh PyQt4-webkit-devel-4.6.2-8.el6.i686.rpm
太多关联libQtCore*.so，放弃rpm安装。