---
title: 信号与系统 | Week 5+6 连续时间傅里叶变换
date: 2026-04-03
summary: 非周期信号的表示、周期信号的傅里叶变换、连续时间傅里叶变换的性质、由线性常系数微分方程表征的系统
---

总体思想：对非周期信号进行周期性延拓，考查该周期延拓信号在基波周期趋于无穷大时所对应连续时间傅里叶级数的变化。

# 4.1 非周期信号的表示

对于有限区间的 $x(t),\, t \in [-T,T]$，我们周期延拓为 $\displaystyle \tilde{x}(t) = \sum_{k} a_k e^{jk\omega_0 t}$，那么 $$a_k = \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} \tilde{x}(t) e^{-jk\omega_0 t}\mathrm dt = \frac{1}{T} \int_{-\infty}^{\infty} x(t) e^{-jk\omega_0 t}\mathrm dt$$
$$\text{let}\,X(j\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t}\mathrm dt  \quad \Rightarrow \quad a_k = \frac{1}{T}X(jk\omega_0)$$

**傅里叶变换**：获得 $x(t)$ 的 频谱$$X(j\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t}\mathrm dt$$

**傅里叶反变换**：从频谱获得 $x(t)$ $$x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(j\omega)e^{j\omega t}\mathrm d\omega$$
**傅里叶变换的收敛**：平方可积条件、Dirichlet 条件


**常见信号的傅里叶变换**：


| 信号                                                                                    | 频谱                                                                                                                                                                                                        | 说明                                        |
| ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| $x(t) = e^{-at}u(t)$                                                                  | $\displaystyle X(j\omega) = \frac{1}{a + j \omega}$<br>$\displaystyle \lvert X(j\omega) \rvert = \frac{1}{\sqrt{a^2+\omega^2}}$<br>$\displaystyle \measuredangle X(j\omega) = - \arctan \frac{\omega}{a}$ | 模长是偶函数，相位是奇函数                             |
| $x(t) = e^{-a\lvert t\rvert}$                                                         | $\displaystyle X(j\omega) = \frac{2a}{a^2 + \omega^2}$<br>$\displaystyle \lvert X(j\omega) \rvert = \frac{2a}{a^2 + \omega^2}$<br>$\measuredangle X(j\omega) = 0$                                         | 实偶信号的傅里叶变换是实偶函数                           |
| $x(t) = \delta(t)$                                                                    | $X(j\omega) = 1$                                                                                                                                                                                          | $\delta (𝑡)$中包括了所有的频率成分，且所有频率分量的幅度、相位都相同 |
| $x(t) = \begin{cases}1, & \lvert t \rvert<T_1 \\\\ 0, & \lvert t \rvert>T_1\end{cases}$ | $\displaystyle X(j\omega) = 2T_1 Sa(\omega T_1)$                                                                                                                                                          |                                           |
| $\displaystyle x(t) = \frac{W}{\pi} Sa\left(\frac{Wt}{\pi}\right)$                    | $X(j\omega) = \begin{cases}1, & \lvert \omega \rvert<W \\\\ 0, & \lvert \omega \rvert>W\end{cases}$                                                                                                         | 形成对偶关系                                    |
| $x(t) = 1$                                                                            | $X(j\omega) = 2\pi \delta(\omega)$                                                                                                                                                                        | 方波信号在 $T_1 \to \infty$ 的极限                |
| $x(t) = u(t)$                                                                         | $\displaystyle X(j\omega) = \frac{1}{j\omega} + \pi \delta(\omega)$                                                                                                                                       |                                           |

# 4.2 周期信号的傅里叶变换

对于周期性复指数信号，不能直接从定义来计算它的频谱。

周期性复指数信号的频谱是冲激函数的线性组合。

$$x(t) = \sum_k a_k e^{jk\omega_0 t} \quad\Leftrightarrow \quad X(j\omega) = 2\pi \sum_{k} a_k \delta(\omega - k \omega_0)$$


**常见周期性信号的傅里叶变换**：

| 信号                                                                | 频谱                                                                                                                 | 说明    |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ----- |
| $x(t) = \sin \omega_0 t$                                          | $\displaystyle X(j\omega) = \frac{\pi}{j}[\delta(\omega - \omega_0) - \delta(\omega + \omega_0)]$<br>              |       |
| $x(t) = \cos \omega_0 t$                                          | $\displaystyle X(j\omega) = \pi[\delta(\omega - \omega_0) +\delta(\omega + \omega_0)]$                             |       |
| $\displaystyle x(t) = \sum_{n = -\infty}^{\infty} \delta(t - nT)$ | $\displaystyle X(j\omega) = \frac{2\pi}{T}\sum_{k = -\infty}^{\infty} \delta\left(\omega - \frac{2\pi}{T}k\right)$ | 均匀冲激串 |

# 4.3~4.5 连续时间傅里叶变换的性质

**线性**：若 $x(t) \leftrightarrow X(j\omega),\, y(t) \leftrightarrow Y(j\omega)$，则 $ax(t) + by(t) \Leftrightarrow aX(j\omega) + bY(j\omega)$

