---
title: Smarty3
id: 2033
categories:
  - PHP
tags:
---

这里大概解读一下附带的README文件

BETA8 需要注意的事情
Smarty3 的API已经被重构过以更好的面向结构话和语法一致性。但是Smarty2的API仍然是支持的，但是会出提示。

当然，也可以手动disable掉这个提示，但是强烈推荐你将你的语法升级到适应Smarty3的语法

Smarty3中所有的方法命名都采用”fooBarBaz”的方式，而且，所有的Smarty属性都含有getters和setters，举例：

老版本中设置Cache的路径

$smarty->cache_dir
现在可以这样作：

$smarty->setCacheDir('foo/')
并且可以通过如下方法获取：

$smarty->getCacheDir()
一些smarty3的api比如以isXX开头的方法已经被取消，因为现在已经有实现相同功能的类似getXX的方法代替了

以下是一个简单的API列表

$smarty->fetch($template, $cache_id = null, $compile_id = null, $parent = null)
$smarty->display($template, $cache_id = null, $compile_id = null, $parent = null)
$smarty->isCached($template, $cache_id = null, $compile_id = null)
$smarty->createData($parent = null)
$smarty->createTemplate($template, $cache_id = null, $compile_id = null, $parent = null)
$smarty->enableSecurity()
$smarty->disableSecurity()
$smarty->setTemplateDir($template_dir)
$smarty->addTemplateDir($template_dir)
$smarty->templateExists($resource_name)
$smarty->loadPlugin($plugin_name, $check = true)
$smarty->loadFilter($type, $name)
$smarty->setExceptionHandler($handler)
$smarty->addPluginsDir($plugins_dir)
$smarty->getGlobal($varname = null)
$smarty->getRegisteredObject($name)
$smarty->getDebugTemplate()
$smarty->setDebugTemplate($tpl_name)
$smarty->assign($tpl_var, $value = null, $nocache = false, $scope = SMARTY_LOCAL_SCOPE)
$smarty->assignGlobal($varname, $value = null, $nocache = false)
$smarty->assignByRef($tpl_var, &$value, $nocache = false, $scope = SMARTY_LOCAL_SCOPE)
$smarty->append($tpl_var, $value = null, $merge = false, $nocache = false, $scope = SMARTY_LOCAL_SCOPE)
$smarty->appendByRef($tpl_var, &$value, $merge = false)
$smarty->clearAssign($tpl_var)
$smarty->clearAllAssign()
$smarty->configLoad($config_file, $sections = null)
$smarty->getVariable($variable, $_ptr = null, $search_parents = true, $error_enable = true)
$smarty->getConfigVariable($variable)
$smarty->getStreamVariable($variable)
$smarty->getConfigVars($varname = null)
$smarty->clearConfig($varname = null)
$smarty->getTemplateVars($varname = null, $_ptr = null, $search_parents = true)
一些API的调用是通过它自己的对象完成的

$smarty->cache->loadResource($type = null)
$smarty->cache->clearAll($exp_time = null, $type = null)
$smarty->cache->clear($template_name, $cache_id = null, $compile_id = null, $exp_time = null, $type = null)

$smarty->register->block($block_tag, $block_impl, $cacheable = true, $cache_attr = array())
$smarty->register->compilerFunction($compiler_tag, $compiler_impl, $cacheable = true)
$smarty->register->templateFunction($function_tag, $function_impl, $cacheable = true, $cache_attr = array())
$smarty->register->modifier($modifier_name, $modifier_impl)
$smarty->register->templateObject($object_name, $object_impl, $allowed = array(), $smarty_args = true, $block_methods = array())
$smarty->register->outputFilter($function_name)
$smarty->register->postFilter($function_name)
$smarty->register->preFilter($function_name)
$smarty->register->resource($resource_type, $function_names)
$smarty->register->variableFilter($function_name)
$smarty->register->defaultPluginHandler($function_name)
$smarty->register->defaultTemplateHandler($function_name)

$smarty->unregister->block($block_tag)
$smarty->unregister->compilerFunction($compiler_tag)
$smarty->unregister->templateFunction($function_tag)
$smarty->unregister->modifier($modifier)
$smarty->unregister->templateObject($object_name)
$smarty->unregister->outputFilter($function_name)
$smarty->unregister->postFilter($function_name)
$smarty->unregister->preFilter($function_name)
$smarty->unregister->resource($resource_type)
$smarty->unregister->variableFilter($function_name)

