---
title: 线性代数 | 1.8 线性变换介绍
date: 2024-12-16
summary: 变换的定义、矩阵变换、线性变换
---

## 变换的定义

> **变换（函数、映射）**：把 $\mathbb R^n$ 的每个向量 $\boldsymbol{x}$ 对应以 $\mathbb R^m$  的一个向量 $T(x)$ 的变换。
>
> **定义域**： $\mathbb R^n$ 是 $T$ 的定义域。
>
> **余定义域（取值空间）**：$\mathbb R^m$ 是 $T$ 的余定义域。
>
> **像**：$\mathbb R^m$ 中向量 $T(\boldsymbol{x})$ 称为 $\boldsymbol{x}$ 的像。
>
> **值域**：所有像 $T(\boldsymbol{x})$ 的集合。

## 矩阵变换

> **矩阵变换**：$T : \boldsymbol{x} \mapsto A \boldsymbol{x}$ 是 $\mathbb R^m$ 到 $\mathbb R^n$ 的像，其中 $A$ 是 $n \times m$ 的矩阵。

矩阵变换的应用：投影变换、剪切变换

- 唯一性问题：$\boldsymbol{b}$ 是否为 $\mathbb R^m$ 中唯一的 $\boldsymbol{x}$ 的像。我们行化简增广矩阵看是否有 $m$ 个主元即可。

- 存在性问题：是否存在 $\mathbb R^m$ 的中的 $\boldsymbol{x}$ 使得它的像为 $\boldsymbol{c}$，我们行化简增广矩阵看是否相容即可。


## 线性变换

> **线性**：线性变换 $T: \mathbb R^m \to \mathbb R^n$ 的特征：
>
> 1. $T(\boldsymbol{u} + \boldsymbol{v}) = T(\boldsymbol{u}) + T(\boldsymbol{v}), \forall \boldsymbol{u,v} \in \mathbb R^m$
> 2. $T(c \boldsymbol{u}) = c T(\boldsymbol{u})$

从这两个特征可以推出以下性质：

3. $T(\boldsymbol{0}) = \boldsymbol{0}$

4. $T(c\boldsymbol{u} + d\boldsymbol{v}) = cT(\boldsymbol{u}) + dT(\boldsymbol{v}), \forall \boldsymbol{u,v} \in \mathbb R^m, c,d \in \mathbb R$