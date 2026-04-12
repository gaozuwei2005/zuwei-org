---
title: 线性代数 | 2.1 矩阵运算
date: 2024-11-30
summary: 矩阵定义、矩阵加法、矩阵乘法、矩阵乘幂、矩阵转置
---

## 矩阵的相关定义

> **矩阵中的元素** *entry*：对于 $m \times n$ 矩阵 $A$，那么 $A$ 的 $(i,j)$ 号元素称为其中的第 $i$ 行第 $j$ 列的元素，记为 $a_{ij}$。
>
> **列向量**：$A$ 的各列是 $\mathbb R^m$ 的向量，记作 $A = \left[
\begin{matrix}
\boldsymbol{a}_1 & \boldsymbol{a}_2 & \cdots & \boldsymbol{a}_n
\end{matrix}
\right]$。
>
> $a_{ij}$ 是第 $j$ 个列向量 $\boldsymbol{a}_j$ 自上而下的第 $i$ 个元素。

> **对角线元素和主对角线**：$m \times n$ 矩阵 $A$ 中 $a_{11}, a_{22}, a_{33}, \cdots$ 称为 $A$ 的**对角线元素**，它们组成 $A$ 的**主对角线**。

> **对角矩阵**：非对角线元素均为 $0$ 的方阵。
>
> **单位矩阵** *identity matrix*：非对角线元素均为 $0$，主对角线元素均为 $1$ 的 $n \times n$ 的矩阵记为 $I_n$。
>
> **零矩阵** *zero matrix*：元素全为 $0$ 的矩阵记为 $\boldsymbol{0}$。若有必要，可以记为 $\boldsymbol{0}_{m \times n}$.

## 矩阵加法与向量乘法 *Sums and Scalar Multiples*

> **相等**：称两个矩阵相等，当且仅当他们有相同的维数（即相同的行数和列数），并且对应元素相等。

> **矩阵加法**：两个 $m \times n$ 矩阵之和仍是一个 $m \times n$ 的矩阵，该矩阵的元素是两个矩阵中对应的元素相加。
> 
> （以列向量的角度描述）该矩阵的各个列向量是两个矩阵中对应向量相加。

> **向量乘法**：若 $r$ 是标量而 $A$ 是一个矩阵，而标量乘法 $rA$ 是一个矩阵，它的每一列是 $A$ 的对应列的 $r$ 倍，每一个元素是 $A$ 的对应元素的 $r$ 倍。

> **定理 1**：设 $A,B,C \in \mathbb R^{m \times n}$，$r,s \in \mathbb R$，则有
>
> 1. 矩阵加法交换律：$A + B = B + A$
> 2. 矩阵加法结合律：$(A + B) + C = A + (B + C)$
> 3. 零矩阵：$A + 0 = A$
> 4. 矩阵加法对标量乘法分配律：$r(A + B) = rA + rB$
> 5. 数的加法对标量乘法分配律：$(r + s) A = rA + sA$
> 6. 数的乘法与标量乘法的结合律：$r(sA) = (rs)A$
>
> **证明**：由于以上定理对相同维数的向量成立，我们将相同维数的矩阵拆成若干个相同维数的向量再予以证明即可。

## 矩阵乘法

**矩阵乘法与线性变换的关系**：矩阵乘法对应的变换，是两个矩阵对应的线性变换的复合，我们来推导该复合变换对应的矩阵是什么。

设 $A \in \mathbb R^{m \times n}, B \in \mathbb R^{n \times p}, \boldsymbol{x} \in \mathbb R^p$，用 $\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_p$ 表示 $B$ 的各列，用 $x_1, x_2, \cdots, x_p$ 表示 $\boldsymbol{x}$ 的元素，那么

$$B\boldsymbol{x} = x_1\boldsymbol{b}_1 + x_2\boldsymbol{x}_2 + \cdots + x_p\boldsymbol{x}_p$$

两边左乘 $A$，由矩阵的线性性质得

$$A(B\boldsymbol{x}) = A(x_1\boldsymbol{b}_1) + A(x_2\boldsymbol{b}_2) + \cdots + A(x_p\boldsymbol{b}_p)$$

因此有

$$A(B\boldsymbol{x}) = \left[
    \begin{matrix}
    A\boldsymbol{b}_1 & A\boldsymbol{b}_2 & \cdots & A\boldsymbol{b}_p  \\\\
    \end{matrix}
    \right] \boldsymbol{x} = (AB)\boldsymbol{x}$$

