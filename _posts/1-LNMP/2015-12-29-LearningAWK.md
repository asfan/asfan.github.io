---
layout: post
title: awk语言学习
category: LNMP
tags: study
keywords: Linux awk
description: awk语言学习
---

####学习背景
服务端的开发、运维、测试同学对awk这个神器一定不会陌生，太多次面对一次性的数据分析任务，我们使用awk、sed、comm、sort、uniq等命令行工具纵横捭阖，处理的酣畅淋漓。但使用了一两年，可能还是停留在awk -F的水平，不免有些贻笑大方。当我check组内代码的时候，也出现新来的小伙伴用管道把n个awk暴力连接起来处理问题的略囧局面，因此，有意识的系统化学习awk既是项目需要，也是个人成长诉求。在15年年末稍显轻松的日子里，为自己充充电。

####参考资料
- [《awk程序设计语言》](https://book.douban.com/subject/1876898/)

####正文

基础结构-模式动作语句：`pattern { action }`

标准命令行：
		
		awk 'patern { action }' <data_file>

从文件中读取awk命令：

		awk -f <cmd-file> <data_file>