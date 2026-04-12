---
title: 线性代数 | 4.2 零空间、列空间和线性变换
date: 2024-11-25
summary: 零空间、零空间的显式刻画、列空间、列空间的显式刻画、零空间和列空间的对比、线性变换的核与值域
---

## 矩阵的零空间 *The Null Space of a Matrix*

齐次方程组和对应的矩阵方程 $A\boldsymbol{x} = \boldsymbol{0}$ 是密切相关的。

> **解集**：齐次方程组 *symtem of homogeneous equations* 中所有可能的解的集合 *solution set of the system*。

> **零空间** *null space*：$\operatorname{Nul} A$ 是所有满足 $A\boldsymbol{x} = \boldsymbol{0}$ 的 $\boldsymbol{x}$ 的集合，它的集合表示 *set notation* 为
>
> $$\operatorname{Nul} A = \\\{\boldsymbol{x} | \boldsymbol{x} \in \mathbb R^n , A\boldsymbol{x} = \boldsymbol{0}\\\}$$
>
> （与线性变换相关的定义）$\operatorname{Nul} A$ 是所有向量 $x \in \mathbb R^n$ 满足通过线性变换 $x \mapsto A\boldsymbol{x}$ 映射到 $\boldsymbol{0} \in \mathbb R^m$ 的集合。

> **定理 2**：$m \times n$ 的矩阵 $A$ 的零空间 $\operatorname{Nul} A$ 是 $\mathbb R^n$ 的一个子空间。
>
> **证明**：从零空间存在零向量（对应平凡解）、对加法封闭、对乘法封闭来证明。

## $\boldsymbol{\operatorname{Nul} A}$ 的显式刻画（基） *An Explicit Description of Nul A*

要认识一个子空间，就要找到它的生成集 *spanning set*，这样的过程称为一个子空间的**显式刻画**。

当我们解出 $A\boldsymbol{x} = \boldsymbol{0}$ 之后，就能得到 $\operatorname{Nul} A$ 的生成集。

1. 我们将 $[\begin{matrix} A & \boldsymbol{0} \end{matrix}]$ 行简化为阶梯型。
2. 将通解表示为以自由变量为系数的向量的线性组合，这些向量即是 $\operatorname{Nul} A$ 的生成集。

这样的过程得到的生成集的性质：

- 该生成集线性无关 *linear independent*。
- 生成集中向量个数 *the number of vectors in the spanning set* 等于自由变量个数 *the number of free variables*。

## 矩阵的列空间 *Column Space of a Matrix*

> **列空间**：$\operatorname{Col} A$ 是 $m \times n$ 矩阵 $A$ 中所有列的所有线性组合 *linear combinations* 组成的集合。若 $A = \left[ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \right]$，则 $\operatorname{Col} A = \operatorname{Span}\\\{ \boldsymbol{a}_1, \boldsymbol{a}_2, \cdots, \boldsymbol{a}_n \\\}$。
> 
> $$\operatorname{Col} A = \\\{ \boldsymbol{b} | \boldsymbol{b} = A \boldsymbol{x}, \boldsymbol{x} \in \mathbb{R}^n \\\}$$
> 
> （与线性变换相关的定义）$\operatorname{Col} A$ 是线性变换 $\boldsymbol{x} \mapsto A\boldsymbol{x}$ 的值域 *range*。

> **定理 3**：$\operatorname{Col} A$ 是 $\mathbb{R}^n$ 的子空间。
>
> **证明**：根据定理 1，以及 $\operatorname{Col} A$ 的定义易得。

> $\operatorname{Col} A = \mathbb{R}^m \Leftrightarrow \forall \boldsymbol{b} \in \mathbb{R}^m, \exists \boldsymbol{x} \in \mathbb R^n, A \boldsymbol{x} = \boldsymbol{b}$
>
> *The column space of an $m \times n$ matrix $A$ is all of $\mathrm R^m$ if and only if the equation $A\boldsymbol{x} = \boldsymbol{b}$ has a solution for each $b$ in $\mathrm R^m$.*

