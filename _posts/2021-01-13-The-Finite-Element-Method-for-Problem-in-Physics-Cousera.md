---
layout:     post
title:      有限元分析基础课程-Cousera
subtitle:   
date:       2021-01-13
author:     Zeyuan
header-img: img/Finite-Element-Analysis-Zeal-CAD.png
catalog: true
tags:
    - 有限元分析
    - FEM
---
- 这里是一个目录
{:toc}

# The Finite Element Method for Problem in Physics - Cousera

这是什么？
这是来自Cousera的有限元分析课程：The Finite Element Method for Problems in Physics， University of Michigan
教师：Krishna Garikipati, Ph.D.

# Unit 1: Linear, elliptic PDE in 1D Elasticity, heat conduction and mass diffusion

## 1.1-1.2 Intro linear elliptic PDE

### e.g. Typical problem - 1D

- 1D heat conduction at steady state
- 1D mass diffusion at steady state
- 1D elasticity at steady state

### Problem case

![image-20210113133153713](https://tva1.sinaimg.cn/large/008eGmZEly1gmm0a2khkhj30yl082afa.jpg)

一根木棍，长度L，左端固连，右端自由。

- $u_g$: x = L处的指定位移 OR t: x = L处的指定拉力
- f: 力分布函数

Find u(x):(0,L) -> R, (0,L) is open interval

Given $u(0) = u_0, u_g \ or \ t$, f(x)

#### Problem formulation

![image-20210113142106626](https://tva1.sinaimg.cn/large/008eGmZEly1gmm1p8462dj31fs0o0k96.jpg)

#### Boundary condition

- u(0), u(L).两端已知。Dirichlet boundary condition

- $\sigma(L) = t $Neumann boundary condition $\Rightarrow (Eu_{ix})_{x = L} = t$, from constitutive relation . 

**For elasticity**: Dirichet boundary condition is called the **displacement boundary condition** and Neumann boundary condition is called the **traction boundary condition**. 

## 1.3 Boundary condition（空间） $\neq$ Initial condition(时间)

<img src="https://tva1.sinaimg.cn/large/008eGmZEly1gmm25yo9hqj30nk05ugob.jpg" alt="image-20210113143710161" style="zoom:50%;" />

### Dirichlet or Neumann?

x = 0, we have Dirichlet b.c.s (boundary conditions), but at x = L, we have either Dirichlet or Neumann

2 situation:

**a) Dirichet b.c.s at x = 0 and x = L**

**b) Dirichlet b.c at x = 0, Neumann b.c at x = L.**

We do not consider both Neumann b.c.s at x = 0 and x = L. 

> 当前，我们只能解决一端是固连的问题（至少有一个Dirichet条件）。原因在于：稳态。steady steate

Consider **Neumann** b.c.s at both ends:
$$
\sigma(0) = Eu_{ix}|_{x = 0} = t_0\\
\sigma(L) = Eu_{ix}|_{x = L} = t_L
$$
Consider u(x) satisfies Neumann b.c.x & DE: $\frac{d\sigma}{dx}+f = 0$ :
$$
\frac{d(Eu_{ix})}{dx}+f = 0
$$
but $u(x) + \bar u$  is also a solution. ($\bar u$ = constant, du/dx = 0), u(x) is not unique

> 想象这个木棍在匀速前进，显然所有的点在局部位移的基础上还有一个大的总体位移，且两端还是满足受力条件。因此想要得到唯一解，必须知道其中一端的位移，比如固连的情况。

Neumann b.c.s alone can be specified for the time-dependent elasticity problem.(Hyperbolic pole differential euaiton)

### Body force f(x), forcing function

$$
\frac{d\sigma(x)}{dx}+f(x) = 0, in(0,L)
$$



forcing function in other pdes.

e.g.

垂直悬挂的木棒，或者处于加速中的木棒<img src="https://tva1.sinaimg.cn/large/008eGmZEly1gmm2ry7nfrj310o09qaen.jpg" alt="image-20210113145817396" style="zoom:50%;" />

