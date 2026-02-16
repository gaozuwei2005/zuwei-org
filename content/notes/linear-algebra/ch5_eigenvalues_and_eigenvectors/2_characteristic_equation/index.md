---
title: 线性代数 | 5.2 特征方程
date: 2024-11-27
summary: 寻找特征值、行列式、特征值与可逆矩阵、特征方程、相似性、特征方程在数列中的应用
---

## 寻找特征值

如果我们想要找出某一个矩阵的所有特征值，那么等价于要寻找所有的 $\lambda$，使得 $\det (A - \lambda I) = 0$。

由于 $\det (A - \lambda I)$ 可以通过行列式的定义，写出一个关于 $\lambda$ 的 $n$ 次方程。由代数基本定理可知，该方程最多会有 $n$ 个解。因此，$n \times n$ 的矩阵最多会有 $n$ 个特征值。

## 行列式、特征值与可逆矩阵

> **定理（可逆矩阵定理（续））**：设 $A$ 是 $n\times n$ 矩阵，则 $A$ 是可逆的当且仅当
>
> - $0$ 不是 $A$ 的特征值。
> - $A$ 的行列式不等于 $0$。
>
> **证明**：在 5.1 中已经讨论过，这里不再赘述。

如果 $A$ 是 $3 \times 3$ 矩阵，那么 $|\det A|$ 是由 $A$ 的列向量为三个同一起点出发的棱生成的平行六面体的体积。

那么可见，平行六面体的体积不等于零当且仅当 $A$ 的列向量线性无关，这等价于 $A$ 是可逆矩阵。

> **定理 3（行列式的性质）**：设 $A,B$ 是 $n \times n$ 矩阵：
>
> - $A$ 可逆的充分条件是 $\det A \ne 0$；
> - $\det AB = \det A \det B$；
> - $\det A^T= \det A$；
> - 若 $A$ 是三角矩阵，那么 $\det A$ 是主对角线元素的乘积。
> - 对 $A$ 的某一行加到另一行，不改变行列式的值；对 $A$ 两行进行交换，行列式变为原来相反数；对 $A$ 某一行数乘 $k$，则行列式变为原来的 $k$ 倍。
>
> 该定理是对之前对行列式讨论的总结。

## 特征方程

> **特征多项式**：$\det (A - \lambda I) = 0$ 称为 $A$ 的**特征多项式**。

> **特征方程**：数值方程 $\det (A - \lambda I) = 0$ 称为 $A$ 的**特征方程**。

该特征方程的根是 $A$ 的所有特征值。该特征方程恰好有 $n$ 个根，其中实根称为实特征值，复根称为复特征值。下面我们只讨论实特征值。

> **（代数）重数**：特征值 $\lambda$ 在特征方程 $\det (A - \lambda I) = 0$ 中作为重根的个数。

## 相似性

> **相似**：假如 $A,B$ 是 $n \times n$ 矩阵，且存在可逆矩阵 $P$，使得 $P^{-1}AP = B$，或等价地 $A = PBP^{-1}$，则我们称 **$A$ 相似于 $B$**（单向）。
> 
> 同时我们，记 $Q = P^{-1}$，则有 $Q^{-1}BQ = A$，则 $B$ 相似于 $A$。
> 
> 因此，我们可以简单地说 $A,B$  是**相似**的。

> **相似变换**：将矩阵 $A$ 变成 $P^{-1}AP$ 的过程称为相似变换。

> **定理 4**：若 $n \times n$ 矩阵 $A,B$ 是相似的，那么它们具有相同的特征多项式，相同的特征值和对应的重数。
>
> **证明**：由于 $A,B$ 相似，那 $$B - \lambda I = P^{-1}AP - P^{-1}\lambda P = P^{-1}(A-\lambda I)P$$
>
> 因此 $$\begin{aligned}
\det (B - \lambda I) &= \det [P^{-1}(A-\lambda I)P] \\\\
&= \det P^{-1} \det (A - \lambda I) \det P
\end{aligned}$$
>
> 由于 $\det P^{-1} \det P = \det (P^{-1}P) = \det I = 1$，因此 
> $$\det (B - \lambda I) = \det (A - \lambda I)$$
>
> 从而它们的特征方程与相应的根相同，定理成立。

## 特征方程在数列中的应用（应用到动力系统）

给定 $n \times n$ 的矩阵 $A$ 和 $\boldsymbol{x\_0} \in \mathbb R^n$，并定义向量序列 $\boldsymbol{x}\_{k + 1} = A \boldsymbol{x}\_k\ (k = 0, 1, 2, \cdots)$，求 $x\_k$ 的通项公式。

我们可以先求出 $A$ 所有的特征根 $\\\{\lambda\_1, \lambda\_2, \cdots, \lambda\_n\\\}$ 与其特征向量的基 $\\\{ \boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots,  \boldsymbol{v}\_n \\\}$，也就是

$$\left\\\{\begin{aligned}
A \boldsymbol{v}\_1 &= \lambda \boldsymbol{v}\_1 \\\\
A \boldsymbol{v}\_2 &= \lambda \boldsymbol{v}\_2 \\\\
&\vdots \\\\
A \boldsymbol{v}\_n &= \lambda \boldsymbol{v}\_n \\\\
\end{aligned}
\right.$$

然后，我们将 $\boldsymbol{x}\_0$ 表示为特征向量 $\\\{ \boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots,  \boldsymbol{v}\_n \\\}$ 的线性组合：

$$\boldsymbol{x}\_0 = 
\left[\begin{matrix}
\boldsymbol{v}\_1 & \boldsymbol{v}\_2 & \cdots & \boldsymbol{v}\_n
\end{matrix}\right]
\left[\begin{matrix}
c\_1 \\\\ c\_2 \\\\ \vdots \\\\ c\_n \\\\
\end{matrix}\right]$$ 

我们对增广矩阵 $\left[\begin{matrix}\boldsymbol{v}\_1 & \boldsymbol{v}\_2 & \cdots & \boldsymbol{v}\_n & \boldsymbol{x}\_0 \end{matrix}\right]$ 进行行简化即可得到系数向量。

因此，

$$\begin{aligned}
\boldsymbol{x}\_{k+1} &= A(
c\_{k1}\boldsymbol{v}\_1 + c\_{k2}\boldsymbol{v}\_2 +
\cdots
c\_{kn}\boldsymbol{v}\_n) \\\\
&= c\_{k1}(A\boldsymbol{v}\_1) + 
c\_{k2}(A\boldsymbol{v}\_2) + 
\cdots +
c\_{kn}(A\boldsymbol{v}\_n)\\\\
&= \lambda\_1 c\_{k1}\boldsymbol{v}\_1 + 
\lambda\_2 c\_{k2}\boldsymbol{v}\_2 + 
\cdots +
\lambda\_n c\_{kn}\boldsymbol{v}\_n
\end{aligned}$$

因此

$$\boldsymbol{x}\_k = 
\lambda\_1^k c\_1 \boldsymbol{v}\_1 + 
\lambda\_2^k c\_2 \boldsymbol{v}\_2 + 
\cdots +
\lambda\_n^k c\_n \boldsymbol{v}\_n$$