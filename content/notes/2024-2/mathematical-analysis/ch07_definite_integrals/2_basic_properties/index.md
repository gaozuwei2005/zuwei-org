---
title: 数学分析 | 7.2 定积分的基本性质
date: 2024-11-27
summary: 有界性、线性性、可加性、单调性、有界性、可积性、积分第一中值定理
---

## 可积函数的有界性质

> **函数可积的必要条件是有界**：若 $f(x)$ 在 $[a,b]$ 上可积，那么 $f(x)$ 在 $[a,b]$ 有界。
>
> **证明**：使用反证法，证明函数无界则函数不可积。
> 
> 对 $[a,b]$ 的任意分法当中，至少有一个区间 $[x_{i_0-1},x_{i_0}]$ 当中 $f(x)$ 是无界的。故 $\forall N > 0,\  \exists \xi_{i_0} \in [x_{i_0-1},x_{i_0}]$，使得
>
> $$|f(\xi_{i_0})| > \frac{\left|\sum\limits_{i \ne i_0} f(\xi_i)\Delta x_i\right| + N}{\Delta x_{i_0}}$$
>
> 那么此时
>
> $$\left|\sum\limits_{i=1}^n f(\xi_i)\Delta x_i\right| \ge |f(\xi_{i_0})| \Delta x_{i_0} - \left|\sum\limits_{i \ne i_0} f(\xi_i)\Delta x_i\right| > N$$
>
> 因此黎曼和可取无穷大，即函数不可积。因此可积函数必有界。

## 定积分的线性性质

> **定积分的线性性质**：若函数 $f(x), g(x)$ 在区间 $[a,b]$ 可积，那么 $k_1 f(x) + k_2 g(x)$ 也可积，且
>
> $$\int_a^b [k_1 f(x) + k_2 g(x)] =  k_1 \int_a^b f(x) + k_2 \int_a^b g(x)$$
>
> **证明**：由于这两个函数均可积，那么我们可以令这两个函数的小区间分法和 $\xi_i$ 取法都一样，那么由极限的四则运算知
>
> $$\begin{aligned}
& \lim_{\lambda \to 0} \sum_{i=1}^n [k_1 f(\xi_i) + k_2 g(\xi_i)]\Delta x_i \\\\
= & k_1 \lim_{\lambda \to 0} f(\xi_i) \Delta x_i + k_2 \lim_{\lambda \to 0} g(\xi_i) \Delta x_i
\end{aligned}$$
>
> 故原定理成立。

## 定积分的可加性

> **定积分的可加性**：若 $f(x)$ 在 $[a,c],[c,b]$ 可积，且 $a  < c < b$，那么 $f(x)$ 在 $[a,b]$ 可积，且
>
> $$\int_a^b f(x) \mathrm dx = \int_a^c f(x) \mathrm dx + \int_c^b f(x) \mathrm dx$$
>
> **证明**：首先，若由于 $f(x)$ 在 $[a,c],[c,b]$ 可积，因此 $f(x)$ 在 $[a,b]$ 有界：
>
> $$|f(x)| \le M$$
> 
> 对于 $f(x)$ 在 $[a,b]$ 上的任意分法，若其中有一个分点是 $c = x_{i_0}$，那么显然有总黎曼和等于两边的黎曼和。
>
> 若 $c$ 不是其中的分点，那么我们把 $c$ 加到分点当中，那么原来包含 $c$ 的区间的 $\xi_{i_0}$ 取值换成另外两个 $\xi_{i_{1}}, \xi_{i_2}$，而
>
> $$|f(\xi_{i_0})\Delta x_{i_0} - f(\xi_{i_1})\Delta x_{i_1} - f(\xi_{i_2})\Delta x_{i_2}| \le 3M\lambda \to 0$$
>
> 因此总黎曼和等于两边的黎曼和。
>
> 综上，$f(x)$ 在 $[a,b]$ 可积，且定积分为两个分区间定积分之和。

若 $c \not\in [a,b]$，由于定积分上下指标大小关系改变的时候，定积分变为相反数，因此也同样成立。

## 定积分的单调性

> **定积分的单调性**：若 $f(x), g(x)$ 在 $[a,b]$ 可积，且
>
> $$f(x) \le g(x), \ \ x\in[a,b]$$
>
> 则
>
> $$\int_a^b f(x) \mathrm dx \le \int_a^b g(x) \mathrm dx$$
>
> **证明**：我们让两个黎曼和都取同样的分法和同样的 $\xi_i$，那么有
>
> $$f(\xi_i) \le g(\xi_i), \forall \xi_i \in [x_{i-1},x_i]$$
>
> 因此
>
> $$\sum_{i=1}^n f(\xi_i) \Delta x_i \le \sum_{i=1}^n g(\xi_i) \Delta x_i$$
>
> 让 $\lambda \to 0$ 取极限， 由极限的不等式性质可得原定理成立。

