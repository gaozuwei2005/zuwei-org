---
title: 信号与系统 | Week 2 离散时间 LTI 系统
date: 2026-03-10
summary: 冲击与阶跃函数、连续时间系统、离散时间系统、系统的基本性质、离散 LTI 系统
---


# 1.4 单位冲击与单位阶跃函数 (cont'd)

**矩形脉冲**：
- $\displaystyle G(t) = u(t) - u(t - \tau) = \begin{cases}1,& 0 <t <\tau \\\\ 0 ,& \text{otherwise}\end{cases}$
- $\displaystyle G(t) = u(t - t_0) - u(t - \tau) = \begin{cases}1,& t_0 <t <\tau \\\\ 0 ,& \text{otherwise}\end{cases}$
![](attachments/Pasted%20image%2020260310104501.png)

**和冲激函数有关的信号**：
- $\displaystyle \int_{-\infty}^{+\infty} f(t) \delta(t) \mathrm dt = f(0)$
- $\displaystyle \int_{-\infty}^{+\infty} f(t - t_0) \delta(t) \mathrm dt = f(t_0)$

**分段不连续的信号求导**：导数不是普通函数段，而是在跳变点产生冲激，冲击量等于跳变的差值。

![](attachments/Pasted%20image%2020260310104354.png)

# 1.5 连续时间与离散时间系统

**连续时间系统**：输入信号和输出响应都是连续时间信号的系统。
- 例：微分方程

**离散时间系统**：输入信号和输出响应都是离散时间信号的系统。
- 例：差分方程

**系统的互联**：许多系统可以分解为若干简单系统的组合
- 级联：上游系统的输出是下游系统的输入 ![](attachments/Pasted%20image%2020260310111113.png)
- 并联：总系统的输入作为多个系统的输入，多个系统的输出作为总系统的输出 ![](attachments/Pasted%20image%2020260310111332.png)
- 反馈联结：系统的输出能够反馈到系统的输入 ![](attachments/Pasted%20image%2020260310111409.png)

# 1.6 系统的基本性质

## 1.6.1 记忆性

**无记忆系统**：在任何时刻，系统的输入只与当前时刻的输入有关，而与时刻以外的输入无关。

**记忆系统**：系统的输入不仅与当前时刻的输入有关，而且与时刻以外的输入有关。

**恒等系统**：任何时刻，输出信号等于输入信号，属于无记忆系统。
- $y(t) = x(t)$ 或 $y[n] = x[n]$.

## 1.6.2 可逆性

**可逆系统**：一个系统对于不同的输入能产生不同的输出，即输入与输出一一对应。

反之为不可逆系统。

**逆系统**：一个可逆系统与另一个系统级联后，为恒等系统。那么下游系统是上游系统的逆系统。 ![](attachments/Pasted%20image%2020260310112538.png)


## 1.6.3 因果性

**因果性**：系统在任何时刻的输出只与当前时刻及此前的输入有关，而与此后的输入无关。

一般而言，实时的物理系统都是因果的。

## 1.6.4 稳定性

**稳定系统**：如果一个系统对于任意有界输入都产生有界输出，则为稳定系统，否则为不稳定系统。

## 1.6.5 时不变性

**时不变性**：当输入信号有一个时移时，系统的输出响应也产生相同时移，此外无其他变化，则该系统是时不变的。

形式化表述：$\forall t,\, x(t) \to y(t)$，有 $x(t - t_0) \to y(t - t_0)$

检验方法：若输入 $x(t)$ 输出 $y(t)$，那么检验若输入 $x(t - t_0)$，输出是否为 $y(t - t_0)$.

## 1.6.6 线性

**线性**：$\forall x_1(t) \to y_1(t),\, x_2(t) \to y_2(t)$，总有 $ax_1(t) + bx_2(t) \to ay_1(t) + by_2(t),\quad \forall a, b \in \mathbb{R/C}$
- 可加性：$x_1(t) + x_2(t) \to y_1(t) + y_2(t)$
- 齐次性：$ax_1(t)\to ay_1(t), \quad \forall a \in \mathbb{R/C}$
![](attachments/Pasted%20image%2020260313164423.png)

如果一个系统是线性的，则只要我们能够把输入信号分解成 *若干个简单信号的线性组合*，就可以对简单输出信号的线性组合而得到系统对原输入信号的响应。

$$x(t) = \sum_{k} a_k x_k(t),\quad x_k(t) \to y_k(t)\quad \Rightarrow \quad y(t) = \sum_k a_k y_k(t)$$

**零输入-零输出特性**：线性系统当输入为零时，输出也为零。

**增量线性系统**：输出响应的增量与输入信号的增量之间是线性的，即 $\displaystyle \frac{\Delta y}{\Delta x} = k$.

增量线性系统可以是做是线性系统 $x(t) \to y_1(t)$ 与和输入无关的响应 $y_0(t)$ 叠加的结果：
- **零状态响应**：$y_0(t) = 0$ 时，$y(t) = y_1(t)$，则系统处于零初始状态，$y_1(t)$ 是零状态响应
- **零输入响应**：$x(t) = 0$ 时，$y(t) = y_0(t)$，则称 $y_0(t)$ 为零输入相应
- 增量线性系统是 *非线性系统*。

![](attachments/Pasted%20image%2020260313164403.png)

本课程主要关注 **线性时不变系统**（Linear Time Invariant System, LTI）。

# 2.1 离散时间 LTI 系统：卷积和

**用单位脉冲表示离散时间信号**：用位移的单位脉冲信号叠加，可以表示任意的离散时间信号：$$x[n] = \sum_{k = -\infty}^{+\infty} x[k] \delta[n - k]$$
**单位脉冲响应**：$\delta[n] \to h[n]$

如果我们知道了单位脉冲响应 $T(\delta[n]) = h[n]$，那么该离散 LTI 系统 $T$ 可以表示为 $$x[n] = \sum_{k = -\infty}^{+\infty} x[k] \delta[n - k] = x[n] * \delta[n]  \quad \Rightarrow \quad y[n] = \sum_{k = -\infty}^{+\infty} x[k] h[n - k] = x[n] * h[n]$$
**一个 LTI 系统可以完全由它的单位脉冲响应 $h[n] = T\\\{\delta[n]\\\}$ 来表征。**

常见 LTI 系统：
- 延时器：$x[n] * \mathbf{\delta[n - n_0]} = x[n - n_0]$
- 累加器：$\displaystyle x[n] * \mathbf{u[n]} = \sum_{k = -\infty}^n x[k]$

**求卷积和 $\displaystyle y[n] = x[n] * h[n] = \sum_{k = -\infty}^{+\infty} x[k]h[n - k]$ 的步骤**：
- 取 $x[k]$ 和 $h[k]$，其中 $k$ 是变量。
- 将 $h[k]$ 翻转，变为 $h[-k]$。
- 假设现在要算 $y[n]$，我们固定 $n$，则：
	- 将 $h[-k]$ 平移 $n$（正则右移 $|n|$，负则左移 $|n|$），变为 $h[-(k - n)] = h[n - k]$
	- 将 $x[k]$ 和 $h[n - k]$ 对应位相乘，并求和，最终得到 $y[n]$ 的值
