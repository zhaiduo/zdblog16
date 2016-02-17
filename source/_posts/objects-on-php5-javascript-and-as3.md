---
title: 'Objects on PHP5, Javascript and AS3'
tags:
  - AS3
  - PHP5
  - javascript
  - 比较
id: 285
categories:
  - 技术研究
date: 2008-07-18 10:58:41
---

PHP5, Javascript and AS3都有面向对象(Object)一说，但它们之间也有着不小的差异。作为我比较喜欢的3种编程语言，我很想把它们放在一起，做一个横向的粗浅的比较。
**AS3 (Action Script 3.0)**
在AS3里每个对象都是类，这个类可以被看作是对象的模板或蓝图。类似于Java，融合了多种语言的特点。不支持嵌套类和私类。感觉太靠近Java，太过严谨的语法让制作Flash的时候失去了一些乐趣，多了一些沉闷。毕竟FLASH不只是AS。
> 最简单的AS3 Class例子
> package mypackage
> {
> public class MyClass
> {
> public var textVariable:String = "some default value";
> public var numericVariable:Number = 17;
> public var dateVariable:Date;
> public function myMethod(param1:String, param2:Number):void
> {
> // do something with parameters
> }
> public function MyClass() // constructor
> {
> textVariable = "Hello there!";
> dateVariable = new Date(2001, 5, 11);
> }
> }
> 
> class MySubClass extends MyClass
> {
> private var numericVariable2:Number = 1;
> override public function myMethod(param1:String, param2:Number):Number
> {
> // do something with parameters
> }
> }
> 
> }
**Javascript **
[Javascript](http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Guide:Details_of_the_Object_Model)是一种基于原型(prototype)的语言，就像一个具有初始值得模板，任何对象都可以作为另一个对象的原型。灵活度较高，比较随意。目前最满意的就是它了。这里有一个我写的[浮动层的例子](/wp-content/data/floating_div.html)，很喜欢这种编程方式：）。
> Object.prototype.inObj = 1;
> function A()
> {
> this.inA = 2;
> }
> A.prototype.inAProto = 3;
> B.prototype = new A;            // Hook up A into B's prototype chain
> B.prototype.constructor = B;
> function B()
> {
> this.inB = 4;
> }
> B.prototype.inBProto = 5;
> x = new B;
> document.write(x.inObj + ', ' + x.inA + ', ' + x.inAProto + ', ' + x.inB + ', ' + x.inBProto);
> [source](http://mckoss.com/jscript/object.htm)
**PHP5**
PHP5借鉴了Java2的对象模型，类型指示弱于AS3。PHP5向OOP靠近是应该的，也是必然的。
> class SimpleClass
> {
> public $var = 'a default value';
> public $public = 'Public';
> protected $protected = 'Protected';
> private $private = 'Private';
> 
> public function displayVar() {
> echo $this-&gt;var;
> }
> 
> function __construct() {
> print "In constructorn";
> $this-&gt;name = "MyDestructableClass";
> }
> 
> function __destruct() {
> print "Destroying " . $this-&gt;name . "n";
> }
> }
> $instance = new SimpleClass();
> $assigned   =  $instance;
> $reference  =&amp; $instance;
> $instance-&gt;var = '$assigned will have this value';
> $instance = null; // $instance and $reference become null