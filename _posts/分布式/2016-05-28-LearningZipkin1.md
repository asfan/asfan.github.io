---
layout: post
title: zipkin系统学习1（zipkin安装）
category: DS
tags: 
keywords: zipkin trace
description: 关于zipkin系统的搭建，组成，原理
---

####学习背景
上半年的时候，信誓旦旦的启动了5个技术项目，但由于自己管理上的原因，导致2个月过去，其中2个核心的项目都没有实质性进展，继去年的流式分发系统后，已经是第二次了。基于这种背景，准备以一到两周的集中时间完成对trace系统第一期的开发。

####参考资料  

- [twitter zipkin 官网](https://twitter.github.io/zipkin/index.html)
- [zipkin github](https://github.com/openzipkin/zipkin)

####正文

#####测试环境安装（2016-05-25 github版本）
**需要注意**：

- github版本，是因为作者大人[Adrian Cole](https://github.com/adriancole)更新example文件夹下测试代码的频度确实有些快。
- docker-composer工具我并没有成功的使用起来，没有深究的原因在于后续会对相关内容进行定制化修改，docker部署并不满足后续发展需求。

**安装步骤**：  

1. github上拉取源码：

		git clone https://github.com/openzipkin/zipkin.git
2. 更新环境依赖包（centOS6.5 x64）：  
		java    (jdk1.8.0_91）  
		scala   (scala-2.11.6)
3. 依次run以下进程：

		./bin/query
		./bin/collector
		./bin/web
		#生成例子数据
		./bin/tracegen
	ps: 由于俺们有长城，在执行编译过程中，有走https到twitter找pom文件的逻辑，统统被墙了。服务器翻墙略费劲儿，尝试curl了一下http链接发现可以请求到，于是修改安装脚本./build.gradle第234行为：  
	
		maven { url 'http://maven.twttr.com/' }
其实只是把s去掉罢了～

执行成功后去浏览器访问相关ip+端口号即可,bootstrap的布局，页面略有些不友好，需要进一步学习。灌完测试数据后的测试界面为(选一张比较酷的图）：

![General preferences pane](/public/img/zipkin/test1.png)






	
	
	
	
	
	
	