---
layout: post
title: awk语言学习
category: 工具
tags: study
keywords: awk shell
description: awk语言学习
---

####学习背景

####参考资料
- [《awk程序设计语言》](https://book.douban.com/subject/1876898/)

####正文

基础结构-模式动作语句：`pattern { action }`

标准命令行：
		
		awk 'patern { action }' <data_file>

从文件中读取awk命令：

		awk -f <cmd-file> <data_file>