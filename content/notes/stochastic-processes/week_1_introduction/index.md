---
title: 随机过程 | Week 1 随机过程的概念和分类
date: 2026-03-06
summary: 随机过程的概念、随机过程的分类、相关函数、自协方差函数、平稳性、遍历性
---

# 1.1 随机过程的概念和分类

**随机过程**：一组随时间 $t$ 变化的随机变量。
- 主要研究多个随机变量之间的关联性。
- 离散参数随机过程：$\\\{X_n,\,n \in \mathbb N\\\}$
- 连续参数随机过程：$\\\{ X(t),\, t \in \mathbb R\\\}$
- *状态*：确定参数 $t$ 时，$X(t)$ 是一个随机变量，称之为状态。
- *样本轨道*：对于一个过程的结果，称为样本 $\omega$，则 $X(t)$ 是一个关于 $t$ 的确定函数，称之为样本轨道。
- 实际上，随机过程是一个关于 $t$ 和 $\omega$ 的 *二元函数*。

**随机过程的分类**：
- 离散参数离散状态：如连续抛掷硬币结果序列、Bernoulli 过程、随机游走序列
- 离散参数连续状态：如一阶自动回归过程 $AR(1)$
- 连续参数离散状态：如排队模型（任意时刻排队旅客数）
- 连续参数连续状态：如布朗运动

随机过程的概率刻画：随机过程可以视作任意维联合分布 $$F_{X(t_1),X(t_2),\cdots,X(t_n)}(x_1,x_2,\cdots,x_n),\quad \forall n, \forall x_1,x_2,\cdots, x_n$$
**(自) 相关函数**：两时刻随机变量乘积的期望，$R_X(t,s) = E[X(t)X(s)],\quad \forall t, s$

**自协方差函数**：$$\begin{aligned}C_X(t,s) &= E\\\{[X(t) - E(X(t))] · [X(s) - E(X(s))]\\\}\quad \forall t, s \\\\ &= R_X(t,s) - E(X(t))·E(X(s))\end{aligned}$$

**平稳性**：刻画随机过程不随时间变化的某种统计特性。
- **宽平稳性**：$E(X(t)) = E(X(s)),\, R_X(t,s) = R_X(t+ D,s+D),\quad \forall t, s, D$
- 对于宽平稳随机过程，相关函数是时间差的一元函数：$R_X(t,s) = R_X(t-s) = R_X(\tau)$
- **严平稳性**：$F_{X(t_1),X(t_2),\cdots,X(t_n)}(x_1,x_2,\cdots,x_n) = F_{X(t_1+D),X(t_2+D),\cdots,X(t_n+D)}(x_1,x_2,\cdots,x_n) ,\quad \forall n, \forall x_1,x_2,\cdots, x_n, D$

**遍历性**：
- 时间平均：$\displaystyle \langle X(t) \rangle = \frac{1}{T} \int_{-T/2}^{T/2} X(t) \mathrm dt$，仍是一个随机变量
- 集平均：$\displaystyle E\langle X(t) \rangle = \int_{-\infty}^{+\infty} x \mathrm d F(x)$，是一个确定的数值
- 均值遍历：$\displaystyle \lim_{T \to \infty} \langle X(t) \rangle = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} X(t) \mathrm dt = E\langle X(t)\rangle$
