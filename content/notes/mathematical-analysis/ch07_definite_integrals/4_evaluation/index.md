---
title: 数学分析 | 7.4 定积分的计算
date: 2024-12-04
summary: 定积分换元法、特殊函数的积分性质
---

## 定积分换元法

> **定积分换元法则**：若 $f(x)$ 在 $[a,b]$ 连续，作变换 $x = \varphi(t)$，其中 $\varphi(t)$ 满足：
>
> - $\varphi(\alpha) = a, \varphi(\beta) = b$, 且 $\phi(t) \in [a,b], \forall t \in [\alpha, \beta]$
> - $\varphi(t)$ 在 $[\alpha, \beta]$ 有连续微商 $\varphi'(t)$ 则
>
> $$\int_a^b f(x) \mathrm dx = \int_\alpha^\beta f(\varphi(t)) \varphi'(t) \mathrm dt$$
>
> **证明**：设 $F(x)$ 是 $f(x)$ 的一个原函数，那么
>
> $$F(\varphi(t)) = F'(\varphi(t))\varphi'(t)\mathrm dt = f(\varphi(t)) \varphi'(t) \mathrm dt$$
>
> 因此 $F(\varphi(t))$ 是 $f(\varphi(t)) \varphi'(t)$ 的原函数。
>
> 由牛顿——莱布尼兹公式可得
>
> $$\left.\int_a^b f(x) \mathrm dx = F(x) \right\vert_a^b$$
>
> $$\left.\int_\alpha^\beta f(\varphi(t)) \varphi'(t) \mathrm dt = F(\varphi(t)) \right\vert_a^b$$
>
> 由于 $a = \varphi(\alpha), b = \varphi(\beta)$，因此两边相等，证毕。

因此使用换元法则的时候，我们只需找到 $x = \varphi(t)$，那么把 $\mathrm dx = \varphi'(t) \mathrm dt$，并把 $x$ 对应的上下限改成 $t$ 对应的上下限即可。

## 特殊函数的积分性质

- 若 $f(x)$ 在 $[-a,a]$ 连续，若 $f(x)$ 是偶函数，那么 $\displaystyle \int_{-a}^a f(x) \mathrm dx = 2 \int_0^a f(x) \mathrm dx$
- 若 $f(x)$ 在 $[-a,a]$ 连续，若 $f(x)$ 是奇函数，那么 $\displaystyle \int_{-a}^a f(x) \mathrm dx = 0$
- 若 $f(x)$ 在以 $T$ 为周期的连续函数，那么 $\displaystyle \int_{a}^{a+T} f(x) \mathrm dx = \int_0^a f(x) \mathrm dx$

