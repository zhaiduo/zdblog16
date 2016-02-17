---
title: swift
tags:
  - 苹果
id: 1929
categories:
  - Coding
---

苹果官方的称法：Swift是一种全新的可以代替Cocoa和Cocoa Touch的脚本编程语言。

总体感觉。

Swift is a data-oriented coarse grained scripting language that supports dataset typing and mapping, dataset iteration, conditional
branching, and procedural composition.

“func hasAnyMatches(list: [Int], condition: Int -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(numbers, lessThanTen)”

摘录来自: Apple Inc. “The Swift Programming Language”。 iBooks. https://itunes.apple.com/WebObjects/MZStore.woa/wa/viewBook?id=881256329