$smarty->utility->compileAllTemplates($extention = '.tpl', $force_compile = false, $time_limit = 0, $max_errors = null)
$smarty->utility->clearCompiledTemplate($resource_name = null, $compile_id = null, $exp_time = null)
$smarty->utility->testInstall()
然后是所有的getters和setters，可以用来获取和设置所有属性，以下是一些例子：

$caching = $smarty->getCaching();      // get $smarty->caching
$smarty->setCaching(true);             // set $smarty->caching
$smarty->setDeprecationNotices(false); // set $smarty->deprecation_notices
$smarty->setCacheId($id);              // set $smarty->cache_id
$debugging = $smarty->getDebugging();  // get $smarty->debuggin
目录结构
和Smarty2结构类似

index.php
/libs/
    Smarty.class.php   #主文件
/libs/sysplugins/  #内部plugin
    internal.
/plugins/   #外部plugin,可自由扩充
    function.mailto.php
    modifier.escape.php2
/templates/   #模板，可以是纯php或传统的smarty模板
    index.tpl
    index_view.php
非常多的Smarty3核心功能函数是放在sysplugins目录底下，你不需要去修改其中的任何文件

它的插件文件则是放在/lib/plugins目录底下，你可以在其中增加你自己的插件文件。

你仍然需要创建自己的cache/,templates/, template_c/, configs/目录，并且要保证cache/，template_c两个目录具有写权限

简单调用
require('Smarty.class.php');
$smarty = new Smarty;
$smarty->assign('foo','bar');
$smarty->display('index.tpl');)))
区别
虽然Smarty3在模板使用起来和以前没有区别，但是其实内部逻辑是截然不同的，却也是能够和2进行兼容

除了以下几点

Smarty3只能运行在PHP5环境下，不再支持PHP4

{php}标签默认是关闭的，可以通过如下方式打开

$smarty->allow_php_tag=true

模板标签将不支持空格，如{ $abc }在Smarty2中可以识别的，但是3里头就不行了，必须这样{$abc}，这样是为了能够更好的支持javascript和css，但是你仍然可以通过设置来支持原来的形式

$smarty->auto_literal = false;

Smarty3的API有一定的不同，但是仍然支持Smarty2

词法特性
Smarty3 采用一个词法分析器来进行模板的解析和编译，基于这种方式，它可以支持一些语法扩展来让生活变得更加美好！

比如模板内部的数学计算，直观，简短的函数参数选项，以及无穷的函数递归，更准确的错误处理等等

新的功能
表达式
支持更加随意的表达式

{$x+$y}                           输入x和y的和
{$foo = strlen($bar)}             变量支持PHP函数
{assign var=foo value= $x+$y}     属性支持表达式
{$foo = myfunct( ($x+$y)*3 )}     函数参数支持表达式
{$foo[$x+3]}                      数组下表支持表达式
引号中可以使用变量

{$foo="this is message {counter}"}
可以在模板里头定义数组

{assign var=foo value=[1,2,3]}
{assign var=foo value=['y'=>'yellow','b'=>'blue']}
{assign var=foo value=[1,[9,8],3]}
简单的变量赋值

{$foo=$bar+2}
可以给指定的数组元素赋值，如果变量存在但不是数组，会先转换成数组，再进行赋值

{$foo['bar']=1}
{$foo['bar']['blar']=1}
同上，可以给数组添加值

{$foo[]=1}
对象的属性支持”.”操作符

{$foo.a.b.c}        =>  $foo['a']['b']['c']
{$foo.a.$b.c}       =>  $foo['a'][$b]['c']
{$foo.a.{$b+4}.c}   =>  $foo['a'][$b+4]['c']
{$foo.a.{$b.c}}     =>  $foo['a'][$b['c']]
变量名中支持变量

$foo         一个普通的变量
$foo_{$bar}  变量名中包含变量
$foo_{$x+$y} 变量名中可以支持表达式
$foo_{$bar}_buh_{$blar}  变量名包含多个变量
{$foo_{$x}}  如果$x是1，则输出$foo_1
支持对象链，即是对象方法的连续调用，很像jquery

{$object->method1($x)->method2($y)}
{for}标签支持类似loop一样的循环

{for $x=0, $y=count($foo); $x<$y; $x++}  ....  {/for}
在FOR循环中可以通过如下特殊标示符限定位置：

$x@iteration  当前循环次数
$x@total     总循环次数
$x@first  循环第一次
$x@last     循环最后一次
新的foreach语法

{foreach $myarray as $var}...{/foreach}
同样是foreach里头的特殊表示符，看的就明白，不翻译了……

$var@key            foreach $var array key
$var@iteration      foreach current iteration count (1,2,3...)
$var@index          foreach current index count (0,1,2...)
$var@total          foreach $var array total
$var@first          true on first iteration
$var@last           true on last iteration
支持while循环

