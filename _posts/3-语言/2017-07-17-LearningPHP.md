---
layout: post
title: PHP闲言碎语
category: 语言
tags: PHP tricks
keywords: PHP PHP7
description: 闲话PHP
---

####学习背景
作为PHP工程师，不断加深对语言本身的理解，这里记录一些语言的新特性，与OO之间的联系。

####正文

1. 关于php interface 和abstract class的使用场景？  
   - [stackoverflow-讨论接口与抽象类的使用场景](https://stackoverflow.com/questions/1814821/interface-or-an-abstract-class-which-one-to-use)
   - 首先写接口/抽象类的程序员定义其他用户如何使用该抽象。如果只限定子类实现的方法，则使用接口；如果除了限定子类实现哪些方法，还提供了通用工具接口，则使用抽象类。一种普遍存在的最佳实践就是：当你拿不准一种抽象该使用抽象类还是接口的时候，设计一个接口，然后用一个抽象类implement它。
   - 具体到语言细节：
   		- interface：可以用implement实现，也可以用extends继承，所有方法必须是public，类实现interface必须实现所有的public function，并且参数表保证一致。关于常量，接口常量与类常量的设计完全相同，唯一不同的就是无法被子类/接口覆盖。
   		- abstract：当类用此关键字修饰时候，则不可以实例化；如果类中有1个或以上抽象方法则该类必须定义为抽象类；
   		- 区别：一个子类可以实现多个接口，但只能继承一个抽象类；并且接口里面的属性不可以被实现TA的类覆盖；

   
2. php foreach是否能保证array的顺序？
	- [鸟哥博客]()
	- 结论就是和key的顺序无关，只与array中元素插入的顺序，先插入的先遍历。称之为线性遍历。而for循环以$i的赋值为基础，和$i的算法相关了。

3. php中 $this self static 都代表那个类？