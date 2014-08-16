---
layout: post
title: "快速入门Objective-C"
category: iOS
tags: [Objective-C,ios]


---

## 头文件.h

首先是头文件，后缀是以 .h头文件，这个文件定义了class的基本结构，有点类似一个类模板，定义class的结构信息

头文件部分

	#import <目录/头文件.h> //代表只引入系统库的类的头文件
	#import "目录/头文件.h" // 代表默认从当前路径下搜索是否存在对应的头文件，如果不存在，则从系统库里面

---	

## 属性 property
	
类定义以及成员变量定义部分，框架

		@property  NSString *firstName;	@property  NSString *someString;
	@property (getter=isFinished) BOOL finished;


+ `property`表示对象所拥有的属性

编译后自动产生Get和Set方法

	NSString *firstName = [somePerson firstName];
		[somePerson setFirstName:@"Johnny"];
	
使用更方便的`Dot syntax`点语法等同于上面

	NSString *firstName = somePerson.firstName;
		somePerson.firstName = @"Johnny";
+ `property`使用下划线前缀访问实例变量
	下滑线前缀使你清楚的知道你使用的实例变量而不是本地变量		- (void)someMethod {		    NSString *myString = @"An interesting string";		    _someString = myString;		}

	也可以使用self效果一样

		- (void)someMethod {		    NSString *myString = @"An interesting string";		    self.someString = myString;		  // or		    [self setSomeString:myString];		}
+ `property`自定义实例变量名称
	书写方式，使用`synthesize`关键字，
	
		@implementation YourClass		@synthesize propertyName = instanceVariableName;		...		@end
		例如：
			@synthesize firstName = ivar_firstName;
		属性称为`firstName`，你可以通过`firstName`和`setFirstName:`访问器方法或者使.形式的访问方法来访问。但是这个实例还有一个备份称为`ivar_firstName`也可以用来来访问`firstname`。
		> 注意如果你使用`@synthesize`但不使用任何具体的实例变量名称
	>	@synthesize firstName;	> 实例变量将于属性名相同，称为**`firstName`**而没有下划线
+ 不用`property`定义实例变量
	如果你想定义自己的实例变量，可以直接把它加在`interface`和`implementation`的大括号中，如下
			@interface SomeClass : NSObject {
				NSString *_myNonPropertyInstanceVariable;		  }		... 		@end
					@implementation SomeClass {		      NSString *_anotherCustomInstanceVariable;		}		... 		@end
		NOTE:
		编译器会在任何情况下自动的synthesize实例变量。如果你实现了属性的 getter 和 setter访问器，或者是readonly的getter。这种情况下编译器将不会自动的实现实例变量，如果你还需要使用实例变量，必须手动实现。				@synthesize property = _property;
			
+ `property`的属性
	**atomic**	默认属性,表示对对象的操作属于原子操作，但是**并不意味着线程安全**
	
	**nonatomic** 不是原子操作，不支持多线程访问安全，但是访问性能高，所以nonatomic比atomic访问更快
	
	
	**readwrite** 默认的属性，表示可以对对象进行读和写，会生成对象相应的setter和getter方法
		**readonly** 表示只允许读取对象的值，只会生成对象的getter方法
		**strong** 默认属性，不要形成抢引用循环
		**weak** 弱引用，其值会在对象被释放后自动设置为nil。
	
	**unsafe_unretained** 一些 Cocoa and Cocoa Touch类无法使用weak引用时，可以使用`unsafe_unretained`代替
	
			**assign** 默认类型,setter方法直接赋值，而不进行retain操作
		**retain** setter方法对参数进行release旧值，再retain新值。
		**copy** setter方法进行Copy操作，与retain一样
#### retain和copy的区别
参考[文章][retain和copy的区别]
实例：
	@interface XYZObject : NSObject	@property NSObject *implicitAtomicObject;          // atomic by default	@property (atomic) NSObject *explicitAtomicObject; // explicitly marked atomic	@end
	
---
参考文献

[Object C初学学习笔记(1)](http://www.cnblogs.com/aigongsi/archive/2012/04/07/2436070.html)

[Programming With ObjectiveC](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/ProgrammingWithObjectiveC.pdf)

[IOS变量的property属性设置和意义总结](http://blog.csdn.net/pingchangtan367/article/details/14000315)

[@property](http://baike.baidu.com/view/5028218.htm)

[retain和copy的区别][retain和copy的区别]

[retain和copy的区别]:http://c.gzl.name/archives/339 "retain和copy的区别"