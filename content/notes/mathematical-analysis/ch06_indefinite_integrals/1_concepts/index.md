---
title: 数学分析 | 6.1 不定积分的概念
date: 2024-11-20
summary: 不定积分的定义、不定积分表
---

这里收录了我在大一上、下学期学习的《数学分析》课程中 **第四章 微商与微分** 的完整笔记。


## 不定积分的定义

> **原函数**：若在区间 $I$ 内每一点，均有 $F'(x) = f(x)$，则称 $F(x)$ 是 $f(x)$ 在 $I$ 上的一个原函数。

> **定理**：若 $F(x)$ 是 $f(x)$ 在区间 $I$ 内的一个原函数，则 $F(x) + c$（$c$ 是任意常数） 是 $f(x)$ 的全体原函数。
>
> **证明**：必要性： 若 $G(x)$ 是 $f(x)$ 的一个原函数，则
>
> $$(G(x) - F(x))' = f(x) - f(x) = 0$$
>
> 因此 $G(x) - F(x) = c$.
>
> 充分性：$(F(x) + c)' = f(x)$ 成立。

> **不定积分**：$f(x)$ 在区间 $I$ 上的原函数全体成为 $f(x)$ 在区间 $I$ 上的不定积分，记为 $\int f(x) \mathrm dx$。
>
> **小部分名称**：
>
> - $\displaystyle\int$：积分号
> - $f(x)$：被积函数
> - $x$：积分变量
> - $f(x)\mathrm dx$：被积表达式。
>
> 若 $F(x)$ 是 $f(x)$ 在 $I$ 上的一个原函数，那么
>
> $$\int f(x) \mathrm dx = F(x) + c$$

## 不定积分表

1. 幂函数：$\displaystyle \int x^n \mathrm dx = \dfrac{1}{n + 1} x^{n + 1} + c,\ (n \ne -1, x > 0)$
2. 反比例函数：$\displaystyle \int \dfrac{1}{x} \mathrm dx = \ln |x| + c\ (x \ne 0)$
3. 幂函数：$\displaystyle \int a^x \mathrm dx = \frac{a^x}{\ln a} + c, (a > 0, a \ne 1)$
   
    $\displaystyle \int e^x \mathrm dx = e^x + c$

4. 三角函数：
   
   $\displaystyle \int \cos x \mathrm dx = \sin x + c$

   $\displaystyle \int \sin x \mathrm dx = -\cos x + c$

   $\displaystyle \int \sec^2 x \mathrm dx = \tan x + c$

   $\displaystyle \int \csc^2 x \mathrm dx = - \cot x + c$

5. 某些分式函数：

   $\displaystyle \int \frac{1}{\sqrt{1 - x^2}} \mathrm dx = \arcsin x + c = - \arccos x + c$

   $\displaystyle \int \frac{1}{\sqrt{1 + x^2}} \mathrm dx = \arctan x + c = - \operatorname{arccot} x + c$

   $\displaystyle \int \frac{1}{|x| \sqrt{x^2 - 1}} = \operatorname{arcsec} x + c = - \operatorname{arccsc} x + c$

> **定理 6.2（不定积分的线性运算法则）**：若 $f(x), g(x)$ 在区间 $I$ 上的原函数存在，且 $k \in \mathbb R$，那么有
>
> $$\int (f(x) \pm g(x)) \mathrm dx = \int f(x) \mathrm dx  \pm \int g(x) \mathrm dx$$
>
> $$\int kf(x) \mathrm dx = k \int f(x) \mathrm dx$$
>
> **证明**：直接验证两边被积函数求导后相同即可。

求一个函数的不定积分，我们常常把它们化成积分表中能积分的函数，从而利用线性法则进行积分。

如果有整式 $\rightarrow$ 化为 $x^n$；

如果有分式 $\rightarrow$ 化为 $\displaystyle \frac{1}{\sqrt{1 - x^2}}, \frac{1}{1 + x^2}, \frac{1}{|x|\sqrt{x^2 - 1}}$；

如果有幂函数 $\rightarrow$ 化为 $a^x, e^x$；

如果有三角函数 $\rightarrow$ 化为 $\sin x, \cos x, \sec^2 x, \csc^2 x$；

