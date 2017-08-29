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

4. trait关键字的特性，应用的场景、最佳实践？
   - 当有一段代码在类之间被copy paste的时候，可以多想想trait关键字；
   - 打破php单继承的限制（后续在设计模式中确定应用场景）5.4之后支持；但是使用的是多个class组合的方式，因此trait本身使用不需要继承，使用use关键字即可；
   - 类中use trait的时候，同名方法的优先级是：类中function > trait中function > 父类中function 
   - use用在trait中时在class内部，use用在namespace时，在class定义外部文件头部，替代include、require
   - 当类中用多个trait的时候，trait内有同名方法会报fatal error。解决方法是显示的使用insteadof确定一个具体的那个方法
   - trait支持属性、方法、静态方法
   - trait中的属性，类无法定义同名
5. php overloading（重载）的含义？
   - php重载与c++等的重载（override）概念不同，指的是动态创建类的属性与方法，而传统重载指的是同名、不同参数列表函数。
   - php实现重载的方法是使用magic methods实现，所有方法都必须是public，方法的参数都不可以通过引用传递。这些magic method 包括：__set __get __iset __unset __call __callStatic

6. final只可以修饰类和方法，继承一个final class会报fatal error
   










