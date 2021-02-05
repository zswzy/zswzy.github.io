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

## 5.04. The best approximation property

Notation:

	- $u^h \isin \mathcal S^h$ the FE solution
	- $w^h \isin \mathcal V^h$ a weighting function
	- $U^h \isin \mathcal S^h=\{U^h \isin H^1(\Omega)|U^h(0)=u_0\}$

Note $U^h = u^h+w^h$

### Theorem (Best approximation property)

$$
a(e,e) \leq a(U^h-u,U^h-u)
$$

> the energy norm of error is the lowest w.r.t the energy norm of error of ANY member in $S^h$ 

Proof:

Consider $a(e+w^h,e+w^h)=a(e,e)+a(w^h,w^h)+2a(e,w^h)$ .

And the $a(e,w^h)$ is 0 according to the consistency property.

So, $a(e+w^h,e+w^h)=a(e,e)+a(w^h,w^h) \geq a(e,e)$

And $a(e+w^h,e+w^h)=a(u^h-u+w^h,u^h-u+w^h)=a(U^h-u,U^h-u)$

Finally, $a(e,e) \leq a(U^h-u,U^h-u) $

## 5.05. The "Pythagorean Theorem"

### Corollary 1

if $S^h=V^h$, $a(u,u) = a(u^h,u^h)+a(e,e)$

proof: using consistent condition

### Corollary 2

The FE solution under estimate the energy norm of the problem: $a(u^h,u^h) \leq a(u,u)$

Proof: from corollary 1

In elestistic problem , the energy norm is the strain energy



> Homogenous D boundary condition: $u^h(0)=0$

## 5.06. Sobolev estimates and convergence of the finite element method

Notation:

$U^h \isin \mathcal S^h=\{U^h \isin H^n(\Omega)|U^h(0)=u_0\}$

> $U^h$ does not necessarily represent the FE solution

Consider $U^h$ such that $U^h(x_A)=u^h(x_A)=d_A$

​	A: global dof, $x_A$ : global numbered node, $d_A$: global numbered tril solution dof

Consider $\tilde U^h$ such that $\tilde U^h(x_A)=u(x_A)$, u is the exact solution

![image-20210205153127010](https://tva1.sinaimg.cn/large/008eGmZEly1gncozjm5e9j315i08stgn.jpg)

### Interpolation error estimate in Sobolev space

$$
||\tilde U^h-u||_m \leq c(h^e)^\alpha ||u||_r
$$

- $\tilde U^h-u$ : interpolation error 
- $h^e$ : element size
- c: constant
- r: regularity of the solution

> $||u||_r$ measure of regularity (smoothness) of u

- $\alpha$: exponent satisfies $\alpha = min(k+1-m,r-m)$
  - k: Polynomial order of the finite-dimensional basis



If r is large(**exact solution is very smooth** ): $\alpha = k+1-m$

​	$||\tilde U^h-u||_m \leq c(h^e)^{k+1-m} ||u||_r$, thus $||\tilde U^h-u||_m \rightarrow 0$ as $h^e \rightarrow 0$ (provided that k+1>m)

This is the convergence property. Provided that the order of the basis function is high. (k+1>m)

## 5.07. Finite element error estimates

Extend the equivelance of H1-energy norm to Hn-energy norm:
$$
c_1||v||_n \leq a(v,v)^{1/2} \leq c_2||v||_n
$$

### Theorem

$$
||e||_n \leq\bar c (h^e)^\alpha ||u||_r
$$

Note that $e  =u^h-u$

Proof:

Using  $c_1||e||_n \leq a(e,e)^{1/2}  \leq a(U^h-u,U^h-u)^{1/2}$ (Best approximation property)

Note that $U^h$ is any element in $S^h$, and we can take $\tilde U^h$ as an $U^h$ :

$c_1||e||_n \leq a(e,e)^{1/2}  \leq a(\tilde U^h-u,\tilde U^h-u)^{1/2} \leq c_2 ||\tilde U^h-u||_n$



And from the interpolation error estimate in Sobolev space (5.6), we have $c_2||\tilde U^h-u||_n \leq c_2c(h^e)^\alpha ||u||_r$



Finally, we have $||e||_n \leq \frac{c_2c}{c_1}(h^e)^\alpha ||u||_r =\bar c(h^e)^\alpha ||u||_r$  



For u **sufficiently smooth**,$\alpha = min(k+1-n,r-n)=k+1-n$ , k: polynomial order of basis function



Consider n=1: $||e||_1 \leq\bar c (h^e)^{\alpha=k} ||u||_r$

- k=1, $||e||_1 \leq\bar c (h^e) ||u||_r$
- k=2, $||e||_1 \leq\bar c (h^e)^2 ||u||_r$

Consider L2 norm: H0 space $||e||_{L^2} \leq\bar c (h^e)^{k+1} ||u||_r$

- k=1, $||e||_{L^2} \leq\bar c (h^e)^{2} ||u||_r$ , converge quadraticly
- k=1, $||e||_{L^2} \leq\bar c (h^e)^{3} ||u||_r$

xs