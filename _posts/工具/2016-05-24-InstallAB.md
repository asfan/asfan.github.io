---
layout: post
title: ab 单独安装
category: 工具
tags: apache ab
keywords: apache ab
description: centOS6.5环境下，独立安装ab工具
---

####背景
一天支持了个在微信朋友圈进行投放的运营小项目，涉及到一些有趣的内容，比如性能调优，以及业务上如何应对平台方的要求标准。比较普适的收益是学习了单独安装ab的方法，毕竟现在简单逻辑的页面，使用nginx还是比较主流的，在此记录一下。

狗哥这边需要快速支持一个接入微信的广告H5。大企鹅作为平台方对二级页面的要求是最少抗1500并发&响应时间少于200ms。看看自己买的8核、16G、50M出口带宽的阿里云ECS，真的是微微一笑，一个静态资源都交给7牛去抗的spa，这种服务器性能真的是没说了（单机，咱也不谈什么高可用了）。

过程中值得记忆的内容包括：
1. 由于nginx+fpm的主流结构，处理了不安装apache，单独安装ab的问题；
2. 微信分享相关的model(在token的暂存处理上，依然有很大的优化空间，单纯使用本地文件，不适用于多机、分布式) + 页面组件 + 为了分享处理的公众号的安全域名备案；
3. 本次使用的一些服务器端性能调优内容。

####参考资料

####正文
#####ab的单独安装（脱离apache环境）
Apache Benchmark(简称ab) 简单易用，通常作为入门级的性能测试工具使用。而ab作为apache的组件，往往是在安装了apache之后单独编译、使用的工具。但在nginx逐渐成为主流服务器的当前，为了ab而安装apache实在太重，所以记录一下单独安装ab的流程：

- ab运行需要依赖apr-util包，安装命令为：  

		yum install apr-util
		
- 安装依赖 yum-utils中的yumdownloader工具（运行yumdownloader命令查看工具是否安装）：

		yum install yum-utils
			
- 安装完相关依赖后，去工作目录执行以下操作：

		mkdir -p /opt/workspace/
		cd /opt/workspace/
		mkdir ./ab
		cd ./ab
		yum install yum-utils.noarch
		yumdownloader httpd-tools*
		rpm2cpio httpd-*.rpm | cpio -idmv
		
#####ab的使用
- 常规使用：
     
		/opt/workspace/ab/usr/bin/ab -n 200000 -c 500 http://testurl

- 系统fd不够的情况，在系统层面把fd个数开大：
		
		ulimit -n 65535
			
	这里有需要注意的问题，ab在压测过程中有其局限性，如本次项目，微信要求跳转二级页最低并发500，200ms返回，完全依赖ab的测试数据。实际测试20000次并发500的请求无论怎么优化（会单独写nginx+fpm优化相关内容）响应时间都在400ms左右，此时奇怪的事情发生了，将总请求次数提升到200000次，平均响应锐减到100ms左右。虽然有服务器程序需要预热等原理解释，但是现象还是比较诡异，后续会以源码阅读的方式看看ab平均响应时间的相关代码～
	
	
	
		


