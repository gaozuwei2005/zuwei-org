---
title: 线性代数 | 额外笔记
date: 2024-12-13
summary: 向量不等式、矩阵乘法与交换律、行列式的性质、特殊矩阵的行列式、秩的性质
---

## 1.3 向量方程

Schwarz 不等式：$|\boldsymbol{v} · \boldsymbol{w}| \le ||\boldsymbol{v}||·||\boldsymbol{w}||$

三角不等式：$||\boldsymbol{v} + \boldsymbol{w}|| \le ||\boldsymbol{v}|| + ||\boldsymbol{w}||$

$n$ 维向量空间：$\mathbb R^n = \\\{\boldsymbol{x} = (x\_1, x\_2, \cdots, x\_n)^T | x\_i \in \mathbb R, i = 1, 2, \cdots, n\\\}$

$n$ 维向量空间的 $n - 1$ 维平面：$\\\{ \boldsymbol{x} = (x\_1, x\_2, \cdots, x\_n)^T | a\_1x\_1 + a\_2x\_2 + \cdots + a\_bx\_n = b, a\_i, x\_i, b \in \mathbb R, i = 1, 2, \cdots, n\\\}$

## 2.1 矩阵运算

如果矩阵乘法 $A,B$ 可以交换，即 $AB = BA$，那么有

1. $(AB)^k = A^kB^k$
2. $(A-B)(A+B) = A^2 - B^2$
3. $(A+B)^2 = A^2 + 2AB + B^2$

## 3.2 行列式的性质

> 若 $A,B$ 都是 $n \times n$ 的矩阵，那么 $\det AB = \det A \det B$

**证明**：若 $A$ 不可逆，那么 $AB$ 也不可逆，于是 $\det AB = \det A \det B = 0$

若 $A$ 可逆，那么我们可以把 $A$ 分解成若干初等矩阵的乘积，使得

$$AB = E\_p E\_{p-1} \cdots E\_1 B$$

于是有

$$|AB| = |E\_p||E\_{p-1}|\cdots |E\_2||E\_1||B| = |A||B|$$


> $\det AB = \det BA ( = \det A\det B)$

> 若 $A$ 存在两行元素成比例，那么 $\det A = 0$.

> $\det A^2 = \det^2 A$
>
> $\det \lambda A = \lambda^n \det A$

## 3.3 克莱姆法则、体积和线性变换

上/下三角矩阵、对角矩阵的行列式，为对角线元素乘积。

反向上三角矩阵的行列式、反向对角矩阵的行列式，为对角线元素乘积乘以 $(-1)^{\frac{n(n-1)}{2}}$ （交换行的次数）

## 4.6 秩

子式定义：在 $m \times n$ 矩阵 $A$ 中，任取 $k$ 行和 $k$ 列位于这些行列交叉处的 $k^2$ 个元素，这些元素按照相对次序组成的 $k \times k$ 矩阵的行列式成为矩阵 $A$ 的 $k$ 阶子式。

阶的第二定义：如果 $A$ 有一个不等于 $0$ 的 $r$ 阶子式 $D$，且所有 $r+1$ 阶子式为 $0$，那么 $R(A) = r$。（证明：最多有 $r$ 个向量线性无关）

> $\max\\\{R(A), R(B)\\\} \le R(A,B) \le R(A) + R(B)$

**证明**：首先，我们可以选取 $[\begin{matrix}A&B\end{matrix}]$ 中对应的 $A$ 和 $B$ 的 $R(A)$ 阶子式和 $R(B)$ 阶子式，所以左边不等式成立。

对 $[\begin{matrix}A&B\end{matrix}]$ 每个分块矩阵列化简之后，只含有 $R(A) + R(B)$ 个非零列，因此右边不等式成立。

> $R(A+B) \le R(A) + R(B)$

**证明**：$R(A+B) \le R\left(\left[\begin{matrix}
A+B & B
\end{matrix}\right]\right) = R(\left[\begin{matrix}A&B\end{matrix}\right]) \le R(A) + R(B)$

> $R(AB) \le \min(R(A), R(B))$

**证明**：由于

$$AB = [\begin{matrix}\boldsymbol{a}\_1 & \boldsymbol{a}\_2 & \cdots & \boldsymbol{a}\_n\end{matrix}] \left[\begin{matrix}b\_{11} & b\_{12} & \cdots & b\_{1m} \\\\
b\_{21} & b\_{22} & \cdots & b\_{2m} \\\\
\vdots & \vdots & \ddots & \vdots \\\\
b\_{n1} & b\_{n2} & \cdots & b\_{nm} \\\\
\end{matrix}\right] = \left[\begin{matrix}
\sum\limits\_{i = 1}^ n b\_{i1} \boldsymbol{a}\_i & 
\sum\limits\_{i = 1}^ n b\_{i2} \boldsymbol{a}\_i & 
\cdots &
\sum\limits\_{i = 1}^ n b\_{im} \boldsymbol{a}\_i
\end{matrix}\right]$$

因此 $AB$ 的列向量由 $A$ 的列向量线性表示出，因此 $R(AB) \le R(A)$。

只要转置就能证出另一部分 $R(AB) = R((AB)^T) = R(B^TA^T) \le R(B^T) = R(B)$。

> 若 $A \in \mathbb R^{m \times n}, B \in \mathbb R^{n \times r}$，且 $AB = \boldsymbol{0}^{m \times r}$，那么 $R(A) + R(B) \le n$

证明：由于 $A \boldsymbol{b}\_i  = \boldsymbol{0}^{m} , \forall i \in [1,r]$，因此 $R(B) \le \operatorname{dim} \operatorname{Nul} A = n - R(A)$

因此 $R(A) + R(B) \le n$