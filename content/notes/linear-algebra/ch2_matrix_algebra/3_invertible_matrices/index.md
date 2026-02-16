---
title: 线性代数 | 2.3 可逆矩阵的特征
date: 2024-12-02
summary: 可逆矩阵定理、可逆矩阵变换
---

## 可逆矩阵定理

> **定理 8（可逆矩阵定理）**：设 $A$ 是 $n \times n$ 的矩阵，那么以下命题是等价的：
>
> 1. （可逆矩阵）$A$ 是可逆的。$A^T$ 是可逆矩阵
> 2. （行简化）$A$ 行等价于 $I_n$。$A$ 有 $n$ 个主元。
> 3. （向量方程）方程 $A \boldsymbol{x} = \boldsymbol{0}$ 仅有平凡解。$\forall \boldsymbol{b} \in \mathbb R^n$，方程 $A \boldsymbol{x} = \boldsymbol{b}$ 至少有一个解。
> 4. （线性无关）$A$ 的各列线性无关。
> 5. （线性变换）线性变换 $\boldsymbol{x} \mapsto A\boldsymbol{x}$ 是一对一的，并且能把 $\mathbb R^n$ 映上 $\mathbb R^n$。
> 6. （列空间）$A$ 的各列生成 $\mathbb R^n$。
>
> **证明**：在前面章节中，命题 2~6 都被证明与命题 1 等价，因此这些命题都等价。

## 可逆线性变换

> **可逆线性变换**：线性变换 $T : \mathbb R^n \mapsto \mathbb R^n$ 是可逆的，若存在函数 $S : \mathbb R^n \mapsto \mathbb R^n$，使得
>
> $$\forall \boldsymbol{x} \in \mathbb R^n, S(T(\boldsymbol{x})) = \boldsymbol{x}$$
> $$\forall \boldsymbol{x} \in \mathbb R^n, T(S(\boldsymbol{x})) = \boldsymbol{x}$$

> **定理 9**：设 $T : \mathbb R^n \rightarrow \mathbb R^n$ 是线性变换，且 $A$ 是 $T$ 的标准矩阵，那么 $T$ 可逆当且仅当 $A$ 是可逆矩阵，这时线性变换 $S(\boldsymbol{x}) = A^{-1} \boldsymbol{x}$ 是 $T$ 的唯一的逆。
>
> **证明**：由于存在 $S$ 使得 $\forall \boldsymbol{x} \in \mathbb R^n, T(S(\boldsymbol{x}))=\boldsymbol{x}$，因此 $T$ 是 $\mathbb R^n \rightarrow \mathbb R^n$ 的映射，因此由可逆矩阵定理可知，$A$ 是可逆的。
>
> 接下来验证 $S$ 是 $T$ 的逆：
>
> $$S(T(\boldsymbol{x})) = A^{-1} A \boldsymbol{x} = \boldsymbol{x}$$
> $$T(S(\boldsymbol{x})) = A A^{-1} \boldsymbol{x} = \boldsymbol{x}$$
>
> 并且由于 $S(\boldsymbol{v}) = \boldsymbol{x}$，对于每个 $\boldsymbol{x} \in \mathbb R^n$，均有唯一的 $\boldsymbol{v}$ 与之对应，因此 $S$ 是 $T$ 唯一的逆。