---
title: 线性代数 | 1.4 矩阵方程 Ax=b
date: 2024-12-12
summary: 线性组合、矩阵方程、解的存在性
---

> **线性组合**：若 $A$ 是 $m \times n$ 矩阵，它的各列是 $\boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n$，对于 $\boldsymbol{x} \in \mathbb R^n$，那么 $A\boldsymbol{x}$ 就是 $A$ 的各列以 $\boldsymbol{x}$ 对应元素为权的线性组合。
> $$A\boldsymbol{x}
= 
\left[
    \begin{matrix}
    \boldsymbol{a}_1 & 
    \boldsymbol{a}_2 & 
    \cdots &
    \boldsymbol{a}_n
    \end{matrix}
\right]
\left[
    \begin{matrix}
    x_1 \\\\
    x_2 \\\\
    \vdots \\\\
    x_n
    \end{matrix}
\right]
=
x_1 \boldsymbol{a}_1 + x_2 \boldsymbol{a}_2 + \cdots + x_n \boldsymbol{a}_n
$$

> **矩阵方程**：$A\boldsymbol{x} = \boldsymbol{b}$

矩阵方程 $A\boldsymbol{x} = \boldsymbol{b}$、向量方程 $x_1 \boldsymbol{a}_1 + x_2 \boldsymbol{a}_2 + \cdots + x_n \boldsymbol{a}_n = \boldsymbol{0}$、增广矩阵 $\left[
    \begin{matrix}
    \boldsymbol{a}_1 & 
    \boldsymbol{a}_2 & 
    \cdots &
    \boldsymbol{a}_n & 
    \boldsymbol{b}
    \end{matrix}
\right]$ 的线性方程组有相同的解集。

## 解的存在性

方程 $A\boldsymbol{x} = \boldsymbol{b}$ 有解当且仅当 $\boldsymbol{b}$ 是 $A$ 的各列的线性组合。

> **定理 4**：设 $A$ 是 $m \times n$ 的矩阵，那么下列命题在逻辑上是等价的。
>
> 1. 对于 $\mathbb R^m$ 中的每个 $\boldsymbol{b}$，方程 $A \boldsymbol{x} = \boldsymbol{b}$ 有解。
> 2. $\mathbb R^m$ 中的每个 $\boldsymbol{b}$ 都是 $A$ 的列的线性组合。
> 3. $A$ 的各列生成 $\mathbb R^m$
> 4. $A$ 在每一行都有一个主元位置。