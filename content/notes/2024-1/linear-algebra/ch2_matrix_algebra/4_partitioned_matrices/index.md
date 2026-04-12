---
title: 线性代数 | 2.4 分块矩阵
date: 2024-12-03
summary: 分块矩阵的定义、分块矩阵的乘法、分块矩阵的逆
---

## 分块矩阵的定义

> **分块矩阵**：将原矩阵用水平线和竖直线分成若干块，把每一块视作一个元素，那么这些元素按照相对顺序描述的矩阵称为 **分块矩阵**，例如划分为两行三列的分块矩阵可以描述为
>
> $$A = 
    \begin{bmatrix}
    A_{11} & A_{12} & A_{13} \\\\
    A_{21} & A_{22} & A_{23} \\\\
    \end{bmatrix}
    $$

## 矩阵加法与标量乘法

若 $A$ 与 $B$ 有相同维数且以相同方式分块，那么其矩阵加法得到的矩阵也是以同样方式分块，并且每一块是 $A,B$ 对应块的矩阵之和。

标量乘上某一个分块矩阵得到的分块矩阵，也是以同样方式分块，并且每个块均乘上该标量。

## 分块矩阵的乘法

分块矩阵 $A, B$ 可以进行矩阵乘法的条件是，$A$ 的列分法和 $B$ 的行分法是一致的。其计算的过程也是使用行列法则，和矩阵乘法的过程一样。

> **矩阵乘法的列行法则**：若 $A \in \mathbb R^{m \times n}, B \in \mathbb R^{n \times p}$，那么有 
>
> $$\begin{aligned}
AB &= \begin{bmatrix}
            \operatorname{col}_1(A) & 
            \operatorname{col}_2(A) & 
            \cdots &
            \operatorname{col}_n(A)
        \end{bmatrix}
        \begin{bmatrix}
            \operatorname{row}_1(B) \\\\
            \operatorname{row}_2(B) \\\\
            \cdots \\\\
            \operatorname{row}_p(B) \\\\
        \end{bmatrix}\\\\
&= \sum\_{k = 1}^n \operatorname{col}\_k (A) \operatorname{row}\_k (B) \\\\
\end{aligned}$$
>
> **证明**：每个 $\operatorname{col}\_k (A) \operatorname{row}\_k (B)$ 中的 $(i,j)$ 的元素，恰好是 $a_{i,k} b_{k,j}$，因此 $AB$ 的 $(i,j)$ 元素为 $\sum\limits_{k = 1}^n a_{i,k} b_{k,j}$，与行列法则相同。

## 分块矩阵的逆

> **分块上三角矩阵**：主对角线以下的块均为零矩阵的分块矩阵。

> **分块对角矩阵**：除主对角线以外的块均为零矩阵的分块矩阵。

要计算分块矩阵的逆，我们一般使用待定每个块，然后用分块矩阵列出若干个方程，并联立解出每个块的表达式。
