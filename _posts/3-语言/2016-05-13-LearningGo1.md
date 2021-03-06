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
- golang中不存在类、对象的概念，因此是一个基于并发模型的语言，并不是完整的面向对象编程。替代方法是以type为中心，定义类型方法，也可以达到部分对象的功能，好处是代码组织上有迹可寻，同一类的用同一个type+一组类型方法即可。同时，类型方法支持值传递和引用传递，以面向对象的角度看，会在编程过程中，大部分使用引用传递。
- 以package来组织代码，名为main的package是整个项目的入口，其余的package以库的形式起作用，被import引进相关的package。目前理解的是，go为了做到环境无关，把相关的库都静态编译成一个可执行文件，因此编译出来的go程序明显体积都大于代码，这是编译类语言中比较少见的。
- main方法作为程序的入口，在main之前执行的为init方法（每个源文件可以且只可以包含一个init方法），是一个现代的用法，更贴近于我们在业务开发中为流程准备的hook。因此该方法在业务上也通常用来：1. 程序执行之前对环境、数据进行检验或者修复，保证程序状态正确；2. 在main程序之前调用后台执行的gorutine。目前看，对init的使用要慎重，因为顺序不可控，起码在ide（gogland）里是如此。
- go语言对格式、引入代码是否被使用的校验是很严格的，如果引入了package、定义了变量，但在程序执行流程中没有使用，则编译无法通过。
- go为强类型语言，因此在值类型变换时要注意精度的问题，数据类型转换可能会有精度损失。fmt.Printf打印各种类型需要熟记，例如bool类型的%t，golang结构独有的%v、%+v等等。输入输出可以参考一下这篇[blog](http://www.cnblogs.com/golove/p/3284304.html)。可以对字符类型做Type操作，但这个操作和别名不完全相同，因为无法调用原有类型的函数：Type TZ int 将int类型一个命名为TZ。
- 区分make和new，首先这两个关键字都是golang语言预留的用于内存分配的原语，
- 4种引用类型：map slice channel interface 其中前三者都常用make初始化。
- go get = git clone + go install 因为gw问题使用：http_proxy=http://localhost:8123 go get来安装所需的包
- go官方所有的源码包都托管在github上，因此，理论上去github上都可以下载
- 同一代码块内的defer，后声明先执行

---

####踩小坑
- 有时使用go build | go install时候编译不过，清除一下pkg库。TODO：梳理一下golang编译过程文件之间的依赖关系。
- 注意包之间的引用，不能直接用包名来作为形参引用，在编译过程会被拒绝。
- **网络**和**并发**是golang的两大核心优势，因此我们在学习过程中也要持续关注语言的应用场景。golang被称为互联网的c语言，在需要写server的时候，使用起来很方便。而实际上一个server需要关注的也就是这两部分，在并发中golang提供的channel和goroutine是**并发**相关的两大feature。
- 使用yaml配置文件解析包的过程中，yaml的key只能用小写，如果混合大小写，则不能识别
- 

---
####想知道
- 在gogland里面定义一个叫producer.yml的文件，结果没有语法提示 pro.yml就行？！为了个啥？









