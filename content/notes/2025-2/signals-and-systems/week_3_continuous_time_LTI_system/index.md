---
title: 信号与系统 | Week 3 连续时间 LTI 系统
date: 2026-03-17
summary: 连续 LTI 系统、LTI 系统的性质、用微分和差分方程描述的因果 LTI 系统、常系数微分方程、奇异函数
---


# 2.2 连续时间 LTI 系统：卷积积分

对于连续时间 LTI 系统：$T\\\{x(t)\\\} = y(t)$，假设系统对于单位冲激信号的响应为 $T\\\{\delta(t)\\\} = h(t)$，那么我们可以将任意输入信号拆分为位移的单位冲击信号线性组合，那么响应信号为位移的 $h(t)$ 的信号线性组合

$$x(t) = \int_{-\infty}^{+\infty} x(\tau) \delta(t - \tau) \mathrm d\tau = x(t) * \delta(t)$$

$$y(t) = T\\\{x(t)\\\} = \int_{-\infty}^{+\infty} x(\tau) \delta(t - \tau) \mathrm d\tau = x(t) * h(t)$$

**连续时间 LTI 系统可以完全由它的单位冲击响应 $h(t)$ 来表征。**

**求卷积和 $\displaystyle y(t) = x(t) * h(t) = \int_{-\infty}^{+\infty} x(\tau) \delta(t - \tau) \mathrm d\tau$ 的步骤**：
- 取 $x(\tau)$ 和 $h(\tau)$，其中 $\tau$ 是变量。
- 将 $h(\tau)$ 翻转，变为 $h(-\tau)$。
- 假设现在要算 $y(t)$，我们固定 $t$，则：
	- 将 $h(-\tau)$ 平移 $t$（正则右移 $|t|$，负则左移 $|t|$），变为 $h(-(\tau - t)) = h(t - \tau)$
	- 计算 $x(t)·h(t - \tau)$ 积分，最终得到 $y(t)$ 的值。

# 2.3 线性时不变系统的性质

## 2.3.1 卷积相关

**（1）交换律**：输入信号与单位脉冲响应信号可以互换。
- $x[n] * u[n] = h[n] * x[n]$
- $x(t) * h(t) = h(t) * x(t)$

![](attachments/Pasted%20image%2020260317111921.png)

**（2）分配律**：*并联* 系统的单位冲激响应等于各子系统单位冲激响应之和。
- $x[n] * (h_1[n] + h_2[n]) = x[n] * h_1[n] + x[n] * h_2[n]$
- $x(t) * (h_1(t) + h_2(t)) = x(t) * h_1(t) + x(t) * h_2(t)$

![](attachments/Pasted%20image%2020260317112125.png)

**（3）结合律**：*级联* 系统的单位冲激响应等于各子系统单位冲激响应的卷积。
- $(x[n] * h_1[n]) * h_2[n] = x[n] * (h_1[n] * h_2[n])$
- $(x(t) * h_1(t)) * h_2(t) = x(t) * (h_1(t) * h_2(t))$

![](attachments/Pasted%20image%2020260317112749.png)

