---
title: 线性代数 | 2.9 维数与秩
date: 2024-12-06
summary: 坐标系、子空间的维数、秩和可逆矩阵定理
---

**此部分内容是 4.4~4.6 的内容的子集，复习时可以直接略过该章节。**

## 坐标系

> **定理 7（唯一表示定理）**：对于向量空间 $V$ 的一个有编号基 $\mathcal B = \\\\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\\\}$，对于 $V$ 中任意一个向量 $\boldsymbol{x}$，存在唯一的一组数 $c_1, c_2, \cdots, c_n$，使得
>
> $$\boldsymbol{x} = c_1 \boldsymbol{b}_1 + c_2 \boldsymbol{b}_2 + \cdots + c_n \boldsymbol{b}_n$$
>
> 证明：运用反证法。若有另一种表示，则两式相减，得到一组基线性表示零向量的非平凡解，矛盾。从而证明定理。

> **坐标**：对于向量空间 $V$ 的一个有编号基 $\mathcal B = \\\\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\\\}$，对于 $V$ 中的某个向量 $\boldsymbol{x}$，**$\boldsymbol{x}$ 相对基 $\mathcal{B}$ 的坐标（$\boldsymbol{x}$ 的 $\mathcal{B} -$坐标）** 是唯一的一组数 $c_1, c_2, \cdots, c_n$，使得
>
> $$\boldsymbol{x} = c_1 \boldsymbol{b}_1 + c_2 \boldsymbol{b}_2 + \cdots + c_n \boldsymbol{b}_n$$

> **坐标向量**：若 $\boldsymbol{x}$ 的 $\mathcal{B} -$坐标是唯一的一组数 $c_1, c_2, \cdots, c_n$，则 **$\boldsymbol{x}$ 相对于 $\mathcal{B}$ 的坐标向量（$\boldsymbol{x}$ 的 $\mathcal{B} -$坐标向量）** 是
>
> $$[x]_{\mathcal{B}} = \left[
    \begin{matrix}
    c_1 \\\\
    c_2 \\\\
    \vdots \\\\
    c_n \\\\
    \end{matrix} \right]$$

若已知 $\boldsymbol{x}$ 在 $\mathbb R^n$ 中的坐标，当确定了一组基 $\mathcal{B}$ 之后，我们希望求出 $[x]_\mathcal{B}$。

我们构建基和 $x$ 的坐标向量的增广矩阵 $\begin{bmatrix}
    \boldsymbol{b}\_1 &
    \boldsymbol{b}\_2 &
    \cdots
    \boldsymbol{b}\_n & 
    \boldsymbol{x}
    \end{bmatrix}$ ，进行行简化即可得到 $
    \begin{bmatrix}
    I_n & 
    \boldsymbol{[x]_\mathcal{B}}
    \end{bmatrix}
$，此时我们就能得到 $x$ 相对于 $\mathcal B$ 的坐标向量。

> **同构**：$V \mapsto W$ 的一对一线性变换称为 $V$ 和 $W$ 上的一个**同构**。每一个在 $V$ 中的向量空间的计算可以完全相同地出现在 $W$ 中。

## 子空间的维数

> **$\dim V$ 的定义**：向量空间的 $V$ 的维数，即 $V$ 的基的向量个数。
>
> 若 $V$ 可由有限集生成，则称 $V$ 是有限维的；否则，称 $V$ 是无限维的。$\\\\\{\boldsymbol{0}\\\\\}$ 的维数为 $0$。

> **定理 14（秩定理）**：$m \times n$ 的矩阵 $A$ 的列空间和行空间的维数相等，且 $A$ 的秩满足
>
> $$\text{rank } A + \text{dim Nul A} = n$$
>
> 证明：
> 
> $$\text{主元列个数} + \text{非主元列个数} = \text{列的个数}$$

> **定理 15（基定理）**：令 $V$ 是一个 $n$ 维向量空间（$n \ge 1$），那么对于 $V$ 中的一个含有 $n$ 个向量的子集 $\mathcal B$，它是 $V$ 的一个基需要满足以下两个条件之一：
>
> - $\mathcal B$ 中向量线性无关；
> - $\mathcal B$ 中向量可张成 $V$，即 $\mathcal B$ 是 $V$ 的一个生成集。
>
> **证明**：
>
> - 线性无关集 $\mathcal B$ 可以扩充为 $V$ 的一个基，由于 $\dim V = n$，因此 $\mathcal B$ 是 $V$ 的一个基；
> - 生成集 $\mathcal B$ 中存在一个子集是 $V$ 的基，由于 $\dim V = n$，因此 $\mathcal B$ 是 $V$ 的一个基。

因此，我们只要知道向量空间的维数 $n$，然后我们只需要找一个大小为 $n$ 的线性无关集或者生成集，就能找到向量空间的基。

## 秩与可逆矩阵定理

> **可逆矩阵定理（续）**：对于 $n \times n$ 矩阵 $A$，下面的命题均等价于 $A$ 是可逆矩阵 ：
>
> - $A$ 的列是 $\mathbb R^n$ 的一个基。
> - $\operatorname{Col} A = \mathbb R^n, \operatorname{rank} A = n, \operatorname{Nul} A = \\\\\{\boldsymbol{0}\\\\\}, \operatorname{dim\  Nul } A = 0$
>
> **证明**：第一个命题显然等于第二个命题，而 $\operatorname{dim\  Nul } A = 0$ 说明没有自由变量，从而使 $A\boldsymbol{x} = \boldsymbol{0}$ 只有平凡解，这与矩阵 $A$ 可逆是等价的。