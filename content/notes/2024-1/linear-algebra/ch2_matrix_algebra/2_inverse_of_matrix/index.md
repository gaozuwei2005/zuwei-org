---
title: 线性代数 | 2.2 矩阵的逆
date: 2024-12-01
summary: 矩阵的逆、可逆矩阵、初等矩阵、求逆算法
---

## 矩阵的逆的定义

为了建立代数系统，我们希望找出矩阵的逆。

一个矩阵 $A \in \mathbb R^{m \times n}$ 可逆，当且仅当 $\exists C,D \in \mathbb R^{n \times m}, \ CA = I_n, AD = I_m$。

然而，我们可以证明若矩阵 $A$ 可逆，则必须 $A$ 是方阵且 $C=D$。

1. 若 $CA = I_n$，那么对于方程 $A\boldsymbol{x} = \boldsymbol{0}$，两边左乘 $C$ 得到 $\boldsymbol{x} = \boldsymbol{0}$，因此方程仅有平凡解。因此 $A$ 中没有自由变量，每一列都是主元列。因此 $A$ 的行数多于列数。
2. 若 $AD = I_m$，那么我们两边右乘 $\boldsymbol{b}$，得到 $A(D\boldsymbol{b}) = \boldsymbol{b}$，因此对于任意 $\boldsymbol{b} \in \mathbb R^m$，方程 $A\boldsymbol{x} = \boldsymbol{b}$ 均有解。因此 $A$ 行变换为阶梯矩阵后没有非零行，因此每一行均有主元，因此 $A$ 的行数等于列数。
3. 由以上两点可知，$n = m$ 且 $CA = AD = I_n$。对于 $CA = I_n$，两边右乘 $D$ 可得 $C(AD) = D$，进一步有 $C = D$。

> **矩阵的逆**：一个 $A \in \mathbb R^{n \times n}$ 是可逆的，若存在一个 $n \times n$ 的矩阵 $C$ 使得
>
> $$CA = I_n \ \land\ AD = I_n $$
>
> 则我们称 $C$ 是 $A$ 的**逆**。
>
> 实际上 $C$ 是由 $A$ 唯一确定的。运用反证法，若 $B$ 是 $A$ 的另一个逆，那么有
>
> $$B = BI = B(AC) = (BA)C = C$$
>
> 我们记 $A$ 的**逆矩阵**为 $A^{-1}$。
>
> 不可逆矩阵有时称为**奇异矩阵**，可逆矩阵有时称为**非奇异矩阵**。

> **定理 4**：设 $A = \left[
\begin{matrix}
a & b \\\\
c & d \\\\
\end{matrix}
\right]$，若 $ad - bc \ne 0$ ，则 $A$ 可逆且
>
> $$A^{-1} = \frac{1}{ad - bc} \left[
    \begin{matrix}
    d & -b \\\\
    -c & a \\\\
    \end{matrix}
\right]
= \frac{1}{\det A} \operatorname{adj} A$$
>
> 若 $ad - bc = 0$，那么 $A$ 不可逆。

> **行列式**：对于 $2 \times 2$ 矩阵 $A = \left[
\begin{matrix}
a & b \\\\
c & d \\\\
\end{matrix}
\right]$，其行列式为 $\det A = ad - bc$.
>
> $2 \times 2$ 矩阵 $A$ 可逆，当且仅当 $\det A \ne 0$。

## 可逆矩阵的性质

> **定理 5**：若 $A$ 是可逆 $n \times n$ 矩阵，那么对于 $\forall \boldsymbol{b} \in \mathbb R^n$，方程 $A \boldsymbol{x} = \boldsymbol{b}$ 有唯一解 $\boldsymbol{x} = A^{-1} \boldsymbol{b}$。
>
> **证明**：首先 $\boldsymbol{x} = A^{-1} \boldsymbol{b}$ 是方程 $A \boldsymbol{x} = \boldsymbol{b}$ 的解。
> 
> $$A (A^{-1} \boldsymbol{b}) = \boldsymbol{b}$$
>
> 其次，若有方程有另一解 $\boldsymbol{u}$，那么 $A \boldsymbol{u} = \boldsymbol{b}$，两边左乘 $A^{-1}$ 可得 $\boldsymbol{u} = A^{-1} \boldsymbol{b} = \boldsymbol{x}$。因此方程有唯一解。

在实际应用中，我们很少先求逆矩阵再做矩阵乘法求出 $A \boldsymbol{x} = \boldsymbol{b}$ 的解。我们一般直接行简化增广矩阵。

