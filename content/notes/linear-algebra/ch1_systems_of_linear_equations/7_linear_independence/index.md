---
title: 线性代数 | 1.7 线性无关
date: 2024-12-15
summary: 线性相关的定义、矩阵各列的线性无关
---

## 线性相关的定义

> $\mathrm R^n$ 中一组向量 $\mathcal V = \\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_p\\\}$ 
> 
> **线性无关**：$\mathcal V$ 线性无关，当且仅当向量方程 $x_1 \boldsymbol{v}_1 + x_2 \boldsymbol{v}_2 + \cdots + x_p \boldsymbol{v}_p = \boldsymbol{0}$ 仅有平凡解。
>
> **线性相关**：$\mathcal V$ 线性相关，当且仅当向量方程 $x_1 \boldsymbol{v}_1 + x_2 \boldsymbol{v}_2 + \cdots + x_p \boldsymbol{v}_p = \boldsymbol{0}$ 存在非平凡解。
>
> 其中该方程称为 $\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_p$ 的线性相关关系。


两个向量组成的集合 $\\\{ \boldsymbol{v}_1, \boldsymbol{v}_2\\\}$ 线性相关，当且仅当一个向量是另一个向量的倍数。

> **定理 7（线性相关集的特征）**：两个或更多个向量的集合 $S = \\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_p\\\}$ 线性相关，当且仅当至少一个向量是其他向量的线性组合。若 $S$ 线性相关，且 $\boldsymbol{v}_1 \ne \boldsymbol{0}$，则某个 $\boldsymbol{v}\_j (j > 1)$ 是它前面向量 $\boldsymbol{v}\_1, \cdots, \boldsymbol{v}\_{j-1}$ 的线性组合。

> **定理 8**：若一个向量组的向量个数超过每个向量的元素个数，那么这个向量组线性相关。

## 矩阵各列的线性无关

矩阵 $A$ 的各列线性无关，当且仅当方程 $A\boldsymbol{x} = \boldsymbol{0}$ 仅有平凡解。