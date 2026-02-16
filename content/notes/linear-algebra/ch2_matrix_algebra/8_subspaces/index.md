---
title: 线性代数 | 2.8 R^n的子空间
date: 2024-12-05
summary: 子空间、列空间、零空间、基
---

**此部分内容是 4.1~4.3 的内容的子集，复习时可以直接略过该章节。**

## 子空间

> **子空间**：$\mathbb R^n$ 的一个子空间是 $\mathbb R^n$ 中的集合 $H$，具有以下三个性质：
>
> - （零向量）$\boldsymbol{0} \in H$
> - （对向量加法封闭）$\forall \boldsymbol{u,v} \in H, \boldsymbol{u} + \boldsymbol{v} \in H$
> - （对标量乘法封闭）$\forall \boldsymbol{u} \in H, c \in \mathbb{R}, c\boldsymbol{u} \in H$

判断一个集合是否为子空间，我们只需验证该集合是否有以上三个性质即可。

子空间的常见例子：

- 三维空间中，通过原点的一个平面。
- **由若干向量生成（张成）的子空间**：$H = \operatorname{Span}\\\{\boldsymbol{v}_1,\boldsymbol{v}_2, \cdots, \boldsymbol{v}_p\\\}$，其中 $\boldsymbol{v}_1,\boldsymbol{v}_2, \cdots, \boldsymbol{v}_p \in \mathbb R^n$。
- **零子空间**：$H = \\\{ \boldsymbol{0} \\\}$。

## 矩阵的列空间

> **列空间**：矩阵 $A$ 的列空间是 $A$ 的各列的线性组合，记作 $\operatorname{Col} A$。

若 $A = \left[\begin{matrix}
\boldsymbol{v}_1 & \boldsymbol{v}_2 & \cdots & \boldsymbol{v}_n
\end{matrix}\right]$，那么 $\operatorname{Col} A = \operatorname{Span}\\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n\\\}$，因此 **$m \times n$ 矩阵 $A$ 的列空间是 $\mathbb R^m$ 的子空间**。

判断一个向量是否在矩阵的列空间当中，我们只需对增广矩阵 $\left[\begin{matrix}A & \boldsymbol{b}\end{matrix}\right]$ 进行行简化，看是否有解即可。

> **列空间（以齐次方程定义）**：矩阵 $A$ 的列空间是齐次方程 $A\boldsymbol{x} = \boldsymbol{b}$ 有解的 $\boldsymbol{b}$ 的集合。

## 矩阵的零空间

> **零空间**：矩阵 $A$ 的零空间是齐次方程 $A\boldsymbol{x} = \boldsymbol{0}$ 的解的集合，记为 $\operatorname{Nul} A$。

> **定理 12**：$m \times n$ 矩阵 $A$ 的子空间是 $\mathbb R^n$ 的子空间。
>
> **证明**：我们需要验证 $\operatorname{Nul} A$ 作为子空间的三个性质。
> - 由于 $A \boldsymbol{0} = \boldsymbol{0}$，因此 $\boldsymbol{0} \in \operatorname{Nul} A$。
> - $\forall \boldsymbol{u}, \boldsymbol{v} \in \operatorname{Nul} A$，由于 $A\boldsymbol{u} = \boldsymbol{0}, A\boldsymbol{v} = \boldsymbol{0}$，因此 $A (\boldsymbol{u} + \boldsymbol{v}) = \boldsymbol{0}$，于是 $\boldsymbol{u} + \boldsymbol{v} \in \operatorname{Nul} A$。
> - $\forall \boldsymbol{u} \in \operatorname{Nul} A, c \in \mathbb R$，由于 $A\boldsymbol{u} = \boldsymbol{0}$，我们两边乘以 $c$，可以得到 $cA\boldsymbol{u} = A (c \boldsymbol{u}) = \boldsymbol{0}$，因此 $c \boldsymbol{u} \in \operatorname{Nul} A$。

## 基

> **基**：$\mathbb R^n$ 中子空间 $H$ 的一个子集 $\mathcal B = \\\{ \boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$ 是 $H$ 的一个基，当且仅当
>
> - 生成集：$H = \operatorname{Span}\\\{ \boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$
> - 线性无关：$\mathcal B$ 中的向量线性无关。

基的一些例子：

- 对于 $n \times n$ 可逆矩阵 $A$，$A$ 中的列组成的集合是 $\mathbb R^n$ 的一个基。
- $n \times n$ 单位矩阵的列组成的集合 $\\\{\boldsymbol{e}_1, \boldsymbol{e}_2, \cdots, \boldsymbol{e}_n\\\}$ 是 $\mathbb R^n$ 的**标准基**。
- $S = \\\{1, t, t^2, \cdots, t^n\\\}$ 是 $\mathbb P_n$ 的**标准基**。

## $\boldsymbol{\operatorname{Nul} A}$ 的基

要认识一个子空间，就要找到它的生成集，这样的过程称为一个子空间的**显式刻画**。

当我们解出 $A\boldsymbol{x} = \boldsymbol{0}$ 之后，就能得到 $\operatorname{Nul} A$ 的生成集。

1. 我们将 $[\begin{matrix} A & \boldsymbol{0} \end{matrix}]$ 行简化为阶梯型。
2. 将通解表示为以自由变量为系数的向量的线性组合，这些向量即是 $\operatorname{Nul} A$ 的生成集。

这样的过程得到的生成集的性质：

- 该生成集线性无关。
- 生成集中向量个数等于自由变量个数。

## $\boldsymbol{\operatorname{Col} A}$ 的基

> **定理 13**：矩阵 $A$ 的主元列构成 $A$ 的列空间的基。
>
> **证明**：首先，由于 $A \sim B$，那么 $A \boldsymbol{x} = \boldsymbol{0}$ 与 $B \boldsymbol{x} = \boldsymbol{0}$ 具有相同的解集，因此 $A$ 的列与 $B$ 的列有相同线性相关关系。
>
> 当我们行简化为阶梯型矩阵之后，剩下的主元列显然是一个 $B$ 的一个基，因此 $A$ 中的主元列是 $A$ 的一个基。
>
> **注意**：我们再取列作为线性基的时候，是取原矩阵的主元列，而不是行简化之后的主元列。