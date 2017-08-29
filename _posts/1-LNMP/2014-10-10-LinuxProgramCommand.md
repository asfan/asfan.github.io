---
layout: post
title: Linux下各个组件的控制命令
category: LNMP
tags: nginx php-fpm apache mysql memcached redis
keywords: 
description: Linux下常用web server组件的控制命令
---
####背景
作为开发工程师，相关组件的控制命令的熟悉十分重要。但是由于使用的时间不连续，场景也多变，因此经常忘记。所以这里就当作一个备忘录

####参考资料
[nginx服务器重启命令、关闭](http://www.cnblogs.com/apexchu/p/4119252.html)  

####正文
1. nginx控制命令：

		nginx -s reload  #修改配置后重新加载生效
		nginx -s reopen  #重新打开日志文件
		nginx -t -c /path/to/nginx.conf #测试nginx.conf文件是否符合语法标准
		nginx -s stop     #快速停止nginx
		nginx -s quit     #完整有序的停止nginx

		ps -ef | grep nginx
		kill -QUIT 主进程号     #从容停止Nginx
		kill -TERM 主进程号     #快速停止Nginx
		pkill -9 nginx         #强制停止Nginx
		nginx -c /path/to/nginx.conf	#启动nginx
		kill -HUP 主进程号		#平滑重启nginx
		
2. php-fpm控制命令：
   php5.3之后 去掉了php-fpm自带的start|stop|reload等命令，直接使用信号量。
   
   		ps aux | grep php-fpm
   		#确认master进程号
   		kill -USR2 [pid] #完成重启
   		kill -INT [pid]  #彻底杀死进程
   	


