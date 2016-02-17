---
title: Google Appengine部署常见问题
tags:
  - GoogleAppEngine
id: 1198
categories:
  - Google与Idea
---

*   部署后，出现500 Server Error，在后台查看日志：
exceptions.SyntaxError'&gt;: invalid syntax
解决办法: 把Exception as foo改成Exception ， foo，因为gae用的版本还是python 2.5.2，而本地测试用的是2.6
*   'NoneType' object has no attribute 'key'
注意检查key是否存在
*   type 'exceptions.IndentationError' : unexpected indent
注意每行后面不要有分号，这不是PHP
*   本地windows调试推荐用time.clock，gae线上用time.time
判断os.environ的SERVER_HOST 和HTTP_USER_AGENT
*   AttributeError: 'list' object has no attribute '_populate_entity'
*   NameError: global name 'downloaderror' is not defined
*   fromstring() argument 1 must be string or read-only buffer, not bool
*   ImportError: No module named google3.apphosting.runtime
*   BadValueError: Property identifier is not multi-line
class StringProperty(verbose_name=None, multiline=False, ...)
If multiline is False, then the value cannot include linefeed characters.