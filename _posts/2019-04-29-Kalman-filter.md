---
layout:     post
title:      卡尔曼滤波器初级教程
subtitle:   观测器的数学模型以及卡尔曼滤波器介绍
date:       2019-04-29
author:     Zeyuan
header-img: img/image737.jpg
catalog: true
tags:
    - 状态观测器
    - 卡尔曼
    - 线性系统
---

# 观测器的一般形式

一般的线性系统的形式：

$\dot x =Ax+Bu $，$y = Cx+Du$

相应的观测器：

$\dot{\hat x} =A\hat x+Bu+K(y-\hat y)$，$\hat y = C\hat x+Du$

写成框图的形式：

![观测器的框图形式](https://tva1.sinaimg.cn/large/007S8ZIlgy1geb94zzdejj31d80ru0yq.jpg)





观测器的误差我们定义为$\dot e_{obs}=\dot x - \dot{\hat x} = (Ax+Bu)-(A\hat x+Bu+K(y-\hat y))=A(x-\hat x)-K(y-\hat y)$

考虑到 $x-\hat x = e_{obs}, y-\hat y = C(x-\hat x)=C e_{obs}$

上式可以写为：$\dot e_{obs}=(A-KC)e_{obs}$

矩阵$A-KC$描述了观测器的动态特征。通过改变K来控制误差函数的衰减率。卡尔曼滤波器提供了一个相对比较好的K的计算方法。

疑问：

- 误差衰减速度是否是越快越好？
- 更快的衰减速度是否意味着更不稳定的状态/

