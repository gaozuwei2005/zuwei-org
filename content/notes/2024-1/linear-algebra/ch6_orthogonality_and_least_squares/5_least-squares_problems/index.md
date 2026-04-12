---
title: 线性代数 | 6.5 最小二乘问题
date: 2024-12-23
summary: 最小二乘解、最小二乘解与可逆矩阵
---


**【最小二乘解】**：方程 $A\boldsymbol{x} = \boldsymbol{b}$ 的解集和 $A^\top A\boldsymbol{x} = A^\top \boldsymbol{b}$ 的非空解集一致。

**【最小二乘解与可逆矩阵】**：对于 $A \in \mathbb R^{m \times n}$，则下列命题等价：

1. $\forall \boldsymbol{b} \in \mathbb R^m$，方程 $A\boldsymbol{x} = \boldsymbol{b}$ 有唯一最小二乘解。且 $\hat{\boldsymbol{x}} = (A^\top A)^{-1} A^\top \boldsymbol{b}$。
2. $A$ 的列线性无关。
3. $A^\top A$ 是可逆的。