---
layout: post
title: 《大数据日志录》总结
date: 2016-06-19
---

    最近翻看了《大数据日志录》一书，作者为国内中科院软件所毕业的张俊林博士。该书涵括了大数据平台所涉及的大部分相关系统及核心实现概述，同时
    包括了大数据在机器学习、推荐系统以及搜索引擎等方面的应用。应该说是难得的一本深入理解大数据技术细节的参考书。看完一些章节，觉得自己当初
    看相关论文的时候都没有挖掘到这么细节的东西，只能检讨自己读的不够细了。有些部分相信作者还是通过看源码得来的总结，所以有时候读的觉得一下
    飞过上万行代码，确实很爽。不过纸上得来终觉浅，绝知此事要躬行。有点重要的系统可能还是得自己去都源码才能理解的更深入。这里主要是简要总结下
    各个章节所涉及到的开源系统。
    
    1. 第一章
       - consistant hash
       - range partition (B+ tree)
    2. 第二章
      - 2PC
      - vector clock
      - Paxos
      - Raft
    3. 第三章
      - Bloom Filter
      - Skiplist
      - LSM tree
      - Merkle hash tree
      - Snappy and LZSS
      - cuckoo hash
    4. 第四章
      - Mesos
      - YARN
    5. 第五章
      - chubby
      - Zookeeper
    6. 第六章
      - PB and thrift
      - Avro
      - Kafka
      - Gossip
    7. 第七章
      - Chukwa
      - Scribe
      - Databus
      - Wormhole
    8. 第八章
      - GFS
      - HDFS
      - HayStack
      - Erasure Code
    9. 第九章
      - RAMCloud, Redis, Membase
    10. BigTable, PNUTS, Megastore, Spanner
    11. Mapreduce, DAG (Drya, FlumeJava, Tez)
    12. Storm, MillWheel
    13. Hive, Shark, Dremel
    14. Tao, Pregel, Giraph, GraphChi, PowerGraph
    15. Mapreduce, BSP and SSP
    16. LR, ALS-WR, LambdaMART, Spectrum Clustering, DistBelief
    17. Percolator, Kineograph, DryadInc
    
    这么多广泛使用的开源系统，重要的数据结构以及计算模型都在这里做了归纳总结，所以这本书真的是费了作者不少功夫的，虽然自己读过其中部分
    论文，但还没见过这么集中总结归纳过的，对于研究和学习都有很好的指导作用。
      
