---
layout: post
title: 网卡监控程序nload安装
category: LNMP
tags: Linux
keywords: nload
description: centOS6.5环境下，独立编译安装nload
---

####背景
年初一个项目，cdn没有上，就进行了推广，导致网卡打满，页面白页的情况。当时用了nload进行监控，感觉不错，能把关键数据展示出来，因此记录一下编译安装过程（C语言编写）。

####参考资料

####正文
#####nload的编译安装
nload是一个实时监控网络流量和带宽使用的**CMD WINDOW**程序，使用两个图表可视化地展示接收和发送的流量，并提供诸如数据交换总量、最小/最大网络带宽使用量等附加信息。在centOS6.5上yum install失效，因此使用以下方法：
	
	yum install gcc gcc-c++ ncurses-devel
	wget http://www.roland-riegel.de/nload/nload-0.7.2.tar.gz
	tar zxvf nload-0.7.2.tar.gz
	cd nload-0.7.2
	./configure
	make & make install
	
最终程序安装在/usr/local/bin/文件夹下的nload程序。

#####使用
	
	#监听eth1网卡设备
	/usr/local/bin/nload eth1
	#监听所有网络设备
	/usr/local/bin/nload -m


#####扩展内容
iptraf
