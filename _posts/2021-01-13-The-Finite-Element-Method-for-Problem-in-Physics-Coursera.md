---
layout:     post
title:      有限元分析基础课程-Coursera
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

# The Finite Element Method for Problem in Physics - Coursera

这是什么？
这是来自Coursera的有限元分析课程：The Finite Element Method for Problems in Physics， University of Michigan
教师：Krishna Garikipati, Ph.D.

# Unit 1: Linear, elliptic PDE in 1D Elasticity, heat conduction and mass diffusion

## Intro linear elliptic PDE

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

- $\sigma(L) = t $Neumann boundary condition $\Rightarrow (Eu_{,x})_{x = L} = t$, from constitutive relation .

> $u_{,x} == \frac{du}{dx}$

**For elasticity**: Dirichet boundary condition is called the **displacement boundary condition** and Neumann boundary condition is called the **traction boundary condition**.

## Boundary condition（空间） $\neq$ Initial condition(时间)

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
\sigma(0) = Eu_{，x}|_{x = 0} = t_0\\
\sigma(L) = Eu_{，x}|_{x = L} = t_L
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

## Strong form of the partial differential equation

### Strong condition

**Strong form formulation:**

Previous pb: find u(x), given $u_0$, $u_g$ (or t), f(x), and the constitutive relation$\sigma = Eu_{,x}$, such that
$$
\frac{d\sigma}{dx}+f = 0, in(0,L)
$$

with Dirichlet b.c.s or Dirichlet+Neumann.

If substuting with constitutive relation:
$$
\frac{d}{dx} (E\frac{du}{dx})+f = 0, in(0,L)
$$

Problem of second derivative. Here is 2 conditions we require:

- We require "strong condition" of "smoothness" on u(x), because the Strong Foem has two spatial derivatives.

- We require the pde to hold pointwice in (0,L)

### An analytic solution

**If E is a constant:**
$$
\frac{d\sigma}{dx}  = -f  \Rightarrow \int_0^y\frac{d\sigma}{dx} dx= -\int_0^y f dx,\ y\isin[0,L]\\
\Rightarrow \sigma(y) - \sigma(0) = -\int_0^y fdx \\
\Rightarrow Eu_{,x}|_y - Eu_{,x}(0) = -\int_0^y fdx \\
\Rightarrow E\frac{du}{dy} = -\int_0^y fdx + E\frac{du}{dx}|_0 \\
\Rightarrow \int _0^zE\frac{du}{dy}dy = -\int_0^z(\int_0^y fdx)d y + \int _0^zE\frac{du}{dx}|_0dy \\
\Rightarrow Eu(z) - Eu(0) = -\int_0^z(\int_0^y fdx)dy+E\frac{du}{dx}|_0z\\
\Rightarrow u(z) = \frac{1}{E}[-\int_0^z(\int_0^y fdx)dy+E\frac{du}{dx}|_0z]+u(0)
$$

$E\frac{du}{dx}|_0$ is determined by applying b.c at z = L.

> 已知u(L)的值就可以反求出$E\frac{du}{dx}|_0$

If b.c. at x = L is a Neumann b.c, we first calculate $u_{,z}$  and then apply b.c $Eu_{,z}(L)$

> Neumann 条件下无法直接知道u(L)，可以先把u(z)表达式求微分，然后用Neumann条件反求出$E\frac{du}{dx}|_0$

## Weak form of the partial differential equation

$$
Find\ u(x)\isin \mathcal{S} = \{u|u(0) = u_0\}
$$

The condition in S is the Dirichlet b.c. at x= 0, only.

**Problem formulation(Weak form):**

Given $u_0$, $\sigma(L) = t$, f(x), and the constitutive relation $\sigma = Eu_{,x}$

Find $u(x)\isin \mathcal{S} = \{u|u(0) = u_0\}$ such that $\forall w\isin \mathcal{V} = \{w|w(0) = 0\} $, (homogenous Dirichlet b.c on w)
$$
\int_0^L w_{i,x}\sigma dx = \int_0^Lwfdx + w(L)t
$$
Let A(x) is the section area in x, we have:
$$
\int_0^L w_{i,x}\sigma Adx = \int_0^LwfAdx + w(L)tA
$$

