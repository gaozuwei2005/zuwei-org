---
title: 数学分析 | Ch19 含参变量的积分
date: 2025-04-09
summary: 普通积分的极限与导数、变上限积分的极限与导数、函数限积分的极限与导数
---

## 含参变量的正常积分
- **普通积分的极限与导数**：若 $f(x, y)$ 在 $[a, b] \times [c, d]$ 连续，则
	- （积分与极限可交换次序）：$\displaystyle I(x) = \int_c^d f(x, y) \mathrm dy$ 连续（函数连续则一致连续，令 $I(x + \Delta x) - I(x)$ 的 $f$ 之差放缩消去区间长度）
	- （积分与导数可交换次序）：若 $f_x(x, y)$ 也在 $[a, b] \times [c, d]$ 连续，则 $\displaystyle I(x) = \int_c^d f(x, y) \mathrm dy$ 在 $[a, b]$ 有连续导函数 $\displaystyle I'(x) = \int_c^d f_x(x, y) \mathrm dy$ （拉格朗日中值定理将导函数定义式转成 $\displaystyle \int_c^d f_x(x + \theta \Delta x, y) \mathrm dy$，然后利用 $f_x(x, y)$ 连续则一致连续消去区间长度）
- **变上限积分的极限与导数**：若 $f(x, y)$ 在 $[a, b] \times [c, d]$ 连续，则
	- $\displaystyle I(x, u) = \int_c^u f(x, y) \mathrm dy$ 连续（放缩 $|I(x, u) - I(x_0, u_0)|$ 凑同一区间，并利用 $f$ 的一致连续和一致有界放缩掉区间长度）
	- 若 $f_x(x, y)$ 也在 $[a, b] \times [c, d]$ 连续，那么 $I(x, u)$ 对各变元有连续偏导数 $\displaystyle I_x(x, u) = \int_c^u f_x(x, y) \mathrm dy$，$I_u(x, u) = f(x, u)$（前者积分号下取导数，后者微积分基本定理）
- **函数限积分的极限与导数**：若 $f(x, y)$ 在 $[a, b] \times [c, d]$ 连续，且 $c(x), d(x)$ 在 $[a,b]$ 连续，且 $c \le c(x), d(x) \le d$，那么
	- $\displaystyle F(x) = \int_{c(x)}^{d(x)} f(x, y) \mathrm dy$ 连续（$F(x) = I(x, d(x)) - I(x, c(x))$，而 $I(x, u), I(x, v)$ 都是连续的，再使用复合函数连续性得证）
	- 若 $f_x(x, y)$ 也在 $[a, b] \times [c, d]$ 连续，且 $c(x), d(x)$ 存在导函数，那么 $\displaystyle F(x) = \int_{c(x)}^{d(x)} f(x, y) \mathrm dy$ 可导，且 $\displaystyle F'(x) = \int_{c(x)}^{d(x)} f_x(x, y) \mathrm dy + f(x, d(x)) d'(x) - f(x, c(x)) c'(x)$（令 $H(x, u, v) = \displaystyle \int_{c}^{d} f(x, y) \mathrm dy$，那么用全微分公式 $\displaystyle F'(x) = \frac{\partial H}{\partial x} + \frac{\partial H}{\partial u} d'(x) + \frac{\partial H}{\partial v} c'(x)$）
- **积分交换次序**：若 $f(x, y)$ 在 $[a, b] \times [c,d]$ 连续，那么 $\displaystyle \int_a^b \mathrm dx \int_c^d f(x, y) \mathrm dy = \int_c^d \mathrm dy \int_a^b f(x, y) \mathrm dx$（证明两个关于 $x$ 的变上限积分的导数相等，然后再计算两者之差为 $0$）