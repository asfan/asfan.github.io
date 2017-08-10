---
layout: post
title: mac下运行php环境
category: LNMP
tags: php
keywords: 
description: 在mac环境下运行php
---
####背景
mbp是我的开发工具，php是我的主要使用语言。因此学习在mac环境下php语言的运行就非常有必要了。而由于php是目前mac版本下默认安装的软件，因此在使用上给我们造成一点点困难，需要特殊学习一下。无论是cgi亦或cli模式都是php常用的场景，以下分别描述一下。

####参考资料
暂无
####正文
查看现有mac系统&php版本：

	more /System/Library/CoreServices/SystemVersion.plist
	php -v
	
我的系统版本为10.11.3、php版本为5.5.30。根据手册指导，去下载对应源码（因为pcntrl是官方的extension）。

	wget http://cn2.php.net/get/php-5.5.30.tar.gz/from/a/mirror
	tar zxvf php-5.5.30.tar.gz
	cd php-5.5.30/ext/pcntl/
	phpize && configure && make
	#查看php extension保存目录
	php -i | grep extension_dir
	cp php-5.5.30/ext/pcntl/module/pcntl.so /usr/lib/php/extensions/no-debug-non-zts-20121212/
		
然后在php.ini文件中增加一句：

	#查看生效ini所在文件目录
	php --ini
	vim /etc/php.ini
	#增加一条
	extension=pcntl.so

####补充	
但mac系统在El Capitan版本之后，增加了Rootless机制，即使在root权限下，不能够随心所欲的读写许多系统路径了。也就是说Rootless机制成为对抗恶意程序的最后防线。  
关闭Rootless的方法如下：
	
	#重启mbp，按住Command+R，进入recovery模式，打开terminal
	csrutil disable
	#重启即可，如果需要恢复
	csrutil enable

这个机制是底裤，如果不是十分有把握的情况下，最好还是使能Rootless。




