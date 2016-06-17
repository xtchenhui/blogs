---
layout: post
title: Paxos Summary
date: 2016-06-17
---

# Paxos Summary

- 通过log副本一致性来保证存储数据的一致性
>只需要大多数(大于N/2+1)节点服务正常，即可保证服务可用，避免慢的节点影响整个请求响应速度。

- 整个过程可以看成是2PC协议的一个升级版本

- phase 1
...* 倡议者proposer向大多数接受者发送prepare请求，附带倡议编号n
...* 接收者收到带有倡议编号n的prepare请求，做如下判断
......* if n<(前面响应过的请他请求的编号) 不做回应
......* else 将接受过的最大编号请求中的倡议编号及value返回给倡议者

- phase 2
... * 倡议者接到大多数接收者对prepare请求的响应，则向这些接收者发送accept请求，带有倡议编号n及其value。倡议值是其接收的响应中具有最大倡议编号的倡议值。如果没有收到任何接收者的Accept请求倡议内容，则可以任意赋值给倡议值value.
... * 如果接收到收到了倡议编号为n的Accept请求，则接收者接受此请求,除非在此期间接收者响应过具有比n更高编号的Prepare请求。

关于学习者获得倡议值得方式有很多，可参见paxos协议的详细介绍文档。

Raft协议对Paxos进行了改进，使其更易理解和实现。主要的变化有如下几个方面：
1. 将一致性协议分成了三个阶段：leader selection, log replication and safety 
2. 将paxos的p2p模式改造为Master-slave模式。在leader selection阶段还是p2p模式，在leader选出来之后，log复制及其安全性则完全采用master-slave方式
了。
