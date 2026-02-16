---
title: 线性代数 | 4.4 坐标系
date: 2024-11-25
summary: 坐标相关定理、坐标的几何表示、$\mathbb{R}^n$ 的坐标映射、一般向量空间的坐标映射
---

确定了向量空间的基，我们就可以在此基础上加上一个坐标系。

## 坐标相关定理与定义

> **定理 7（唯一表示定理）** *The Unique Representation Theorem*：对于向量空间 $V$ 的一个有编号基 $\mathcal B = \\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，对于 $V$ 中任意一个向量 $\boldsymbol{x}$，存在唯一的一组数 *there exists a unique set of scalars* $c_1, c_2, \cdots, c_n$，使得
>
> $$\boldsymbol{x} = c_1 \boldsymbol{b}_1 + c_2 \boldsymbol{b}_2 + \cdots + c_n \boldsymbol{b}_n$$
>
> 证明：运用反证法。若有另一种表示，则两式相减 *subtracting*，得到一组基线性表示零向量的非平凡解，矛盾。从而证明定理。

> **坐标** *coordinate*：对于向量空间 $V$ 的一个有编号基 $\mathcal B = \\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，对于 $V$ 中的某个向量 $\boldsymbol{x}$，**$\boldsymbol{x}$ 相对基 $\mathcal{B}$ 的坐标（$\boldsymbol{x}$ 的 $\mathcal{B} -$坐标）** 是唯一的一组数 $c_1, c_2, \cdots, c_n$ *coordinates of x relative to the basis B (B-coordinate of x)*，使得
>
> $$\boldsymbol{x} = c_1 \boldsymbol{b}_1 + c_2 \boldsymbol{b}_2 + \cdots + c_n \boldsymbol{b}_n$$

> **坐标向量** *coordinate vector*：若 $\boldsymbol{x}$ 的 $\mathcal{B} -$坐标是唯一的一组数 $c_1, c_2, \cdots, c_n$，则 **$\boldsymbol{x}$ 相对于 $\mathcal{B}$ 的坐标向量（$\boldsymbol{x}$ 的 $\mathcal{B} -$坐标向量）** *the coordinate vector of x (relative to B) or the B-coordinate vector of x*是
>
> $$[x]_{\mathcal{B}} = \left[
    \begin{matrix}
    c_1 \\\\
    c_2 \\\\
    \vdots \\\\
    c_n \\\\
    \end{matrix} \right]$$

> **坐标映射** *coordinate mapping*：映射 $x \mapsto [x]_{\mathcal{B}}$ 是 **由 $\mathcal B$ 确定的 $\mathbb R^n \mapsto \mathbb R^n$ 的坐标映射** *coordinate mapping (determined by B)*。

$\boldsymbol{x}$ 的 $\mathcal{B-}$坐标揭示了如何从 $\mathcal B$ 中的向量求 $\boldsymbol{x}$。

## 坐标的几何表示 *A Graphical Interpretation of Coordinates*

基中的向量所在的直线构成坐标轴 *axis*。基中的向量是各个坐标轴的单位向量 *unit of measurement on each axis*。

## $\mathbb{R}^n$ 中的坐标映射

已知 $\boldsymbol{x}$ 在 $\mathbb R^n$ 中的坐标，当确定了一组基 $\mathcal{B}$ 之后，我们希望求出 $[x]_\mathcal{B}$。

我们构建基和 $x$ 的坐标向量的增广矩阵 $
    \begin{bmatrix}
    \boldsymbol{b}\_1 &
    \boldsymbol{b}\_2 &
    \cdots
    \boldsymbol{b}\_n & 
    \boldsymbol{x}
    \end{bmatrix}$ ，进行行变换即可得到 $
    \begin{bmatrix}
    I\_n & 
    \boldsymbol{[x]\_\mathcal{B}}
    \end{bmatrix}$