## The strong form and weak form are equivalent

### Strong form -> Weak form

Consider the strong form:
$$
\frac{d\sigma}{dx}+f = 0, in(0,L)
$$

Dirichlet at x=  0 +Neumann at x=L, consititutive condition: $u(0) = u_0, \sigma(L) = t, \sigma = Eu_{,x} $

Introduce $ w\isin \mathcal{V} = \{w|w(0) = 0\} $, w: weighting funciton.

Multiply w, A (sectional area) into strong form, and integrate
$$
\int _0^LwA\frac{d\sigma}{dx}dx+\int _0^LwAfdx = 0, in(0,L)
$$

Integrate by part:
$$
\Rightarrow  wA\sigma |_0^L - \int _0^Lw_{,x}A\sigma dx+\int _0^LwAfdx = 0 \\
\Rightarrow \int _0^Lw_{,x}A\sigma dx = \int _0^LwAfdx + wA\sigma |_0^L \\
\Rightarrow \int _0^Lw_{,x}A\sigma dx = \int _0^LwAfdx + w(L)A\sigma(L) -w(0)A\sigma(0) = \int _0^LwAfdx + w(L)At
$$



So we have the weak form.

### Weak form -> Strong form

Starting from the weak form formulation:

Given $u_0$, $\sigma(L) = t$, f(x), A, and the constitutive relation $\sigma = Eu_{,x}$

Find $u(x)\isin \mathcal{S} = \{u|u(0) = u_0\}$ such that $\forall w\isin \mathcal{V} = \{w|w(0) = 0\} $, (homogenous Dirichlet b.c on w)
$$
\int_0^L w_{,x}\sigma Adx = \int_0^LwfAdx + w(L)tA
$$
Integrate by part:
$$
w\sigma A|_0^L -  \int_0^L w\sigma_{,x} Adx = \int_0^LwfAdx + w(L)tA\\
\Rightarrow w(L)t A -w(0)\sigma(0)A-  \int_0^L w\sigma_{,x} Adx = \int_0^LwfAdx + w(L)tA \\
\Rightarrow  \int_0^L w\sigma_{,x} Adx + \int_0^LwfAdx = 0\\
\Rightarrow  \int_0^L w(\sigma_{,x}+f) Adx  = 0
$$
This holds for all $w\isin \mathcal{V} = \{w|w(0) = 0\}$. We choose $w(x) = \phi(x)(\sigma_{,x}+f)$, where
$$
\phi(x) >0 \ for \ x\isin(0,L)\\
\phi(x) =0 \ for \ x\isin\{0,L\}\\
$$
So we have:
$$
\Rightarrow  \int_0^L \phi(x) (\sigma_{,x}+f)^2 Adx  = 0, \\
\phi(x) (\sigma_{,x}+f)^2 A \geq 0, \ A>0\\
\Rightarrow \sigma_{,x}+f = 0 \ for \ x\isin(0,L)
$$
Finally:
$$
\frac{d\sigma}{dx}+f = 0 \ for \ x\isin(0,L)
$$
This is the strong form. Also contain the Dirichlet and Neuman conditions.

e.o.d

## Intro to C++ (pointers, iterators)

<img src="/Users/Zeyuan/Library/Application Support/typora-user-images/image-20210116234925800.png" alt="image-20210116234925800" style="zoom:50%;" />

# Unit 2: Approximation. The finite-dimensional weak form

## 2.01. The Galerkin, or finite-dimensional weak form

The strong and weak form:

