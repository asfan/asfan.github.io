---
layout: post
title: PHP基础（1）
category: PHP
tags: PHP
keywords: PHP foundation
description: php基础训练
---

####学习背景
　　基础不牢靠，自己也没有底气。要做一个好的phper，基础是根本。第一篇从手册入手，之前老大说要看5遍，诚不欺我。
****



####参考资料
- [《php手册》](https://secure.php.net/manual/zh/) 

****

####正文

- 纯php文件省略结尾标志：  
防止include或者require该文件时，加入不应该有的空行或者换行符号。psr-2风格要求纯php一定要做到：  
		
		1. 省略结尾标志；
		2. 文件末尾空一行；
		3. 换行符必须是LF；
- 检验一个参数是否为整数，有个小坑：  

		$a = '5';
		is_init($a); //false
		$a = 'xxx';
		is_init(intval($a)); //true
		
		//合理的写法可能是：
		is_numeric($a) && (intval($a) - $a == 0)
		
- string转int，从string的位置0开始向后到不是number的位置为止:  

		//测试
		$x = 'hahah';
		$y = '3haha';
		$z = 'ha5ha';
		
		var_dump(intval($x));//0
		var_dump(intval($y));//3
		var_dump(intval($z));//0

- 类型转换

















