---
layout: post
title: Linux下文本处理工具
category: LNMP
tags: Linux sort 
keywords: text processing
description: linux cmd params check
---

###学习背景

作为后端同学，很多时候会涉及到轻量级的文本处理。如：不熟悉代码中查找某一段，切割、排序得出新的结果文件，文件内数据格式化后输入脚本...  
对windows接触不多，暂时还是以linux、mac等类unix系统命令行为主。awk因为其特殊性，单独写了一篇[《awk语言学习》](/2015/12/29/LearningAWK.html)

###参考资料  

暂无

###正文

1. **sort:**
	- 简述：顾名思义是个排序的工具，man会说的很详细，列举一下常用的情况。
	- 用法：sort -u （去除重复行） | sort -r （默认升序，修改为降序）| sort -o （专用于重定向到原文件，等于是对源文件排序的解决方案）| sort -n （以数字排序，解决11排在2之前这种情况）|  sort -k <列的排序数字> -t <单行分割符> （以分隔符分割后的第k列排序）

2. **comm：**
	- 简述：comm是个相对简陋的取文件交并集工具
	- 用法：comm -1 -2 a b 取a、b文件的交集，我们可以把a、b分别看作两个集合：1为A-B的差集 2为B-A的差集 3为A∩B的交集，在哪个集合前加“-”就是去掉这部分