---
title: 随机过程 | Week 7~9 泊松过程
date: 2026-04-24
summary: 定义与概率分布、联合分布、条件分布、到达时刻、事件间隔
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

记 $p_k(t) = P\\\{ N(t) = k \\\}$，将会有 $$P\\\{N(\Delta t) = 1\\\} = \lambda \Delta t + o (\Delta t)$$ $$P\\\{ N(\Delta t) \ge 2\\\} = o(\Delta t)$$

$\lambda$ 可以视作单位时间内某时间的平均发生次数：$$\lambda = \lim_{\Delta t \to 0}\frac{P(N(\Delta t)) = 1}{\Delta t}$$

**Poisson 过程的概率分布**：$$P(N(t) = k) = \frac{(\lambda t)^k}{k!} e^{-\lambda t}$$
其中 $\lambda$ 称为到达率或强度，代表单位时间内时间发生的平均次数

证明：使用概率母函数 $G(z, t)$，将会满足 $\displaystyle \frac{\partial G(z,t)}{\partial t} = G(z, t) \lambda (z - 1)$，微分方程的解为 $$G(z, t) = e^{\lambda t (z - 1)} = e^{-\lambda t} \sum_{k = 0}^{\infty} \frac{(\lambda t)^k}{k!} z^k$$

**Poisson 过程的数字特征**：
- $E(N(t)) = D(N(t)) = \lambda t$
- $R_N(t,s)=E[N(t)N(s)]=\lambda^2 ts+\lambda \min\\\{t,s\\\}$


# 性质

## 联合分布

**联合分布**：对于任意 $0<t_1<t_2<\cdots<t_m,\quad  0\le k_1\le k_2\le\cdots\le k_m$ 有 $$\begin{aligned}  
& P\bigl(N(t_1)=k_1,\ N(t_2)=k_2,\ \cdots,\ N(t_m)=k_m\bigr) \\\\  
={}&  
\frac{(\lambda t_1)^{k_1}}{k_1!}  
\frac{\bigl(\lambda(t_2-t_1)\bigr)^{k_2-k_1}}{(k_2-k_1)!}  
\cdots  
\frac{\bigl(\lambda(t_m-t_{m-1})\bigr)^{k_m-k_{m-1}}}{(k_m-k_{m-1})!}  
e^{-\lambda t_m}.  
\end{aligned}$$
证明：以 $0<t_1<t_2<\cdots<t_m$ 砍成不相交的连续的段，用独立增量性 + 平稳增量性就可以得出。

## 条件分布

**条件分布**：
- 对于 $0 < s < t$ ，砍成 $[0, s], [s, t]$，前后独立。 $$P\bigl(N(t)=m \mid N(s)=k\bigr)  =  \frac{[\lambda(t-s)]^{m-k}}{(m-k)!}e^{-\lambda(t-s)},  \qquad \forall m\ge k$$
- 对于 $0 < s < t$，枚举前后半的区间各发生了多少次，然后可以发现凑出了组合数。 $$P\bigl(N(t)=m \mid N(s)=k\bigr)  =  \frac{k!}{m!(k-m)!}  
\left(\frac{t}{s}\right)^m  \left(1-\frac{t}{s}\right)^{k-m},  \qquad \forall m\le k$$
## 到达时刻

**到达时刻**：从 $0$ 时刻到第 $n$ 次时间发生的到达时刻 $S_n$ 服从 $\Gamma$ 分布.

概率函数：$$F_{S_n}(t) = P(S_n \le t) = P(N(t) \ge n) = \sum_{k = n}^{\infty} e^{-\lambda t}\frac{(\lambda t)^k}{k!}$$
概率密度函数：$$\begin{aligned}f_{S_n}(t) &= \frac{\mathrm dF_{S_n}(t)}{\mathrm dt} = \sum_{k = n}^{\infty} \left( \frac{\lambda^k t^{k - 1}}{(k - 1)!} e^{-\lambda t} - \lambda \frac{(\lambda t)^k}{k!} e^{-\lambda t} \right) \\\\ &= \lambda e^{-\lambda t} \frac{(\lambda t)^{n - 1}}{(n - 1)!}\end{aligned}$$
或者用微元分析法，也可以得到概率密度函数：如果要在 $[t, t + \Delta t]$ 内发生了第 $n$ 次事件，那么 $[1, t]$ 应该共发生 $(n - 1)$ 次时间，因此 $$\begin{aligned}f_{S_n} &= \lim_{\Delta t \to 0} \frac{P(t \le S_n \le t + \Delta t)}{\Delta t} \\\\ &= \lim_{\Delta t \to 0} \frac{P(N(t) = n - 1, N(t + \Delta t) - N(t) = 1)}{\Delta t} \\\\ &= \lambda e^{-\lambda t} \frac{(\lambda t)^{n - 1}}{(n - 1)!}\end{aligned}$$
**到达时刻的联合分布**：规定任意 $n$ 次事件的到达时刻，可以得到概率密度函数为 $$g_{S_1, S_2,\cdots, S_n}(s_1, s_2, \cdots, s_n) = \lambda^n e^{-\lambda s_n}$$

**到达时刻的条件分布**：规定了总共发生次数的前提下，我们如果设定每次事件的发生时刻，那么这种分布是均匀分布，也就是说无论规定发生时刻在哪里，概率都是一样的。 $$f_{S_1,\cdots,S_n \mid N(t)}  (s_1,\cdots,s_n \mid N(t)=n)  =  \frac{n!}{t^n},  \qquad 0 \le s_1 < \cdots < s_n \le t$$
证明：用微元分析法，拆成互不相交的区间，微元区间都发生一次，其他区间发生零次。全部概率乘起来，让微元求极限，就可以得到概率密度。

## 事件间隔

事件间隔随机变量实际上和事件第几次发生无关，服从参数为 $\lambda$ 的指数分布 $$f_{T_k} (t)  = \lambda e^{-\lambda t},\quad t \ge0$$
概率函数：那么相当于在 $[0, t]$ 之间没有发生任何事件 $$F_{T_k}(t) = P(N(t) = 0) = e^{-\lambda t}$$

实际上从任意时刻开始的事件发生间隔都是一样的指数分布，具有无记忆性。
