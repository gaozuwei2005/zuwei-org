---
title: 线性代数 | 6.3 正交投影
date: 2024-12-23
summary: 正交分解定理、最佳逼近定理、矩乘计算投影向量
---

**【正交分解定理】**：对于 $\mathbb R^n$ 的子空间 $W$ 和 $\boldsymbol{y} \in \mathbb R^n$，则 $\boldsymbol{y}$ 可以唯一标识为 $\boldsymbol{y} = \hat{\boldsymbol{y}} + \boldsymbol{z}$，其中 $\hat{\boldsymbol{y}} \in W,\  \boldsymbol{z} \in W^{\perp}$

**正交投影**：$\operatorname{proj}_{W} \boldsymbol{y} = \hat{\boldsymbol{y}}$.

**【最佳逼近定理】**：对于 $\mathbb R^n$ 的子空间 $W$ 和 $\boldsymbol{y} \in \mathbb R^n$，则 $\operatorname{proj}_{W} \boldsymbol{y}$ 是 $W$ 中最接近 $\boldsymbol{y}$ 的点。

$$\Vert \boldsymbol{y} - \hat{\boldsymbol{y}} \Vert \le \Vert \boldsymbol{y} - \boldsymbol{u} \Vert$$

**【矩乘计算投影向量】**：对于 $\mathbb R^n$ 的子空间 $W$ 和 $\boldsymbol{y} \in \mathbb R^n$，则

$$\operatorname{proj}_{W} \boldsymbol{y} = (\boldsymbol{u}·\boldsymbol{u}_1)\boldsymbol{u}_2 + (\boldsymbol{u}·\boldsymbol{u}_2)\boldsymbol{u}_2 + \cdots + (\boldsymbol{u}·\boldsymbol{u}_n)\boldsymbol{u}_n$$

$$\operatorname{proj}_{W} \boldsymbol{y} = UU^\top \boldsymbol{y}$$