> **定理 6（可逆矩阵的性质）**：
>
> 1. （可逆矩阵的可逆矩阵）若 $A$ 是可逆矩阵，那么 $A^{-1}$ 也可逆并且 
> $$(A^{-1})^{-1} = A$$
> 2. （矩阵乘积的可逆矩阵）若 $A, B$ 都是维数相同的可逆矩阵，那么 $AB$ 也可逆，并且 $AB$ 的逆矩阵是 $A,B$ 的逆矩阵以相反顺序的乘积。
> $$(AB)^{-1} = B^{-1}A^{-1}$$
> 3. （转置矩阵的可逆矩阵）若 $A$ 可逆，那么 $A^T$ 也可逆，并且它的逆是 $A^{-1}$ 的转置：
> $$(A^T)^{-1} = (A^{-1})^T$$
>
> **证明**：
>
> 1. 由于可逆矩阵满足
>
> $$AA^{-1} = I, A^{-1} A = I$$
>
> 因此可以互相推出 $A, A^{-1}$ 各是对方的逆矩阵。
>
> 2. 我们验证 $B^{-1}A^{-1}$ 是否为 $AB$ 的逆矩阵即可证明
>
> $$(B^{-1}A^{-1})AB = B^{-1}(A^{-1}A)B = B^{-1}B = I$$
>
> $$AB(B^{-1}A^{-1}) = A(BB^{-1})A^{-1} = AA^{-1} = I$$
>
> 3. 我们验证 $(A^{-1})^T$ 是否为 $A^T$ 的逆矩阵即可证明
>
> $$(A^{-1})^TA^T = (AA^{-1})^T = I^T = I$$
>
> $$A^T(A^{-1})^T = (A^{-1}A)^T = I^T = I$$
>
> **推广**：若干个维数相同的矩阵的乘积是可逆的，它的逆是这些矩阵的逆按照相反顺序的乘积
>
> $$(A_1 A_2 \cdots A_p)^{-1} = A_p^{-1} \cdots A_2^{-1} A_1^{-1}$$

## 初等矩阵

> **初等矩阵**：将单位矩阵进行一次初等行变换所得到的矩阵。
>
> 对于某初等矩阵 $E \in \mathbb R^{m \times m}$ 和某矩阵 $A \in \mathbb R^{m \times n}$，那么 $EA$ 相当于对 $A$ 执行 $E$ 所代表的初等行变换后的矩阵。

每个初等矩阵 $E$ 都是可逆的，它的逆矩阵是对应能将 $E$ 变换为 $I$ 的行变换。

> **定理 7**：对于矩阵 $A \in \mathbb R^{n \times n}$ 可逆，当且仅当 $A$ 行等价于 $I_n$。并且将 $A$ 行变换为 $I_n$ 的一系列初等行变换，也可以让 $I_n$ 行变换为 $A^{-1}$。
>
> **证明**：由于 $A$ 是可逆矩阵，因此 $\forall \boldsymbol{b} \in \mathbb R^n$，$A \boldsymbol{x} = \boldsymbol{b}$ 均有解，因此每行均有一个主元，因此 $A \sim I_n$。
>
> 因此我们有一系列初等矩阵使得
>
> $$E_p E_{p - 1} \cdots E_2 E_1 A = I_n$$
>
> 由于初等矩阵均存在逆矩阵，因此它们的乘积也存在逆矩阵，两边左乘它们乘积的逆可得
>
> $$A = (E_p E_{p - 1} \cdots E_2 E_1)^{-1}$$
>
> 因此 $A$ 是这一系列初等矩阵乘积的逆。于是有
>
> $$\begin{aligned}
A^{-1} &= [(E_p E_{p - 1} \cdots E_2 E_1)^{-1}]^{-1}\\\\
&= E_p E_{p - 1} \cdots E_2 E_1 \\\\
&= E_p E_{p - 1} \cdots E_2 E_1 I
\end{aligned}$$
>
> 因此这一系列行变换可以将 $I$ 行变换为 $A^{-1}$。

## 求 $\boldsymbol{A^{-1}}$ 的算法

> **求 $\boldsymbol A$ 的逆矩阵算法**：想增广矩阵 $\left[\begin{matrix} A & I \end{matrix}\right]$ 进行行化简即可得到 $\left[\begin{matrix} I & A^{-1} \end{matrix}\right]$。
>
> **证明**：由于在行化简的时候，我们对 $A, I$ 进行的行变换是一样的，因此由定理 7 可知这是成立的。

如果我们只需要逆矩阵的某一列，那么我们可以行化简 $\left[\begin{matrix} A & \boldsymbol{e}_i \end{matrix}\right]$ 即可得到 $A^{-1}$ 的第 $i$ 列。