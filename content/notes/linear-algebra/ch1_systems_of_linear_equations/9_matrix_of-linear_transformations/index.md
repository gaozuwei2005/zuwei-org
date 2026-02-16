---
title: 线性代数 | 1.9 线性变换的矩阵
date: 2024-12-17
summary: 线性变换的标准矩阵、几何线性变换、存在与唯一性问题、线性变换与线性关系
---

## 线性变换的标准矩阵

我们希望找出线性变换 $T: \boldsymbol{x} \mapsto A\boldsymbol{x}$ 中的矩阵 $A$。而 $A$ 的各列可以用该线性变换对 $I$ 的各列的作用来表示。

> **定理 10**：设 $T: \mathrm R^n \rightarrow \mathrm R^m$ 是线性变换，那么存在唯一的矩阵 $A \in \mathrm R^{m \times n}$，使得 $T : \boldsymbol{x} \mapsto A\boldsymbol{x}$。
>
> 矩阵 $A$ 是**线性变换 $T$ 的标准矩阵**。
>
> 其中 $A$ 的第 $j$ 列是 $T(\boldsymbol{e}_j)$，其中 $\boldsymbol{e}_j$ 是 $I_n$ 的第 $j$ 列。
>
> $$A = \left[
    \begin{matrix}
    T(\boldsymbol{e}_1) & 
    T(\boldsymbol{e}_2) & 
    \cdots & 
    T(\boldsymbol{e}_n)
    \end{matrix}
\right]$$
>
> **证明**：记 $\boldsymbol{x} = I_n\boldsymbol{x} = x_1\boldsymbol{e}_1 + x_2\boldsymbol{e}_2 + \cdots + x_n\boldsymbol{e}_n$，由于 $T$ 是线性变换，因此
>
> $$\begin{aligned}
T(\boldsymbol{x}) &= T(x_1\boldsymbol{e}_1 + x_2\boldsymbol{e}_2 + \cdots + x_n\boldsymbol{e}_n) \\\\
&= x_1 T(\boldsymbol{e}_1) + x_2 T(\boldsymbol{e}_2) + \cdots + x_n T(\boldsymbol{e}_n) \\\\
&= \left[
    \begin{matrix}
    T(\boldsymbol{e}_1) & 
    T(\boldsymbol{e}_2) & 
    \cdots & 
    T(\boldsymbol{e}_n)
    \end{matrix}
\right] 
\left[
    \begin{matrix}
    x_1 \\\\
    x_2 \\\\
    \vdots \\\\
    x_n
    \end{matrix}
\right] \\\\
&= A \boldsymbol{x} \\\\
\end{aligned}$$

每一个从 $\mathrm R^n \rightarrow \mathrm R^m$ 的线性变换都可以看作是矩阵变换。线性变换强调映射的性质，矩阵变换描述这样的映射如何实现。

## 几何线性变换

我们看该变换对 $(1,0), (0,1)$ 的效果即可得出变换矩阵。

### 对称

- 关于某一轴对称（$x, y$ 轴）：$\left[
    \begin{matrix}
    1 & 0 \\\\
    0 & -1 \\\\
    \end{matrix}
\right]$，$\left[
    \begin{matrix}
    -1 & 0 \\\\
    0 & 1 \\\\
    \end{matrix}
\right]$

- 关于 $45^\circ$ 斜线对称（$y = x, y = -x$）：$\left[
    \begin{matrix}
    0 & 1 \\\\
    1 & 0 \\\\
    \end{matrix}
\right]$，$\left[
    \begin{matrix}
    0 & -1 \\\\
    -1 & 0 \\\\
    \end{matrix}
\right]$

- 关于原点对称：$\left[
    \begin{matrix}
    -1 & 0 \\\\
    0 & -1 \\\\
    \end{matrix}
\right]$

### 收缩与拉伸

- 水平和垂直：$\left[
    \begin{matrix}
    k & 0 \\\\
    0 & 1 \\\\
    \end{matrix}
\right]$，$\left[
    \begin{matrix}
    1 & 0 \\\\
    0 & k \\\\
    \end{matrix}
\right]$