**时移**：信号时移造成频谱线性相移。若 $x(t) \leftrightarrow X(j\omega)$，则 $x(t - t\_0) \leftrightarrow X(j\omega) e^{-j\omega t\_0}$

**共轭与奇偶性**：若 $x(t) \leftrightarrow X(j\omega)$，则 $x^\*(t) \leftrightarrow X^\*(-j\omega)$ 
- 若 $x(t)$ 是实信号，则 $X(j\omega) = X^*(-j\omega)$，频谱为 *共轭偶函数*。这说明此时 $X(j\omega)$ 的实部是偶函数、虚部是奇函数、幅度是偶函数、相位是奇函数。
- 若 $x(t)$ 是偶函数，则 $X(j\omega) = X(-j\omega)$，也为偶函数
- 若 $x(t)$ 是实偶信号，则 $X(j\omega)$ 是实偶函数。
- 若 $x(t)$ 是偶函数，则 $X(j\omega) = -X(-j\omega)$，也为奇函数
- 若 $x(t)$ 是实奇信号，则 $X(j\omega)$ 是虚奇函数。
- 令 $x(t) = x_e(t) + x_o(t)$，则对应的 $X(j\omega) = X_e(j\omega) + jX_o(j\omega)$

**微分与积分**：
- 时域微分：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle \frac{\mathrm dx(t)}{\mathrm dt} \leftrightarrow j\omega X(j\omega)$.
- 时域积分：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle \int_{-\infty}^{t} x(\tau)\mathrm d\tau \leftrightarrow \frac{1}{j\omega}X(j\omega) + \pi X(0)\delta(\omega)$.
- 频域微分：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle -jtx(t) \leftrightarrow \frac{\mathrm d X(j\omega)}{\mathrm d\omega}$.
- 频域积分：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle -\frac{1}{jt} x(t) + \pi x(0) \delta(t) \leftrightarrow \int_{-\infty}^{\omega} X(j\tau)\mathrm d\tau$.

**尺度变换**：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle x(at) \leftrightarrow \frac{1}{\lvert a \rvert} X\left(j\frac{\omega}{a}\right)$.
- 令 $a = -1$，则有 $x(-t) \leftrightarrow X(-j\omega)$.

**对偶性**：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle X(jt) \leftrightarrow 2\pi x\left(-\omega\right)$.

**Parseval 定理**：若 $x(t) \leftrightarrow X(j\omega)$，则 $\displaystyle \int_{-\infty}^{\infty} |x(t)|^2 \mathrm dt = \frac{1}{2\pi} \int_{-\infty}^{\infty} |X(j\omega)|^2 \mathrm d\omega$

**卷积性质**：若 $x(t) \leftrightarrow X(j\omega),\, h(t) \leftrightarrow H(j\omega)$，则 $x(t) * h(t) \leftrightarrow X(j\omega) H(j\omega)$.
- **频域分析**：对于 LTI 系统的卷积，我们不妨傅里叶变换获得 $X(j\omega)$ 和 $H(j\omega)$，再做一个对位相乘 $Y(j\omega) = X(j\omega)H(j\omega)$，再做傅里叶反变换即可获得卷积 $y(t) = x(t)*h(t)$，这样做，避免了直接卷积。

**相乘性质**：若 $s(t) \leftrightarrow S(j\omega),\, p(t) \leftrightarrow P(j\omega)$，则 $\displaystyle s(t)p(t) \leftrightarrow \frac{1}{2\pi} S(j\omega)*T(j\omega)$.
- 信号的相乘，可以视作一个信号（调制信号）控制另一个信号（载波）的幅度
- 通常而言，载波信号的频率比调制信号的频率明显高很多。载波信号适于传输信息，调制信号是原始的信息波形，二者相乘即可将我们的信息放在载波上来传送。
- 对于正弦幅度调制，由于 $\cos \omega_0 t \leftrightarrow \pi[\delta(\omega - \omega_0) +\delta(\omega + \omega_0)]$，卷积后，相当于把调制信号的频谱移到载频的位置。


![](attachments/Pasted%20image%2020260410164810.png)

例：$r(t)\sin\omega_0t$，$r(t)\cos\omega_0 t$

# 4.7 由线性常系数微分方程表征的系统

对于线性常系数微分方程 $$\sum_{k = 0}^N a_k \frac{\mathrm d^k y(t)}{\mathrm d t^k} = \sum_{k = 0}^M b_k \frac{\mathrm d^k x(t)}{\mathrm d t^k},\quad a_k, b_k \in \mathbb R$$
我们将其进行傅里叶变换，得到 $$\sum_{k = 0}^N a_k(j\omega)^k Y(j\omega) = \sum_{k = 0}^M b_k(j\omega)^k X(j\omega)$$
得到 LTI 系统的频率响应是一个 *有理函数*（可写成两个多项式相除） $$H(j\omega) = \frac{Y(j\omega)}{X(j\omega)} = \frac{\sum_{k = 0}^M b_k(j\omega)^k}{\sum_{k = 0}^N a_k(j\omega)^k}$$


# Conclusion

![](attachments/Pasted%20image%2020260410165649.png)

![](attachments/Pasted%20image%2020260410165710.png)

![](attachments/Pasted%20image%2020260410165759.png)
