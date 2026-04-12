---
title: 线性代数 | 4.1 向量空间与子空间
date: 2024-11-25
summary: 向量空间、子空间、由集合生成的子空间
---

## 向量空间 *Vector Space*

> **向量空间**：一些可视作向量的对象构成的非空集合 *nonempty set* $V$。定义两个运算： 向量加法 *addition*、标量乘法 *multiplication by scalars (real numbers)*。
>
> 对于所有 $\boldsymbol{u,v,w} \in V, c,d \in R$，均有以下公理 *axioms*
>
> - 向量加法封闭性：$\boldsymbol{u} + \boldsymbol{v} \in V$
> - 向量加法交换律：$\boldsymbol{u} + \boldsymbol{v} = \boldsymbol{v} + \boldsymbol{u}$
> - 向量加法结合律：$(\boldsymbol{u} + \boldsymbol{v}) + \boldsymbol{w} = \boldsymbol{u} + (\boldsymbol{v} + \boldsymbol{w})$
> - 零向量 *zero vector*：有且仅有一个零向量 $\boldsymbol{0}$，使得 $\boldsymbol{u} + (-\boldsymbol{u}) = \boldsymbol{0}$
> - 相反向量：对于每个向量 $\boldsymbol{u}$，有且仅有一个相反向量 $-\boldsymbol{u}$，使得 $\boldsymbol{u} + (-\boldsymbol{u}) = \boldsymbol{0}$
> - 标量乘法封闭性 *scalar multiple*：$c\boldsymbol{u} \in V$
> - 标量乘法对向量加法分配律：$(c + d) \boldsymbol{u} = c \boldsymbol{u} + d \boldsymbol{u}$
> - 标量乘法结合律：$c(d\boldsymbol{u})  =(cd)\boldsymbol{u}$
> - 单位标量：$1 \boldsymbol{u} = \boldsymbol{u}$
> 
>  由以上性质可以推出其他性质（有关零向量与相反向量 *negative vector*）：
>
> - $0\boldsymbol{u} = \boldsymbol{0}$
> - $c\boldsymbol{0} = \boldsymbol{0}$
> - $-\boldsymbol{u} = (-1)\boldsymbol{u}$

向量空间的例子：

- $\mathbb{R}^n\ (n \ge 1)$
- $n$ 维空间所有有向线段 *arrow (directed line segments)* 的集合。向量加法满足平行四边形法则 *parallelogram rule*，标量乘法是有向线段的拉伸。
- 最高次数 *degree* 为 $n$ 次的所有多项式 *polynomial* $\mathbb{P}_n$
- $\mathbb{D} \to \mathbb{R}$ 的全体实值函数 *real-valued function* 的集合。

## 子空间 *Subspaces*

> **子空间**：向量空间 $V$ 中的一个子空间 $H$ 满足：
>
> - $V$ 中的零向量也在 $H$ 中；
> - 对向量加法封闭 *closed under vector additon*：$\forall \boldsymbol{u,v}\in H, \boldsymbol{u + v}\in H$
> - 对标量乘法封闭 *colsed under multiplication by scalars*：$\forall c\in \mathbb{R}, \boldsymbol{u} \in V, c\boldsymbol{u}\in V$

以上三个定义可以保证**子空间也是向量空间**，即子空间也满足刚才的十多个性质。

同时任何向量空间，相对于其他更大的向量空间而言，也可以视作一个子空间。

（是或非）子空间的例子：

- 零子空间 *zero subspace* $\\\{\boldsymbol{0}\\\}$
- 三维空间中 $x = 0$ 的平面 $H = \left\\\{ \left.\begin{bmatrix} s \\\\ t \\\\ 0 \end{bmatrix}\right\vert s, t \in \mathbb R\right\\\}$。注意 $\mathbb R^2$ 不是 $\mathbb R^3$ 的子空间；
- 过原点的直线 *line through the origin*。注意不过原点的直线不是子空间。
- 过原点的平面 *plane through the origin*。注意不过原点的平面不是子空间。

## 由一个集合生成的子空间 *A Subspace Spanned by a Set*

> **线性组合** *linear combination*：一些向量的任意标量乘法之和 *any sum of scalar multiples of vectors*。

> **生成（张成）子空间**：$H = \operatorname{Span}\\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n\\\}$ 是所有可以表示为 $\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n$ 的线性组合的向量的集合 *Subspace spanned (generated) by a set*。
>
> **生成集（张成集）**：在上面的定义中，$\\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n\\\}$ 是 $H$ 的生成集 *spanning (generating) set*。

> **定理 1：** 若 $\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n \in V$，则 $\operatorname{Span}\\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n\\\}$ 是 $V$ 的一个子空间。
>
> **证明**：从张成子空间存在零向量、对加法封闭、对乘法封闭来证明。

如果要证明一个向量空间是否为另一个向量空间的子空间，我们只需找出这个向量空间表示为生成集 $\\\{\boldsymbol{v}_1, \boldsymbol{v}_2, \cdots, \boldsymbol{v}_n\\\}$，再证明这些向量均属于另一个向量空间即可。

**如何认识一个向量空间**：找出它的生成集。

判断一个向量是否在一个生成子空间中：建立生成集与该向量的增广矩阵，判断其是否相容。