> **矩阵乘法**：设 $A \in \mathbb R^{m \times n}, B \in \mathbb R^{n \times p}$，$B$ 的各列为 $\boldsymbol{b}_1, \boldsymbol{b}_2, \cdots, \boldsymbol{b}_p$，那么 $AB \in \mathbb R^{m \times p}$ 中的每一列是 $A$ 的各列以 $B$ 的对应列的元素为权的线性组合。
>
> $$AB = \left[
    \begin{matrix}
    A\boldsymbol{b}_1 & A\boldsymbol{b}_2 & \cdots & A\boldsymbol{b}_p  \\\\
    \end{matrix}
    \right]$$
>
> 当 $A$ 的列数等于 $B$ 的行数的时候，$AB$ 才有意义.
>
> **计算 $\boldsymbol{AB}$ 的行列法则**：若 $AB$ 有定义，那么 $AB$ 的第 $i$ 行第 $j$ 列的元素是 $A$ 的第 $i$ 行和 $B$ 的第 $j$ 列对应元素的乘积之和
>
> $$(AB)\_{ij} = \sum\_{k = 1}^p a\_{ik} b\_{kj}$$

由 $\boldsymbol{AB}$ 的行列法则可知，我们也可以将 $A$ 拆成行向量来定义矩阵乘法

> **矩阵乘法（以行向量分解）**：设 $A \in \mathbb R^{m \times n}, B \in \mathbb R^{n \times p}$，$A$ 的各行为 $\operatorname{row}_1(A), \operatorname{row}_2(A), \cdots, \operatorname{row}_m(A)$，那么 $AB \in \mathbb R^{m \times p}$ 中的每一行中的元素是 $A$ 的对应行分别以 $B$ 的不同列为权的线性组合。
>
> $$\operatorname{row}_i(AB) = \operatorname{row}_i(A)·B$$

## 矩阵乘法的性质

> **定理 2**：设 $A,B,C$ 是矩阵，则
>
> 1. 矩阵乘法结合律：$A(BC) = (AB)C$
> 2. 矩阵乘法对矩阵加法左分配律：$A(B + C) = AB + AC$
> 3. 矩阵乘法对矩阵加法左分配律：$(A + B)C = AC + BC$
> 4. 矩阵乘法与标量乘法的交换律与结合律：$r(AB) = (rA)B = A(rB), \forall r \in \mathbb R$
> 5. 单位矩阵的性质：$I_m A = A = A I_n, \forall A \in \mathbb R^{m \times n}$
>
> **证明**：
>
> 1. 方法一：矩阵左乘是一种线性变换函数，而函数复合是可结合的。方法二：对于 $\boldsymbol{c}_i$，有 $A(B\boldsymbol{c}_i) = (AB)\boldsymbol{c}_i$，因此将每一列均使用该等式可证。
> 2. 将 $B,C$ 拆分为列向量，则有 $A(\boldsymbol{b}_j + \boldsymbol{c}_j) = A\boldsymbol{b}_j + A\boldsymbol{c}_j$。
> 3. 将 $A,B$ 拆分为行向量，则有 $(\operatorname{row}_i (A) \operatorname{row}_i (B)) C = \operatorname{row}_i (A)C + \operatorname{row}_i (B)C$
> 4. 将 $B$ 拆分为列向量可证。
> 5. 使用矩阵乘法可证。

矩阵乘法区别于一般数的乘法，并不满足部分性质：

1. 一般情况下 $AB \ne BA$;
2. 矩阵乘法不符合消去律，即若 $AB = AC$，那么一般情况下，$B = C$ 并不成立。
3. 若 $AB = 0$，那么一般 $A = 0 \lor B = 0$ 不成立。

## 矩阵的乘幂

> **矩阵的乘幂**：设 $A \in \mathbb R^{n \times n}, k \in N^*$，则 $A^k$ 是 $k$ 个 $A$ 的乘积
>
> $$A^k = \underbrace{A·A \cdots A}_{k 个}$$

## 矩阵的转置 *transpose*

> **矩阵的转置**：设 $A \in \mathbb R^{n \times m}$，则 $A$ 的转置 $A^T \in \mathbb R^{m \times n}$ 有
>
> $$a^T_{ij} = a_{ji}, \forall i \in [1,n], j \in [1,m]$$

> **定理 3**：设 $A,B$ 是矩阵，那么
>
> 1. $(A^T)^T = A$
> 2. $(A + B)^T = A^T + B^T$
> 3. $(rA)^T = rA^T, \forall r \in \mathbb R$
> 4. $(AB)^T = B^TA^T$
>
> **证明**：根据矩阵的转置的定义均可证
>
> **推广**：若干个矩阵的乘积的转置，等于它们的转置的相反顺序的乘积。
>
> $$(A_1 A_2 \cdots A_p)^T = A_p^T \cdots A_2^T A_1^T$$