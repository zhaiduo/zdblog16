---
title: 博客移到Serversea
id: 220
categories:
  - 窄多废话
date: 2007-11-28 13:47:09
tags:
---

空间终于换到了[Serversea](http://www.serversea.com/referrals/processreferral.php?refere=MTQ2OQ==&dmn=)，虽然在国外，感觉速度还可以，支持的模块也比以前多，之前不支持URL rewrite功能，现在终于可以让博客页面地址简单化，利于搜索引擎收录。后台使用的是plesk，和cpanel差不多功能，这两款应该是目前国外使用的比较多的两种虚拟空间控制系统。下面是空间的主要配置：

**PHP Version 4.3.9** (不足的是现在都PHP 5.2.5，还没有升级到PHP5，zend framework也没办法测试啦)
(关于PHP Startup: Unable to load dynamic library php_mysql.dll的错误：解决办法复制libmysql.dll到/system32/目录下，重启Apache就可以了)
'./configure' '--build=i686-redhat-linux-gnu' '--host=i686-redhat-linux-gnu' '--target=i386-redhat-linux-gnu' '--program-prefix=' '--prefix=/usr' '--exec-prefix=/usr' '--bindir=/usr/bin' '--sbindir=/usr/sbin' '--sysconfdir=/etc' '--datadir=/usr/share' '--includedir=/usr/include' '--libdir=/usr/lib' '--libexecdir=/usr/libexec' '--localstatedir=/var' '--sharedstatedir=/usr/com' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--cache-file=../config.cache' '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' '--enable-force-cgi-redirect' '--disable-debug' '--enable-pic' '--disable-rpath' '--enable-inline-optimization' '--with-bz2' '--with-db4=/usr' '--with-curl' '--with-exec-dir=/usr/bin' '--with-freetype-dir=/usr' '--with-png-dir=/usr' '--with-gd=shared' '--enable-gd-native-ttf' '--without-gdbm' '--with-gettext' '--with-ncurses=shared' '--with-gmp' '--with-iconv' '--with-jpeg-dir=/usr' '--with-openssl' '--with-png' '--with-pspell' '--with-xml' '--with-expat-dir=/usr' '--with-dom=shared,/usr' '--with-dom-xslt=/usr' '--with-dom-exslt=/usr' '--with-xmlrpc=shared' '--with-pcre-regex=/usr' '--with-zlib' '--with-layout=GNU' '--enable-bcmath' '--enable-exif' '--enable-ftp' '--enable-magic-quotes' '--enable-sockets' '--enable-sysvsem' '--enable-sysvshm' '--enable-track-vars' '--enable-trans-sid' '--enable-yp' '--enable-wddx' '--with-pear=/usr/share/pear' '--with-imap=shared' '--with-imap-ssl' '--with-kerberos' '--with-ldap=shared' '--with-mysql=shared,/usr' '--with-pgsql=shared' '--with-snmp=shared,/usr' '--with-snmp=shared' '--enable-ucd-snmp-hack' '--with-unixODBC=shared,/usr' '--enable-memory-limit' '--enable-shmop' '--enable-calendar' '--enable-dbx' '--enable-dio' '--enable-mbstring=shared' '--enable-mbstr-enc-trans' '--enable-mbregex' '--with-mime-magic=/usr/share/file/magic.mime' '--with-apxs2=/usr/sbin/apxs'

**disable_functions**
shell_exec,exec,virtual,passthru,proc_close,proc_get_status,proc_open,proc_terminate,system

**Apache/2.0.52(Red Hat)**

**Loaded Modules**
core prefork http_core mod_so mod_access mod_auth mod_auth_anon mod_auth_dbm mod_auth_digest util_ldap mod_auth_ldap mod_include mod_log_config mod_env mod_mime_magic mod_cern_meta mod_expires mod_deflate mod_headers mod_usertrack mod_setenvif mod_mime mod_dav mod_status mod_autoindex mod_asis mod_info mod_dav_fs mod_vhost_alias mod_negotiation mod_dir mod_imap mod_actions mod_speling mod_userdir mod_alias mod_rewrite mod_proxy proxy_ftp proxy_http proxy_connect mod_cache mod_suexec mod_disk_cache mod_file_cache mod_mem_cache mod_cgi mod_fcgid mod_jk mod_perl sapi_apache2 mod_python mod_ssl

bcmath
BCMath support     enabled

bz2
BZip2 Support     Enabled
BZip2 Version     1.0.2, 30-Dec-2001

calendar
Calendar support     enabled

ctype
ctype functions     enabled

curl
CURL support     enabled
CURL Information     libcurl/7.12.1 OpenSSL/0.9.7a zlib/1.2.1.2 libidn/0.5.6

dba
DBA support     enabled
Supported handlers     cdb cdb_make db4 inifile flatfile

dbx
dbx support     enabled
dbx version     1.0.0
supported databases     MySQL ODBC PostgreSQL Microsoft SQL Server FrontBase Oracle 8 (oci8) Sybase-CT

Directive    Local Value    Master Value
dbx.colnames_case    lowercase    lowercase

dio
dio support     enabled

domxml
DOM/XML     enabled
DOM/XML API Version     20020815
libxml Version     20616
HTML Support     enabled
XPath Support     enabled
XPointer Support     enabled
DOM/XSLT     enabled
libxslt Version     1.1.11
libxslt compiled against libxml Version     2.6.14
DOM/EXSLT     enabled
libexslt Version     1.1.11

exif
EXIF Support     enabled
EXIF Version     1.4 $Id: exif.c,v 1.118.2.35 2005/03/05 18:30:47 rasmus Exp $
Supported EXIF Version     0220
Supported filetypes     JPEG,TIFF

ftp
FTP support     enabled

gd
GD Support     enabled
GD Version     bundled (2.0.28 compatible)
FreeType Support     enabled
FreeType Linkage     with freetype
GIF Read Support     enabled
GIF Create Support     enabled
JPG Support     enabled
PNG Support     enabled
WBMP Support     enabled
XBM Support     enabled

gettext
GetText Support     enabled

gmp
gmp support     enabled

iconv
iconv support     enabled
iconv implementation     glibc
iconv library version     2.3.4

imap
IMAP c-Client Version     2001
SSL Support     enabled
Kerberos Support     enabled

ldap
LDAP Support     enabled
RCS Version     $Id: ldap.c,v 1.130.2.10 2004/06/01 21:05:33 iliaa Exp $
Total Links     0/unlimited
API Version     3001
Vendor Name     OpenLDAP
Vendor Version     20213

mbstring
Multibyte Support     enabled
Japanese support     enabled
Simplified chinese support     enabled
Traditional chinese support     enabled
Korean support     enabled
Russian support     enabled
Multibyte (japanese) regex support     enabled

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

mime_magic
mime_magic support    enabled

mysql
MySQL Support    enabled
Active Persistent Links     0
Active Links     0
Client API version     4.1.20

openssl
OpenSSL support     enabled
OpenSSL Version     OpenSSL 0.9.7a Feb 19 2003

overload
User-Space Object Overloading Support     enabled

pcre
PCRE (Perl Compatible Regular Expressions) Support     enabled
PCRE Library Version     4.5 01-December-2003

posix
Revision     $Revision: 1.51.2.2 $

pspell
PSpell Support     enabled

session
Session Support     enabled
Registered save handlers     files user

shmop
shmop support     enabled

sockets
Sockets Support     enabled

standard
Regex Library     Bundled library enabled
Dynamic Library Support     enabled

tokenizer
Tokenizer Support     enabled

wddx
WDDX Support    enabled
WDDX Session Serializer     enabled

xml
XML Support     active
XML Namespace Support     active
EXPAT Version     expat_1.95.7

yp
YP Support     enabled

zlib