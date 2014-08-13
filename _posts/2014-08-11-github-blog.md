---
layout: post
title: "如何使用jekll在github上建立blog"
description: ""
category: git 
tags: [git,blog,github]
---


### 1.创建Repository

在 [https://github.com](https://github.com)上创建名为
jasongj.github.com的资源库

### 2.安装Jekyll-Bootstrap

	git clone https://github.com/plusjade/jekyll-	bootstrap.git jasongj.github.com
	cd jasongj.github.com
	git remote set-url origin git@github.com:jasongj/	jasongj.github.com.git
	git push origin master

过几分钟后你[http://jasongj.github.com](http://jasongj.github.com)你就可以访问你的blog了。

### 3.安装jekyll
	$ git clone https://github.com/plusjade/jekyll-bootstrap.git
	$ cd jekyll-bootstrap	//进入blog的目录
	$ jekyll serve			//启动jekyll服务器

访问[http://localhost:4000](http://localhost:4000)就可以在本地查看你的blog

---
### 安装jekyll
	$ gem install jekyll
	$ cd jasongj.github.com 
	$ jekyll serve
	
---
### 写文章或者创建页面

	$ rake post title="Hello World"		//创建名字为hello world的文章
	$ rake page name="about.md"			//创建一个新的页面
	$ rake page name="pages/about.md"	//创建一个嵌套页面
	
	$ rake page name="pages/about"
	# this will create the file: ./pages/about/index.html
	
### 发布所写的文章

	$ git add .
	$ git commit -m "Add new content"
	$ git push origin master
	

参考文章

[Jekyll QuickStart](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)



