---
layout: post
title: Go语言学习（1）
category: 语言
tags: Go
keywords: go1.6
description: 学习go语言记录第一篇
---

###背景
内部推出了一个比赛，主题是在限定条件的服务器环境下，如何实现一个最快的echo server。技术方案当然是不设限制，由于在去年下半年涉及了一部分流式分发系统的设计内容，以及组内陈杰大牛的一直推广，对go产生了一些兴趣。所以最终选择了go1.6方向的调研，十分幸运的是近来有些时间去学习一下相关知识。

--



###参考资料
- [《go语言编程》](https://book.douban.com/subject/11577300/)
- [godoc](http://localhost:6060)

--

###正文

####语言特性
- golang中不存在类、对象的概念，因此是一个并发模型的语言，并不是面向对象
- 以package来组织代码，名为main的package是整个项目的入口，其余的package以库的形式起作用，被import进相关的package。
- main方法作为程序的入口，在main之前执行的为init方法（每个源文件可以且只可以包含一个init方法），该方法通常用来：1. 程序执行之前对环境、数据进行检验或者修复，保证程序状态正确；2. 在main程序之前调用后台执行的gorutine
- go语言对格式、引入代码是否被使用的校验是很严格的，如果引入了package、定义了变量，但在程序执行流程中没有使用，则编译无法通过。
- go为强类型语言，因此在值类型变换时要注意精度的问题。fmt.Printf打印各种类型需要熟记，例如bool类型的t%。输入输出可以参考一下这篇[blog](http://www.cnblogs.com/golove/p/3284304.html)。可以对字符类型做Type操作，但这个操作和别名不完全相同，因为无法调用原有类型的函数：Type TZ int 将int类型一个命名为TZ，


####踩小坑
- 有时使用go build | go install时候编译不过，清除一下pkg库。TODO：关于编译之间的依赖关系。










