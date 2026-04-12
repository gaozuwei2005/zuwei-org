---
title: 线性代数 | 6.1 内积、长度和正交性
date: 2024-12-18
summary: 内积、向量的长度、$\mathbb R^n$ 中的距离、正交向量、正交补、角度
---

## 内积

> **点积**：两个向量的点积为 $\boldsymbol{u · v} = \boldsymbol{u}^T\boldsymbol{v}$.

> **【内积的性质】**：
>
> - $\boldsymbol{u·v} = \boldsymbol{v·u}$
> - $(\boldsymbol{u} + \boldsymbol{v})·\boldsymbol{w} = \boldsymbol{u}·\boldsymbol{w} + \boldsymbol{v}·\boldsymbol{w}$
> - $(c\boldsymbol{u})·\boldsymbol{v} = c(\boldsymbol{u·v}) = \boldsymbol{u}·(c\boldsymbol{v})$
> - $(c_1\boldsymbol{u}_1 + c_2\boldsymbol{u}_2 + \cdots + c_p\boldsymbol{u}_p)·\boldsymbol{v} = c_1(\boldsymbol{u}_1·\boldsymbol{v}) + c_2(\boldsymbol{u}_2·\boldsymbol{v}) + \cdots +  c_p(\boldsymbol{u}_p·\boldsymbol{v})$

## 向量的长度

> **长度（范数）**：向量 $\boldsymbol{v}$ 的长度是非负数 $\Vert\boldsymbol{v}\Vert$，定义为
>
> $$\Vert\boldsymbol{x}\Vert  = \sqrt{\boldsymbol{v}·\boldsymbol{v}} = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2}$$

在二维、三维空间中，范数的定义和向量长度的定义是一致的。

> **范数的性质**：$\Vert c\boldsymbol{v} \Vert = |c| \Vert \boldsymbol{v} \Vert$.

> **单位向量**：长度为 $1$ 的向量。
>
> **单位化**：将一个非零向量除以自身的长度，就可以得到一个单位向量，即 $\boldsymbol{u} = \dfrac{\boldsymbol{v}}{\Vert \boldsymbol{v} \Vert}$，该过程称为 $\boldsymbol{v}$ 的单位化。

## $\mathbb R^n$ 中的距离

> **距离**：$\mathbb R^n$ 中两个向量 $\boldsymbol{u,v}$ 之间的距离为 
> 
> $$\operatorname{dist}(\boldsymbol{u}, \boldsymbol{v}) = \Vert \boldsymbol{u} - \boldsymbol{v} \Vert = \sqrt{(u_1-v_1)^2 + (u_2 - v_2)^2 + \cdots + (u_n - v_n)^2}$$

在二维、三维空间中，距离的定义和两点距离的定义是一致的。

## 正交向量

> **正交**：如果 $\boldsymbol{u}·\boldsymbol{v} = 0$，那么 $\boldsymbol{u}$ 和 $\boldsymbol{v}$ 是 **（相互）正交** 的。

> **【毕达哥拉斯（勾股）定理】**：两个向量 $\boldsymbol{u}, \boldsymbol{v}$ 正交的充分必要条件是 $\Vert \boldsymbol{u} + \boldsymbol{v} \Vert^2 = \Vert \boldsymbol{u} \Vert^2 + \Vert \boldsymbol{v} \Vert^2$

## 正交补

> **向量与平面正交**：若向量 $\boldsymbol{z}$ 与子空间 $W$ 中任意向量都正交，则称 $\boldsymbol{z}$ 正交于 $W$。
>
> **正交补**：与子空间 $W$ 正交的向量 $\boldsymbol{z}$ 组成的集合称为 $W$ 的正交补，记作 $W^\perp$，读作 $W$ 正交补。

> **【正交补的性质】**：$W^\perp$ 是 $\mathbb R^n$ 的一个子空间。

> **【正交补与行列零空间的关系】**：若 $A$ 是 $m \times n$ 矩阵，那么：
> 
> （1）$A$ 的行空间的正交补是 $A$ 的零空间；
>
> $$(\operatorname{Row} A)^\perp = \operatorname{Nul} A$$
> 
> （2）$A$ 的列空间的正交补是 $A^T$ 的零空间。
>
> $$(\operatorname{Col} A)^\perp = \operatorname{Nul} A^T$$
>
> **证明**：
> 
> （1）由于 $\operatorname{Nul} A$ 中的每一个向量与 $A$ 的每一行向量正交，因此与行空间正交。反之，如果 $\boldsymbol{x}$ 与 $\operatorname{Row} A$ 正交，那么必然也和 $A$ 的每个行向量正交，因此 $A\boldsymbol{x} = \boldsymbol{0}$。
>
> （2）我们用 $A^T$ 替换（1）中的 $T$ 得到 $(\operatorname{Row} A^T)^\perp = \operatorname{Nul} A^T$，即 $(\operatorname{Col} A)^\perp = \operatorname{Nul} A^T$。

## 角度

原点和 $\boldsymbol{u,v}$ 的终点确定的三角形的三边边长为 $\Vert \boldsymbol{u} \Vert, \Vert \boldsymbol{v} \Vert, \Vert \boldsymbol{u} - \boldsymbol{v} \Vert$，根据余弦定理可知，**两向量夹角**为

$$\cos \theta = \frac{\Vert \boldsymbol{u} \Vert^2 + \Vert \boldsymbol{v} \Vert^2 - \Vert \boldsymbol{u} - \boldsymbol{v} \Vert^2}{2 \Vert \boldsymbol{u} \Vert\Vert \boldsymbol{v} \Vert}$$

其中 $\cos \theta$ 就是统计学中的相关系数。