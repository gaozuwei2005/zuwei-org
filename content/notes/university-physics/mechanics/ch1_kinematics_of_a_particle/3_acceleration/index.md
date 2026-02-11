---
title: 大学物理 | 1.3 加速度
date: 2024-11-20
summary: 加速度的定义、微积分知识
---


## 加速度的定义

> **平均加速度**：速度对时间的平均变化率，方向与 $\Delta \boldsymbol{v}$ 相同。
>
> $$\boldsymbol{a} = \frac{\Delta \boldsymbol{v}}{\Delta t}$$

> **瞬时加速度**：速度随时间的瞬时变化率。方向与 $\mathrm d \boldsymbol{v}$ 相同。反映速度变化快慢的物理量。单位 $m / s^2$
>
> $$\boldsymbol{a} = \lim\limits_{\Delta t \to 0} \frac{\Delta \boldsymbol{v}}{\Delta t} = \frac{\mathrm d \boldsymbol{v}}{\mathrm d t} = \frac{\mathrm d^2 x}{\mathrm d t^2}$$

速度的大小或方向发生变化时，都有加速度。

## 微积分知识

- **等号两边同时求导**：若 $f(x) = g(x)$，两边对于任意的 $x$ 值相等，是同一条曲线，那么
$$ \frac{\mathrm d f(x)}{\mathrm d x} = \frac{\mathrm d g(x)}{\mathrm d x}$$

> **定积分**：设 $y = f(x)$，那么 $\frac{\mathrm dy}{\mathrm dx} = e(x)$，则有
> 
> $$\Delta y_i = e(\xi_i) \Delta x_i$$
> 
> 那么有
> 
> $$S = \lim_{\lambda \to 0} \sum_{i=1}^n e(\xi_i)\Delta x_i = \int_{a}^b e(x)\mathrm dx = \lim_{\lambda \to 0} \sum_{i=1}^n \Delta y_i = y_n - y_0$$
> 
> $$\int_a^b e(x) \mathrm dx = \left.f(x)\right|_a^b = f(b) - f(a)$$

- **等号两边同时积分**：

在同一等式中，若有需要积分的两个自变量，如 $\mathrm dt$ 和 $\mathrm dx$，且二者有函数关系如 $x = x(t)$。

那么可对等式进行 **变量分离**（如 $x$ 在左边，$t$ 在右边），得到

$$f(x) \mathrm dx = g(t) \mathrm dt$$

我们两边对各自变量积分，上下限必须 **一一对应**，即 $x_a = x(t_a), x_b = x(t_b)$，则

$$\int_{x_a}^{x_b} f(x) \mathrm dx = \int_{t_a}^{t_b} g(t) \mathrm dt$$

