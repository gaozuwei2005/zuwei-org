---
title: 线性代数 | 5.1 特征向量与特征值
date: 2024-11-25
summary: 定义、特征值的相关定理、特征向量与差分方程
---

对于线性变换 $\boldsymbol{x} \mapsto A \boldsymbol{x}$ 中，有一些特殊向量，$A$ 对它们的作用是很简单的，只是对原向量的放缩。

## 特征值、特征向量与特征空间的定义

> **特征值与特征向量**：对于 $n \times n$ 矩阵 $A$ 和非零向量 $\boldsymbol{x}$，若存在 $\lambda \in \mathbb R$，使得 $A \boldsymbol{x} = \lambda \boldsymbol{x}$，有非平凡解 $\boldsymbol{x}$，则称 $\lambda$ 为 $A$ 的**特征值**，$\boldsymbol{x}$ 称为**对应于 $\lambda$ 的特征向量**。

对于某一个 $\boldsymbol{x}$，我们只需验证 $A\boldsymbol{x}$ 是否为 $\boldsymbol{x}$ 的若干倍即可判断 $\boldsymbol{x}$ 是否为特征向量。

对于某一个 $\lambda$，我们需要验证 $A \boldsymbol{x} = \lambda \boldsymbol{x}$，有非平凡解，等价于

$$(A - \lambda I) \boldsymbol{x} = \boldsymbol{0}$$

即我们需要验证 $A - \lambda I$ 中的列是否线性相关（行简化之后有自由变量）。

可以注意到对于一个特征值，要么没有特征向量，要么有无穷多个特征向量，它们**组成 $A - \lambda I$ 的零空间**。

> **特征空间**：方程 $(A - \lambda I) \boldsymbol{x} = \boldsymbol{0}$ 所有解的集合称为 **$A$ 的对应于 $\lambda$ 的特征空间**。
> 
> 该集合是 $A - \lambda I$ 的零空间，也是 $\mathbb R^n$ 的子空间，由零向量和所有对应于 $\lambda$ 的特征向量组成。

我们可以求 $A - \lambda I$ 的零空间的显式刻画（基），来认识 $A$ 的对应于 $\lambda$ 的特征空间。

行简化在数值计算中会出现舍入误差，从而出现错误的主元素。

## 特征值的相关定理

> **定理 1**：三角矩阵的主对角线的元素是其特征值。
>
> **证明**：$A - a\_{ii}I$ 中对角线上第 $i$ 行第 $i$ 列的值为 $0$，从而方程有自由变量。

> **一个结论**：$A$ 有零特征值的充要条件是 $A$ 不可逆，也充要于 $A \boldsymbol{x} = \boldsymbol{0}$ 有非平凡解。

> **定理 2**：若 $\lambda\_1, \lambda\_2, \cdots, \lambda\_p$ 是 $n \times n$ 矩阵 $A$ 的互不相同的特征值，且 $\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_p$ 分别是 $A$ 的对应于 $\lambda\_1, \lambda\_2, \cdots, \lambda\_p$ 的特征向量，那么向量集合 $\\\{\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_p\\\}$ 线性无关。
>
> **证明**：假设线性相关，那么存在最小的 $r \in [2,p]$ 和非全零的 $c\_1, c\_2, \cdots, c\_{r-1} \in R$，使得
>
> $$c\_1 \boldsymbol{v\_1} + c\_2 \boldsymbol{v\_2} + \cdots + c\_{r-1} \boldsymbol{v\_{r-1}} = \boldsymbol{v}\_r$$
>
> 两边同时左乘 $A$，并将 $A\boldsymbol{v}\_j = \lambda\_j \boldsymbol{v}\_j$ 代入得到
>
> $$c\_1 \lambda\_1  \boldsymbol{v\_1} + c\_2 \lambda\_2  \boldsymbol{v\_2} + \cdots + c\_{r-1} \lambda\_{r-1}  \boldsymbol{v\_{r-1}} = \lambda\_r \boldsymbol{v\_r}$$
>
> 二式减去一式乘 $\lambda\_r$ 得到
>
> $$c\_1 (\lambda\_1 - \lambda\_r) \boldsymbol{v\_1} + 
c\_2 (\lambda\_2 - \lambda\_r)  \boldsymbol{v\_2} +
\cdots + 
c\_{r-1} (\lambda\_{r-1} - \lambda\_r)  \boldsymbol{v\_{r-1}} 
= \boldsymbol{0}$$
> 
> 由于非全零的 $c\_1, c\_2, \cdots, c\_{r-1} \in R$ 和 $\lambda\_j - \lambda r$ 全不为零，因此 $\\\{ \boldsymbol{v\_1} ,\boldsymbol{v\_2}, \cdots, \boldsymbol{v\_{r-1}} \\\}$ 线性相关，矛盾。

## 特征向量与差分方程

对于一阶差分方程

$$\boldsymbol{x}\_{k+1} = A \boldsymbol{x}\_k \ (k = 0, 1, 2, \cdots)$$

若 $A$ 是 $n \times n$ 矩阵，则该方程是 $\\\{\boldsymbol{x}\_k\\\}$ 的递归表示，而通项公式为 $\boldsymbol{x}\_{k} = A^k \boldsymbol{x}\_0 \ (k = 0, 1, 2, \cdots)$

构造该方程的解的最简单的方法是取 $A$ 的一个特征值 $\lambda$ 和对应于 $\lambda$ 的特征向量 $\boldsymbol{x}\_0$，然后令

$$\boldsymbol{x}\_{k} = \lambda^k \boldsymbol{x}\_0 \ (k = 0, 1, 2, \cdots)$$

则为原方程的解。