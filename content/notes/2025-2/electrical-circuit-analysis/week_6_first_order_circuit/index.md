---
title: 电路基础 | Week 6 一阶电路
date: 2026-04-07
summary: 无源 RC 电路、无源 RL 电路、奇异函数、RC 电路的阶跃响应、RL 电路的阶跃响应
---

# 7.1 简介

对纯电阻电路使用基尔霍夫定理会产生代数方程，而对RC和RL电路使用基尔霍夫定理则会产生微分方程。

RC和RL电路的微分方程是一阶的，因此这类电路统称为一阶电路。

响应的分类：初始状态、初始输入、自然、强迫、暂态、稳态、完全

# 7.2 无源 RC 电路（零输入响应）

![](../week_5_capacitance_and_inductance/attachments/Pasted%20image%2020260407083107.png)
开关往左接入时是充电，往右接入时是放电（无源 RC 电路）。

此时对电路进行分析得到 一阶常系数齐次微分方程 $$C \frac{\mathrm dv}{\mathrm dt} + \frac{v}{R} = 0 \Leftrightarrow \int_0^t\frac{\mathrm dv}{v} = \int_0^t- \frac{\mathrm dt}{RC} \Leftrightarrow \ln \frac{v}{v_0} = -\frac{t}{RC} \Leftrightarrow v = v_0 e^{-\frac{t}{RC}}$$
**时间常数**：$\tau = RC$，它决定了放电速率的快慢，当 $\tau$ 越大，电路放电越慢。

![](attachments/Pasted%20image%2020260407083728.png)

# 7.3 无源 RL 电路（零输入响应）

![](attachments/Pasted%20image%2020260407090759.png)

对电路进行分析得到 $$L \frac{\mathrm di}{\mathrm dt} + Ri = 0 \Leftrightarrow \int_0^t \frac{d_i}{i} = - \int_0^t\frac{R\mathrm dt}{L} \Leftrightarrow i = I_0 e^{-\frac{Rt}{L}}$$
电流常数 $\displaystyle \tau = \frac{L}{R}$.

# 7.4 奇异函数

奇异函数及其导数都是不连续的。

**单位阶跃函数**：$\displaystyle u(t) = \begin{cases}0,&t<0\\\\1,&t\ge0\end{cases}$
![](attachments/Pasted%20image%2020260410142400.png)

单位阶跃函数可以表示电压或电流的急剧变化。

开关在 $t = t_0$ 合上：乘一个 $u(t-t_0)$.

**单位阶跃函数**：$\displaystyle \delta(t) = \frac{\mathrm du(t)}{\mathrm dt} = \begin{cases}undefined,&t=0\\\\0,&otherwise\\\\\end{cases}$
- 积分为 $1$：$\displaystyle \int_{0^-}^{0^+} \delta(t) \mathrm dt = 1$.

刚刚加电源对电容充电时，电流是一个阶跃函数。

**单位斜坡函数**：$\displaystyle r(t) = \begin{cases}0,&t<0\\\\t,&t\ge0\end{cases}$


三个函数之间的关系：
- $\displaystyle \delta(t) = \frac{\mathrm du(t)}{\mathrm dt},\, u(t) = \frac{\mathrm dr(t)}{\mathrm dt}$
- $\displaystyle u(t) = \int_{-\infty}^t \delta(t) \mathrm dt,\, r(t) = \int_{-\infty}^t u(t) \mathrm dt$

# 7.5 RC 电路的阶跃响应

电路的阶跃响应：电路受到阶跃函数激励时的行为，可以视作*开关闭合*或者电源输入乘上了 $u(t)$。激发它的可以是电压源或电流源。

![](attachments/Pasted%20image%2020260410150337.png)

相应电压的推导得到一阶常系数非齐次微分方程：$$C \frac{\mathrm dv}{\mathrm dt} + \frac{v- V_su(t)}{R} = 0\Leftrightarrow \frac{\mathrm dv}{\mathrm dt} = \frac{V_s - v}{RC}$$
且 $v(0) = V_0$（电容已经完成初始充电），那么解得 $$v(t) =\begin{cases}V_0,&t<0\\\\V_s+(V_0-V_s)e^{-t/\tau},&t\ge 0\end{cases}$$

![](attachments/Pasted%20image%2020260410150424.png)

**完全响应的分解公式 1**：$全响应 = 自由响应 + 强迫响应$

在这里 $$v = v_n + v_f = V_0e^{-t/\tau} + V_s(1 - e^{-t/\tau})$$
自由响应指的是电容原先的电荷逐渐耗散，强迫响应指的是电路在 $V_s$ 激励下进行充电。

**完全响应的分解公式 2**：$全响应 = 暂态响应 + 稳态响应$

在这里 $$v = v_t + v_{ss} = (V_0 - V_s) e^{-t/\tau} + V_s \, (V)$$
暂态响应指的是初始电压与目标电压的差值会随着时间而无限衰减至零，而稳态响应是无穷时间后电压的值。

可以写成 $$v(t) = [v(0) - v(\infty)]e^{-t/\tau} + v(\infty)$$
需要知道初始电压、终值电压、时间常数三值即可写出相应公式。

# 7.6 RL 电路的阶跃响应

![](attachments/Pasted%20image%2020260410155441.png)

依据 $全响应 = 暂态响应 + 稳态响应$ 可以得到 $$i(t) = \frac{V_s}{R}(1 - e^{-t/\tau})\, (A),\quad (t > 0)$$
