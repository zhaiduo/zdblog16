---
title: Obj-C初学的几个要点
tags:
  - Obj-C
id: 1789
categories:
  - MAC
---

打算复习一下Objective-C，再学习了一下[Try Objective-C](http://tryobjectivec.codeschool.com/)，总结它讲的一些要点。

NSNumber相加要换成NSUInteger:
NSUInteger higgiesAgeInt = [higgiesAge unsignedIntegerValue];
NSLog(@"Higgie is actually %lu years old.", higgiesAgeInt );

初始化：
NSString *emptyString = [[NSString alloc] init];
NSString *copy = [[NSString alloc] initWithString:otherString];

**Block**
void (^logMessage)(void) = ^{
  NSLog(@"Hello from inside the block");
};

void (^sumNumbers)(NSUInteger, NSUInteger) = ^(NSUInteger num1, NSUInteger num2){
  NSLog(@"The sum of the numbers is %lu", num1 + num2);
};

**Class示例**
####MyFirstObjcClass.h
@interface MyFirstObjcClass : NSObject{
    NSString *_othervalue;
}
@property NSString *firstName;
@property (readonly) NSString *lastName;
- (void) changeLastName:(NSString *)newLastName;
- (MyFirstObjcClass *) initWithFirstName:(NSString *)firstName
                      lastName:(NSString *)lastName;
@end

####MyFirstObjcClass.m
#import "MyFirstObjcClass.h"
@implementation MyFirstObjcClass
- (MyFirstObjcClass *) init;
{
    NSLog(@"Cool, a new class is being initialized");
    _firstName = @"Duo";
    _lastName = @"Zhai";
    return [super init];
}
- (MyFirstObjcClass *) initWithFirstName:(NSString *)firstName
                      lastName:(NSString *)lastName;
{
   _firstName = firstName;
   _lastName = lastName;
   return [super init];
}
- (void) changeLastName:(NSString *)newLastName;
{
  _lastName = newLastName; //下划线开头的Class方法内部变量
}
@end

实例化：
MyFirstObjcClass *person = [[MyFirstObjcClass alloc] initWithFirstName:@"Duo" lastName:@"Zhai"];