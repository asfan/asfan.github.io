---
layout: post
title: Socket编程
category: 网络编程
tags: socket linux select poll epoll
keywords: 套接字 socket编程 UNIX系统
description: 对socket相关编程进行一下复习，并且review一下常用linux下io多路复用的系统函数
---

###学习背景
socket是web编程基础中的基础，从本科到硕士再到工作，都曾经应用过相关知识。但工作这三年多来，一直都在忙于业务，没机会去care基础知识，造成和人沟通时候似是而非，非常没有专业性。因此在有时间的前提下，首先review一下这部分内容。web server编程不会浅尝辄止，学习的路径为：linux进程状态 -> linux socket -> select poll epoll原理 -> libevent -> redis/php-fpm/nginx。这里会多写几篇，把相关内容解释清楚。

---

###参考资料
- [《LINUX进程状态分类》](https://github.com/tobegit3hub/understand_linux_process/blob/master/process_basic/status.md)
- [《PTRACE分析》](https://idea.popcoeunt.org/2012-12-11-linux-process-states/)

---

###正文

---
