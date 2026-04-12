---
title: 线性代数 | 4.5 向量空间的维数
date: 2024-11-25
summary: 维数的定义、有限维空间的子空间、列空间和零空间的维数
---

## 维数的定义

> **定理 9**：若向量空间 $V$ 有一组基 $\mathcal B = \\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，那么 $V$ 中任意包含多于 $n$ 个向量的集合一定线性相关。
>
> **证明**：利用 $\boldsymbol{x} \mapsto [\boldsymbol{x}]_\mathcal B$ 映射到 $\mathbb{R}^n$ 上考虑。
> 
> 设 $\\\{\boldsymbol{v\_1}, \boldsymbol{v\_2}, \cdots, \boldsymbol{v\_p}\\\}$ 是数量大于 $n$ 的 $V$ 的子集，那么坐标向量为 $\\\{[\boldsymbol{v\_1}]\_{\mathcal{B}}, {[\boldsymbol{v\_2}]}\_{\mathcal{B}}, \cdots, {[\boldsymbol{v\_p}]}\_{\mathcal{B}}\\\}$。
>
> 由于 $p > n$，因此这些坐标向量必定线性相关，从而原来的向量也线性相关。

> **定理 9 推论（逆否命题）**：若向量空间 $V$ 具有一组基 $\mathcal{B} = \\\{\boldsymbol{b_1}, \boldsymbol{b_2}, \cdots, \boldsymbol{b_n}\\\}$，那么 $V$ 中的线性无关集，向量数量必定不超过 $n$。

> **定理 10**：若向量空间 $V$ 具有一组基 $\mathcal{B} = \\\{\boldsymbol{b_1}, \boldsymbol{b_2}, \cdots, \boldsymbol{b_n}\\\}$，那么 $V$ 的所有基的向量个数一定为 $n$。
>
> **证明：** 设 $\mathcal{B'}$ 是另一组基，数量为 $p$。
>
> 由于 $B'$ 中向量线性无关，那么由**定理 9** 可知 $p \le n$；
>
> 由于 $B$ 中向量线性无关，那么由**定理 9** 可知 $n \le p$。
>
> 综上，$n = p$。

> **$\dim V$ 的定义**：向量空间的 $V$ 的维数 *dimension of V*，即 $V$ 的基的向量个数。
>
> 若 $V$ 可由有限集生成，则称 $V$ 是有限维的 *finite-dimensional*；否则，称 $V$ 是无限维的 *infinite-dimensional*。$\\\{\boldsymbol{0}\\\}$ 的维数为 $0$。

一般而言，$\dim \mathbb{P}_n = n + 1$，所有多项式的空间 $\mathbb P$ 是无限维的。

## 有限维空间的子空间

> **定理 11**：若 $H$ 是有限维向量空间 $V$ 的子空间，那么 $H$ 也是有限维向量空间，且
>
> $$\dim H \le \dim V$$
>
> **证明**：$H$ 的基的数量等于 $\dim H$。而因为这个基是 $S$ 的一个线性无关集，因此不能超过 $\dim V$，因此 $\dim H \le \dim V$。

> **定理 12（基定理）** *The Basis Theorem*：令 $V$ 是一个 $n$ 维向量空间（$n \ge 1$），那么对于 $V$ 中的一个含有 $n$ 个向量的子集 $\mathcal B$，它是 $V$ 的一个基需要满足以下两个条件之一：
>
> - $\mathcal B$ 中向量线性无关；
> - $\mathcal B$ 中向量可张成 $V$，即 $\mathcal B$ 是 $V$ 的一个生成集。
>
> **证明**：
>
> - 线性无关集 $\mathcal B$ 可以扩充为 $V$ 的一个基，由于 $\dim V = n$，因此 $\mathcal B$ 是 $V$ 的一个基；
> - 生成集 $\mathcal B$ 中存在一个子集是 $V$ 的基，由于 $\dim V = n$，因此 $\mathcal B$ 是 $V$ 的一个基。

因此，我们只要知道向量空间的维数 $n$，然后我们只需要找一个大小为 $n$ 的线性无关集或者生成集，就能找到向量空间的基。

## $\operatorname{Nul} \boldsymbol{A}$ 和 $\operatorname{Col} \boldsymbol{A}$ 的维数

> $\operatorname{Nul} A$ 的维数是方程 $A \boldsymbol{x} = \boldsymbol{0}$ 中自由变量的个数 *free variables*。
>
> $\operatorname{Col} A$ 的维数是 $A$ 中主元列的个数 *pivot columns*。