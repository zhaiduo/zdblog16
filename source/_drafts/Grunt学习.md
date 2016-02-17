---
title: Grunt学习
id: 2030
categories:
  - webapp
tags:
---

http://www.gruntjs.org/docs/getting-started.html

安装：npm install -g grunt-cli

npm init命令会自动创建一个基本的package.json文件。

{
    "name": "my-project-name", // 项目名称
    "version": "0.1.0", // 项目版本
    "devDependencies": { // 项目依赖
        "grunt": "~0.4.1", // Grunt库
        "grunt-contrib-jshint": "~0.6.0", //以下三个是Grunt内置任务
        "grunt-contrib-nodeunit": "~0.2.0",
        "grunt-contrib-uglify": "~0.2.2"
    }
}

添加Grunt和Grunt插件到一个现有的package.json中最简单的方式就是使用npm install <module> --save-dev命令。

一个Gruntfile由下面几部分组成：
**"wrapper"函数(包装函数)**
module.exports = function(grunt) {
    // 在这里处理Grunt相关的事情
}

**项目和任务配置**
大多数Grunt任务所依赖的配置数据都被定义在传递给grunt.initConfig方法的一个对象中。

**加载的Grunt插件和任务**
// 加载提供"uglify"任务的插件
grunt.loadNpmTasks('grunt-contrib-uglify');

**自定义任务**
// 一个非常基础的default任务
    grunt.registerTask('default', 'Log some stuff.', function() {
        grunt.log.write('Logging some stuff...').ok();
    });
定义的项目特定的任务可以不定义在Gruntfile中；它们可以定义在一个外部.js文件中，然后通过grunt.loadTasks方法来加载。

常用任务：
grunt-contrib-uglify 插件的uglify任务被配置用于压缩一个源文件 Minify files with UglifyJS
grunt-contrib-concat Concatenate files.
grunt-contrib-jshint Validate files with JSHint.
grunt-contrib-htmlmin Minify HTML.
grunt-contrib-imagemin Minify PNG and JPEG images.
grunt-contrib-sass Compile Sass to CSS.
grunt-contrib-stylus Compile Stylus files to CSS.
grunt-init-gruntfile Create a basic Gruntfile with grunt-init.
grunt-contrib-compress Compress files and folders.
grunt-contrib-qunit Run QUnit unit tests in a headless PhantomJS instance.
grunt-init-jquery Create a jQuery plugin with grunt-init, including QUnit unit tests.

大多数的人都知道foo/*.js将匹配位于foo/目录下的所有的.js结尾的文件, 而foo/**/*.js将匹配foo/目录以及其子目录中所有以.js结尾的文件

在这个函数里面我们以初始化我们的配置(任务配置)对象：
grunt.initConfig({
});
pkg: grunt.file.readJSON('package.json');
module.exports = function(grunt){
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json')
    });
}