---
layout:     post
title:      Summary-chapter1
subtitle:   
date:       2020-05-25
author:     Zeyuan
header-img: img/ibmpower9supercomputer.jpg
catalog: true
tags:
    - ST7
---
- 这里是一个目录
{:toc}

# Summary Chapter1

HPC: High Performance Computing

- **Flops** ：**floating point operations per second**

Supercomputer结构：

一般来说，一个supercomputer由一个个的cluster组成，cluster是一群PC的集合，或者说是node的集合，node里面包含了很多的处理器，每个处理器由很多的core组成。

- cores, with vetor units
- Multi-core processor
- Multi-core PC/node
- Multi-core PC cluster
- Super- Computer
- hardware accelerators

Some HPC or Large Scale PC-clusters exist in some Clouds
 But no *SuperComputer* available in a cloud

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3uwkdrsaj313k0u07c7.jpg" alt="image-20200524152314118" style="zoom: 33%;" />

3种经典的并行结构：

- **Shared-memory machines** 好多implementation，不同成本，不同速度<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3uxscpnij30tq0mqgwo.jpg" alt="image-20200524152423834" style="zoom:33%;" />
- **Distributed-memory machines**（cluster）速度和成本取决于interconnection。all supercomputers are **clusters** with a **hierarchical architecture**<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3uy8clcgj30ae070q38.jpg" alt="image-20200524152504278" style="zoom:50%;" />
- **Distributed Shared Memory** **machines (DSM):**<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gf3uyx8yztj30uc0aiaeu.jpg" alt="image-20200524152543055" style="zoom:50%;" />



![image-20200524153242427](https://tva1.sinaimg.cn/large/007S8ZIlgy1gf5fdxs7ljj30og06oabc.jpg)

在自己处理器RAM里的数据速度 > 别的处理器的RAM > 其他node

Fault tolerance

Energy Consumption
