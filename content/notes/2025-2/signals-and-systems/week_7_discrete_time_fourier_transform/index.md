---
title: 信号与系统 | Week 7 离散时间傅里叶变换
date: 2026-04-10
summary: 离散时间傅里叶变换
---

# 5.1 离散时间傅里叶变换

对于非周期信号 $x[n]$，我们将其周期延拓为周期为 $N \to \infty$ 的 $\tilde x[n]$，频率为 $\omega_0 = \displaystyle \frac{2\pi}{N}$.

$$a_k = \frac{1}{N}\sum_{n = -\infty}^{\infty} x[n] e^{jk\omega_0n} = \frac{1}{N} X(e^{jk\omega_0})$$
其中 $\displaystyle X(e^{j\omega}) = \sum_{n = -\infty}^{\infty} x[n] e^{j\omega n}$.

那么 $$x[n] = \frac{1}{2\pi}\sum_{k = \langle N \rangle} X(e^{jk\omega_0}) e^{jk\omega_0 n}\omega_0$$

**离散时间傅里叶变换对**：
- 傅里叶变换：$$X(e^{j\omega}) = \sum_{n = -\infty}^{\infty} x[n] e^{-j\omega n}$$
- 傅里叶反变换：$$x[n] = \frac{1}{2\pi} \int_{2\pi} X(e^{j\omega}) e^{j\omega n} \mathrm d\omega$$

**常见信号的傅里叶变换**：


| 信号                                                                                       | 频谱                                                                                                           | 说明                                        |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------- |
| $x[n] = a^nu[n],\, \lvert a\rvert<1$                                                     | $\displaystyle X(e^{j\omega}) = \frac{1}{1-ae^{-j\omega}}$                                                   | 模长是偶函数，相位是奇函数                             |
| $x[n] = a^{\lvert n \rvert},\, \lvert a \rvert < 1$                                      | $\displaystyle X(e^{j\omega}) = \frac{1-a^2}{1 + a^2 - 2a \cos \omega}$                                      | 实偶信号的傅里叶变换是实偶函数                           |
| $x[n] = \delta[n]$                                                                       | $X(e^{j\omega}) = 1$                                                                                         | $\delta [n]$ 中包括了所有的频率成分，且所有频率分量的幅度、相位都相同 |
| $x[n] = \begin{cases}1, & \lvert n \rvert\le N_1 \\\\ 0, & \lvert n \rvert>N_1\end{cases}$ | $\displaystyle X(e^{j\omega}) = \frac{\sin [2(N_1 + 1)\frac{\omega}{2}]}{\sin \frac{\omega}{2}}$             | 实偶信号的傅里叶变换是实偶函数                           |
| $\displaystyle x[n] = \frac{W}{\pi} \text{sinc}\left(\frac{Wn}{\pi}\right)$              | $X(e^{j\omega}) = \begin{cases}1, & \lvert \omega \rvert<W \\\\ 0, & W<\lvert \omega \rvert\le \pi\end{cases}$ | 形成对偶关系                                    |
| $x[n] = 1$                                                                               | $\displaystyle X(e^{j\omega}) = 2\pi \sum_{l = -\infty}^{\infty}\delta(\omega - 2\pi l)$                     | 方波信号在 $n \to \infty$ 的极限                  |

