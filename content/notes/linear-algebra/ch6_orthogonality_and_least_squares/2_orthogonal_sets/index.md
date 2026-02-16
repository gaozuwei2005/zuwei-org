---
title: 线性代数 | 6.2 正交集
date: 2024-12-18
summary: 正交投影、单位正交集
---

**正交集**：若集合 $S = \\\{\boldsymbol{u}_1, \boldsymbol{u}_2, \cdots, \boldsymbol{u}_p\\\}$  是正交集，那么集合内两个不同向量都正交，即 $\boldsymbol{u}_i · \boldsymbol{u}_j = 0, \forall i \ne j$.

**【正交集是线性无关集】**：若集合 $S = \\\{\boldsymbol{u}_1, \boldsymbol{u}_2, \cdots, \boldsymbol{u}_p\\\}$  是正交集，那么 $S$ 也是线性无关集，因此 $S$ 是 $\operatorname{Span} S$ 的一一组基。

**【正交基下的坐标】**：对于一个正交基 $\\\{\boldsymbol{u}_1, \boldsymbol{u}_2, \cdots, \boldsymbol{u}_p\\\}$，$\boldsymbol{v}$ 在 $\boldsymbol{u}_j$ 的坐标为 $c_j = \dfrac{\boldsymbol{y}·\boldsymbol{u}_j}{\boldsymbol{u}_j^2}$.（投影向量的长度）

## 正交投影

**正交投影**：$\displaystyle \operatorname{proj}_{L} \boldsymbol{y} = \hat{\boldsymbol{y}} = \frac{\boldsymbol{y}·\boldsymbol{u}}{\boldsymbol{u}^2}·\boldsymbol{u}$

**正交分量**：$\boldsymbol{z} = \boldsymbol{y} - \operatorname{proj}_L \boldsymbol{y}$

其中，$L = \operatorname{Span}\\\{ \boldsymbol{u} \\\}$.

## 单位正交集

**【矩乘判断单位正交列矩阵】**：$m \times n$ 矩阵 $U$ 具有单位正交列向量的充要条件为 $U^\top U = I$。

**【单位正交列矩阵的性质】**：对于单位正交列矩阵 $U \in \mathbb R^{m \times n}$，$\boldsymbol{x, y} \in \mathbb R^n$，则

1. $\Vert U\boldsymbol{x} \Vert = \Vert \boldsymbol{x} \Vert$
2. $(U\boldsymbol{x})·(U\boldsymbol{y}) = \boldsymbol{x} · \boldsymbol{y}$