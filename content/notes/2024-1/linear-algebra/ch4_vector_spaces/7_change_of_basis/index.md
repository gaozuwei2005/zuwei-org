---
title: 线性代数 | 4.7 基的变换
date: 2024-11-25
summary: 向量空间中基的变换、$\mathbb R^n$ 中基的变换
---

## 向量空间中基的变换

> **定理 15**：若 $\mathcal B = \\\{ \boldsymbol{b}\_1, \boldsymbol{b}\_2, \cdots, \boldsymbol{b}\_n \\\}, \mathcal C = \\\{ \boldsymbol{c}\_1, \boldsymbol{c}\_2, \cdots, \boldsymbol{c}\_n \\\}$ 均是向量空间 $V$ 的基，则存在 $n \times n$ 的矩阵 $\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}$ 使得
>
> $$[\boldsymbol{x}]\_\mathcal C = \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} [\boldsymbol{x}]\_\mathcal B$$
>
> 其中 $\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}$ 称为**由 $\mathcal{B}$ 到 $\mathcal{C}$ 的坐标变换矩阵**。该矩阵的列是 $\mathcal B$ 中的向量的 $\mathcal C-$坐标向量。
>
> $$\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} = \left[ \begin{matrix}
    [\boldsymbol{b}\_1]\_\mathcal C & 
    [\boldsymbol{b}\_2]\_\mathcal C & 
    \cdots &
    [\boldsymbol{b}\_n]\_\mathcal C
\end{matrix} \right]$$
>
> **证明**：两边左乘 $P\_C$ 可得
>
> $$\begin{aligned}
P\_C[\boldsymbol{x}]\_\mathcal C &= P\_C \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} [\boldsymbol{x}]\_\mathcal B \\\\
\boldsymbol{x} &=  \left[ \begin{matrix}
    P\_C[\boldsymbol{b}\_1]\_\mathcal C & 
    P\_C[\boldsymbol{b}\_2]\_\mathcal C & 
    \cdots &
    P\_C[\boldsymbol{b}\_n]\_\mathcal C
\end{matrix} \right] [\boldsymbol{x}]\_\mathcal B \\\\
&=\left[ \begin{matrix}
   \boldsymbol{b}\_1 & 
   \boldsymbol{b}\_2 & 
    \cdots &
   \boldsymbol{b}\_n
\end{matrix} \right] [\boldsymbol{x}]\_\mathcal B \\\\
&= P\_B [\boldsymbol{x}]\_\mathcal B \\\\
&= \boldsymbol{x}
\end{aligned}$$

由于 $\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}$ 中的列是线性无关集 $\mathcal B$ 中的向量的坐标向量，因此它们线性无关，从而可知 $\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}$ 是可逆矩阵，则有

$$\left( \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} \right)^{-1}[\boldsymbol{x}]\_\mathcal C =  [\boldsymbol{x}]\_\mathcal B$$

其中 $\left( \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} \right)^{-1}$ 是将 $\mathcal C-$坐标变为 $\mathcal B-$坐标的矩阵，即

$$\mathop P\limits\_{\mathcal B \leftarrow  \mathcal C}  = \left( \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} \right)^{-1}$$

## $\mathbb R^n$ 中基的变换

对于 $\mathbb R^n$ 的两个基 $\mathcal B = \\\{ \boldsymbol{b}\_1, \boldsymbol{b}\_2, \cdots, \boldsymbol{b}\_n \\\}, \mathcal C = \\\{ \boldsymbol{c}\_1, \boldsymbol{c}\_2, \cdots, \boldsymbol{c}\_n \\\}$，进行基的变换，就需要找出 $\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}$。

**方法一**：构造一个合并在一起的增广矩阵

$$\left[
    \begin{matrix}
    \boldsymbol{c}\_1 & 
    \boldsymbol{c}\_2 & 
    \cdots & 
    \boldsymbol{c}\_n &
    \boldsymbol{b}\_1 & 
    \boldsymbol{b}\_2 &
    \cdots & 
    \boldsymbol{b}\_n
    \end{matrix}
\right]$$

对其行简化便可得到

$$\left[
    \begin{matrix}
    \boldsymbol{I}\_n &
    \mathop P\limits\_{\mathcal C \leftarrow  \mathcal B}
    \end{matrix}
\right]$$

**方法二**：先将 $\mathcal B-$坐标转换为标准坐标，再转换为 $\mathcal C-$坐标。由 $P\_\mathcal C [\boldsymbol{x}]\_\mathcal C = \boldsymbol{x}$ 得到 $[\boldsymbol{x}]\_\mathcal C = P\_\mathcal C^{-1} \boldsymbol{x}$

因此

$$[\boldsymbol{x}]\_\mathcal C = P\_\mathcal C^{-1} \boldsymbol{x} = P\_\mathcal C^{-1} P\_\mathcal B [\boldsymbol{x}]\_\mathcal B$$

那么有

$$\mathop P\limits\_{\mathcal C \leftarrow  \mathcal B} = P\_\mathcal C^{-1} P\_\mathcal B $$