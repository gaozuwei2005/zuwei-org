---
title: 数学分析 | 6.2 换元积分法与分部积分法
date: 2024-11-21
summary: 换元积分法、分部积分法、有理函数的积分、三角函数有理式的积分
---


## 换元积分法

> **定理 6.3（第一换元法或凑微分法）**：设
>
> $$\int g(u) \mathrm du = G(u) + c$$
>
> 并且 $u = \phi'(x)$ 可微，那么
>
> $$\int g(\phi(x)) \phi'(x) \mathrm dx  = G(\phi(x)) + c$$
>
> **证明**：只需验证右边导数等于左边的被积函数即可。

要应用换元积分法，我们需要被积表达式写成

$$\begin{aligned}
&\int g(\phi(x)) \phi'(x) \mathrm dx  \\\\
=& \int g(\phi(x)) \mathrm d\phi(x) \\\\
=& G(\phi(x)) + c
\end{aligned}$$

### 常见拆分方式

- $\displaystyle \frac{1}{x^2 - a^2} = \frac{1}{2a} \left(\frac{1}{x - a} - \frac{1}{x + a}\right)$

常见的换元方式：

- $\displaystyle \mathrm dx = \frac{1}{a} \mathrm d(ax)$
- $\displaystyle \mathrm dx = \frac{1}{a} \mathrm d(ax+b)$
- 

## 分部积分法

对于关于 $x$ 的可微函数 $u,v$，我们已知

$$\mathrm d(uv) = v\mathrm du + u \mathrm dv$$

$$\int u \mathrm dv = uv - \int v \mathrm d u$$

> **定理 6.5（分部积分公式）** ：若 $u(x), v(x)$ 可导，若 $v(x)u'(x)$ 存在原函数，那么 $u(x)v'(x)$ 也存在原函数，
>
> $$\int u(x)v'(x)\mathrm dx = u(x)v(x) - \int u'(x)v(x)\mathrm dx$$

使用分部积分法时，$v'(x)$ 需要易于积分，并且 $u'(x)v(x)$ 需要易于积分。

**选取 $\boldsymbol{u(x)}$ 的次序（从高到低）：对反幂三指**。对数函数、反三角函数、幂函数、三角函数、指数函数。

$$\begin{aligned}
\int f(x) \ln x \mathrm dx &= F(x) \ln x  &&- \int \frac{F(x)}{x} \mathrm dx \\\\
\int f(x) \arctan x \mathrm dx&= F(x) \arctan x &&- \int \frac{F(x)}{\sqrt{1 - x^2}} \mathrm dx \\\\
\int f(x)x^n \mathrm dx &= F(x)x^n &&- \int F(x)·nx^{n-1} \mathrm dx\\\\
\int f(x)\sin x \mathrm dx &= - F(x)\cos x && - \int F(x) \cos x \mathrm dx \\\\
\int f(x)e^x \mathrm dx &= -F(x)e^x && - \int F(x)e^x \mathrm dx 
\end{aligned}$$

what，例子好玄妙。

初等函数的原函数可能不再是初等函数：例如

$$\int e^{-x^2} \mathrm dx, \int \frac{\sin x}{x} \mathrm dx, \int \sin x^2 \mathrm dx$$

## 有理函数的积分

> **有理函数** ：两个多项式的商。
>
> $$R(x) = \frac{P_n(x)}{Q_m(x)}$$
>
> 其中 $P_n(x), Q_m(x)$ 分别是 $n$ 次多项式和 $m$ 次多项式。当 $n < m$ 时，$R(x)$ 为 **真分式**。

当 $R(x)$ 不是真分式时，可以使用多项式除法将其表示为一个多项式与一个真分式之和。

> **分式分解：** 任一真分式理论上可分解为四种真分式之和。
>
> $$\begin{aligned}
&(1)\frac{A}{x-a} && (2) \frac{A}{(x-a)^n} \\\\
&(3)\frac{Bx+C}{x^2+px+q} && (4) \frac{Bx+C}{(x^2+px+q)^n}
\end{aligned}$$
> 
> 其中 $p^2-4q < 0, n = 2, 3, \cdots$
>
> 需要结合代数基本定理和待定系数法证明。

四种分式均可积：

$$\begin{aligned}
(1)&\int \frac{A}{x-a} \mathrm dx = A \ln |x-a| + C; \\\\
(2)&\int \frac{A}{(x-a)^n} \mathrm dx = \frac{A}{1-n} (x-a)^{1-n} + C,\ n =2, 3, \cdots \\\\
(3)&\int \frac{x + b}{x^2 + px + q} \mathrm dx\\\\
=& \frac{1}{2} \int \frac{(2x + p) + (2b - p)}{x^2 + px + q} \mathrm dx \\\\
=& \frac{1}{2} \int \frac{\mathrm d(x^2 + px + q)}{x^2 + px + q} \mathrm dx + \frac{2b - p}{2} \int \frac{\mathrm d(x + \frac{p}{2})}{(x + \frac{p}{2})^2 + (q - \frac{p^2}{4})} \\\\
& （拆成两个部分，均可积） \\\\
(4)&\int \frac{x + b}{(x^2 + px + q)^n} \mathrm dx \\\\
=& \frac{1}{2} \int \frac{(2x + p) + (2b - p)}{(x^2 + px + q)^n} \mathrm dx \\\\
=& \frac{1}{2} \int \frac{\mathrm d(x^2 + px + q)}{(x^2 + px + q)^n} \mathrm dx + \frac{2b - p}{2} \int \frac{\mathrm d(x + \frac{p}{2})}{[(x + \frac{p}{2})^2 + (q - \frac{p^2}{4})]^n} \\\\
& （拆成两个部分，均可积） \\\\
\end{aligned}$$

在分解分式的过程中，我们使用待定系数法、特殊值法、或者拼凑法。

## 三角函数有理式的积分

> **三角函数有理式**：三角函数和常数经有限次的四则运算所得到的式子。通常记为 $R(\sin x, \cos x)$

我们知道万能公式

$$\begin{aligned}
\sin x &= 2 \sin \frac{x}{2} \cos \frac{x}{2} = \frac{2 \tan \frac{x}{2}}{1 + \tan^2 \frac{x}{2}}\\\\
\cos x &= \cos^2 x - \sin^2 x = \frac{1 - \tan^2 \frac{x}{2}}{1 + \tan^2 \frac{x}{2}} \\\\
\end{aligned}$$

令 $\tan \frac{x}{2} = t$（称为 **万能变换**），则 $x = 2\arctan t, \mathrm dx = \frac{2}{1 + t^2} \mathrm dt$

$$\int R(\sin x, \cos x) \mathrm dx = \int R \left(\frac{2t}{1 + t^2}, \frac{1 - t^2}{1 + t^2}\right) \frac{2}{1 + t^2} \mathrm dt$$

这样我们就把三角函数有理式转换为有理函数，积分可通过刚才的讨论求出。

最终，我们再把积分后的 $t$ 替换为 $\tan \frac{x}{2}$ 即为最终的结果。