{while $foo}...{/while}
{while $x lt 10}...{/while}
可以直接使用PHP的函数

{time()}
新增加了一个{function}的标签，可以定义一个可供调用的函数块（我喜欢这功能，哈哈！）

{function}...{/function}
该标签必须有一个name属性，用来指名该函数名称，也是调用的时候需要用到的

下面是一个例子

/* 定义一个函数 */
{function name=menu level=0}

    {foreach $data as $entry}
        {if is_array($entry)}*   {$entry@key}

            {menu data=$entry level=$level+1}
        {else}*   {$entry}
{/function}

/* 给函数传递的参数 */
{$menu = ['item1','item2','item3' => ['item3-1','item3-2','item3-3' =>
    ['item3-3-1','item3-3-2']],'item4']}

/* 调用那个函数 */
{menu data=$menu}
{function}功能函数必须有一个name属性，并且可以拥有任意多个的其它属性

代码块不缓存，可以使用{nocache}标签默认是关闭的

{nocache} ... {/nocache}
还可以作为属性

{$foo nocache=true}
{$foo nocache}
{foo bar="baz" nocache=true}
{foo bar="baz" nocache}
{time() nocache=true}
{time() nocache}
返回当前模板的方法

$smarty.cur_template
变量作用域和存储
在Smarty2中，所有的变量都存储在Smarty对象中，因此所有的变量在所有模板和子方法中都可以获取

在Smarty3中，可以自己定义的将变量存储在主Smarty对象中，或者用户自己定义的对象中，甚至是用户自己的模板对象中

而且这些对象可以通过链式串接起来。

在链的末尾的对象可以获取到对象链之前的对象中存储的所有变量。

Smarty对象必须是链的根对象，但是对象链却是可以独立于Smarty对象存在的

所有的Smarty的赋值方法都可以用在data对象或者模板对象

除了上面说几个方面，全局变量还有一种特殊的存储方式

一个Smarty的数据对象(data Object)可以通过如下方式创建

$data = $smarty->createData();    // 创建根数据对象
$data->assign('foo','bar');       // 赋值操作
$data->config_load('my.conf');      // 加载配置文件

$data = $smarty->createData($smarty);   // 以Smarty作为父对象，创建数据对象

$data2= $smarty->createData($data);     // 以data作为父对象，创建数据对象data2
创建一个模板对象(template object) 可以通过createTemplate方法，它的参数传递和fetch()/display()方法一致

函数定义方式

function createTemplate($template, $cache_id = null, $compile_id = null, $parent = null)
举例

$tpl = $smarty->createTemplate('mytpl.tpl'); // 创建一个模板对象，没有父对象
$tpl->assign('foo','bar');                   // directly assign variables
$tpl->config_load('my.conf');

$tpl = $smarty->createTemplate('mytpl.tpl',$smarty); // 以Smarty为父对象，创建模板对象
fetch()/display() 两个方法将隐式的创建一个模板对象

如果不指定父对象，则默认父对象将指向Smarty对象

如果一个模板是通过include方式调用的，则子模板的父对象将指向引用它的模板对象

所有当前模板变量和父对象的模板变量都是可以获取的，但是如果是通过{assign}或者{$foo=…}这样的方法创建或者修改变量

则它的作用域将只停留在当前模板对象

Smarty3中，在赋值变量的时候可以指定它的作用域，有4个值local,parent,root,global

{assign var=foo value='bar'}       // no scope is specified, the default 'local'
{$foo='bar'}                       // same, local scope
{assign var=foo value='bar' scope='local'} // same, local scope
{assign var=foo value='bar' scope='parent'} // Values will be available to the parent object
{$foo='bar' scope='parent'}                 // (normally the calling template)
{assign var=foo value='bar' scope='root'}   // Values will be exported up to the root object, so they can
{$foo='bar' scope='root'}                   // be seen from all templates using the same root.
{assign var=foo value='bar' scope='global'} // Values will be exported to global variable storage,
{$foo='bar' scope='global'}
扩展
Smarty3的扩展都是继承至Smarty – Internal – PluginBase的类

所有的扩展都包含一个Smarty对象实例的$this->smarty属性

模板继承
你可以在模板中写{block} … {/block}快，并且这些块可以在子模板中进行覆盖

parent.tpl:

<html>
    <head>
        <title>{block name='title'}My site name{/block}</title>
    </head>
    <body>

# {block name='page-title'}Default page title{/block}

        <div id="content">
            {block name='content'}
            Default content
            {/block}
        </div>
    </body>
</html>
child.tpl:

