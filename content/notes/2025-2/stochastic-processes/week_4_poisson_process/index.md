---
title: 随机过程 | Week 7~9 泊松过程
date: 2026-04-17
summary: 定义与概率分布
---

# 定义与概率分布

**计数过程**：$N(t)$ 表示 $[0, t]$ 内发生的某种事件次数的过程。

**Poisson 过程, 泊松过程**：是一种计数过程，满足以下四个条件：
- 一开始尚未发生任何事件：$N(t) = 0$
- 平稳增量性：长度相同的时间内的统计规律相同 $N(t) - N(s)$ 只依赖于 $t-s$
- 独立增量性：不相交时间段内的增量相互独立即
$$N(t_4)-N(t_3)\quad \text{和}\quad N(t_2)-N(t_1)$$
在 $t_1<t_2\le t_3<t_4​$ 时独立。
- 微元时间 $\Delta t$ 内发生超过 1 次事件的概率无穷小
$$\lim_{\Delta t\to 0} \frac{P(N(t+\Delta t)-N(t)\ge 2)} {P(N(t+\Delta t)-N(t)=1)}=0$$

**Poisson 过程的概率分布**：$$P(N(t) = k) = \frac{(\lambda t)^k}{k!} e^{-\lambda t}$$
其中 $\lambda$ 称为到达率或强度，代表单位时间内时间发生的平均次数

**Poisson 过程的数字特征**：
- $E(N(t)) = D(N(t)) = \lambda t$
- $R_N(t,s)=E[N(t)N(s)]=\lambda^2 ts+\lambda \min\{t,s\}$
