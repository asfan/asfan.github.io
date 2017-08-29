---
layout: post
title: Linux下各软件参数查看
category: LNMP
tags: Linux
keywords: linux
description: linux cmd params check
---

####学习背景

涉及到软件安装的时候，总需要查看已有软件包所处状态，本文纯属经验备忘。

####参考资料  

暂无

####正文

1. 查看当前linux版本（centOS6.5）：

		uname -a
		more /etc/issue
		cat /proc/version
		more /etc/redhat-release
		
2. nginx查看编译参数：
		
		your_application_path/nginx -V
		
	nginx查看读取的conf文件
		
		your_application_path/nginx -t
		
3. apache查看编译参数:

		cat your_build_path/apache2/build/config.nice

4. 查看php编译参数：

		your_application_path/php -i | grep configure
		
5. 查看mysql编译参数：

		cat your_application_path/mysql/bin/mysqlbug"|grep configure
		
6. 查看redis配置参数：

		#查看-c参数后的文件内容
		ps aux | grep redis
		
		

		

		
