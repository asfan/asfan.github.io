---
layout: post
title: Linux服务运维工具
category: LNMP
tags: Linux
keywords: Linux free top
description: linux服务器运维工具
---

####背景
服务器环境搭建与运维属于后端工程师知识体系中的底层内容，需要扎实的基础与巩固。而且在环境运维过程中，往往能够加深我们对与操作系统，进、线程模型的理解。


####参考资料
[[blog]《Linux命令工具 top详解》—— 大CC](http://www.cnblogs.com/me115/p/3842081.html)

####正文

1. free  
	查看本机内存情况，

2. top  

- linux下性能分析工具。关键字：**实时**，**CPU**，**内存**，**执行时间**  
- Linux（centOS下）执行top：  
![top default command window](/public/img/linuxtop/top_default.jpg)
- 进入交互界面：
	- P cpu排序
	- M 内存排序
	- c 折叠/打开全部命令行