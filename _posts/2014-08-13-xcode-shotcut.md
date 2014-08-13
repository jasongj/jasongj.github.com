---
layout: post
title: "xcode技巧"
description: ""
category: xcode
tags: [xcode,ios]
---
{% include JB/setup %}

### xcode快捷键

`Command + Shift + Y` 显示/隐藏调试区的快捷键是

`Command 1~ 8`: 跳转到导航区的不同位置

`Command 0` :显示/隐藏导航区

`Command Alt 1~ 6`:在不同检测器之间跳转

`Command Alt 0`: 显示/关闭工具区.

`Control Command Alt 1~4`: 在不同库之间跳转

`Control 1~ 6`: 在Jump bar的不同标签页的跳转。

`Command + Shift + O` 呼出Open Quickly

`Command + Control + J` 跳转到光标指向的类

`Command + J` 转换 assistant editor 的焦点

`Command + Option + J` 跳至 filter bar

---
### xcode行为

单屏,通过隐藏工具板以及设置输出窗口占据整个调试区使输出窗口的有效区域最大化,设置如下

![image](/assets/20140813/single_monitor_debug.png)

然后运行程序,然后观察Xcode,看它是不是按照你的命令在执行。

![image](/assets/20140813/single_monitor_debug.gif)

当程序暂停的时候,你可能也想改变Xcode的行为,到Running栏下的Pauses事件,然后改变其设置,向下面这样:

![image](/assets/20140813/PausesBehavior.png)


自定义行为—设置一个快捷键。当被触发的时候,它使Xcode转变到我指定的为下一次开发而优化的布局,名为`Dev Mode`。我们可以通过点击`Behavior`偏好设置的左下角的`+`,然后将其取名为`Dev Mode`,双击`Dev Mode`右边的`Command (⌘)`符号然后输入`Command shift .`来定义一个快捷键

![image](/assets/20140813/hotkey_assignment.gif)

接下来为该事件设置相应动作:

![image](/assets/20140813/DevModeBehavior.png)

现在,只要你按下`Command shift .`就会触发上面设置的动作,即出现一个相同的整洁的开发界面


---
### 代码片段 Code Snippets

下面可能是你使用单例模式的常用代码模板

	+ (instancetype)sharedObject {
	  static id _sharedInstance = nil;
	  static dispatch_once_t oncePredicate;
	  dispatch_once(&oncePredicate, ^{
	    _sharedInstance = [[self alloc] init];
	  });
	  return _sharedInstance;
	}

+ 用快捷键`Command Option Control 2`来打开代码片段库，在代码片段库中你会看到默认的包含在Xcode中的代码片段库。
+ 选中整个`+sharedObject`方法，将其拖拽到代码片段库中。

![image](/assets/20140813/snippet.gif)

新创建的代码片段将会在代码片段库的最底部，你可以将其拖拽到任何你想拖拽的文件当中去，让我们来尝试一下。

双击刚刚新建的代码片段，然后点击edit.弹出的视图非常使用，实际上它们都很重要，所以做个简短的解释。

+ Title and Summary：代码片段库中该代码片段的名字和简述
+ Platform and Language:代码片段匹配的平台和编程语言
+ Completion Shortcut:在Xcode中输入的快捷键
+ Completion Scopes:代码片段作用的范围，这对于保持代码片段库整洁来说十极好的。

向下面一样填充里面的属性：

![image](/assets/20140813/SS-Snippet.png)

#### 令牌
当你加入令牌时，代码片段将会变得非常强大，因为它允许你在片段中标记代码，而不需要硬编码。通过使用Tab键使得他们非常容易修改，就像自动补全一样。

在片段中仅仅只要输入`<#TokenName#>`就可以添加一个令牌，创建一个令牌使用`shared<#ObjectName#>`替代`sharedObject`，看起来像这样：


![image](/assets/20140813/SS-Snippet2.png)

点击`Done`来保存该片段，然后来用用它。

---

[参考文献](http://www.raywenderlich.com/72021/supercharging-xcode-efficiency)