---
layout: post
title: "快速入门Objective-c 2"
description: ""
category: ios
tags: [ios,objective-c]
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
	
	@interface XYZPerson : NSObject  		@property (readonly) NSString *uniqueIdentifier;
	 - (void)assignUniqueIdentifier;	@end
	
XYZPerson.m 文件.m inteface里面定义了私有private属性，	
	@interface XYZPerson ()	@property (readwrite) NSString *uniqueIdentifier;	@end	@implementation XYZPerson	...	@end

此时XYZPerson类扩展于NSObject
### protrol
<ProtocolA,ProtocolB> 代表实现了ProtocolA 和 ProtocolB 协议，这个Protocol和java语言里面的interface意义相同,同时协议分为可选协议和必须实现两中
	@protocol XYZPieChartViewDataSource	- (NSUInteger)numberOfSegments;	- (CGFloat)sizeOfSegmentAtIndex:(NSUInteger)segmentIndex;	@optional    //非必须实现	- (NSString *)titleForSegmentAtIndex:(NSUInteger)segmentIndex;	- (BOOL)shouldExplodeSegmentAtIndex:(NSUInteger)segmentIndex;	@required	- (UIColor *)colorForSegmentAtIndex:(NSUInteger)segmentIndex;	@end
当方法是可选的时候，在调用之前，必须检查方法是否实现
	NSString *thisSegmentTitle;	    if ([self.dataSource respondsToSelector:@selector(titleForSegmentAtIndex:)])		{	        thisSegmentTitle = [self.dataSource titleForSegmentAtIndex:index];	    }协议可以继承其他的协议
	@protocol MyProtocol <NSObject>
	@end### block syntax
Block是iOS4.0+ 和Mac OS X 10.6+ 引进的对C语言的扩展，用来实现匿名函数的特性	^{	     NSLog(@"This is a block");	}
你可以把块代码当作参数传递给方法
	[task beginTaskWithCallbackBlock:^{	        [self hideProgressIndicator];	}];

` (void (^)(void))`定义了一个无参数无返回值的block

	- (void)beginTaskWithCallbackBlock:(void (^)(void))callbackBlock;
	
	- (void)beginTaskWithCallbackBlock:(void (^)(void))callbackBlock {	    ...	    callbackBlock();	}



参考文章
---
[iOS设计模式——Category](http://blog.csdn.net/lovefqing/article/details/8289851)
[iOS的category和protocol](http://www.2cto.com/kf/201402/280727.html)
[iOS中block的探究](http://www.cocoachina.com/newbie/basic/2012/0718/4462.html)
