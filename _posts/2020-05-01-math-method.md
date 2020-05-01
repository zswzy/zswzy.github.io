---
layout:     post
title:      常用数学工具
subtitle:   矩阵运算，数学技巧等
date:       2020-05-01
author:     Zeyuan
header-img: img/image737.jpg
catalog: true
tags:
    - 数学工具
    - 线性代数
---
<link rel="stylesheet" type="text/css" href="auto-number-title.css" />

# 常用数学工具
## 雅可比（Jacobi）矩阵
在系统线性化，或者求函数的级数展开时经常会遇到多维的函数，这些函数的求导需要使用雅可比矩阵，具体的定义如下：

函数 $\textbf{f}: \mathbb{R}^n \to \mathbb{R}^m$，自变量$\textbf{x} \in \mathbb{R}^n$ 映射到 $\textbf{f(x)} \in \mathbb{R}^m$.

雅可比矩阵
$$
\textbf{J} = \left[
 \begin{matrix}
   \frac{\partial{\textbf{f}}}{\partial{x_1}} & \cdots & \frac{\partial{\textbf{f}}}{\partial{x_n}}
  \end{matrix}
  \right]= \left[
  \begin{matrix}
  \frac{\partial{f_1}}{\partial{x_1}} & \cdots & \frac{\partial{f_1}}{\partial{x_n}}\\
  \vdots & \ddots & \vdots\\
  \frac{\partial{f_m}}{\partial{x_1}} & \cdots & \frac{\partial{f_m}}{\partial{x_n}}
  \end{matrix}
  \right] \in \mathbb{R}_{m\times n}
$$
- 记忆方法：$\textbf{f}$的微分应为
$$
d\textbf{f} = \textbf{J} \times d\textbf{x} = \textbf{J} \times \left[
\begin{matrix}
dx_1 \\
\vdots \\
dx_n
\end{matrix}
\right]
$$
需要满足相同的维度，即$\textbf{J}$ 的某一排需要和这一列$\textbf{x}$相乘，所以$\textbf{J}$的每一排都是对固定的f维度对每一维x求导。

- 矩阵的分量：$\textbf{J}_{ij} = \frac{\partial{f_i}}{\partial{x_j}}$

- 函数$\textbf{f}$在$\textbf{x}_0$处的线性化为：
$$
\textbf{f}(\textbf{x_0}+d\textbf{x}) = \textbf{f}(\textbf{x_0}) + \textbf{J}_{\textbf{f},\textbf{x} = \textbf{x}_0}\times d\textbf{x} + o(\|d\textbf{x}\|)
$$
其中
$$ d\textbf{x} = \left[
\begin{matrix}
dx_1 \\
\vdots \\
dx_n
\end{matrix}
\right]
$$
- 雅可比矩阵的逆矩阵为反函数的雅可比矩阵。

**与梯度的关系**：
***雅可比矩阵是该函数梯度的转置！！:scream::scream::scream:***
（主要是由于在梯度中小量的表示通常是行向量）
