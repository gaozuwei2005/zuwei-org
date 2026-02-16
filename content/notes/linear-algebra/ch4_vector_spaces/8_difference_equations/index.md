---
title: 线性代数 | 4.8 差分方程的应用
date: 2024-11-25
summary: 离散时间信号、信号空间中的线性无关性、线性差分方程
---

## 离散时间信号

> **离散时间信号**：定义在整数上的函数。可以用数列将其表示。
>
> 若只表示在非负整数上的函数，则对于 $k < 0$ 的 $y\_k$ 项可以假设取值为 $0$ 或予以忽略。
>
> 离散时间信号的向量空间记作 $\mathbb S$。

## 信号空间 $\mathbb S$ 中的线性无关性

称 $n$ 个信号 $\boldsymbol{s}\_1, \boldsymbol{s}\_2, \cdots, \boldsymbol{s}\_n$

$$c\_1\boldsymbol{s}\_1 + c\_2\boldsymbol{s}\_2 + \cdots + c\_n\boldsymbol{s}\_n = \boldsymbol{0}$$

仅有平凡解，则我们称 $\boldsymbol{s}\_1, \boldsymbol{s}\_2, \cdots, \boldsymbol{s}\_n$ 线性独立。

> **Casorati 矩阵** (/kəˈsɔːrəti/)：我们取一个整数值 $x$，则对于该 $x$ 值的 Casorati 矩阵为
>
> $$\left[
    \begin{matrix}
        \boldsymbol{s}\_1(x) & \boldsymbol{s}\_2(x) & \cdots & \boldsymbol{s}\_n(x) \\\\
        \boldsymbol{s}\_1(x+1) & \boldsymbol{s}\_2(x+1) & \cdots & \boldsymbol{s}\_n(x+1) \\\\
        \vdots & \vdots & \ddots & \vdots \\\\
        \boldsymbol{s}\_1(x+n-1) & \boldsymbol{s}\_2(x+n-1) & \cdots & \boldsymbol{s}\_n(x+n-1) \\\\
    \end{matrix}
    \right]$$

若对于至少一个 $x$ 值，满足

$$\left[
    \begin{matrix}
        \boldsymbol{s}\_1(x) & \boldsymbol{s}\_2(x) & \cdots & \boldsymbol{s}\_n(x) \\\\
        \boldsymbol{s}\_1(x+1) & \boldsymbol{s}\_2(x+1) & \cdots & \boldsymbol{s}\_n(x+1) \\\\
        \vdots & \vdots & \ddots & \vdots \\\\
        \boldsymbol{s}\_1(x+n-1) & \boldsymbol{s}\_2(x+n-1) & \cdots & \boldsymbol{s}\_n(x+n-1) \\\\
    \end{matrix}
    \right] 
    \left[
    \begin{matrix}
    c\_1 \\\\
    c\_2 \\\\
    \ldots \\\\
    c\_n
    \end{matrix}
    \right] 
 =  \left[
    \begin{matrix}
    0 \\\\
    0 \\\\
    \ldots \\\\
    0
    \end{matrix}
    \right] $$

仅有平凡解，即此时的 Casorati 矩阵可逆，那么就可以证明这些信号线性无关。

## 线性差分方程

> **线性差分方程**：对于 $a\_0, a\_1, \cdots, a\_n \in R$，且 $a\_0, a\_n \ne 0$，给定信号 $\boldsymbol{z}$，则方程
>
> $$\sum\_{i=0}^n a\_i \boldsymbol{y}(k + n-i) = \boldsymbol{z}(k), \forall k \in Z$$
>
> 称为一个 **$\boldsymbol n$ 阶线性差分方程（线性递归关系）**。
>
> 若 $\boldsymbol{z} = \boldsymbol{0}$，则方程是齐次的。否则方程是非齐次的。