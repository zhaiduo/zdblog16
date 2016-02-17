---
title: Fun with AS3
id: 558
categories:
  - Flash
tags:
---

Function Returns a Function
appendExclamation("actionsnippit")("dot")("com")("is")("live");
function appendExclamation(str:String):Function{
  trace(str + "! ");
  return appendExclamation;
}

var e:String = "addEventListener";
stage[e]("click", function():void{
	trace("clicked", arguments[0]);
});

stage.addEventListener(MouseEvent.CLICK, onStageClick);
function onStageClick(evt:MouseEvent):void {
	trace("clicked", evt);
}

DisplayObject describeType()
for each(var prop:String in describeType(DisplayObject).factory.accessor.@name){
	trace(prop);
}

for (var i:int = 0; i<4; i++){
	this["phase"+i]();
}
function phase0():void{
	trace("phase 0");
}
function phase1():void{
	trace("phase 1");
}
function phase2():void{
	trace("phase 2");
}
function phase3():void{
	trace("phase 3");
}

function cubicBezier(x1:Number, y1:Number, x2:Number, y2:Number,
						  x3:Number, y3:Number, x4:Number, y4:Number, resolution:Number=.03):void {
	var b:Number,pre1:Number,pre2:Number,pre3:Number,pre4:Number;
	for (var a = 0; a <1; a+=resolution) {
		b=1-a;
		pre1=(a*a*a);
		pre2=3*(a*a)*b;
		pre3=3*a*(b*b);
		pre4=(b*b*b);
		canvas.setPixel(pre1*x1 + pre2*x2 + pre3*x4 + pre4*x3 ,
						 pre1*y1 + pre2*y2 + pre3*y4 + pre4*y3, color);
	}
}

shapes_arr.sortOn("width", Array.NUMERIC);

setProps(s, {x:100, y:100, scaleX:2, scaleY:2, rotation:45});
with(s) x = 100, y = 100, scaleX = 2, scaleY = 2, rotation = 45;

 // don't call recursive(), use setTimeout instead
setTimeout(recursive,0);