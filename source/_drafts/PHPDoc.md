---
title: PHPDoc
id: 1895
categories:
  - 杂项
tags:
---

@param 方法、函数的参数
@param 参数类型$参数名参数说明
@author 作者
@author 作者名<xxx@gmail.com>
@return 返回值
@return 返回值类型返回值说明
@version 版本说明
@version 版本号
@copyright 版权信息
@copyright Copyright &copy; 2012, 公司名或作者名
@since 第一次添加的日期或版本
@since 2012-01-01 或
@since version 1.0
@property 类的属性说明
@property属性类型$属性名属性说明
@access 方法的访问权限
@access private | protected | public @link 链接
@link URL link_text
@see 参见锚点
@see  file.ext|elementname|class::methodname()|class::$variablename|functionname()
@example  代码示例
@example /path/to/example.php 示例描述

@abstract	 	抽象类的变量和方法
@access	public, private or protected	文档的访问、使用权限. @access private 表明这个文档是被保护的。
@author	张三 <xxx@gmail.com>	文档作者
@copyright	名称 时间	文档版权信息
@deprecated	version	文档中被废除的方法
@deprec	 	同 @deprecated
@example	/path/to/example	文档的外部保存的示例文件的位置。
@exception	 	文档中方法抛出的异常，也可参照 @throws.
@global	类型：$globalvarname	文档中的全局变量及有关的方法和函数
@ignore	 	忽略文档中指定的关键字
@internal	 	开发团队内部信息
@link	URL	类似于license 但还可以通过link找到文档中的更多个详细的信息
@name	变量别名	为某个变量指定别名
@magic	 	phpdoc.de compatibility
@package	封装包的名称	一组相关类、函数封装的包名称
@param	如 [$username] 用户名	变量含义注释
@return	如 返回bool	函数返回结果描述，一般不用在void（空返回结果的）的函数中
@see	如 Class Login（）	文件关联的任何元素（全局变量，包括，页面，类，函数，定义，方法，变量）。
@since	version	记录什么时候对文档的哪些部分进行了更改
@static	 	记录静态类、方法
@staticvar	 	在类、函数中使用的静态变量
@subpackage	 	子版本
@throws	 	某一方法抛出的异常
@todo	 	表示文件未完成或者要完善的地方
@var	type	文档中的变量及其类型
@version	 	文档、类、函数的版本信息

PHP Doc安装

pear channel-discover pear.phpdoc.org
pear remote-list -c phpdoc
pear install phpdoc/phpDocumentor-2.3.1

使用方法，在要生成文档的项目所在目录运行:

%PHP_PEAR_BIN_DIR%phpdoc -d . -t docs