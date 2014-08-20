---
layout: post
title: "linux命令问题集合"
categories: linux
- 
tags:
- 


---
### 修改root密码
---
系统恢复后，无法使用root登录，可以使用以下方法重新设置root密码

	sudo passwd
	Enter new UNIX password:
	Retype new UNIX password:
	然后在用新设置的密码登录即可
	

### 批量杀进程

	ps -ef|grep wen|grep -v grep|cut -c 9-15|xargs kill -9

运行这条命令将会杀掉所有含有关键字`wen`的进程



* `ps -ef` 是linux里查看所有进程的命令。
* `grep wen` 的输出结果是，所有含有关键字`wen`的进程。
* `grep -v grep` 是在列出的进程中去除含有关键字"grep"的进程。
* `cut -c 9-15` 是截取输入行的第9个字符到第15个字符，而这正好是进程号PID。
* `xargs kill -9` 中的 xargs 命令是用来把前面命令的输出结果（PID）作为`kill -9`命令的参数，并执行该命令。`kill -9`会强行杀掉指定进程。

其它类似的情况，只需要修改"`grep wen`"中的关键字部分就可以了。

另一种方法，使用awk

	ps x|grep gas|grep -v grep |awk '{print $1}'|xargs kill -9



参考文献
---
[如何重设Ubuntu的登录密码及root用户登录系统](http://13521308103.iteye.com/blog/1930322)
[Linux下批量杀掉 包含某个关键字的 程序进程](http://www.cnblogs.com/lichkingct/archive/2010/08/27/1810463.html)