---
title: 数学分析 | 8.2 微积分在几何与物理中的运用
date: 2024-12-11
summary: 参数方程简单闭曲线面积、极坐标平面图形面积、旋转体体积
---

直角坐标系下两函数在闭合区间下围成的面积：$\displaystyle A = \int_a^b [f(x) - g(x)]\mathrm dx$

同时我们也可以对 $y$ 积分，不过要换成反函数。

在实际计算中，我们看对哪一维积分好算就用哪个。

### 参数方程表示的简单闭曲线面积

如果要计算参数方程的闭合曲线面积，那么我们要将 $\mathrm dx$ 换成参数 $x'(t) \mathrm dt$，并将上下限改成对应参数 $t$ 的上下限。

对于简单闭曲线 $T : \begin{cases}x = \varphi(t) \\\\ y = \phi(t)\end{cases},\ \alpha \le t \le \beta$ 且满足 $\varphi(\alpha) = \varphi(\beta), \phi(a) = \phi(b)$，假设 $x$ 值域是 $[a,b]$，可以按照参数 $a = \varphi(t_1), b = \varphi(t_2)$ 分成上下两段，那么面积就为

$$\begin{aligned}
S &= \int_a^b (y_2(x) - y_1(x)) \mathrm dx\varphi'(t) \mathrm dt
\end{aligned}$$

我们把它拆成两部分可以得到，前面一部分是 $t_1 \sim t_2$，后面一部分是 $t_2 \sim \beta$ 与 $\alpha \sim t_1$，那么两个一相减就得到 $[t_1 \sim t_2] - [t_2 \sim \beta] - [\alpha \sim t_1] = [t_1 \sim t_2] + [\beta \sim t_2] + [t_1 \sim \alpha] = [\beta \sim \alpha]$，最终反过来的原因估计是和**行走旋转方向**有关。因此

$$S = -\int_{\alpha}^{\beta} \phi(t) \varphi'(t) \mathrm dt = - \oint_{T} y \mathrm dx$$

结合可得平面简单闭合曲线所围成的区域的面积 $\displaystyle S = \frac{1}{2}\oint (x\mathrm dy - y\mathrm dx)$

### 极坐标下平面图形的面积

我们将所求平面图形在定义域 $[\alpha, \beta]$ 像计算黎曼和一样分成若干段，然后每一段近似成扇形面积，那么就可以算出它的总面积

$$A = \frac{1}{2} \int_{\alpha}^{\beta} r^2(\theta) \mathrm d \theta$$

「近似」的严谨表述，$r^2(\theta)$ 连续，那么黎曼和的每一项在被积函数取区间内最值之间。于是得出黎曼和的极限是体积。

### 旋转体的体积

我们将旋转体按照定义域 $[a,b]$ 分成若干段，那么每一段都可以近似看作一个圆柱，于是我们就可以将这些圆柱体积相加即可。

$$A = \pi \int_{a}^b f^2(x) \mathrm dx$$

「近似」的严谨表述，$f^2(x)$ 连续，那么黎曼和的每一项在被积函数取区间内最值之间。于是得出黎曼和的极限是体积。

这一方法可以推广到任意立体。我们按照某一维对其分成若干段，每一段都是一个柱体，我们再将它们相加即可。

$$A = \int_a^b S(x) \mathrm dx$$