**（4）交换律与结合律的推论**：级联系统中，各子系统的先后次序可以调换。
- $(x[n] * h_1[n]) * h_2[n] = (x[n] * (h_2[n]) * h_1[n]$
- $(x(t) * h_1(t)) * h_2(t) = (x(t) * (h_2(t)) * h_1(t)$
- 以上成立的前提：$h_1[n], h_2[n]$ 都是 LTI 系统，并且每一步的卷积都收敛（每一步中间信号都必须存在）。

![](attachments/Pasted%20image%2020260317112924.png)


**（5A）卷积积分的性质**：满足微分、积分、时移
- 微分：$\displaystyle x'(t) * h(t) = x(t) * h'(t) = y'(t)$
- 累次微分：$\displaystyle x^{(m)}(t) * h^{(n)}(t) = y^{(m+n)}(t)$
- 积分：$\displaystyle \left( \int_{-\infty}^{t} x(\tau), d\tau \right) * h(t) = x(t) * \left( \int_{-\infty}^{t} h(\tau), d\tau \right) = \int_{-\infty}^{t} y(\tau), d\tau$
- 时移：$\displaystyle x(t-t_0) * h(t) = x(t) * h(t-t_0) = y(t-t_0)$

**（6）卷积和的性质**：满足差分、前缀和、时移
- 差分：$\displaystyle (x[n]-x[n-1]) * h[n] = x[n] * (h[n]-h[n-1]) = y[n]-y[n-1]$
- 前缀和：$\displaystyle \left(\sum_{k=-\infty}^{n} x[k]\right) * h[n] = x[n] * \left(\sum_{k=-\infty}^{n} h[k]\right) = \sum_{k=-\infty}^{n} y[k]$
- 时移：$\displaystyle x[n-n_0] * h[n] = x[n] * h[n-n_0] = y[n-n_0]$

## 单位冲激响应相关

**（1）记忆性**：LTI 系统无记忆的 *充要条件* 为，单位脉冲响应信号为 $h[n] = k \delta[n]$ 或 $h(t) = k \delta(t)$，此时 $$x[n] * h[n] = kx[n],\quad x(t) * h(t) = kx(t)$$

**（2）可逆性**：若 LTI 系统是可逆的，那么它的逆系统也是可逆的，此时 $$h[n] * g[n] = \delta[n],\quad h(t) * g(t) = \delta(t)$$
**（3）因果性**：
- LTI 系统具有因果性的 *充要条件* 为，单位脉冲响应的负数域的部分均为 $0$ $$\forall n < 0,\ h[n] = 0,\quad \forall t < 0,\ h(t) = 0$$
- **初始松弛条件**：对于任意时刻，只要该时刻之前系统的输入为0，则该时刻之前系统的输出也必然为0。该条件与因果性的充要条件等价。


**（4）稳定性**：假设输入信号 $x[n]$ 有界，即 $|x[n]| \le A$，则有 $$|y[n]| = \left| \sum_{k = -\infty}^{\infty}h[k]x[n - k] \right| \le A \sum_{k = -\infty}^{+\infty}|h[k]|$$
- 对于离散时间 LTI 系统，若 $\displaystyle \sum_{k = -\infty}^{+\infty}|h[k]|$  收敛则系统稳定。
- 对于连续时间 LTI 系统，若 $\displaystyle \int_{-\infty}^{+\infty} |h(t)|\mathrm dt$  收敛则系统稳定。


**用单位阶跃响应描述系统**：也常用系统对单位阶跃函数输入信号的响应来 表述 LTI 系统，记作 $s[n]$ 或 $s(t)$，那么可见 $s[n]$ 是 $h[n]$ 的前缀和，$s(t)$ 是 $h(t)$ 的前缀积分 $$s[n] = \sum_{k = \infty}^{n} h[k], \quad s(t) = \int_{-\infty}^{t}h(\tau)\mathrm d\tau$$
# 2.4 用微分和差分方程描述的因果 LTI 系统

## 2.4.1 线性常系数微分方程

**线性常系数微分方程**：$$\sum_{k = 0}^N a_k \frac{\mathrm d^k y(t)}{\mathrm d t^k} = \sum_{k = 0}^M b_k \frac{\mathrm d^k x(t)}{\mathrm d t^k},\quad a_k, b_k \in \mathbb R$$
它的解是齐次解和特解之和：$y(t) = y_p(t) + y_h(t)$，其中 $y_h(t)$ 是齐次方程解 $$\sum_{k = 0}^N a_k \frac{\mathrm d^k y(t)}{\mathrm d t^k} = 0$$
可以通过特征方程求解得到。



对两边同时积分并转换为递推形式可得：$$y(t) = \frac{1}{a_N} \left( \sum_{k = 0}^M b_k x_{(N - k)}(t) - \sum_{k = 0}^{N - 1} a_k y_{(N - k)}(t) \right)$$
初始条件分为两种，初始松弛→零输入相应为零，非零起始状态则增量线性

## 2.4.2 线性常系数差分方程

**线性常系数差分方程**：$$\sum_{k = 0}^N a_k y[n -k] = \sum_{k = 0}^M b_kx[n - k]$$
它的解是齐次解和特解之和 $y[n]  = y_h[n] + y_p[n]$。

可以转写成递推形式：$$y[n] = \frac{1}{a_0} \left( \sum_{k = 0}^M b_k x[n - k] - \sum_{k = 1}^N a_k y[n - k] \right)$$

**有限脉冲响应（FIR）**：非递归方程 $$y[n] = \frac{1}{a_0}\sum_{k = 1}^N a_k y[n - k] $$

无限脉冲响应：有限脉冲响应的补集，具有无限长的单位脉冲响应。

对于差分方程，它的特解也是齐次解和特解之和。**其中特解对应受迫响应部分，齐次解对应自由响应部分。**

线性常系数差分或微分方程对应 **增量线性系统**，它的响应等于**零状态响应与零输入相应**组成。

# 2.5 奇异函数


$\delta(t)$ 不是一般能够用解析式表达的函数，只能通过它对其他信号的作用来定义。

**用卷积定义 $\delta(t)$**：$\delta(t)$ 是恒等系统的单位冲激响应信号，满足 $$T\\\{x(t)\\\} = x(t) * \delta(t) = x(t),\quad \forall x(t)$$


**用积分定义 $\delta(t)$**：$\delta(t)$ 是与任何信号卷积在 $t = 0$ 处的值不变的信号，即 $$g(0) = \int_{-\infty}^{+\infty} g(\tau) \delta(\tau) \mathrm d\tau,\quad \forall g(t)$$
**$\delta(t)$ 的性质**：
- $\displaystyle \int_{-\infty}^{+\infty} \delta(\tau)\mathrm d\tau = 1 * \delta(t) = 1$
- $f(t)\delta(t) = f(0)\delta(t)$
- $\delta(t) = \delta(-t)$
- $\displaystyle \delta(at) = \frac{1}{|a|}\delta(t)$

单位冲击偶：$\displaystyle u_{1}(t) = \frac{\mathrm d\delta(t)}{\mathrm dt}$

![](attachments/Pasted%20image%2020260324102707.png)

单位冲击偶的性质：
- $\displaystyle \int_{-\infty}^{+\infty}u_1(t) \mathrm dt = 0$
- $\displaystyle \forall g(t),\, \int_{-\infty}^{+\infty} g(\tau - t)u_1(\tau)\mathrm d\tau = \frac{\mathrm dg(-t)}{\mathrm dt}= -g'(-t)$
- $\displaystyle \forall g(t),\, \int_{-\infty}^{+\infty} g(\tau)u_1(\tau)\mathrm d\tau = -g'(0)$，可以视作在积分意义下的定义
- $u_k(t) = \underbrace{u_1(t)*u_1(t)*\cdots*u_1(t)}_{k}$

理想积分器：$\displaystyle u_{-1}(t) = \int_{-\infty}^{t} \delta(\tau)\mathrm d\tau = u(t)$

理想积分器的性质：
- $\displaystyle \forall g(t),\, \int_{-\infty}^{+\infty} g(\tau)u_{-1}(\tau)\mathrm d\tau = \int_{-\infty}^{t} x(\tau)\mathrm d\tau$，可以视作在积分意义下的定义
- $u_{-k}(t) = \underbrace{u_{-1}(t)*u_{-1}(t)*\cdots*u_{-1}(t)}_{k}$


单位斜坡函数：$u_{-2}(t) = u_{-1}(t) * u_{-1}(t) = tu(t)$


单位斜坡函数的性质：
- 两次累次积分：$\displaystyle \forall g(t),\, \int_{-\infty}^{+\infty} g(\tau)u_{-2}(\tau)\mathrm d\tau = \int_{-\infty}^{t} \left(\int_{-\infty}^{\tau}x(\sigma)\mathrm d\sigma\right)\mathrm d\tau$，可以视作在积分意义下的定义