### 剪切变换

- 水平和垂直：$\left[
    \begin{matrix}
    1 & k \\\\
    0 & 1 \\\\
    \end{matrix}
\right]$，$\left[
    \begin{matrix}
    1 & 0 \\\\
    k & 1 \\\\
    \end{matrix}
\right]$

### 投影

- 投影到不同轴上（水平和垂直）：$\left[
    \begin{matrix}
    1 & 0 \\\\
    0 & 0 \\\\
    \end{matrix}
\right]$，$\left[
    \begin{matrix}
    0 & 0 \\\\
    0 & 1 \\\\
    \end{matrix}
\right]$

## 存在与唯一性问题

### 满射与存在性

> **满射**：若 $\mathrm R^m$ 中每个 $\boldsymbol{b}$ 是 $\mathrm R^n$ 中至少一个 $\boldsymbol{x}$ 的像，那么我们称映射 $T: \mathrm R^n \rightarrow \mathrm R^m$ 为**到 $\mathrm R^m$ 上的映射**。

“$T$ 是否把 $\mathrm R^n$ 映到 $\mathrm R^m$ 上？” 是存在性问题：

我们需要判断对于 $\mathrm R^m$ 中的每个 $\boldsymbol{b}$，方程 $A\boldsymbol{x} =  \boldsymbol{b}$ 是否至少有一个解。

### 单射与唯一性

> **单射**：若 $\mathrm R^m$ 中每个 $\boldsymbol{b}$ 是 $\mathrm R^n$ 中至多一个 $\boldsymbol{x}$ 的像，那么我们称映射 $T: \mathrm R^n \rightarrow \mathrm R^m$ 为**一对一映射**。

“$T$ 是否一对一？” 是存在性问题：

我们需要判断对于 $\mathrm R^m$ 中的每个 $\boldsymbol{b}$，方程 $A\boldsymbol{x} =  \boldsymbol{b}$ 是否有唯一的解或者没有解。

## 线性变换与线性关系

> **定理 11**：设 $T: \mathrm R^n \to \mathrm R^m$ 为线性变换，则 $T$ 是一对一的，当且仅当方程 $A\boldsymbol{x} = \boldsymbol{0}$ 仅有平凡解。
>
> **证明**：由于 $T$ 是线性的，那么 $T(\boldsymbol{0})=\boldsymbol{0}$。
> 
> 如果 $T$ 是一对一的，那么 $T(\boldsymbol{x}) = \boldsymbol{0}$ 至多有一个解，因此只有平凡解。
>
> 如果$T$ 不是一对一的，那么 $\exists \boldsymbol{b} \in \mathrm R^m，T(\boldsymbol{x}) = \boldsymbol{b}$ 有两个相异的解 $\boldsymbol{u}, \boldsymbol{v}$，故
>
> $$T(\boldsymbol{u} - \boldsymbol{v}) = T(\boldsymbol{u}) - T(\boldsymbol{v}) = \boldsymbol{b} = \boldsymbol{b} = \boldsymbol{0}$$
>
> 又因 $T(\boldsymbol{x}) = \boldsymbol{0}$ 多于一个解，于是 $T$ 不是一对一的。

> **定理 12**：设 $T: \mathrm R^n \to \mathrm R^m$ 为线性变换，设 $A$ 是 $T$ 的标准矩阵，那么
>
> - $T$ 把 $\mathrm R^n$ 映上 $\mathrm R^m$ $\Leftrightarrow$ $A\boldsymbol{x} = \boldsymbol{b}, \forall \boldsymbol{b} \in \mathrm R^m$ 均有解 $\Leftrightarrow$ $A$ 的列生成 $\mathrm R^m$。
> - $T$ 是一对一的 $\Leftrightarrow$ $A\boldsymbol{x} = \boldsymbol{0}$ 仅有平凡解 $\Leftrightarrow$ 当且仅当方程 $A$ 的列线性无关。