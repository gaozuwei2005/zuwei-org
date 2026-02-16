---
title: 数学分析 | 8.1 泰勒公式
date: 2024-12-10
summary: 三种余项、麦克劳林公式
---

**泰勒公式的三种余项**：

$$\displaystyle f(x) = \sum_{i = 0}^n \frac{f^{(i)}(a)}{i!} (x - a)^i  + R_n(x)$$

**皮亚诺余项**：$R_n(x) = o((x-a)^n)$

**积分型余项、拉格朗日余项**（前提是 $a$ 邻域内有 $n + 1$ 导数）：$\displaystyle R_n = \dfrac{1}{n!} \int_a^x (x-t)^n f^{(n+1)}(t) \mathrm dt = \dfrac{f^{(n+1)}(\xi)}{(n+1)!}  (x-a)^{n+1}$

**柯西余项**：$\displaystyle R_n = \frac{(x-a)^{n+1}}{n!} (1-\theta)^n f^{(n+1)}(a+\theta(x-a))$

> **需要进一步理解拉格朗日余项、柯西余项的意义**

**初等函数的麦克劳林公式**：

$\displaystyle e^x = \sum_{i=0}^n \frac{x^i}{i!} + \frac{e^{\theta x}}{(n+1)!}x^{n+1}$

$\displaystyle \sin x = \sum_{i=0}^{k} \frac{(-1)^{i}}{(2i+1)!}x^{2i+1} + \dfrac{(-1)^{k+1}\cos \theta x}{(2k+3)!} x^{2k+3}$

$\displaystyle \cos x = \sum_{i=0}^k \frac{(-1)^i}{(2i)!}x^{2i} + \frac{(-1)^{k+1}\cos\theta x}{(2k+2)!}  x^{2k+2}$

$\displaystyle \ln(1+x) = \sum_{i=1}^n \frac{(-1)^{i-1}}{i} x^i + \frac{(-1)^n(1 + \theta x)^{-(n+1)}}{n+1} x^{n+1}$

这里的余项需要写成柯西余项，以便于证明其趋向于 $0$。

$\displaystyle (1+x)^n = \sum_{i = 0}^n \frac{a^{\underline i}}{i!} x^n + R_n (x)$