---
title: 线性代数 | 3.3 克拉默法则、体积和线性变换
date: 2024-11-29
summary: 克拉默法则、逆矩阵公式、用行列式表示面积或体积、线性变换
---

## 克拉默法则 *Cramer's Rule*

对于任意 $n \times n$ 的矩阵 $A$ 和 $\boldsymbol{b} \in \mathbb R^n$，令 $A_i(\boldsymbol{b})$ 表示 $A$ 中第 $i$ 列用 $\boldsymbol{b}$ 替换得到的矩阵：

$$A_i(\boldsymbol{b}) = \left[
    \begin{matrix}
    \boldsymbol{a}\_1  & \cdots & \boldsymbol{a}\_{i-1} & \boldsymbol{b} & \boldsymbol{a}\_{i+1} & \cdots & 
    \boldsymbol{a}\_n
    \end{matrix}
\right]$$

> **定理 7（克拉默法则）**：设 $A$ 是一个可逆的 $n \times n$ 的矩阵，$\forall \boldsymbol{b} \in \mathbb R^n$，方程 $A\boldsymbol{x} = \boldsymbol{b}$ 的唯一解为
>
> $$\boldsymbol{x}_i = \frac{\det A_i(\boldsymbol{b})}{\det A},\ i = 1,2,\cdots,n$$
>
> **证明**：记 $A = \begin{bmatrix}\boldsymbol{a}\_1 & \boldsymbol{a}\_2 & \cdots & \boldsymbol{a}\_n \end{bmatrix}$，$I = \begin{bmatrix}\boldsymbol{e}\_1 & \boldsymbol{e}\_2 & \cdots & \boldsymbol{e}\_n \end{bmatrix}$，那么有
>
> $$\begin{aligned}
A I\_i(\boldsymbol{x}) &=A \begin{bmatrix}\boldsymbol{e}\_1 & \cdots & \boldsymbol{e}\_{i-1} & \boldsymbol{x} & \boldsymbol{e}\_{i+1} & \cdots & \boldsymbol{e}\_n \end{bmatrix} \\\\
&= \begin{bmatrix}A\boldsymbol{e}\_1 & \cdots & A\boldsymbol{e}\_{i-1} & A\boldsymbol{x} & A\boldsymbol{e}\_{i+1} & \cdots & A\boldsymbol{e}\_n \end{bmatrix} \\\\
&= \begin{bmatrix}\boldsymbol{a}\_1 & \cdots & \boldsymbol{a}\_{i-1} & \boldsymbol{b} & \boldsymbol{b}\_{i+1} & \cdots & \boldsymbol{b}\_n \end{bmatrix} \\\\
&= A_i(\boldsymbol{b}) \\\\
\end{aligned}$$
>
> 因此 
>
> $$\det A \det I_i(x) = \det A_i(b)$$
>
> 其中 $\det I_i(x) = x_i$（沿第 $i$ 行展开可知）。因此
>
> $$\det A·x_i = \det A_i(b)$$

因此，要用克拉默法则求解矩阵方程，我们需要求出系数矩阵，以及用某向量替换系数矩阵的任意一列得到的矩阵，各自的行列式，然后相除即得未知向量。

## 逆矩阵公式 *A Formula for $A^{-1}$*

运用克拉默法则，我们可以求出 $n \times n$ 矩阵 $A$ 的逆，对于 $A^{-1}$ 的第 $j$ 列为 $\boldsymbol{x}$，有

$$A \boldsymbol{x} = \boldsymbol{e}_j$$

记 $a_{i,j}^{-1}$ 为 $A^{-1}$ 的 $(i,j)$ 号元素，则有

$$a_{ij}^{-1} = \frac{\det A_i(\boldsymbol{e}_j)}{\det A}$$

而分子刚好为行列坐标颠倒的余因子

$$\det A\_i(\boldsymbol{e}\_j) = (-1)^{i+j} \det A\_{ji} = C\_{ji}$$

因此

$$A^{-1} = \frac{1}{\det A}
\left[
    \begin{matrix}
    C_{11} & C_{21} & \cdots & C_{n1} \\\\
    C_{12} & C_{22} & \cdots & C_{n2} \\\\
    \vdots & \vdots & \ddots & \vdots \\\\
    C_{1n} & C_{2n} & \cdots & C_{nn} \\\\
    \end{matrix}
\right]$$

其中右边的余因子矩阵称为 **$A$ 的伴随矩阵** *adjugate (or classical adjoint) of A*，记为 $\operatorname{adj} A$，

>  **定理 8（逆矩阵公式 *An Inverse Formula*）**：设 $A$ 是一个可逆的 $n \times n$ 的矩阵，那么 
> 
> $$A^{-1} = \frac{1}{\det A} \operatorname{adj} A$$

## 用行列式表示面积或体积

> **定理 9（行列式与面积、体积的关系）**：
> （1）设 $A$ 是一个 $2 \times 2$ 的矩阵，那么 $A$ 的列向量为邻边的平行四边形的面积为 $|\det A|$。
> 
> （2）设 $A$ 是一个 $3 \times 3$ 的矩阵，那么那么 $A$ 的列向量为邻边的平行六面体的面积为 $|\det A|$。
>
> **证明**：首先，该定理对于 $n$ 阶对角矩阵显然成立，面积 / 体积即为对角线上元素之和。
>
> 其次，对于任意一个 $n$ 阶矩阵，我们可以对其列变换为一个对角矩阵，那么我们需要讨论三种列变换对于行列式与面积的影响：
>
> - 将某一列 $\boldsymbol{v}_i$ 的 $k$ 倍加到另一列 $\boldsymbol{v}_j$ 上，则则 $\boldsymbol{v}_j$ 的终点将会沿着平行 $\boldsymbol{v}_i$ 的方向移动，此时面积 / 体积将不会改变。此时行列式不会改变。
> - 将某一列乘以系数 $k$，那么面积 / 体积也会乘以系数 $|k|$，行列式乘以系数 $k$。
> - 将某两列交换，则面积 / 体积不会改变，行列式变为原来的相反数，绝对值仍然不会改变。
>
> 因此定理证毕。

给定平行四边形的四个顶点，我们可以选择一个顶点和与其相邻的其他两个顶点，然后我们将坐标相减就可以得到两条邻边，我们在计算它的行列式即可。

## 线性变换

> **定理 10**：设 $T : \mathbb R^m \to \mathbb R^n$ 是一个 $n \times n$ 矩阵 $A$ 确定的线性变换，设 $\mathbb R^n$ 中的一个 $n$ 维平行体对应矩阵 $B$，它的面积 / 体积为 $S = |\det B|$，那么通过 $T$ 变换后的 $n$ 维平行体的面积 / 体积为
>
> $$S' = |\det A|·S$$
>
> **证明**：由行列式的性质可知，设 $A$ 是线性变换 $A$ 对应的矩阵，那么
>
> $$S' = |\det AB| = |\det A|·|\det B| = |\det A| · S$$

该定理可以将 $n$ 维平行体拓展为 $n$ 维空间中围成的一个区域，至于证明，我们可以可以用若干个平行体的体积的和来近似这个区域的体积。