> **坐标变换矩阵** *change-of-coordinates matrix*：对于 $\mathbb R^n$ 的一组基 $\mathcal{B} = \\\{\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_n \\\}$，则从 $\mathcal B$ 到 $\mathbb R^n$ 中标准基的坐标变换矩阵为一个 $n \times n$ 的矩阵
>
> $$P_\mathcal B = \left[\begin{matrix}
    \boldsymbol{b}_1 &
    \boldsymbol{b}_2 &
    \cdots
    \boldsymbol{b}_n
    \end{matrix}\right]$$
>
> 则有 *change-of-coordinates equation*
>
> $$\boldsymbol{x} = P_\mathcal B [\boldsymbol{x}]_\mathcal B$$

由于 $P_\mathcal B$ 中的列线性独立，因此矩阵可逆，因此有

$$P_\mathcal B^{-1} \boldsymbol{x} = [\boldsymbol{x}]_\mathcal B$$

这相当于我们如果知道 $\boldsymbol{x}$ 的原坐标，我们可以通过这个变换得到 $\boldsymbol{x}$ 的 $\mathcal B-$坐标表示。这是 $\mathbb R^n \mapsto \mathbb R^n$ 的一对一线性变换。

这个性质对于一般向量空间也成立。

## 一般向量空间的坐标映射 *Coordinate Mapping*

> **定理 8**：令 $\mathcal{B} = \\\{\boldsymbol{b}\_1, \boldsymbol{b}\_2, \cdots, \boldsymbol{b}\_n \\\}$ 是向量空间 $V$ 的一个基，那么坐标映射 $x \mapsto [x]_\mathcal B$ 是 $V \to \mathbb R^n$ 的一对一且映到 $\mathrm R^n$的线性变换 *one-to-one linear transformation from $V$ onto $\mathrm R^n$*。
>
**证明**：

1. 验证 $x \mapsto [x]\_\mathcal B$ 对向量加法和标量乘法封闭即可。
2. 由于基是线性无关，因此坐标映射是一对一的。由于对于任意坐标 $[\boldsymbol{x}]\_\mathcal B$ 都有对应的 $V$ 的向量，所以坐标映射映上 $\mathrm R^n$。

> **推广（坐标映射的线性性）** *linearity*： $\forall \boldsymbol{u}\_1, \boldsymbol{u}\_2, \cdots, \boldsymbol{u}\_p \in V, c\_1, c\_2, \cdots, c\_p \in R$，有
>
> $$[c\_1 \boldsymbol{u}\_1 + c\_2 \boldsymbol{u}\_2 + \cdots + c\_p \boldsymbol{u}\_p]\_\mathbb B = c\_1 [\boldsymbol{u}\_1]\_\mathbb B + c\_2 [\boldsymbol{u}\_2]\_\mathbb B + \cdots + c\_p [\boldsymbol{u}\_p]\_\mathbb B$$

> **同构** *isomorphism*：$V \mapsto W$ 的一对一线性变换称为 $V$ 和 $W$ 上的一个**同构**。每一个在 $V$ 中的向量空间的计算可以完全相同地出现在 $W$ 中 (indistinguishable as vector spaces)。

例如，$\mathcal{B} = \\\{1, t, t^2, t^3\\\}$ 是 $\mathbb P_3$ 的标准基，那么对于任意 $\boldsymbol{p} = a_0 + a_1t + a_2t^2 + a_3t^3$，其坐标为 $\[\boldsymbol{p}\]\_\mathcal B = 
    \begin{bmatrix}
    a\_0 \\\\
    a\_1 \\\\
    a\_2 \\\\
    a\_3 \\\\
    \end{bmatrix}$。那么我们称 $\boldsymbol{p} \mapsto [\boldsymbol{p}]_\mathcal B$ 为 $\mathbb P_3$ 到 $\mathbb R^4$ 的同构。

对于某一个陌生的线性空间，我们可以先找它的基 $\mathcal B$，并将所有的向量 $\boldsymbol{v}$ 线性变换为 $\mathbb R^n$ 的坐标 $[\boldsymbol{v}]_\mathcal B$。由于这样的变换是同构的，那么原线性空间的线性相关、解方程等等的问题就可以转换为坐标向量在 $\mathbb R^n$ 上的问题。