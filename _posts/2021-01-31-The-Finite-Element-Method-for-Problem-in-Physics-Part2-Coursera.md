---

layout:     post
title:      有限元分析基础课程Part2-Coursera
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

### H1  norm

H1 Hibert norm
$$
||v||_1=\sqrt{\frac{1}{m(\Omega)^{1/n_{sd}}}\int_\Omega (v^2+m(\Omega)^{\frac{2}{n_{sd}}}(v_{,x})^2)dx}
$$
(A more general norm is called Sobolev norm.)

We can also extend this to Hn norm by including the first n derivatives.



H0 norm:
$$
||v||=\sqrt{\frac{1}{m(\Omega)^{1/n_{sd}}}\int_\Omega v^2dx}
$$
H0 norm is equivelant to L2 norm.

### Energy norm of v

The energy norm of v is
$$
(\int_\Omega v_{,x}Ev_{,x})^{1/2}
$$
---- strain enenrgy of v

### Equivalence of norm:

We can choose the constant c1, c2 to bound the energy norm from below and above by the H1 norm.
$$
c_1||v||_1 \leq (\int_\Omega v_{,x}Ev_{,x})^{1/2} \leq c_2||v||_1
$$

### Inner product notation

The L2 inner product of $w$ and $f$ :
$$
(w,f):=\int_\Omega wfdx
$$
Bilinear form notation:
$$
a(w,u):=\int_\Omega w_{,x}Eu_{,x}dx
$$

> when w=u, it is the energy norm

## 5.03. Consistency of the finite element method

Recall the weak form
$$
\int _\Omega w_{,x}Eu_{,x}Adx = \int _\Omega wfAdx+w(L)tA \\
$$
Abstract notation:
$$
a(w,u)=(w,f)+(w,t)_L \tag{A}
$$
Finite dimensional weak form:
$$
a(w^h,u^h)=(w^h,f)+(w^h,t)_L \tag{C}
$$
Note that (A) hold for all $w \isin \mathcal V \supset \mathcal V^h$, so it holds for $w=w^h$:
$$
a(w^h,u)=(w^h,f)+(w^h,t)_L \tag{B}
$$
Compare (B) and (C):
$$
a(w^h,u^h-u)=0
$$
Here we define the error e:
$$
e := u^h-u
$$

### Consistency condition

$$
a(w^h,u)=(w^h,f)+(w^h,t)_L \tag{B}\\
$$

>  Interpretation: $a(w^h,e)=0$ It means that the projection of the error on the space $\mathcal V^h$ is 0. Any error exists is outside of our (working) space.( We have done well in our space ). Any error is orthogonal to $\mathcal V^h$. 

Note: the exact solution also satisfy the finite dimensional weak form. The FEM can recover the exact solution. Not the case for other numerical methods.