Given $u_0$,t, f(x), and the constitutive relation![image-20210118225516142](https://tva1.sinaimg.cn/large/008eGmZEly1gms8nsjlx9j30vq08zn37.jpg)



The finite element method is based on the approximate version of the Weak form .

$u \isin \mathcal S, w \isin \mathcal V$,$ \mathcal S$ and $\mathcal V$ are infinite-dimensional function spaces.

> 比如，S和V可以是任意n阶多项式函数空间

Construct approximation in finite-dimensional function spaces.

> 比如，S和V仅为0和1阶多项式函数空间

### Finite-dimensional Weak form/ Galerkin weak form

The idea is to restrict the solution space of weighting function space.

**Finite-dimensional Weak form/ Galerkin weak form:**
$$
Find \\
u^h(x) \isin \mathcal S^h \subset \mathcal S \\
\mathcal S^h = \{u^h \isin H^1(0,L)|u^h(0) = u_0\}\\
Such \ that\\ 
\forall w^h \isin \mathcal V^h \subset  \mathcal V\\
\mathcal V^h = \{w^h \isin  H^1(0,L)|w^h(0) = 0 \}
$$

> H为希尔伯特函数空间

$$
\int_0^Lw_{,x}^h \sigma^hAdx = \int_0^Lw^hfAdx + w^h(L)tA
$$


## 2.02-2.03. Basic Hilbert spaces

Function spaces - **Hibert spaces**

Recall
$$
u^h \isin \mathcal S^h = \{u^h \isin H^1(0,L)|u^h(0) = u_0\}
$$

### $L^2$ function 

Consider a  function v: (0,L) -> R

Define the function v to be L^2  - function if v is square integralable in (0,L):
$$
\int_0^L v^2dx < \infin
$$
 e.g.: constant, finite polymominal function, Heaviside function etc. are L2, Dirac is not L2

We can in general define L^p function. L^p control the integral behaviour of a function. -> bounded

How about control the derivative? --> Regularity. Hibert space.

### Hibert space

$ v(x) \isin H^1(0,L)$ if
$$
\int_0^L (v^2+L^2v_{,x}^2)dx<\infin
$$

> 由于求导会改变实际物理量的单位，因此引入 $L^2$ 来使量纲统一。

In general use $m(0,L)^{1/d} = L$. m is a mesure. e.g,:  in R^3, d = 3, m(Omega)^{1/d}=m(Omega)^{1/3} = 'length'.
$$
\int_0^L (v^2+(m(0,L))^2v_{,x}^2)dx<\infin
$$
Now
$$
u^h \isin \mathcal S^h = \{u^h \isin H^1(0,L)|u^h(0) = u_0\}
$$
u^h and u_{,x}^h are suare integralable

e.g.: constant, finite polynomial, combination of constant and polynomial(分段但连续)。连续函数在导数jump处也可以满足H1，但如果函数不连续，那么肯定不是H1。原因：在不连续处导数为狄拉克函数，无法二次积分。 

![截屏2021-01-19 下午7.59.44](https://tva1.sinaimg.cn/large/008eGmZEgy1gmt97wpneqj30t10hwdpg.jpg)

## 02.04. The finite element method for the one-dimensional, linear, elliptic partial differential equation

Starting from the **Galekin (finite-dimensional)** Weak form:
$$
Find \\
u^h \isin \mathcal S^h = \{u^h \isin H^1(0,L)|u^h(0) = u_0\} \\
Such \ that\\
\forall w^h \isin \mathcal V^h = \{w^h \isin H^1(0,L)|w^h(0) = 0\}, \\
\int_0^L w_{,x}^h\sigma ^h A dx = \int_0^Lw^hfA dx + w^h(L)tA
$$

> $ u^h $ is also called "trial function". This imply that \sigma is also finite-dimensional.
> $$
> \sigma^h = Eu^h_{,x}\\
> However,\ f(x) = f(x)
> $$
> Note that f (the known data) is not finite dimensional, no approximation.
>
> t is a point value

The aim now is to obtain $u^h$ and $w^h$. (Or alternatively, $S^h$ and $V^h$)

**Key idea: Partition (0,L) into "finite elements", which are disjoint subdomains of (0,L)**. 将区间分段覆盖。

### Paritioning

$$
Partitioning \ \Omega = (0,L) \ into \\
\Omega^1 = (x^1,x^2)\\
\Omega^2 = (x^2,x^3)\\
...\\
\Omega^e = (x^e,x^{e+1})\\
\Omega^{n_{el}} = (x^{n_{el}},x^{n_{el}+1})\\
\Omega^e \ is\ open\ interval\\
\bar \Omega = \bar \cup _{e=1}^{e=n_{el}}\Omega^e \\
\bar \Omega  \ is \ the\ closure\ of\ \Omega\\
\bar \Omega = \Omega \cup \part \Omega\ (boundary\ of\ \Omega)
$$



![截屏2021-01-19 下午8.22.40](https://tva1.sinaimg.cn/large/008eGmZEgy1gmt9vcimtwj30vp0j0dqs.jpg)

![截屏2021-01-19 下午8.36.59](https://tva1.sinaimg.cn/large/008eGmZEly1gmtaal2rxcj30qj0fatfc.jpg)

###  Terminology

- $x^e$ is a node of the partition
- $\Omega^e$ is an element

Galerkin Weak form:
$$
\int_{\Omega} w_{,x}^h\sigma^hAdx = \int_{\Omega}w^hfAdx + w^h(L)tA \\
$$

$$
\Longrightarrow \sum_{e-1}^{n_{el}}\int_{\Omega_e} w_{,x}^h\sigma^hAdx = \sum_{e-1}^{n_{el}} \int_{\Omega_e}w^hfAdx + w^h(L)tA \\
$$

Represent $S^h$ and $V^h$ over each $\Omega^e$

## 2.05-2.06 Basis function

Galerkin Weak form:

$$
\Longrightarrow \sum_{e-1}^{n_{el}}\int_{\Omega_e} w_{,x}^h\sigma^hAdx = \sum_{e-1}^{n_{el}} \int_{\Omega_e}w^hfAdx + w^h(L)tA \\
$$

Representation of $u^h$ and $w^h$, over each $\Omega^e$. (Local representation)

Define local basis function over $\Omega^e = (x^e,x^{e+1})$. Finite number of basis function over $\Omega^e$, and so over $\Omega$.

**The basis function over $\Omega^e$: polynominals: linear** 

![截屏2021-01-21 下午11.10.36](https://tva1.sinaimg.cn/large/008eGmZEly1gmvpyzjuhhj31bq0qq1kx.jpg)

![截屏2021-01-21 下午11.24.36](https://tva1.sinaimg.cn/large/008eGmZEly1gmvqd9f823j31f40s41kx.jpg)

## 2.07-2.08 The bi-unit domain

Each physical domain is associated with a local domain - bi-unit domain. The global basis function is associated with local  definition of local basis function, with each node $x^e$, with campact support in $\Omega^{e-1}$ and $\Omega^e$.

![截屏2021-01-23 下午12.01.45](https://tva1.sinaimg.cn/large/008eGmZEly1gmxi11x1m8j315u0oingf.jpg)

## 2.09-2.10 The finite dimensional weak form as a sum over element subdomains

$$
\xi _{,x} = \frac{2}{h^e}\\
x_{,\xi}= \frac{h^e}{2}
$$

$h^e$ is the length of the element e.g. $h^e = x^{e+1}-x^e$
$$
u_{,x}^h=\sum_{A=1}^{N_{n_e}}N_{,\xi}^A\xi_{,x}d_e^A = \sum_{A=1}^{N_{n_e}}N_{,\xi}^A(\frac{2}{h^e})d_e^A \\
w_{,x}^h=\sum_{A=1}^{N_{n_e}}N_{,\xi}^A\xi_{,x}c_e^A = \sum_{A=1}^{N_{n_e}}N_{,\xi}^A(\frac{2}{h^e})c_e^A
$$
Consider the integral
$$
\int_{\Omega^e}w_{,x}^h\sigma^hAdx=\int_{\Omega^e}w_{,x}^hEAu_{,x}^hdx\\
=\int_{\Omega^e}(\sum_{A=1}^{N_{n_e}}N_{,\xi}^A\frac{2}{h^e}c_e^A)EA(\sum_{A=1}^{N_{n_e}}N_{,\xi}^B\frac{2}{h^e}d_e^B)dx
$$

$$
\int_{\Omega^e}w^hf(x(\xi))Adx=\int_{\Omega^e}(\sum_AN^Ac_e^A)f(x(\xi))Adx
$$

Note that $dx = \frac{dx}{d\xi}d\xi=\frac{h^e}{2}d\xi$

So we have:
$$
\int_{\Omega^e}w_{,x}^h\sigma^hAdx= \int_{\Omega^\xi}(\sum_{A=1}^{N_{n_e}}N_{,\xi}^A\frac{2}{h^e}c_e^A)EA(\sum_{A=1}^{N_{n_e}}N_{,\xi}^B\frac{2}{h^e}d_e^B)\frac{h^e}{2}d\xi\\
\int_{\Omega^e}w^hf(x(\xi))Adx=\int_{\Omega^\xi}(\sum_AN^Ac_e^A)f(x(\xi))A\frac{h^e}{2}d\xi
$$

# Unit 3 Linear algebra; the matrix-vector form

## 3.01 - 3.06  The matrix-vector weak form

Recall, for the first element,
$$
\int_{\Omega^e}w_{,x}^h\sigma^hAdx= \int_{\Omega^\xi}(N_{,\xi}^2\frac{2}{h^e}c_e^2)EA(\sum_{B=1}^{N_{n_e}}N_{,\xi}^B\frac{2}{h^e}d_e^B)\frac{h^e}{2}d\xi \\
\int_{\Omega^e}w^hfAdx=\int_{\Omega^\xi}(N^2c_e^2)f(x(\xi))A\frac{h^e}{2}d\xi
$$
for a general element:
$$
\int_{\Omega^e}w_{,x}^h\sigma^hAdx= \int_{\Omega^\xi}(\sum_{A=1}^{N_{n_e}}N_{,\xi}^A\frac{2}{h^e}c_e^A)EA(\sum_{A=1}^{N_{n_e}}N_{,\xi}^B\frac{2}{h^e}d_e^B)\frac{h^e}{2}d\xi = \sum_{A,B}c_e^A(\int_{\Omega^\xi}N_{,\xi}^A\frac{2EA}{h^e}N_{,\xi}^Bd\xi)d_e^B\\
\int_{\Omega^e}w^hf(x(\xi))Adx=\int_{\Omega^\xi}(\sum_AN^Ac_e^A)f(x(\xi))A\frac{h^e}{2}d\xi=\sum_Ac_e^A\int_{\Omega^\xi}N^Af\frac{Ah^e}{2}d\xi
$$
for e=1, there is no sum over A. Instead use A=2.

> $w^h(0)=0$, so, $w_{e=1}^h=N^2c_e^2$

**To eliminate the sum, we use the matrix form** 
$$
\sum_{A,B}^{N_e=2}c_e^A(\int_{\Omega^\xi}N_{,\xi}^A\frac{2EA}{h^e}N_{,\xi}^Bd\xi)d_e^B \\
=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{2EA}{h^e}(\int_{\Omega^\xi}\left[\begin{matrix}N_{,\xi}^1N_{,\xi}^1&N_{,\xi}^1N_{,\xi}^2\\N_{,\xi}^2N_{,\xi}^1&N_{,\xi}^2N_{,\xi}^2\end{matrix}\right]d\xi)\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] \tag{*}
$$

> The condition is A is uniform over the element.

Recall $N^1(\xi) = \frac{1-\xi}{2}, N^2(\xi) = \frac{1+\xi}{2}$, $N^1_{,\xi} = -\frac{1}{2}, N^2_{,\xi} = \frac{1}{2}$
$$
(*)=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{2EA}{h^e}\left[\begin{matrix}\frac{1}{4}&-\frac{1}{4}\\-\frac{1}{4}&\frac{1}{4}\end{matrix}\right](\int_{\Omega^\xi}d\xi)\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] \\
=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{2EA}{h^e}\left[\begin{matrix}\frac{1}{4}&-\frac{1}{4}\\-\frac{1}{4}&\frac{1}{4}\end{matrix}\right]\times2\times\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right]\\
=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right]
$$
Using the same method, we have
$$
\sum_Ac_e^A\int_{\Omega^\xi}N^Af\frac{Ah^e}{2}d\xi=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{fAh^e}{2}\left[ \begin{matrix} 1 \\ 1 \end{matrix} \right]
$$

### Conclusion of new formulation of a matrix form over a general element

$$
\int_{\Omega^e}w_{,x}^h\sigma^hAdx=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] \\
\int_{\Omega^e}w^hfAdx=\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{fAh^e}{2}\left[ \begin{matrix} 1 \\ 1 \end{matrix} \right]
$$

* Special case: e=1
  $$
  \int_{\Omega^e}w_{,x}^h\sigma^hAdx=c_e^2 \frac{EA}{h^e}\left[\begin{matrix}-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] \\
  \int_{\Omega^e}w^hfAdx= c_e^2 \frac{fAh^e}{2}
  $$
  

Recall the galerkin weak form:
$$
\int_{\Omega} w_{,x}^h\sigma^hAdx = \int_{\Omega}w^hfAdx + w^h(L)tA \\
$$
Using matrix representation,
$$
c_1^2 \frac{EA}{h^1}\left[\begin{matrix}-1&1\end{matrix}\right]\left[ \begin{matrix} d_1^1 \\ d_1^2 \end{matrix} \right]+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] =c_1^2 \frac{fAh^1}{2}+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\left[ \begin{matrix} \frac{fAh^e}{2} \\ \frac{fAh^e}{2} \end{matrix} \right]+c^2_{n_{el}}tA
$$

### Conclusion of new formulation of a matrix form over the whole interval

$$
\int_{\Omega} w_{,x}^h\sigma^hAdx = \int_{\Omega}w^hfAdx + w^h(L)tA \\
\Updownarrow \\
c_1^2 \frac{EA}{h^1}\left[\begin{matrix}-1&1\end{matrix}\right]\left[ \begin{matrix} d_1^1 \\ d_1^2 \end{matrix} \right]+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] =c_1^2 \frac{fAh^1}{2}+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\left[ \begin{matrix} \frac{fAh^e}{2} \\ \frac{fAh^e}{2} \end{matrix} \right]+c^2_{n_{el}}tA
$$

