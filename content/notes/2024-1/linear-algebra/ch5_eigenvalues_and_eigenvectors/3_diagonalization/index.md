---
title: 线性代数 | 5.3 对角化
date: 2024-12-02
summary: 对角化、矩阵的对角化、有重特征根的矩阵
---

## 对角化

我们希望将 $A$ 分解为 $A = PDP^{-1}$（其中 $D$ 是对角矩阵），从而用矩阵表示 5.2 中提到的动力系统。

首先，对角矩阵的幂是容易计算的

$$\left[ 
    \begin{matrix}
    \lambda\_1 & 0 & \cdots & 0 \\\\
    0 & \lambda\_2 & \cdots & 0 \\\\
    \vdots & \vdots & \ddots & \vdots \\\\
    0 & \cdots & 0 & \lambda\_n
    \end{matrix}
 \right]^k
 = \left[ 
    \begin{matrix}
    \lambda\_1^k & 0 & \cdots & 0 \\\\
    0 & \lambda\_2^k & \cdots & 0 \\\\
    \vdots & \vdots & \ddots & \vdots \\\\
    0 & \cdots & 0 & \lambda\_n^k
    \end{matrix}
 \right]$$

那么，如果我们可以分解 $A = PDP^{-1}$（其中 $D$ 是对角矩阵），那么 $A$ 的幂的计算也是简单的，我们只需要计算三次矩阵乘法即可。

$$\begin{aligned}
A^k &= (PDP^{-1})^k \\\\
&= P (DP^{-1}P)^{k-1} DP^{-1} \\\\
&= P D^k P^{-1}
\end{aligned}$$

> **可对角化**：若方阵 $A$ 相似于对角矩阵 $D$，即 $A = PDP^{-1}$，那么我们称 $A$ **可对角化**。

> **定理 5（对角化定理）**：$n \times n$ 矩阵 $A$ 可对角化的充分必要条件是 $A$ 有 $n$ 个线性无关的特征向量。
>
> 此时 $P$ 的列向量是 $A$ 的 $n$ 个线性无关的特征向量，$D$ 主对角线上的元素是 $A$ 对应于 $P$ 中特征向量的特征值。
>
> 因此 $P$ 的列向量是 $\mathbb R^n$ 的一个基，我们称其为**特征向量基**。
>
> **证明：（必要性）** 首先，$A = PDP^{-1} \Leftrightarrow AP = PD$，而
>
> $$AP = A\left[\begin{matrix}
\boldsymbol{v}\_1 & \boldsymbol{v}\_2 & \cdots & \boldsymbol{v}\_n
\end{matrix}\right]
 = \left[\begin{matrix}
A\boldsymbol{v}\_1 & A\boldsymbol{v}\_2 & \cdots & A\boldsymbol{v}\_n
\end{matrix}\right]$$
>
> $$PD = P\left[ 
    \begin{matrix}
    \lambda\_1 & 0 & \cdots & 0 \\\\
    0 & \lambda\_2 & \cdots & 0 \\\\
    \vdots & \vdots & \ddots & \vdots \\\\
    0 & \cdots & 0 & \lambda\_n
    \end{matrix}
 \right] = \left[\begin{matrix}
\lambda\_1\boldsymbol{v}\_1 & \lambda\_2\boldsymbol{v}\_2 & \cdots & \lambda\_n\boldsymbol{v}\_n
\end{matrix}\right]$$
>
> 因此 $AP = PD$ 等价于
>
> $$\left\\\{
\begin{aligned}
A\boldsymbol{v}\_1 &= \lambda\_1\boldsymbol{v}\_1 \\\\
A\boldsymbol{v}\_2 &= \lambda\_2\boldsymbol{v}\_2 \\\\
&\cdots \\\\
A\boldsymbol{v}\_n &= \lambda\_2\boldsymbol{v}\_n \\\\
\end{aligned}
\right.$$
>
> 由于 $P$ 可逆，因此 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$ 线性无关，于是等价于 $\lambda\_1, \lambda\_2, \cdots, \lambda\_n$ 是 $A$ 的特征根，$\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$ 是分别对应于这些特征根的特征向量。
>
> **（充分性）** 对于 $A$ 的任意 $n$ 个特征向量 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$ 和与其对应的特征根 $\lambda\_1, \lambda\_2, \cdots, \lambda\_n$，我们可以运用刚才的三次等价变换得到 $AP=PD$。
>
> 当 $n$ 个特征向量 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$ 线性独立的时候，$P$ 可逆，因此有 $A = PDP^{-1}$。

## 矩阵的对角化

给定一个方阵，我们需要将其对角化，进行以下步骤即可：

1. 求出 $A$ 的所有特征根 $\lambda\_1, \lambda\_2, \cdots, \lambda\_n$。
2. 求 $A$ 对应于这些特征根的线性无关的特征向量 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$。我们只需找出所有特征空间的基即可。
3. 构造 $P = \left[\begin{matrix}\boldsymbol{v}\_1 & \boldsymbol{v}\_2 & \cdots & \boldsymbol{v}\_n\end{matrix}\right]$，$D = \left[     \begin{matrix}    \lambda\_1 & 0 & \cdots & 0 \\\\    0 & \lambda\_2 & \cdots & 0 \\\\    \vdots & \vdots & \ddots & \vdots \\\\    0 & \cdots & 0 & \lambda\_n    \end{matrix} \right]$

> **定理 6**：有 $n$ 个相异特征值的 $n \times n$ 的矩阵可对角化。
>
> **证明**：对于这些特征值，我们找出对应特征空间的一个基向量 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_n$，由于它们是线性无关的，因此 $P$ 可逆，于是 $A$ 可对角化。
>
> **注意**：本定理仅描述了矩阵可对角化的**充分条件**，而不是充要条件。
> 
> 有少于 $n$ 个相异特征值的矩阵也可能可对角化，只需要各个特征空间的维数之和为 $n$ 即可。接下来，我们将会叙述该充要条件。

## 特征方程有重根（特征值不都相异）的矩阵

> **定理 7**：设 $A$ 是 $n \times n$ 的矩阵，其相异特征值为 $\lambda\_1, \lambda\_2, \cdots, \lambda\_p$，那么
>
> 1. 对于所有 $1 \le k \le p$，$\lambda\_k$ 的特征空间的维数小于等于 $\lambda\_k$ 的代数重数。
> 2. 矩阵 $A$ 可对角化的**充分必要条件**是所有不同特征空间的维数之和等于 $n$。具体而言需要满足以下条件
>   
>       （1）特征方程有 $n$ 个实根；（不一定要相异）
>       
>       （2）每个特征值对应的特征空间的维数（几何重数）等于该特征值的代数重数。
> 
> 1. 若 $A$ 可对角化，且 $\mathcal B\_k$ 是对应于 $\lambda\_k$ 的特征空间的基，那么 $\mathcal B\_1, \mathcal B\_2, \cdots, \mathcal B\_p$ 中所有向量组成 $\mathbb R^n$ 的基。
>
> **证明**：（略）