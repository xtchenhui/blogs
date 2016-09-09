---
date: 2016-09-09
title: Scale Memcached at Facebook
---

The property of workload decided the choose of memcached in Facebook to speedup read performance. 
##Three levels of scaling
1. Cluster Level:
  many feature is enabled in the memcache client, such as serialization,compression, request routing, error handling and request batching.
  Also there is an auxiliary configuration system to update available server information.
  * problem: too many fetch request in each web page request
  * solution: construct DAG of these data requests to identify groups of data items which could be fetched concurrently. 
  
  * problem: UDP or TCP?
  * solution: get request via UDP to reduce overhead, set and delete via TCP for reliability
  
  * problem: incast congestion
  * solution: use a sliding window mechanism to control outstanding requests. client receives response, then sent next request.
  
  * problem: stale sets and thundering herds
  * solution: assign lease token for each set operation in every 10s,get requests within 10s after one lease token assigned, will be waiting
  for a short of time to get the renewed data.
  
  * problem: different data sets have different access frequency and latency cost
  * solution: seperated pools to store different kind of data items. one pool for small data but high frequency, one pool for infrequency 
  keys but high cost for database access,one special pool for specific application, one general pool for any other data items
  
  * problem: avoid hot spots in the memcache server pool
  * solution: replication of certain category of keys which will be fetched simultaneously by many clients that one server can not handle.
  replication is better than key space dividing, because it could help sharding the high volume requests.
  
2. Region Level:
3. Inter-Region Level:
