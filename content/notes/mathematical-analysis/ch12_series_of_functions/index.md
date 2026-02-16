---
title: 数学分析 | Ch12 函数项级数
date: 2025-02-28
summary: 函数序列一致收敛、函数级数一致收敛
---

## 函数序列一致收敛
### 定义
- 收敛定义：收敛点 $\rightarrow$ 收敛域，极限值 $\rightarrow$ 极限函数（$\displaystyle\lim_{n \to \infty} f_n(x) = f(x)$）
- 一致收敛定义：$N = N(\epsilon, x_0)$，所有点的收敛值对于每个 $\epsilon$ 有一个公共的 $N$.
- 一致收敛定义2：$\displaystyle \rho_n = \sup_{a \le x \le b}|f_n(x) - f(x)| \to 0 (n \to +\infty)$
- 一致收敛否定：存在 $\epsilon$，对于每个 $N$，存在 $n > N, x_0 \in X$ 使得 $|f_n(x) - f(x)| \ge \epsilon$
- 一致有界定义：$\forall n \in N^*, x \in X, |f_n(x)| \le M$
### 分析性质
- 连续：若 $f_n(x)$ 连续且一致收敛，那么 $f(x)$ 连续，或者称 $\displaystyle\lim_{x \to x_0}$ 和 $\displaystyle\lim_{n \to \infty}$ 可以交换顺序（$f(x_0)$ 接近 $f_n(x_0)$ 接近 $f_n(x)$）
- 可积：若 $f_n(x)$ 连续且一致收敛，那么 $f(x)$ 定积分等于 $f_n(x)$ 定积分的极限，或者称 $\displaystyle\lim_{n \to \infty}$ 和 $\displaystyle\int_a^b$ 可以交换顺序（积分差值放缩为 $\epsilon·(b - a)$）
- 可微：若 $f_n(x)$ 逐点收敛且 $f_n'(x)$ 一致收敛，那么 $f'(x)$ 等于 $f'\_n(x)$ 的极限，或者称 $\displaystyle\lim\_{n \to \infty}$ 和 $\frac{\mathrm d}{\mathrm dx}$ 可以交换顺序（先证变上限积分极限相等，然后求导反过来）

## 函数级数一致收敛
### 定义
- 收敛定义：和函数序列的一样，收敛点 $\rightarrow$ 收敛域（定义域）
- 一致收敛定义：和函数 $S_n(x)$ 在定义域内一致收敛到 $S(x)$
### 判别法
- 柯西原理：函数项级数一致收敛，充要于上下界充分大的部分和小于 $\epsilon$（必要性：$[n+1,n+p] = [1,n+p] - [1,n]$，用绝对值不等式；充分性：$S_n(x)$ 接近充分大的 $S_{n+p}(x)$ 接近 $S_n(x)$）
- M 判别法：若函数项级数可放缩掉 $x$ 变成数项级数 $|u_k(x)| \le M_k$，且 $M_k$ 级数收敛，那么原函数项级数一致收敛
- 狄利克雷判别法：若 $b_n(x)$ 部分和一致有界，$a_n(x)$ 对 $n$ 单调且一致趋于 $0$，那么乘积级数一致收敛（柯西原理 + 放缩 $b_k$ 部分和 $\le 2M$，$|a_n(x)| \le \epsilon$ +阿贝尔引理）
- 阿贝尔判别法：若 $b_n(x)$ 部分和一致收敛，$a_n(x)$ 对 $n$ 单调且一致有界，那么乘积级数一致收敛（柯西原理 + 放缩 $b_k$ 部分和 $\le \epsilon$（柯西原理），$|a_n(x)| \le M$ + 阿贝尔引理）
### 分析性质
- 连续：若 $u_n(x)$ 在闭区间上连续，且级数一致收敛，那么 $S(x)$ 在闭区间上连续（$S_n(x)$ 连续，套用函数序列分析性质1）
- 迪尼定理：若在闭区间上 $u_n(x) \ge 0$ 且连续，那么在闭区间上级数一致收敛充要于在闭区间上 $S(x)$ 连续（首先，$S_n(x)$ 连续。必要性刚才已证，充分性用反证法，不一致收敛，那么存在 $\epsilon$，可构造出无穷的上升 $n_k$，有界 $x_k$ 对使得 $\forall m, \exists n_k \ge m, S(x_k) \ge S_{n_k}(x_k) + \epsilon \ge S_m(n_k) + \epsilon$，使用波尔查诺-魏尔斯特拉斯定理，$x_k$ 存在收敛于 $x_0$ 的子序列，那么上式可 $x_k \to x_0$ 变成 $\forall m, S(x_0) \ge S_m(x_0) +\epsilon$，矛盾）
- 逐项积分：若在闭区间上 $u_n(x)$ 连续，且级数一致收敛，那么在闭区间上 $S(x)$ 积分等于 $u_n(x)$  逐项积分的级数。或者称 $\displaystyle\int_a^b$ 和 $\displaystyle \sum_{k = 1}^{\infty}$ 可以交换顺序（$S_n(x)$ 连续且一致收敛，级数 $S_n(x)$ 的积分等于积分的级数，再套用函数序列分析性质2）
- 逐项求导：若在闭区间上 $u_n(x)$ 级数逐点收敛，$u_n'(x)$ 级数一致收敛，那么 $S'(x)$ 等于 $u'(x)$ 级数。或者称 $\displaystyle\frac{\mathrm d}{\mathrm dx}$ 和 $\displaystyle \sum_{k = 1}^{\infty}$ 可以交换顺序（$S_n(x)$ 逐点连续，且 $S'_n(x)$  一致收敛，再套用函数序列分析性质3）