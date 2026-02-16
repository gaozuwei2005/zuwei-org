---
title: 线性代数 | 5.4 特征向量与线性变换
date: 2024-12-11
summary: 线性变换的矩阵、$V$ 到 $V$ 的线性变换、$\mathbb R^n$ 上的线性变换、相似性
---

## 线性变换的矩阵

我们接下来会研究两个向量空间之间的线性变换。

对于 $n$ 维向量空间 $V$ 和 $m$ 维向量空间 $W$，$T$ 是 $V$ 到 $W$ 的线性变换，我们需要定义并找出 $T$ 的标准矩阵。

若 $V$ 的基为 $\mathcal B = \\\{\boldsymbol{b}\_1, \boldsymbol{b}\_2, \cdots, \boldsymbol{b}\_n\\\}$，$W$ 的基为 $\mathcal C = \\\{\boldsymbol{c}\_1, \boldsymbol{c}\_2, \cdots, \boldsymbol{c}\_n\\\}$，对于 $\boldsymbol{x} \in V$，若 $\boldsymbol{x} = r\_1 \boldsymbol{b}\_1 + r\_2 \boldsymbol{b}\_2 + \cdots + r\_n \boldsymbol{b}\_n$，那么

$$T(\boldsymbol{x}) = T(r\_1 \boldsymbol{b}\_1 + r\_2 \boldsymbol{b}\_2 + \cdots + r\_n \boldsymbol{b}\_n) = r\_1 T(\boldsymbol{b}\_1) + r\_2 T(\boldsymbol{b}\_1) + \cdots + r\_n T(\boldsymbol{b}\_n)$$

因此

$$\begin{aligned}
[T(\boldsymbol{x})]\_{\mathcal C} &= r\_1 [T(\boldsymbol{b}\_1)]\_\mathcal C + r\_2 [T(\boldsymbol{b}\_2)]\_\mathcal C + \cdots + r\_n [T(\boldsymbol{b}\_n)]\_\mathcal C \\\\
&= \left[
    \begin{matrix}
        [T(\boldsymbol{b}\_1)]\_\mathcal C & [T(\boldsymbol{b}\_2)]\_\mathcal C & \cdots & [T(\boldsymbol{b}\_n)]\_\mathcal C
    \end{matrix}
\right]
\left[
    \begin{matrix}
    r\_1 \\\\
    r\_2 \\\\
    \vdots \\\\
    r\_n
    \end{matrix}
\right] \\\\
&= M [\boldsymbol{x}]\_\mathcal B
\end{aligned}$$

> **线性变换相对于两个基的矩阵**：对于两个向量空间 $V,W$，它的基是 $\mathcal B, \mathcal C$，那么从 $V$ 到 $W$ 的线性变换 $T$ 相对于基 $\mathcal B, \mathcal C$ 的矩阵为
>
> $$M = \left[
    \begin{matrix}
        [T(\boldsymbol{b}\_1)]\_\mathcal C & [T(\boldsymbol{b}\_2)]\_\mathcal C & \cdots & [T(\boldsymbol{b}\_n)]\_\mathcal C
    \end{matrix}
\right]$$
>
> 那么 $T$ 对 $\boldsymbol{x}$ 的作用，我们已知 $[\boldsymbol{x}]\_\mathcal B$，那么作用后的坐标为
>
> $$[T(\boldsymbol{x})]\_\mathcal C = M [\boldsymbol{x}]\_\mathcal B$$

##  $V$ 到 $V$ 的线性变换

> **同向量空间线性变换相对于同基的矩阵**：对于一个向量空间 $V$，它的基是 $\mathcal B$，那么从 $V$ 到 $V$ 的线性变换 $V$ 相对于基 $\mathcal B, \mathcal B$ 的矩阵，称为 $T$ 相对于 $\mathcal B$ 的矩阵，或 $T$ 的 $\mathcal B-$矩阵。此时
>
> $$[T]\_\mathcal B = \left[
    \begin{matrix}
        [T(\boldsymbol{b}\_1)]\_\mathcal B & [T(\boldsymbol{b}\_2)]\_\mathcal B & \cdots & [T(\boldsymbol{b}\_n)]\_\mathcal B
    \end{matrix}
\right]$$
>
> 于是对于一个 $\boldsymbol{x} \in V$，有
>
> $$[T(\boldsymbol{x})]\_\mathcal C = M [\boldsymbol{x}]\_B$$

## $\mathbb R^n$ 上的线性变换

> **定理 8（对角矩阵表示）**：设 $A = PDP^{-1}$，且 $D$ 为 $n \times n$ 对角矩阵，若 $P$ 由 $\mathbb R^n$ 的一个基 $\mathcal B$ 中的向量组成，那么 $D$ 是变换 $T: \boldsymbol{x} \mapsto A \boldsymbol{x}$ 的 $\mathcal B-$矩阵。
>
> **证明**：
> 
> 首先，对于 $P$ 有
>
> $$P[\boldsymbol{x}]\_\mathcal B = \boldsymbol{x},\ [\boldsymbol{x}]\_\mathcal B = P^{-1} \boldsymbol{x}$$
>
> 因此
> 
> $$\begin{aligned}
[T]\_\mathcal B &= \left[
    \begin{matrix}
        [T(\boldsymbol{b}\_1)]\_\mathcal B & [T(\boldsymbol{b}\_2)]\_\mathcal B & \cdots & [T(\boldsymbol{b}\_n)]\_\mathcal B
    \end{matrix}
\right] \\\\
&= \left[
    \begin{matrix}
        [A\boldsymbol{b}\_1]\_\mathcal B & 
        [A\boldsymbol{b}\_2]\_\mathcal B & 
        \cdots & 
        [A\boldsymbol{b}\_n]\_\mathcal B
    \end{matrix}
\right] \\\\
&= \left[
    \begin{matrix}
        P^{-1}A\boldsymbol{b}\_1 & 
        P^{-1}A\boldsymbol{b}\_2 & 
        \cdots & 
        P^{-1}A\boldsymbol{b}\_n
    \end{matrix}
\right] \\\\
&= P^{-1}AP \\\\
&= P^{-1} (PDP^{-1}) P \\\\
&= D \\\\
\end{aligned}$$

## 矩阵表示的相似性

事实上，定理 8 可以推广到 $D$ 不是对角矩阵的情况。我们只需要找到任何一个和 $A$ 相似的矩阵即可。该定理的原理：若 $A = PCP^{-1}$，则有

$$(PCP^{-1})\boldsymbol{x} = PC [x]\_{\mathcal B} = P[A\boldsymbol{x}]\_\mathcal B = A\boldsymbol{x}$$

在 $\mathbb R^n$ 上进行的矩阵变换 $\boldsymbol{x} \mapsto A\boldsymbol{x}$，相当于在以 $\mathcal B$ 为基上进行的矩阵变换 $[x]\_{\mathcal B} \mapsto [A\boldsymbol{x}]\_\mathcal B$，它们的标准矩阵分别是 $A,C$，所以我们会称 $A,C$ 是相似的。