## $\boldsymbol{\operatorname{Col} A}$ 的显式刻画（基）

> **定理**：矩阵 $A$ 的主元列构成 $A$ 的列空间的基。
>
> **证明**：首先，由于 $A \sim B$，那么 $A \boldsymbol{x} = \boldsymbol{0}$ 与 $B \boldsymbol{x} = \boldsymbol{0}$ 具有相同的解集，因此 $A$ 的列与 $B$ 的列有相同线性相关关系。
>
> 当我们行简化为阶梯型矩阵之后，剩下的主元列显然是一个 $B$ 的一个基，因此 $A$ 中的主元列是 $A$ 的一个基。
>
> **注意**：我们再取列作为线性基的时候，是取原矩阵的主元列，而不是行简化之后的主元列。

## $\boldsymbol{\operatorname{Nul} A}$ 与 $\boldsymbol{\operatorname{Col} A}$ 的对比 *constrast*

- 维度大小：对于 $m \times n$ 矩阵 $A$，
  - $\operatorname{Nul} A$ 是 $\mathbb R^n$ 的子空间 *Subspace*。
  - $\operatorname{Col} A$ 是 $\mathbb R^m$ 的子空间 *Subspace*。
- 显式刻画：
  - $\operatorname{Nul} A$ 被被隐式定义的 *implicitly defined*。需要行简化才能得到显式刻画。
  - $\operatorname{Col} A$ 是被显式定义的 *explicitly defined*。取 $A$ 中各列即可。
- 张成判断：
  - $\operatorname{Nul} A$ 中的元素满足 $A\boldsymbol{x} = \boldsymbol{0}$。
  - $\operatorname{Col} A$ 中的元素满足 $A\boldsymbol{x} = \boldsymbol{b}$ 有解（相容）*consistent*。
- 线性变换 *linear transformation*：
  - $\operatorname{Nul} A = \\\{\boldsymbol{0}\\\}$ 当且仅当 $A\boldsymbol{x} = \boldsymbol{0}$ 仅有平凡解，线性变换 $\boldsymbol{x} \mapsto A\boldsymbol{x}$ 一对一 *one-to-one*；
  - $\operatorname{Col} A = \mathbb{R}^m$ 当且仅当 $\forall \boldsymbol{b} \in \mathbb{R}^m, A \boldsymbol{x} = \boldsymbol{b}$ 有解，线性变换 $x \mapsto A\boldsymbol{x}$ 将 $\mathbb R^n$ 映上 $\mathbb R^m$ *map $\mathbb R^n$ onto $\mathbb R^m$*。

## 线性变换的核与值域

> **线性变换** *linear transformation*：从向量空间 $V$ 映射到 *into* 向量空间 $W$ 的规则 *rule*：$x \mapsto T(x)$，满足
> - 对加法封闭：$\forall \boldsymbol{u,v} \in V, T(\boldsymbol{u} + \boldsymbol{v}) = T(\boldsymbol{u}) + T(\boldsymbol{v})$.
> - 对标量乘法封闭：$\forall c \in \mathbb R, \boldsymbol{u} \in V, T(c\boldsymbol{u}) = cT(\boldsymbol{u})$.

> **线性变换的核（零空间）** *kernel (null space) of $T$*：$V$ 中所有满足 $T(\boldsymbol{u}) = \boldsymbol{0} \in W$ 的集合。
>
> 若 $T$ 可以表示为 $\boldsymbol{x} \mapsto A\boldsymbol{x}$，则 $T$ 的核即为 $\operatorname{Nul} A$。

> **线性变换的值域** *range of $T$*：所有 $T(\boldsymbol{u}), \boldsymbol{u} \in V$ 的集合。
>
> 若 $T$ 可以表示为 $\boldsymbol{x} \mapsto A\boldsymbol{x}$，则 $T$ 的核即为 $\operatorname{Col} A$。

可见 $T$ 的核是 $V$ 的子空间，$T$ 的值域是 $W$ 的子空间。

线性变换的例子：
- 微分运算是一个线性变换。
- 齐次线性微分方程是一个线性变换的核。