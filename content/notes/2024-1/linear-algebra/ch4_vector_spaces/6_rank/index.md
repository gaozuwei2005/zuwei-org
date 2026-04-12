---
title: 线性代数 | 4.6 秩
date: 2024-11-20
summary: 行空间、秩定理、秩与方程组的情况的关系、秩与可逆矩阵定理
---

可以发现，$A$ 中线性无关行和线性无关列的个数是一样的，我们需要进一步讨论这一规律。

> **秩**：$\operatorname{Col} A$ 的维数，即线性无关列的数量。

## 行空间

> **行空间**：若 $A$ 是一个 $m \times n$ 的矩阵，则其所有行向量张成的线性空间成为 $A$ 的**行空间**。记为 $\operatorname{Row} A$。

行空间有以下性质：

- $\operatorname{Row} A$ 是 $\mathbb R^n$ 的子空间。
- $\operatorname{Col} A^T = \operatorname{Row} A$.

> **行等价**：两个矩阵 $A,B$ 行等价当且仅当它们的行空间相同。
>
> **证明**：由于 $A$ 经过行简化得到 $B$，那么$A,B$ 的行向量是对方行向量的线性组合，$\operatorname{Row} A = \operatorname{Row} B$。

> **定理 13** ：对于两个矩阵，若 $A,B$ 行等价，且 $B$ 是阶梯型矩阵，则 $B$ 的非零行构成 $A$ 的一个基。
>
> **证明**：因 $B$ 是阶梯型矩阵，因此非零行向量是 $\operatorname{Row} B$ 的基。又因 $\operatorname{Row} A = \operatorname{Row} B$，因此这个基也是 $A$ 的基。

## 秩定理


> **定理 14【秩定理】**：$m \times n$ 的矩阵 $A$ 的列空间和行空间的维数相等，且 $A$ 的秩满足
>
> $$\text{rank } A + \text{dim Nul A} = n$$
>
> 证明：
> 
> $$\text{主元列个数} + \text{非主元列个数} = \text{列的个数}$$

- 推论：$\text{Rank }A \le \min (m,n)$.

- 推论：$\text{dim Row }A = \text{dim Row} A^T = \text{Rank }A = \text{Rank }A^T$.
  - 证明：矩阵的非零子式的行列式在转置之后不变。

- $\operatorname{Row} A$ 与 $\operatorname{Nul} A$ 的公共向量只有零向量，事实上二者相互垂直。对应地， $\operatorname{Col} A$ 与 $\operatorname{Nul} A^T$ 也相互垂直。

## 应用到方程组

若系数矩阵的秩等于行数时，说明 $\operatorname{Rank} A=n$，则 $A \boldsymbol{x} = \boldsymbol{b}$ 对于任意的 $\boldsymbol{b}$ 均有解。

当系数矩阵的秩小于增广矩阵的秩时，方程组无解。

当系数矩阵的秩等于增广矩阵的秩时，方程组有解。

当系数矩阵的秩和增广矩阵的秩，与系数矩阵的行数和列数都相等，方程有唯一解。

## 秩与可逆矩阵定理

> **可逆矩阵定理（续）**：对于 $n \times n$ 矩阵 $A$，下面的命题均等价于 $A$ 是可逆矩阵 ：
>
> - $A$ 的列是 $\mathbb R^n$ 的一个基。
> - $\operatorname{Col} A = \mathbb R^n, \operatorname{rank} A = n, \operatorname{Nul} A = \{\boldsymbol{0}\}, \operatorname{dim\  Nul } A = 0$
>
> **证明**：第一个命题显然等于第二个命题，而 $\operatorname{dim\  Nul } A = 0$ 说明没有自由变量，从而使 $A\boldsymbol{x} = \boldsymbol{0}$ 只有平凡解，这与矩阵 $A$ 可逆是等价的。
>
> **拓展**：当然也可以行空间相关的命题加入可逆矩阵定理。