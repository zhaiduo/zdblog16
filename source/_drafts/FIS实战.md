---
title: FIS实战
tags:
  - 百度
id: 2046
categories:
  - webapp
---

$ fis install firstblood-demo
install [firstblood-demo@latest]

fis release -d ../firstblood_output
发布到绝对路径

fis release -d /home/work/ouput
# win
fis release -d d:/work/output
使用配置文件的 deploy节点配置 进行发布，此配置可将代码上传至远端

fis release -d remote
以上所有发布规则任意组合使用（一次编译同时上传到多台远端机器 & 项目根目录下的output & 调试服务器根目录 & 本地绝对路径）

fis releaes -d remote,qa,rd,output,preview,D:/work/output

添加 --md5 [level] 或 -m [level] 参数，在编译的时候可以对文件自动加md5戳，从此告别在静态资源url后面写?version=xxx的时代

添加 --lint 或 -l 参数，支持在编译的时候根据项目配置自动代码检查

添加 --test 或 -t 参数，支持在编译的时候对代码进行自动化测试

添加 --pack 或 -p 参数，对产出文件根据项目配置进行打包

添加 --optimize 或 -o 参数，对js、css、html进行压缩

添加 --domains 或 -D 参数，为资源添加domain域名

$ fis install firstblood-conf

add to fis-conf.js

//Step 1\. 取消下面的注释开启simple插件，注意需要先进行插件安装 npm install -g fis-postpackager-simple
 fis.config.set('modules.postpackager', 'simple');

//通过pack设置干预自动合并结果，将公用资源合并成一个文件，更加利于页面间的共用

//Step 2\. 取消下面的注释开启pack人工干预
 fis.config.set('pack', {
     'lib.js': [
         'demo.js',
         'script.js'
     ]
 });

////////////////////
fis release -omp -d ../firstblood_output

fis server start -p 8888

fis server stop

在刚刚的firstblood项目中执行命令：

$ fis release --md5 --optimize --watch

FIS通过插件扩展可以完美的支持模块化的前端开发方案，我们通过FIS的二次封装能力，封装了一个功能完备的纯前端模块化方案pure。接下来就让我们使用pure，体验一下在FIS构建能力的支持下，如何轻松的完成一个高性能的纯前端模块化项目的构建与优化工作。

其次通过浏览两者的脚本文件，我们会发现fis-quickstart-demo的脚本中都添加了 define 包装

define('main', function(require, exports, module){
    //content
});

内部初始化的配置数是：

fis.config.init({
    project : {
        charset : 'utf8',
        md5Length : 7
    }
});

issues:
=================
Error: .uglify-js "return outside of function"

JavaScript does not allow return outside function bodies. Acorn and Esprima both handle this correctly. You should open an issue with UglifyJS about this.

======================================
PT实例

输出目录
//fis release -op -d ./dist
fis.config.set('project.charset', 'utf8');
fis.config.set('project.md5Length', 7);
//fis.config.set('project.include', 'vendor/**');
//fis.config.set('project.fileType.text', 'tpl, js, css');
//fis.config.set('project.fileType.image', 'swf, cur, ico');