> Remark: $u_e^h(x(\xi)) =\sum_AN^A(\xi)d_e^A$ ,  $w_e^h(x(\xi)) =\sum_B N^B(\xi)c_e^A$ 
>
> $u^h(x^e)=d_e^1$, $u^h(x^{e+1})=d_e^2$, $w^h(x^e)=c_e^1$, $w^h(x^{e+1})=c_e^2$: the Kronecker-delta property of the basis function ensure that the nodel dofs of the solution filed are indeed its values of the node.

Note that the following map holds between local and global dofs 

- local dof A in element e: $d_e^A$.

- global dof of $x_{e+A-1}$: $d_{e+A-1}$: the value at $x=x_{e+A-1}$
  $$
  d_e^A = d_{e+A-1}
  $$
  

  - e.g.: $d_1^1=d_1,d_1^2=d_2,...,d_{e=n_{el}}^1=d_{e=n_{el}},d_{e=n_{el}}^2=d_{e=n_{el+1}}$

Similarly, 
$$
c_e^A = c_{e+A-1}
$$
![截屏2021-01-26 下午5.07.10](https://tva1.sinaimg.cn/large/008eGmZEly1gn17k6i1ptj319i0kunel.jpg)

### Notation

- Element stiffness matrix: $K_e = \frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]$
- Element  force vector: $F_e= \left[ \begin{matrix} \frac{fAh^e}{2} \\ \frac{fAh^e}{2} \end{matrix}\right]$

