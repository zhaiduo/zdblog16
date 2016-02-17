---
title: 关于mysql_real_escape_string
id: 203
categories:
  - PHP
date: 2007-08-23 18:58:56
tags:
---

今天有空看了看多用户博客[lyceum](http://lyceum.ibiblio.org/downloads/)和[WordPress MU](http://mu.wordpress.org/download/)。在WP-db.php有这样一段代码：

[code lang="php"]function escape($string) {
return addslashes( $string ); // Disable rest for now, causing problems
if( !$this->dbh || version_compare( phpversion(), '4.3.0' ) == '-1' )
return mysql_escape_string( $string );
else
return mysql_real_escape_string( $string, $this->dbh );
} [/code]

很好的说明了addslashes和mysql_real_escape_string的区别，虽然国内很多PHP coder仍在依靠addslashes防止SQL注入（包括我在内），我还是建议大家加强中文防止SQL注入的检查。

[addslashes的问题](http://shiflett.org/blog/2006/jan/addslashes-versus-mysql-real-escape-string)在于黑客可以用0xbf27来代替单引号，而addslashes只是将0xbf27修改为0xbf5c27，成为一个有效的多字节字符，其中的0xbf5c仍会被看作是单引号，所以addslashes无法成功拦截。

当然addslashes也不是毫无用处，它是用于单字节字符串的处理，多字节字符还是用mysql_real_escape_string吧。

另外对于php手册中get_magic_quotes_gpc的举例：

[code lang="php"]if (!get_magic_quotes_gpc()) {
$lastname = addslashes($_POST['lastname']);
} else {
$lastname = $_POST['lastname'];
}[/code]

最好对magic_quotes_gpc已经开放的情况下，还是对$_POST['lastname']进行检查一下。