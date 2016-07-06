---
layout: post
title: Http 基础知识（1）
category: 基础
tags: http interview
keywords: http RFC2616
description: http基础
---

####学习背景
http/https协议是互联网开发中最常用的协议，有着自己独特的魅力。本篇会记录一些http/https的基础内容，对于应届同学和实习生同学而言，可能会涉及到一些面试时被问到的问题。

####参考资料  

- [《HTTP权威指南》](https://book.douban.com/subject/10746113/)

这个的读书笔记之前有记录，视心情整理一番再说。

####正文
#####定义 - from [wikipedia](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)
> 超文本传输协议（HyperText Transfer Protocol）是互联网上应用最为广泛的一种网络协议。设计HTTP最初的目的是为了提供一种发布和接收HTML页面的方法。通过HTTP或者HTTPS协议请求的资源由统一资源标识符（Uniform Resource Identifiers，URI）来标识。

#####常见的误解
- http/https只能运行在tcp/ip七层即应用层？  
*尽管TCP/IP协议是互联网上最流行的应用，HTTP协议中，并没有规定必须使用它或它支持的层。事实上，HTTP可以在任何互联网协议上，或其他网络上实现。HTTP假定其下层协议提供可靠的传输。因此，任何能够提供这种保证的协议都可以被其使用。因此也就是其在TCP/IP协议族使用TCP作为其传输层。*

#####状态码
- 1xx 消息——请求已被服务器接收，继续处理
- 2xx 成功——请求已成功被服务器接收、理解、并接受
- 3xx 重定向——需要后续操作才能完成这一请求
- 4xx 请求错误——请求含有词法错误或者无法被执行
- 5xx 服务器错误——服务器在处理某个正确请求时发生错误

常见包括：

- 100 continue 继续
- 200 success 成功
- 301 Permanently Moved 永久移动
- 302 Temporarily Moved 暂时移动
- 400 Bad Request 请求错误（client)
- 403 Forbidden 禁止访问
- 404 Not Found 找不到
- 500 Internal Server Error 服务器内部错误
- 502 Bad Gateway 网关错误
- 503 Service Unavailable 服务不可用

实际开发中关于http的小tips：  
a. 自定义http头的传递问题：  
	在设计系统时，方案是利用http头传递trace相关的id参数等，但在实际使用php curl进行传递时下游并没有获取相关参数。定位发现是下游机器以nginx作为自己的前端服务器，在未配置的情况下，将http自定义头放弃了。可以发现的是nginx与apache不同，apache是在自己的进程内对php进行处理，配合http头解析不需要做额外工作。但nginx是依赖fpm处理php逻辑，有socket交互过程，因此只有在参数中显示配置相关参数才能正常传递。











 