### The final formulation of the matrix form over the whole interval

$$
c_1^2 \frac{EA}{h^1}\left[\begin{matrix}-1&1\end{matrix}\right]\left[ \begin{matrix} d_1^1 \\ d_1^2 \end{matrix} \right]+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\frac{EA}{h^e}\left[\begin{matrix}1&-1\\-1&1\end{matrix}\right]\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right] \\

\Updownarrow\\

EA\left[\begin{matrix}c_2&c_3&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix} 
-\frac{1}{h^1}&\frac{1}{h^1}+\frac{1}{h^2}&-\frac{1}{h^2}&0&0&0 \\
0&-\frac{1}{h^2}&\frac{1}{h^2}+\frac{1}{h^3}&-\frac{1}{h^3}&0&0 \\
\vdots&\vdots&\ddots&\ddots&\ddots&\ddots\\
0&0&0&-\frac{1}{h^{n_{el}-1}}&\frac{1}{h^{n_{el}-1}}+\frac{1}{h^{n_{el}}}&-\frac{1}{h^{n_{el}}}\\
0&0&0&0&-\frac{1}{h^{n_{el}}}&\frac{1}{h^{n_{el}}}
\end{matrix}\right]\left[\begin{matrix}d_1\\d_2\\d_3&\\\vdots\\d_{n_{el}}\\d_{n_{el}+1}\end{matrix}\right]\\
=A_{e=1}^{n_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\underline{K_e}\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right]
$$

