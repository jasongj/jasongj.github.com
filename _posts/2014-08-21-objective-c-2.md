---
layout: post
title: "Objective学习2"
categories: ios
- 
tags: ios,objective-c
- 


---
### 类别Category

Category常用来定义实例方法和类方法，

	@interface UIColor (AAPLApplicationSpecific)
	
	+ (UIColor *)aapl_applicationGreenColor;
	
	+ (UIColor *)aapl_applicationBlueColor;
	@end
	
	@implementation UIColor (AAPLApplicationSpecific)

	+ (UIColor *)aapl_applicationGreenColor {
    	return [UIColor colorWithRed:0.255 green:0.804 blue:0.470 alpha:1];
	}	
	@end
	
`+`代表类方法   `-`代表实例方法

我们扩展了UIColor类，然后直接调用其类方法

	[UIColor aapl_applicationBlueColor];
	
category并不常用来定义属性，因为它不会自动生产getter和setter方法

当我们需要对一个类只添加方法时，使用category简单而且有效对类扩展的方式

**Category的用途**

1. 将类的实现代码分散到多个不同的文件和框架中。

2. 创建对像以后方法的前向引用。

3. 向对象添加非正式协议（informal protocol）。



	
### 类扩展Extension
---
XYZPerson.h 文件
.h文件里面定义的属性和方法均为public
	
	@interface XYZPerson : NSObject


XYZPerson.m 文件


此时XYZPerson类扩展于NSObject








你可以把块代码当作参数传递给方法
	[task beginTaskWithCallbackBlock:^{

` (void (^)(void))`定义了一个无参数无返回值的block

	- (void)beginTaskWithCallbackBlock:(void (^)(void))callbackBlock;
	
	- (void)beginTaskWithCallbackBlock:(void (^)(void))callbackBlock {



参考文章
---
[iOS设计模式——Category](http://blog.csdn.net/lovefqing/article/details/8289851)
[iOS的category和protocol](http://www.2cto.com/kf/201402/280727.html)
[iOS中block的探究](http://www.cocoachina.com/newbie/basic/2012/0718/4462.html)