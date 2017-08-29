---
layout: post
title: Git&GitHub使用
category: 学习
tags: Git GitHub
keywords: Git
description: Learning to use Git&GitHub
---

####学习背景
记得12、13年的时候，小师妹说过她本科的孩纸们都在玩github，作为一个嵌入式开发工程师，真心不屑一顾了一番，然后继续自己貌似高大上的google research，真是每天都在鄙视昨天sb的自己。找工作时候，阴差阳错成为了互联网大潮中一朵小小浪花，天天search、clone、pull，真正发现了git的美，特此记录一下常用的场景。

####参考资料  

- [廖雪峰Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)


###正文
####个人的一些理解：

- git&github的区别  
	git：		一个单机的版本控制软件，利用fs完美的解决了版本问题(没有远端中心节点的概念，保持c2c的结构)。  
	github：	作为开放源码的中心节点服务，最大的优势是为广大码农提供一片交流空间，而加入这片空间的工具是git，可以说是个以码交友的client。

#####个人常用的场景：  

- 使用他人项目：

		#从github上下载全部信息的代码
		git clone xxx   
	
		#从github更新代码  ＝ fetch + merge
		git pull
	
- 维护自己的代码：
		
		#修改提交到本地（无论是new or modify，一定要先add）
		git add xxx
		git commit xxx -m 'xxx'
	
- 创建远程repository  
  在github上创建，是可视化界面，因此不多说，主要讲一下几种命令行的情况：
  		
  		#远端github已建立repository的情况，在本地文件夹
  		git init
  		
  		#绑定远端分支（origin是远程分支的一个名字）
		git remote add origin https://github.com/xxx/xxx.github.io.git
		
		#远端更新(拉取远端代码合并，有冲突就解决)
		git pull origin master
		
		#远端上传（推送本地版本代码入github repository）
		git push origin master
		
- 一些查看命令  
  
  		#查看代码改动、分支情况
  		git status
  		
- 远端repository相关操作
	
		#查看所有远程库
		git remote -v
		
		#重命名远程库
		git remote rename <original name> <current name>
		
		#删除远程库
		git remote rm
		
- 分支相关操作  
	git的分支是超轻量级，并不是拷贝一份代码的副本，而是利用指针，记录变化。
	
		#创建新分支(从master拉取一个test分支）
		git checkout -b test master
		
		#查看当前有哪些分支
		git branch
		
		#切换到分支<x>
		git branch <x>
		
- 对比svn的软连接，git提供了submodule命令以帮助使用者快速将其他git项目代码copy到当前项目下，同时利用更新可以随时拿到submodule的最新代码，使用过程如下：

		#在当前git库中增加外部连接（submodule连接）
		git submodule add http://github.com/asfan/test.git ./test
		git commit
		#使用过程中，从远端库上clone下来带有submodule的代码，submodule不会被自动的拉到本地，需要执行以下
		git submodule init
		git submodule update
		# 到相关文件夹下确定一下代码被拉取成功，则ok

- 从github上fork他人项目源代码到自己repository的代码，通常要保持和源代码的同步，此处记录一下操作流程（以自己的yaf为例）：

		# 将自己repo上的remote项目clone到本地
		git clone https://github.com/laruence/yaf.git ./yaf
		# 将他人最新项目代码关联到本地git
		git remote add upstream https://github.com/laruence/yaf.git
		# 合并源代码更新到本地
		git fetch upstream
		git checkout master
		git merge upstream/master
		git push origin master
		
		
		
		
		
		
  		
		
	
	
	
	