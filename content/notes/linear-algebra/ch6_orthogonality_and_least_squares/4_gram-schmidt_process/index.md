---
title: 线性代数 | 6.4 Gram-Schimidt 方法
date: 2024-12-23
summary: Gram-Schimidt 方法、QR 分解
---

**【Gram-Schimidt 方法】**：对于 $\mathbb R^n$ 子空间 $W$ 的一个基 $\\\{\boldsymbol{x}\_1, \boldsymbol{x}\_2, \cdots, \boldsymbol{x}\_p\\\}$，我们构造等价的正交基  $\\\{\boldsymbol{v}\_1, \boldsymbol{v}\_2, \cdots, \boldsymbol{v}\_p\\\}$：

$$\begin{aligned}
\boldsymbol{v}\_1 &= \boldsymbol{x}\_1 \\\\
\boldsymbol{v}\_i &= \boldsymbol{x}\_i - \sum\_{j = 1}^{i - 1} \operatorname{proj}\_{\boldsymbol{v}\_j} \boldsymbol{x}\_i\\\\
\end{aligned}$$

正交基中每个基都除以它的长度，即可得到标准正交基。

**【QR 分解】**：若 $m \times n$ 矩阵 $A$ 各列线性无关，则 $A$ 可以分解为 $A = QR$。其中 $Q$ 是 $m \times n$ 的矩阵，各列形成 $\operatorname{Col} A$ 的标准正交基，$R$ 是 $n\times n$ 上三角可逆矩阵，且对角线上的元素是正数。

本质：用正交基表示某一个基。