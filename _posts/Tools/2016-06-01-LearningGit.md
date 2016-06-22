---
layout: post
title: Git&GitHub使用
category: Tools
tags: Git GitHub
keywords: Git
description: Learning to use Git&GitHub
---

####学习背景
记得12、13年的时候，小师妹说过她本科的孩纸们都在玩git，作为一个嵌入式开发工程师，真心不屑一顾了一番，然后继续自己貌似高大上的google research，真是每天都在鄙视昨天sb的自己。找工作时候，阴差阳错成为了互联网浪潮中一朵小小浪花，天天search、clone、pull，真正发现了github的美，特此记录一下常用的场景。

####参考资料  

- [廖雪峰Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)


####正文
#####个人的一些理解：

- git&github的区别  
	git：		一个单机的版本控制软件，利用fs完美的解决了版本问题。  
	github：	作为开放源码的中心节点服务，最大的优势是为广大码农提供一片交流空间，而加入这片空间的工具是git，可以说是个以码交友的client。

#####个人常用的场景：  

- 使用他人项目：

		#从github上下载全部信息的代码
		git clone xxx   
	
		#从github更新代码  ＝ fetch + merge
		git pull
	
- 维护自己的代码：
		
		#修改提交到本地
		git add xxx
		git commit xxx -m 'xxx'
	
- 创建远程repository
		
		
	
	
	
	