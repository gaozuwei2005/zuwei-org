---
title: 数学分析 | Ch14 傅里叶级数
date: 2025-03-21
summary: 定义、展开方法、收敛性
---

## 定义
三角级数 $\displaystyle \frac{a_0}{2} + \sum_{n = 1}^{\infty} (a_n \cos nx + b_n \sin nx)$，其中 $a_n, b_n$ 是傅里叶系数
## 展开方法
- 对周期函数进行任意长度为周期定积分都相等（$\displaystyle \int_a^{a + T} = \int_a^0 + \int_0^T + \int_T^{a + T} = \int_0^T$ ）
- 三角函数系的正交性：$\{1, \sin nx, \cos nx \mid n \in N\}$ 中任意两个不同函数的乘积在 $[- \pi, \pi]$ 上的定积分为 $0$（单函数显然，乘积函数可以用积化和差化成单函数）
- 若 $f(x)$ 可以展开成一致收敛的三角级数，那么 $\displaystyle \left\{ \begin{aligned} a_n = \frac{1}{\pi} \int_{- \pi}^{\pi} f(x) \cos nx \mathrm dx \\\\ b_n = \frac{1}{\pi} \int_{- \pi}^{\pi} f(x) \sin nx \mathrm dx \end{aligned} \right.$，其中 $n \ge 0$（乘 $\cos nx$ 或 $\sin nx$ 之后剩下对 $\cos^2 nx$ 或 $\sin^2 nx$ 的积分等于 $\pi$）
- 若 $f(x)$ 是奇函数，则 $a_n = 0$；若 $f(x)$ 是偶函数，则 $b_n = 0$.
- 类三角函数系的正交性：$\displaystyle \left\\\{1, \sin n \frac{\pi}{l} x, \cos n \frac{\pi}{l} x \mid n \in N \right \\\}$
- 偶延拓：对于 $[0, l]$ 的函数展开，令 $F_e(x) = f(|x|)$ 且周期为 $2l$ 的周期偶函数，那么 $\displaystyle F_e(x) \sim \frac{a_0}{2} + \sum_{n = 1}^{\infty} a_n \cos \frac{n \pi}{l} x$，其中 $\displaystyle a_n = \frac{2}{l} \int_0^l f(x) \cos \frac{n \pi}{l} x \mathrm dx$
- 奇延拓：当 $f(0) = 0$ 时，对于 $[0, l]$ 的函数展开，令 $F_o(x) = (-1)^{[x < 0]} f(|x|)$ 且周期为 $2l$ 的周期奇函数，那么 $\displaystyle F_e(x) \sim \sum_{n = 1}^{\infty} b_n \sin \frac{n \pi}{l} x$，其中 $\displaystyle b_n = \frac{2}{l} \int_0^l f(x) \sin\frac{n \pi}{l} x \mathrm dx$
## 收敛性*
- 狄利克雷积分：将 $a_n,  b_n$ 代入三角级数当中，通过和差化积化去和式可得 $\displaystyle S_n(f;x)= \frac{1}{\pi} \int_{-\pi}^{\pi} f(u) D_n(u - x) \mathrm dx$，其中 $\displaystyle D_n(t) = \frac{\sin(n + \frac{1}{2}) t}{2 \sin \frac{t}{2}}$.
- 若 $S_n(f; x)$ 有极限 $S$，那么有 $\displaystyle S_n(f;x_0) - S =  \frac{1}{\pi} \int_{-\pi}^{\pi} [f(x_0 + t) + f(x_0 - t) - 2S] D_n(t) \mathrm dt$