---

layout:     post
title:      有限元分析基础课程-Coursera
subtitle:   
date:       2021-01-31
author:     Zeyuan
header-img: img/bigstock-Abstract-Futuristic-Stripe-Lin-294971134.jpg
catalog: true
tags:
    - 有限元分析
    - FEM
---
- 这里是一个目录
{:toc}
# Unit5 : Analysis of the finite element method

## 5.01-5.02. Norms

Consider the finite-dimensional trial solution , $u^h$, also called the "finite element solution".

The trial function is continuous over$\Omega$，but its derivative is not continous over $\Omega$ but only over $\Omega^e$.
$$
u^h \isin \mathcal C^0(\Omega)
$$
And u^h is also in H1: (n_sd is the dimension of the space)
$$
u^h \isin H^1(\Omega)\\
\int_\Omega ((u^h)^2+m(\Omega)^{2/n_{sd}}(u_{,x}^h)^2 )dx<\infin
$$
![image-20210131150024569](https://tva1.sinaimg.cn/large/008eGmZEly1gn6vzokbqtj31hz0u04qp.jpg)

