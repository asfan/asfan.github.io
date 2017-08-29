---
layout: post
title: Redis安装
category: 网络编程
tags: redis
keywords: 
description: redis应用之安装篇
---

####学习背景
REDIS作为目前互联网领域常用的内存数据结构存储服务，在weibo内部很早就开始使用，并广泛部署。是我司最常用的队列、缓存替代服务，在业务方正逐步替代MC和MCQ，作为缓存和队列使用。而在应用开发过程中，一直都只是使用动态平台提供的实例，对其安装、部署和维护并没有很深的了解。在自己做一些小应用的情况下，恰好学习一下。

####参考资料
- [《redis官网》](http://redis.io/download)

####正文
各个平台下有相对成熟的包管理器，可以快速安装服务端实例。如linux发行版中常用的yum、apt-get，mac中的home brew、port以及windows下的...(sorry 不太了解 囧）。但经过进一步学习，我们会发现redis本身是一个非常简单的C程序，源码编译并不复杂，由于之后继续会阅读redis源码，所以记录一下mac环境下的源码编译：  

	#官网下载redis源码
	git clone https://github.com/antirez/redis.git ./
	#进入根文件夹编译完成
	make & make test
	#redis会依赖一些库，但这些库的更新不会随着重新make而更新，因此在依赖库（jemalloc,lua,hiredis,）发生变化时
	make distclean



