---
layout: post
title: zk学习笔记
category: 学习
tags: paxos
keywords: paxos zookeeper
description: 熟悉paxos算法，活用zookeeper工程
---

###背景
分布式系统固有的一致性问题，paxos算法提供了经过实践验证的精妙解法（可见分布式系统的一致性原理与实践）。在最佳实践中包括google的chubby：使用了带租约的paxos算法，而yahoo根据paper实现了开源组件zookeeper，协议也使用了paxos的变种ZAB协议。其中，相关的协议包括不限于：raft,ViewStamp,ZAB都是paxos的工程实践。

---

###参考资料
- [《paxos》](https://github.com/bigbully/Dapper-translation/blob/master/dapper%E5%88%86%E5%B8%83%E5%BC%8F%E8%B7%9F%E8%B8%AA%E7%B3%BB%E7%BB%9F%E5%8E%9F%E6%96%87.pdf)
- [《如何浅显易懂地解说Paxos的算法？》](https://www.zhihu.com/question/19787937)
- [《分布式一致性原理、Paxos算法与Zookeeper的ZAB协议、Zookeeper使用介绍》](http://www.voidcn.com/article/p-zltmqxdk-tr.html)
- [《ZooKeeper Recipes and Solutions》](https://zookeeper.apache.org/doc/r3.4.9/recipes.html#ch_recipes)

---

###正文
- Paxos算法 （略，参考资料）
- ZK PHP/Golang client使用
- ZK 最佳实践(PHP Golang实现) 

---