> **推论 1**：设 $f(x)$ 在 $[a,b]$ 可积，且 $f(x) \ge 0\ (a \le x \le b)$，那么
>
> $$\int_a^b f(x) \mathrm dx \ge 0$$

> **推论 2**：设 $f(x)$ 在 $[a,b]$ 可积，且 $m \le f(x) \le M \ (a \le x \le b)$，那么
>
> $$m(b-a) \le \int_a^b f(x) \mathrm dx \le M(b-a)$$

## 定积分的有界性

> 若 $f(x)$ 在 $[a,b]$ 可积，则
>
> $$\left| \int_a^b f(x) \mathrm dx \right| \le \int_a^b |f(x)| \mathrm dx$$
>
> **证明**：由 $f(x)$ 在 $[a,b]$ 可积，可知 $|f(x)|$ 在 $[a,b]$ 可积（记住这个结论）。由
>
> $$- |f(x)| \le f(x) \le |f(x)|$$
>
> 那么
>
> $$-\int_a^b |f(x)| \mathrm dx \le \int_a^b f(x) \mathrm dx  \le \int_a^b |f(x)| \mathrm dx$$

## 闭区间连续函数的可积性

### 一致连续性的定义

### 康托定理

### 闭区间连续函数的可积性

## 积分第一中值定理

> **定理 7.8（积分第一中值定理）**：若 $f(x), g(x)$ 在 $[a,b]$ 上连续，并且 $g(x)$ 在 $[a,b]$ 不变号，那么 $\exists \xi \in [a,b]$，使得
>
> $$\int_a^b f(x)g(x) \mathrm dx = f(\xi) \int_a^b g(x) \mathrm dx$$
>
> **证明**：设 $g(x) \ge 0$，记 $f(x)$ 在 $[a,b]$ 的最大值和最小值分别为 $M, m$，那么 $\forall x \in [a,b]$，有
>
> $$m g(x) \le f(x) g(x) \le M g(x)$$
>
> 于是
>
> $$m \int_a^b g(x) \mathrm dx \le \int_a^b f(x)g(x) \mathrm dx \le M\int_a^b g(x) \mathrm dx $$
>
> 若 $\int_a^b g(x) \mathrm dx = 0$，那么 $\xi$ 取任意一点均满足要求。
>
> 若 $\int_a^b g(x) \mathrm dx > 0$，那么
>
> $$m \le \frac{\int_a^b f(x)g(x) \mathrm dx}{\int_a^b g(x) \mathrm dx} \le M$$
>
> 由连续函数介值定理知，$\exists \xi \in [a,b]$，使得
>
> $$f(\xi) = \frac{\int_a^b f(x)g(x) \mathrm dx}{\int_a^b g(x) \mathrm dx}$$
>
> **推论**：当 $g(x) = 1$ 时，若 $f(x)$ 在 $[a,b]$ 上连续，那么 $\exists \xi \in [a,b]$，使得
>
> $$\int_a^b f(x) \mathrm dx = f(\xi) (b-a) $$

> **变上限定积分**：设 $f(x)$ 在 $[a,b]$ 可积，则 $\displaystyle F(x) = \int_a^x f(t)\mathrm dt$ 是 $f(x)$ 的变上限定积分。

> **定理 7.9**：设 $f(x)$ 在 $[a,b]$ 可积，则 $\displaystyle F(x) = \int_a^x f(t)\mathrm dt$ 是 $[a,b]$ 的连续函数。
>
> **证明**：由于 $f(x)$ 在 $[a,b]$ 可积，那么 $f(x)$ 在 $[a,b]$ 有界，因此 $\displaystyle |f(x)| \le M, \forall x \in [a,b]$。
> 
> 对于任意 $x, x+\Delta x \in [a,b]$，有
>
> $$\begin{aligned}
&|F(x+\Delta x) - F(x)| \\\\
=& |\int_a^x f(t)\mathrm dt - \int_a^{x + \Delta x} f(t)\mathrm dt| \\\\
=& |\int_x^{x + \Delta x} f(t)\mathrm dt| \\\\
\le & |\int_x^{x + \Delta x} |f(t)|\mathrm dt| \\\\
\le & M |\Delta x| \\\\
\end{aligned}$$
>
> 当 $\Delta \to 0$ 时，$F(x + \Delta x) - F(x) \to 0$，因此 $F(x)$ 在 $[a,b]$ 连续。