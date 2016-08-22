---
layout: post
title: Dynamo Design Summary
date: 2016-08-22
---


Dynamo is published by Amazon as a key-value storage implementation. It contains many design principles for the distributed system. 
I use the SNAKE analysis method to disect the inter details of this system.

1.**Scenario**: The objective of Dynamo is used for high-availability and frequent key/value fetching situations, such as the shopping cart service in Amazon website. Customer should be able to change his/her shopping cart at any time even with one datacenter outages
or some server goes offline. So this kind of high-availability request the designer to scarifice some data consistency to guarrantee
the availability, which is the AP in the "cap" theory.

2. **Needs**: Just like Amazon, it has hundreds of million peak requests during the shopping festival season, also it demands 99.9% request should be finished in 500ms. 
