---
layout: post
title: "Markerdown learning"
description: "Markerdown"
category: Markerdown
tags: [Markerdown]
---
{% include JB/setup %}


### 代码例子 

	function test(){
		console.info("test");
	}

---

### 区块引用 

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的

> This is the first level of quoting.
>> This is test.
>> Back to the first level.

---

### 列表

无序列表使用星号、加号或是减号作为列表标记：

* 一
* 二

有序列表

1. Bird
2. McHale
3. Parish

如果要在列表项目内放进引用，那 ’>‘ 就需要缩进

*	A list item with a blockquote:
	> This is a blockquote
    > inside a list item.


---

### 区段元素

#### 链接

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.


---

参考式的链接是在链接文字的括号后面再接上另一个方括号

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"
----------


隐式链接标记功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号，如果你要让 "Google" 链接到 google.com，你可以简化成：

[Google][]

[Google]: http://google.com/

### 强调

使用反引号 (```)

Markdown 使用星号（*）和底线（_）作为标记强调字词的符号，被 * 或 _ 包围的字词会被转成用 `<em>` 标签包围，用两个 * 或 _ 包起来的话，则会被转成 `<strong>`，例如：

*single asterisks*

**double asterisks**


### 图片



### 表示自动链接

<http://www.diguage.com/>

---

### 反斜杠

Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用 `<em>` 标签），你可以在星号的前面加上反斜杠：

\*literal asterisks\*

	\   反斜线
	`   反引号
	*   星号
	_   底线
	{}  花括号
	[]  方括号
	()  括弧
	#   井字号
	+   加号
	-   减号
	.   英文句点
	!   惊叹号


---