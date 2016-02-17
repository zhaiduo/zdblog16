---
title: Swift精要
tags:
  - swift
id: 2081
categories:
  - APP
  - MAC
---

前提：
＊ 没有 main 主函数，类似于js
＊ 不用换行分号
＊ let 是常量 var 是变量 ：指定类型
＊ ()用法
＊ ［］表示数组, 字符串只能用双引号 “”。 ［ ：］ 表示关联数组
＊ for in 同js
＊ if 必须是布尔条件，必须要有{}
＊ var name:String?="adam"
* if let name 来检测常量name是否赋值成功 name ＝ nil 将会失败
* for i in 0..<4{}
* func test(a:String,b:UInt) -> (Int,Int){return (1,2)}
* func test(b:Int...)  b is an array
* func inside func is OK, like js. Also return func as value

func test(b:Int...) -> (Int -> Int){
    func hh(x:Int) -> Int{
        var c=0
        for m in b{
            c+=m*m+x
        }
        return c
    }
    return hh   //(Int -> Int)  => hh
    //return hh(x)  Int => hh(x)   //注意区别，返回带参数，还是不带
}

var hhh=test(1,2,3)
hhh(3)

* 闭包
var numbers=[1,2,3]
numbers.map({
    (number:Int) -> Int in
    let a=3*number
    return a
})
简写：／／省略类型和返回
var test=numbers.map({ number in 3*number })
＊类 Class
class subpage:page{
    var mmm:Int=0
    var kkk:Int{
        get{
            return 1;
    }
        set{
            mmm=newValue
    }
    }
    init(){
        super.init()
        self.name="subOK"
    }
    override func sayHi() {
        print("subHi")
    }
}
var nnn=subpage();
* enum 枚举 rawValue如果是整数，只需初始化第一个，xcode6.1有效
＊ struct 结构体 总是被复制，而class是被引用
* protocal 协议可以被类、枚举、结构体扩展
＊ extension 可以扩展数据类型Int等
＊ generics 泛型

  