{extends file='parent.tpl'}

{block name='title'}
    Child title
{/block}
grandchild.tpl:

{extends file='child.tpl'}

{block name='title'}Home - {$smarty.block.parent}{/block}
{block name='page-title'}My home{/block}
{block name='content'}
    {foreach $images as $img}
        ![{$img.description}]({$img.url})
    {/foreach}
{/block}
可以通过extends标签来指定被继承的模板，并在子模板中通过重写父模板的同名block块，达到覆盖的目的

同时，可以通过{$smarty.block,parent}获取到父block的内容

上面的grandchild.tpl将生成如下内容

<html>
    <head>
        <title>Home - Child title</title>
    </head>
    <body>

# My home

        <div id="content">
            ![image](/example.jpg)
            ![image](/example2.jpg)
            ![image](/example3.jpg)
        </div>
    </body>
</html>
注意，在子模板中，所有在{block} … {/block}之外的内容都将被忽略

这种继承支持多文件，多重继承，意味着可以无线的继承下去

还可通过{block}的append和prepend属性来插入父模板结构中

PHP 流
待补充…

变量过滤

‍smarty 的过滤器 分为
• Prefilter
• Postfilter
• Output filter
这三种，这里分别解释一下
Prefilter：在smarty模板编译成php代码之前调用
Postfilter：在smarty模板编译成php代码之后调用
Output Filters：在smarty 准备显示编译过的代码时调用
这里的顺序应该是 tpl源文件 =〉Prefilter =〉编译tpl文件 => Postfilter =>保存到磁盘=> 编译过的php文件执行=〉Output Filters（=〉如果有smarty cache的话，Output Filters的内容会缓存） =>结果输出。

创建filter的方式也一般有三种：
1：执行时 注册一个 filter,此时可以用以下三种函数调用：
Prefilters         void register_prefilter(mixed impl)
Postfilters      void register_postfilter(mixed impl)
Output filters void register_outputfilter(mixed impl)
这里的impl 指 回调的函数名， 或者形如：array($object, 'method_name')或array('class_name', 'method_name')的数组

执行时 注册的例子：
function highlight($output, &$smarty)
{
// highlight the word "smarty" on our template source
return str_replace('smarty', '**smarty**', $output);
}
$smarty->register_outputfilter('highlight');
$smarty->display('templates/example1.tpl');
2:手动加载一个过滤器
一个过滤器插件的文件应该放在plug-in目录里面，而且文件 和 函数的命名也要遵循一定的规则
如：一个prefilter，那么他的文件名应为：prefilter.nameoffilter.php , 其函数名字应为：smarty_prefilter_nameoffilter($source, &$samrty);
如以下函数：
function smarty_outputfilter_append_benchmark_data($source, &$smarty)
{
global $benchmark;
$source .= '<div id="benchmark">';
$source .= 'Generated in ' . $benchmark . ' secs.';
$source .= '</div>';
return $source;
}
?>
保存在outputfilter.append_benchmark_data.php这个文件里面，
我们调用这个插件时：
$smarty->load_filter('output', 'append_benchmark_data');
３：自动加载的过滤器
这里我们需要修改：Smarty.class.php文件里面的autoload_filters　这个变量，格式如下：
var $autoload_filters = array('output' => array('append_benchmark_data'));

以下就以一个过滤　源文件中的注释代码的过滤器来说明一下怎么写　过滤器插件：
include_once('libs/Smarty.class.php');
$smarty = new Smarty;
function remove_html_comments($source, &$smarty)
{
// remove any html comments from the template source, even
// if they span multiple lines
return preg_replace('/<!--.*-->/Ums', '', $source);
}
$smarty->register_prefilter('remove_html_comments');
$smarty->load_filter('output', 'trimwhitespace');//加载这个过滤器是为了去掉空行，这过滤器是smarty自带的
$smarty->display('remove_comments.tpl');

这样我们就可以去掉网页原代码里面的一些　注释　和　空行，这样就可以稍微减少点网络传输量，增强一点用户的体验。

我们还可以编写过滤器　来　压缩网页文件　，　或过滤、高量网页中的默写词汇。

PHP 模板
对于那些希望在模板中纯粹写PHP的人员来说，Smarty提供了一个php的选项，纯PHP和有以下几个不同的地方：

PHP模板将不进行编译，直接被引擎调用
PHP模板将不具备任何安全属性
Smarty默认不开启PHP模板，可以$smarty->allow_php_templates=true来打开
如果你想使用php模板，只需要使用php资源类型

$smarty->display('php:foo.php');
你还可以在模板里头混合着用

{include file="php:foo.php"}