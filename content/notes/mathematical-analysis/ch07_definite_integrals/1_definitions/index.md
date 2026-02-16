---
title: 数学分析 | 7.1 定积分的概念
date: 2024-11-26
summary: 定积分的定义、概念、说明
---

> **定积分**：设函数 $f(x)$ 在区间 $[a,b]$ 有定义，用分点 $a = x_0 < x_1 < \cdots < x_n = b$，分成 $n$ 个小区间。设 $\lambda = \max\limits_{1 \le i \le n} |\Delta x_i|$，任取 $\xi \in [x_{i-1},x_i]$，若
>
> $$I = \lim_{\lambda \to 0} \sum_{i=1}^n f(\xi_i)\Delta x_i = \int_a^b f(x)\mathrm dx$$
>
> 存在，那么称 **$f(x)$ 在 $[a,b]$ 可积**。并称 **$I$ 为 $f(x)$ 在 $[a,b]$ 的定积分**。
>
> **小部分名称**：
>
> - $a,b$：定积分的上限和下限
> - $[a,b]$：积分区间
> - $f(x)$：被积函数。

由定义可知，当 $\lambda$ 确定，由小区间的分法和 $\xi_i$ 的取法，和式的值（记为 $\sigma$）不是唯一决定的，因此该和式不是一个严格的函数，通常称其为 $f(x)$ 的黎曼和。

下面用 $\epsilon - \delta$ 给出更严格的定义：

> **定积分是黎曼和的极限**：设函数 $f(x)$ 在区间 $[a,b]$ 有定义，$I$ 是常数，$\forall \epsilon > 0, \exists \delta > 0$，使得 $[a,b]$ 的任意分法和 $\xi \in [x_{i-1},x_i]$ 的任意取法，只要 $\max\limits_{1 \le i \le n} |\Delta x_i| < \delta$，均有
> 
> $$|\sigma - I| =  \left|\sum_{i=1}^n f(\xi_i)\Delta x_i - I\right| < \epsilon$$
>
> 则称 $\sum\limits_{i=1}^n f(\xi_i)\Delta x_i$ 的极限为 $I$，因此 **$f(x)$ 在 $[a,b]$ 的定积分为 $I$**。

关于定积分的三点说明：

- 定积分是对应函数曲边梯形的**代数和**：$x$ 轴以上的面积减去 $x$ 轴以下的面积。
- 定积分是一个数，它的值和取决于**被积函数和积分的上下限**，与积分变量采用什么字母、小区间分法和 $\xi_i$ 的取法无关。
- 若积分上下限有 $a>b$，那么分法为 $a = x_0 > x_1 > \cdots >x_n = b$，取法为 $\xi_i \in [x_{i}, x_{i-1}]$，但此时 $\Delta x_i < 0$，那么有

    $$\int_a^b f(x) \mathrm dx = - \int_b^a f(x) \mathrm dx$$

- 当 $a=b$ 时，我们规定

    $$\int_a^b f(x) \mathrm dx = 0$$

如果我们已知函数在指定区间上可积，说明黎曼和的极限存在，那么我们直接找其中一种小区间的分法和 $\xi_i$ 的取法和计算极限即可。