路径基于dist目录
fis.config.set('pack', {
    '/js/all.js': [
//        /^/(js|vendor)/(.*.js)/i
//	,
        "/js/jquery-1.11.1.min.js",
		"/vendor/jquery.appear.js",
		"/vendor/jquery.easing.js",
		"/vendor/jquery.cookie.js",
		"/vendor/bootstrap/js/bootstrap.js",
		"/vendor/jquery.validate.js",
		"/vendor/jquery.stellar.js",
		"/vendor/jquery.knob.js",
		"/vendor/jquery.gmap.js",
		"/vendor/twitterjs/twitter.js",
		"/vendor/isotope/jquery.isotope.js",
		"/vendor/owl-carousel/owl.carousel.js",
		"/vendor/jflickrfeed/jflickrfeed.js",
		"/vendor/magnific-popup/magnific-popup.js",
		"/vendor/mediaelement/mediaelement-and-player.js",
		"/js/theme.plugins.js",
		"/js/theme.js",
		"/vendor/rs-plugin/js/jquery.themepunch.tools.min.js",
		"/vendor/rs-plugin/js/jquery.themepunch.revolution.js",
		"/vendor/circle-flip-slideshow/js/jquery.flipshow.js",
        "js2/jquery.validate.min.js",
        "js2/validate-additional-methods.js",
		"/js/views/view.home.js",
		"/js/views/view.contact.js",
        "/js2/md5.js",
        "/js2/common-scripts.js",
        "/js2/login-in-page.js",
		"/js/custom.js"
    ],
	'/css/all.css': [
//        /^/(css|vendor)/(.*.css)/i
//	,
        "vendor/bootstrap/css/bootstrap.css",
		"vendor/font-awesome/css/font-awesome.css",
		"vendor/owl-carousel/owl.carousel.css",
		"vendor/owl-carousel/owl.theme.css",
		"vendor/magnific-popup/magnific-popup.css",
		"vendor/isotope/jquery.isotope.css",
		"vendor/mediaelement/mediaelementplayer.css",
		"css/theme.css",
		"css/theme-elements.css",
		"css/theme-animate.css",
		"vendor/rs-plugin/css/settings.css",
		"vendor/circle-flip-slideshow/css/component.css",
		"css/theme-responsive.css",
		"css/skins/default.css",
		"css/custom.css",
		"css/custom_final.css"
    ]
});

fis.config.merge({
    roadmap : {
        path : [
            {
                //所有widget目录下的js文件
                reg : /^/(js2|js|vendor)/(.*.js)/i,
                //是模块化的js文件（标记为这种值的文件，会进行amd或者闭包包装）
                isMod : false,
                //默认依赖lib.js
                //requires : [ 'lib.js' ],
                //向产出的map.json文件里附加一些信息
                //extras : { author : 'Adam' },
                //编译后产出到 /static/widget/xxx 目录下
                release : '/$&'
            },
			{
                //所有widget目录下的js文件
                reg : /^/(css|vendor)/(.*.)(css)/i,
                //requires : [ 'base.css' ],
                //向产出的map.json文件里附加一些信息
                //extras : { author : 'Adam' },
                //编译后产出到 /static/widget/xxx 目录下
                release : '/$&'
            },
			{
                //所有image目录下的.png，.gif文件
                reg : /^/(css|img|vendor)/(.*).(?:jpg|jpeg|png|gif)/i,
                //访问这些图片的url是 '/m/xxxx?log_id=123'
                //url : '/m/$1?log_id=123',
                //发布到/static/pic/xxx目录下
                release : '/$&'
            },
			{
                reg : /^/(css|img|vendor)/(.*).(?:eot|ttf|woff|svg)/i,
                //访问这些图片的url是 '/m/xxxx?log_id=123'
                //url : '/m/$1?log_id=123',
                release : '/$&'
            },
            {
                //前面规则未匹配到的其他文件
                reg : /.*/,
                //编译的时候不要产出了
                release : false
            }
        ]
    }
});

===============Make

deploy:
	@echo	*************************************
	@echo	Deploy to js/all.js,css/all.css
	@echo	*************************************
	@rm -rf "js/all.js"
	@cp "dist/js/all.js" "js/"

	@rm -rf "css/all.css"
	@cp "dist/css/all.css" "css/"

=============================
fis-plus旧版   fis才是新版
==========================
cd D:Program Filesnodejs
cnpm install -g fis-plus
cnpm install -g lights

demo中包括common和home两个模块，目录结构是这样的：

├── common   //公用资源模块
│   ├── fis-conf.js  //配置文件
│   ├── page     //页面模板目录
│   ├── plugin   //smarty plugin目录
│   ├── static   //静态资源目录
│   └── widget   //模块化组件目录
└── home    //业务模块
    ├── fis-conf.js
    ├── page
    ├── static
    ├── test    //测试数据目录
    └── widget

//进入common模块路径
$ cd common

//编译发布common模块
$ fisp release -c

//进入home模块路径
$ cd ../home

//编译发布home模块
$ fisp release -c

//启动本地server服务
$ fisp server start

//在浏览器中访问页面，看demo效果
http://localhost:8080/home/page/index

=======================================

站点目录结构

