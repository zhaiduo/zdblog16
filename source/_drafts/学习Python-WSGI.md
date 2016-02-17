---
title: 学习Python WSGI
tags:
  - GoogleAppEngine
  - python
id: 1189
categories:
  - Google与Idea
---

WSGI(Web Server Gateway Interface)可以说是Python的servlet，高于版本2.2.2的Python都把它作为默认的标准库。它不是一个web framework，而是作为促进服务器与应用程序之间的交互的接口，连接framework和server。从Google Appengine我们可以了解到run_wsgi_app的运作模式，但是对[WSGI](http://www.python.org/dev/peps/pep-0333/)来说仍然是个未知领域，什么是environ，start_response有什么用，这些都要求我们对WSGI要有基本的认识，从底层了解Python Web Server的运作模式，才能更好的构建自己的基于WSGI的框架，并以此作为深入了解Python Web应用的一项主要功课。

为使用户定义的类（该类含有必不可少的 .next() 方法）返回迭代器，需要使 __iter__() 方法返回 self 。
生成器yield最典型的用途是用来定义迭代器。
生成器yield是这样一个函数，它记住上一次返回时在函数体中的位置。对生成器函数的第二次（或第 n 次）调用跳转至该函数中间，而上次调用的所有局部变量都保持不变。
def __iter__(self):
        status = '200 OK'
        response_headers = [('Content-type', 'text/plain')]
        self.start(status, response_headers)
        yield "Hello world!n"
//Since App Engine doesn't support streaming responses, returning or yielding are equivalent, so we'll simply use return, for simplicity.
yield象“终止”一样，生成器“记住”了它数据状态。但生成器比“终止”要更进一步：生成器还“记住”了它在流控制构造（在命令式编程中，这种构造不只是数据值）中的位置。由于连续性使您在执行框架间任意跳转，而不总是返回到直接调用者的上下文。
在 Python 2.2+ 中使函数成为生成器工厂是它主体某处的一个或多个 yield 语句。如果 yield 发生， return 一定只发生在没有伴随任何返回值的情况中。然而，一个较好的选择是，安排函数体以便于完成所有 yield 之后，执行就“跳转到结束”。但如果遇到 return ，它导致产生的生成器抛出 StopIteration 异常，而不是进一步生成值。

参考资料：

DIY framework: http://pythonpaste.org/webob/do-it-yourself.html
DiveintoPython3: http://diveintopython3.org/