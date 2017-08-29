---
layout: post
title: YAF框架
category: 学习
tags: yaf框架&编辑
keywords: yaf
description: yaf框架编译，优化&扩展开发
---

###学习背景
微博落地鸟哥的yaf框架，使用c extension开发，专注业务。

###参考资料  

- [《Yaf(Yet Another Framework)用户手册》](http://www.laruence.com/manual/)

 

###正文
先标记一个小坑：  

	注意yaf版本与php版本的对应：
		实测yaf-2.2.8	=> php-5.6
		最新版yaf对应	=> php-7.2

####PHP扩展安装步骤
正常php扩展安装步骤如下（yaf也是同样的步骤）：
	
	/path/to/phpize
	./configure --with-php-config=/path/to/php-config
	make
	#可以增加一步
	make test
	sudo make install









 

