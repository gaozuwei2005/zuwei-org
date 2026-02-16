---
title: 线性代数 | 4.3 线性无关集和基
date: 2024-11-25
summary: 零空间、零空间的显式刻画、列空间、列空间的显式刻画、零空间和列空间的对比、线性变换的核与值域
---

我们希望生成集尽可能「有效」，那么我们就希望这个生成集能够线性无关。

## 线性无关集 *Linearly Independent Sets*

> **线性无关与线性相关** *Linearly Independent and Linearly Dependent*：
> 
> 对于一个线性空间 $V$ 中的有标号集合 *indexed set* $\\\{ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \\\}$，若向量方程 *vector equation*
>
> $$c_1\boldsymbol{a}_1 + c_2\boldsymbol{a}_2 + \cdots + c_n\boldsymbol{a}_n = \boldsymbol{0}$$
>
> 1. 只有平凡解 *has only the trivial solution*，则 $\\\{ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \\\}$ **线性无关（线性独立）** *linearly independent*。
> 2. 具有非平凡解 *nontrivial solution*，则 $\\\{ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \\\}$ **线性相关** *linearly dependent*。
> 
>       在这个情况下 $c_1\boldsymbol{a}_1 + c_2\boldsymbol{a}_2 + \cdots + c_n\boldsymbol{a}_n = \boldsymbol{0}$。称为 $\boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n$ 的一种线性相关关系 *linear dependence relation*。

> **定理 4**：若 $\\\{ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \\\}$ **线性相关**，则 $\exists j \in [1,n],  \boldsymbol{a}_j$ 可以表示为 $\boldsymbol{a}_2, \cdots, \boldsymbol{a}_{j-1}$ 的线性组合 *linear combination of the preceding vectors*。

## 基 *basis*

> **基** *basis*：子空间 $H$ 的一个子集 *subspace* $\mathcal B = \\\{ \boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$ 是 $H$ 的一个基，当且仅当 $\mathcal B$
>
> - 是 $H$ 的生成集 *spanning set*：$H = \operatorname{Span}\\\{ \boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$
> - 线性无关 *linearly independent*：$\mathcal B$ 中的向量线性无关。

基的一些例子：

- 对于 $n \times n$ 可逆矩阵 *invertible matrix* $A$，$A$ 中的列 *column* 组成的集合是 $\mathbb R^n$ 的一个基。
- $n \times n$ 单位矩阵的列组成的集合 $\\\{\boldsymbol{e}_1, \boldsymbol{e}_2, \cdots, \boldsymbol{e}_n\\\}$ 是 $\mathbb R^n$ 的**标准基** *standard basis*。
- $S = \\\{1, t, t^2, \cdots, t^n\\\}$ 是 $\mathbb P_n$ 的**标准基** *standard basis*。

## 生成集定理 *The Spanning Set Theorem*

> **定理 5（生成集定理）** *The Spanning Set Theorem*：若 $H = \operatorname{Span}\\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，令 $S = \\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，则由
> - 若 $b_i$ 可以表示为 $S$ 中其他向量的线性组合，则 $S \setminus \\\{\boldsymbol{b}_i\\\}$ *the set formed by $S$ by removing $\boldsymbol{b}_i$* 也是 $H$ 的生成集。
> - $S$ 的某一个子集是 $H$ 的一个基。
>
> **证明**：第一部分的证明通过系数表示，代入消元 *substituting the expression* 可以证明。
> 
> 第二部分是第一部分的结果 *repeat this process until the spanning set is lineatly independent and hen is a basis of $H$*。

## $\boldsymbol{\operatorname{Nul} A}$ 与 $\boldsymbol{\operatorname{Col} A}$ 的基 *Bases for Nul A and Col A*

> **定理 6**：矩阵 $A$ 的主元列 *pivot columns* 是 $\operatorname{Col} A$ 的一个基。
>
> **证明**：$A$ 中任意一个主元列表示的向量都不是前面主元列的线性组合 *no vector in the set is a linear combination of the vectors that precede it*。且行变换得到的前后矩阵的相关关系都一样。

注意：行变换前后矩阵的列空间会变化。提取主元列时必须提取原矩阵的主元列。

## 基的性质

- **基是尽可能小的生成集。** *smallest spanning set* 在生成集删除向量到线性无关之后，若再删除某个向量，则这个向量将不能被剩下的向量线性表示，故不能生成原子空间。
- **基是尽可能大的线性无关集。** *largest independent set* 对于一个基，若再添加一个向量，则这个向量必然可以被原来的基向量线性表示，使得线性相关。