>  A is the operator

$$
c_1^2 \frac{fAh^1}{2}+\sum_{e=2}^{N_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\left[ \begin{matrix} \frac{fAh^e}{2} \\ \frac{fAh^e}{2} \end{matrix} \right]\\
\Updownarrow\\
\frac{fA}{2}\left[\begin{matrix}c_2&c_3&c_4&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix}
h^1+h^2\\
h^2+h^3\\
\vdots\\
h^{n_{el}-1}+h^{n_{el}}\\
h^{n_{el}}
\end{matrix}\right] \\
=A_{e=1}^{n_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\underline{F_e}
$$

$$
c^2_{n_{el}}tA \Longleftrightarrow \left[\begin{matrix}c_2&c_3&c_4&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix}
0\\
0\\
\vdots\\
tA
\end{matrix}\right]
$$

Combine all together:
$$
EA\left[\begin{matrix}c_2&c_3&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix} 
-\frac{1}{h^1}&\frac{1}{h^1}+\frac{1}{h^2}&-\frac{1}{h^2}&0&0&0 \\
0&-\frac{1}{h^2}&\frac{1}{h^2}+\frac{1}{h^3}&-\frac{1}{h^3}&0&0 \\
\vdots&\vdots&\ddots&\ddots&\ddots&\ddots\\
0&0&0&-\frac{1}{h^{n_{el}-1}}&\frac{1}{h^{n_{el}-1}}+\frac{1}{h^{n_{el}}}&-\frac{1}{h^{n_{el}}}\\
0&0&0&0&-\frac{1}{h^{n_{el}}}&\frac{1}{h^{n_{el}}}
\end{matrix}\right]\left[\begin{matrix}d_1\\d_2\\d_3&\\\vdots\\d_{n_{el}}\\d_{n_{el}+1}\end{matrix}\right] \\
=\frac{fA}{2}\left[\begin{matrix}c_2&c_3&c_4&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix}
h^1+h^2\\
h^2+h^3\\
\vdots\\
h^{n_{el}-1}+h^{n_{el}}\\
h^{n_{el}}
\end{matrix}\right]+\left[\begin{matrix}c_2&c_3&c_4&\dots&c_{n_{el}}&c_{n_{el}+1}\end{matrix}\right]\left[\begin{matrix}
0\\
0\\
\vdots\\
tA
\end{matrix}\right] \\

\Updownarrow\\

A_{e=1}^{n_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\underline{K_e}\left[ \begin{matrix} d_e^1 \\ d_e^2 \end{matrix} \right]=A_{e=1}^{n_{el}}\left[ \begin{matrix} c_e^1 & c_e^2 \end{matrix} \right]\underline{F_e}+\left[\begin{matrix}
0\\
0\\
\vdots\\
c_{n_{el}+1}tA
\end{matrix}\right]
$$
