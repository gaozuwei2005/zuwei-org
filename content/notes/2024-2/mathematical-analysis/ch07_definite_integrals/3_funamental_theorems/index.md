---
title: 数学分析 | 7.3 微积分基本定理
date: 2024-12-03
summary: 变上限定积分可导、微积分基本定理、微积分基本公式
---

## 变上限定积分可导

> **定理 7.10**：设 $f(x)$ 在 $[a,b]$ 可积，则 $\displaystyle G(x) = \int_a^x f(t) \mathrm dt$ 是 $[a,b]$ 的可导函数，且 $G'(x) = f(x), \forall x \in [a,b]$。
>
> **证明**：
>
> $$\frac{G(x + \Delta x) - G(x)}{\Delta x} = \frac{1}{\Delta x} \int_{x}^{x + \Delta x} f(t) \mathrm dt$$
>
> 由积分中值定理可知，$\exists \xi \in [x, x + \Delta x]$，使得
>
> $$\int_{x}^{x + \Delta x} f(t) \mathrm dt = f(\xi) \Delta x$$
>
> 因此
>
> $$\lim_{\Delta x \to 0} \frac{G(x + \Delta x) - G(x)}{\Delta x} = \lim_{\Delta x\to 0} f(\xi) = f(x)$$
>
> **几何解释**：变动的曲边梯形的面积变化率就是纵坐标。

该定理指出，任何连续函数都有原函数存在，其中一个原函数是 $f(x)$ 的变上限定积分。

## 微积分基本定理

> **微积分基本定理（1）**：设 $f(x)$ 在 $[a,b]$ 上**连续**，$F(x)$ 是 $f(x)$ 在 $[a,b]$ 的任意一个原函数，则
>
> $$\int_a^b f(x)\mathrm dx = F(b) - F(a)$$
>
> **证明**：由于 $\displaystyle G(x) = \int_a^x f(t) \mathrm dt$ 是 $f(x)$ 的一个原函数，因此
>
> $$F(x) = G(x) + c$$
>
> 于是
>
> $$\begin{aligned}
F(b) - F(a) &= \left(\int_a^b f(t) \mathrm dt + c\right) - \left(\int_a^a f(t) \mathrm dt + c\right) \\&= \int_a^b f(t)\mathrm dt
\end{aligned}$$

> **微积分基本定理（2）**：设 $f(x)$ 在 $[a,b]$ 上**可积**，$F(x)$ 是 $f(x)$ 在 $[a,b]$ 的任意一个原函数，则
>
> $$\int_a^b f(x)\mathrm dx = F(b) - F(a)$$
>
> **证明**：对于 $[a,b]$ 的任意分法：
>
> $$a = x_0 < x_1 < \cdots < x_n = b$$
>
> 由微分中值定理可知， $\exists \xi_i \in [x_{i-1}, x_i]$，使得
>
> $$\begin{aligned}
&F(b) - F(a)\\
=&\sum_{i = 1}^n (F(x_i) - F(x_{i-1}))\\
=&\sum_{i = 1}^n f(\xi_i) \Delta x_i
\end{aligned}$$
>
> 这刚好是 $\displaystyle \int_a^b f(x)\mathrm dx$ 的定义，我们令 $\displaystyle\lambda = \max_{1 \le i \le n} \{\Delta x_i\} \to 0$，那么有
>
> $$F(b) - F(a) = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i) \Delta x_i = \int_a^b f(x) \mathrm dx$$

## 微积分基本公式

> **微积分基本公式（牛顿——莱布尼兹 (Newton- Leibniz)公式）**：
>
> $$\left.\int_a^b f(x) \mathrm dx =  F(x) \right\vert_a^b$$
>
> 其中 $F(x)$ 是 $f(x)$ 的任意一个原函数。