业务功能模块化，针对常见的业务模型，抽象出以下层级关系：

站点(site)：一般指能独立提供服务，具有单独二级域名的产品线。如旅游产品线或者特大站点的子站点（lv.baidu.com）。
模块(module)：具有较清晰业务逻辑关系的功能业务集合，一般也叫系统子模块，多个子系统构成一个站点。
页面(page): 具有独立URL的输出内容，多个页面一般可组成子系统。
组件(widget)：能独立提供功能且能够复用的独立资源，它可以是独立的JS、CSS或者是由JS、CSS和页面组成的页面碎片。
静态资源(static)：非组件资源目录，包括模板页面引用的静态资源和其他静态资源（favicon,crossdomain.xml等）。
插件(plugin): 模板插件目录(可选，对于特殊需要的产品线，可以独立维护)。
测试数据(test): 页面对应的测试数据目录。
FIS规范定义了两类模块： common模块与 业务模块。

common模块: 为其他业务模块提供规范、资源复用的通用模块。
业务模块: 根据业务、URI等将站点进行划分的子系统站点模块。

站点整体目录结构示意：

|---site
|     |---common //通用子系统
|     |      |---config //smarty配置文件
|     |      |---page //模板页面文件目录，也包含用于继承的模板页面
|     |            └── layout.tpl
|     |      |---widget //组件的资源目录，包括模板组件,JS组件,CSS组件等
|     |      |     └── menu   //widget模板组件
|     |      |     |    └── menu.tpl
|     |      |     |    └── menu.js
|     |      |     |    └── menu.css
|     |      |     └── ui   //UI组件
|     |      |          └── dialog  //JS组件
|     |      |          |    └──dialog.js
|     |      |          |    └──dialog.css
|     |      |          └── reset //CSS组件
|     |      |               └── reset.css
|     |      |---static //非组件静态资源目录，包括模板页面引用的静态资源和其他静态资源
|     |      |---plugin //模板插件目录(可选，对于特殊需要的产品线，可以独立维护)
|     |      |---fis-conf.js //fis配置文件
|     |---module1 //module1子系统
|     |      |---test
|     |      |---config
|     |      |---page
|     |            └── index.tpl
|     |      |---widget
|     |      |---static
|     |      |     └── index //index.tpl模板对应的静态资源
|     |      |          └── index.js
|     |      |          └── index.css
|     |      |---fis-conf.js //fis配置文件

        ......

路径说明

页面(page)：存放在 模块根目录/page 下，url访问路径为 /模块名/page/页面名，例如path_to_user_module/page/view.tpl，访问url为：/user/page/view。页面静态资源存储的位置为：

tpl ：path_to_module/page/页面名.tpl
 js ：path_to_module/page/页面名.js
css ：path_to_module/page/页面名.css
css组件：一般来说，CSS组件是最简单的组件，它的存储方式为：

#widget目录下的css文件皆为css组件，建议存放在widget/ui目录下
css ：path_to_module/widget/ui/组件名/组件名.css
js组件：支持AMD规范的js组件，js组件存储的方式为：

#widget目录下的js文件皆为js组件，建议存放在widget/ui目录下
js ：path_to_module/widget/ui/组件名/组件名.js
模板组件：存放在 模块根目录/widget 下，每个widget包含至少一个与widget目录**同名**的tpl，同时可以有与widget 同名 的js、css作为其静态资源。组件存储方式为：

tpl ：path_to_module/widget/组件名/组件名.tpl
 js ：path_to_module/widget/组件名/组件名.js
css ：path_to_module/widget/组件名/组件名.css
配置文件(fis-conf.js)：fis配置文件存放在模块根目录下 path_to_user_module/fis-conf.js ，smarty配置文件存放在：

conf：path_to_module/config/模块名/
smarty插件：与smarty插件相关的都存放在plugin目录下，存储位置为：

插件：path_to_module/plugin/
测试数据(test)：fis开发环境允许在本地开发中设置测试数据进行调试，测试数据以页面模板为单位进行组织，其存储方式为：

tpl：path_to_module/page/模块名/页面名.tpl
data：path_to_module/test/page/页面名.json(或php)
组件化