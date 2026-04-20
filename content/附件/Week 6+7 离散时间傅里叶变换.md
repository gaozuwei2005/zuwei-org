# 5.1 离散时间傅里叶变换

对于非周期信号 $x[n]$，我们将其周期延拓为周期为 $N \to \infty$ 的 $\tilde x[n]$，频率为 $\omega_0 = \displaystyle \frac{2\pi}{N}$.

$$a_k = \frac{1}{N}\sum_{n = -\infty}^{\infty} x[n] e^{jk\omega_0n} = \frac{1}{N} X(e^{jk\omega_0})$$
其中 $\displaystyle X(e^{j\omega}) = \sum_{n = -\infty}^{\infty} x[n] e^{j\omega n}$.

那么 $$x[n] = \frac{1}{2\pi}\sum_{k = \langle N \rangle} X(e^{jk\omega_0}) e^{jk\omega_0 n}\omega_0$$

**离散时间傅里叶变换对**：
- 傅里叶变换：$$X(e^{j\omega}) = \sum_{n = -\infty}^{\infty} x[n] e^{-j\omega n}$$
- 傅里叶反变换：$$x[n] = \frac{1}{2\pi} \int_{2\pi} X(e^{j\omega}) e^{j\omega n} \mathrm d\omega$$

**常见信号的傅里叶变换**：


| 信号                                                                                       | 频谱                                                                                                                | 说明                                        |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| $x[n] = a^nu[n],\, \lvert a\rvert<1$                                                     | $\displaystyle X(e^{j\omega}) = \frac{1}{1-ae^{-j\omega}}$                                                        | 模长是偶函数，相位是奇函数                             |
| $x[n] = a^{\lvert n \rvert},\, \lvert a \rvert < 1$                                      | $\displaystyle X(e^{j\omega}) = \frac{1-a^2}{1 + a^2 - 2a \cos \omega}$                                           | 实偶信号的傅里叶变换是实偶函数                           |
| $x[n] = \delta[n]$                                                                       | $X(e^{j\omega}) = 1$                                                                                              | $\delta [n]$ 中包括了所有的频率成分，且所有频率分量的幅度、相位都相同 |
| $x[n] = \begin{cases}1, & \lvert n \rvert\le N_1 \\ 0, & \lvert n \rvert>N_1\end{cases}$ | $\displaystyle X(e^{j\omega}) = \frac{\sin [2(N_1 + 1)\frac{\omega}{2}]}{\sin \frac{\omega}{2}}$                  | 实偶信号的傅里叶变换是实偶函数                           |
| $\displaystyle x[n] = \frac{W}{\pi} \text{sinc}\left(\frac{Wn}{\pi}\right)$              | $X(e^{j\omega}) = \begin{cases}1, & \lvert \omega \rvert<W \\ 0, & W<\lvert \omega \rvert\le \pi\end{cases}$      | 形成对偶关系                                    |
| $x[n] = 1$                                                                               | $\displaystyle X(e^{j\omega}) = 2\pi \sum_{l = -\infty}^{\infty}\delta(\omega - 2\pi l)$                          | 方波信号在 $n \to \infty$ 的极限                  |
| $x[n] = u[n]$                                                                            | $\displaystyle X(e^{j\omega}) = \frac{1}{1 - e^{-j\omega}} + \sum_{k = -\infty}^{\infty} \delta(\omega - 2\pi k)$ | 分为奇偶信号                                    |

# 5.2 周期信号的傅里叶变换

对于离散时间周期信号，它对应的频域是周期性的冲激串：$$x[n] = e^{jk\omega_0 n} \quad \Leftrightarrow \quad X(e^{j\omega}) = \sum_{l = -\infty}^{\infty} 2\pi \delta(\omega - k \omega_0 - 2\pi l)$$
$$x[n] = \sum_{k = \langle N \rangle}e^{jk\omega_0 n} \quad \Leftrightarrow \quad X(e^{j\omega}) = 2\pi \sum_{k = -\infty}^{\infty} a_k \delta(\omega - k \omega_0)$$

| 信号                                                                | 频谱                                                                                                                                        | 说明    |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| $x[n] = \cos \omega_0 n$                                          | $\displaystyle X(e^{j\omega}) = \pi\sum_{k = -\infty}^{\infty} [\delta(\omega - \omega_0 - 2\pi k) + \delta(\omega + \omega_0 - 2\pi k)]$ |       |
| $\displaystyle x[n] = \sum_{k = -\infty}^{\infty} \delta(n - kN)$ | $\displaystyle X(e^{j\omega}) = \frac{2\pi}{N}\sum_{k = -\infty}^{\infty} \delta\left(\omega - \frac{2\pi}{N}k\right)$                    | 均匀冲激串 |

# 5.3~5.7 离散时间傅里叶变换的性质

**周期性**：$x[n] \leftrightarrow X(e^{j\omega})$，则 $X(e^{j(\omega + 2\pi)} = X(e^{j\omega})$

**线性**：若 $x[n] \leftrightarrow X(e^{j\omega}),\, y[n] \leftrightarrow Y(e^{j\omega})$，则 $ax[n] + by[n] \Leftrightarrow aX(e^{j\omega}) + bY(e^{j\omega})$


**时移**：
- 信号时移造成频谱线性相移。若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $x[n - n_0] \leftrightarrow X(e^{j\omega}) e^{-j\omega t_0}$
- 频谱频移造成信号线性相移。若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $x[n]e^{j\omega_0 n} \leftrightarrow X(e^{j(\omega - \omega_0)})$


**共轭与奇偶性**：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $x[-n] \leftrightarrow X(e^{-j\omega})e^{-j\omega t_0}$ 
- 若 $x[n]$ 是实信号，则 $X(e^{j\omega}) = X^*(e^{-j\omega})$，频谱为 *共轭偶函数*。这说明此时 $X(e^{j\omega})$ 的实部是偶函数、虚部是奇函数、幅度是偶函数、相位是奇函数。
- 若 $x[n]$ 是偶函数，则 $X(e^{j\omega}) = X(e^{-j\omega})$，也为偶函数
- 若 $x[n]$ 是实偶信号，则 $X(e^{j\omega})$ 是实偶函数。
- 若 $x[n]$ 是偶函数，则 $X(e^{j\omega}) = -X(e^{-j\omega})$，也为奇函数
- 若 $x[n]$ 是实奇信号，则 $X(e^{j\omega})$ 是虚奇函数。
- 令 $x[n] = x_e[n] + x_o[n]$，则对应的 $X(e^{j\omega}) = X_e(e^{j\omega}) + jX_o(e^{j\omega})$

**差分与累加**：
- 时域差分：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $x[n] - x[n - 1] \leftrightarrow (1 - e^{-j\omega} X(e^{j\omega})$.
- 时域累计：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle \sum_{k = -\infty}^{n} x[k] \leftrightarrow \frac{X(e^{j\omega})}{1 - e^{-j\omega}} + \pi X(e^{j0}) \sum_{k = -\infty}^{\infty} \delta(\omega - 2\pi k)$.
 - 频域微分：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle nx[n] \leftrightarrow j\frac{\mathrm d X(e^{j\omega})}{\mathrm d\omega}$.
 %%- 频域积分：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle -\frac{1}{jt} x[n] + \pi x(0) \delta[n] \leftrightarrow \int_{-\infty}^{\omega} X(j\tau)\mathrm d\tau$. %%

**时域内插**：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle x_k[n] \leftrightarrow X(e^{jk\omega})$ 相反关系

**Parseval 定理**：若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle \sum_{n = -\infty}^{\infty} |x[n]|^2 \mathrm dt = \frac{1}{2\pi} \int_{2\pi} |X(e^{j\omega})|^2 \mathrm d\omega$

**卷积性质**：若 $x[n] \leftrightarrow X(e^{j\omega}),\, h[n] \leftrightarrow H(e^{j\omega})$，则 $x[n] * h[n] \leftrightarrow X(e^{j\omega}) H(e^{j\omega})$.
- **频域分析**：对于 LTI 系统的卷积，我们不妨傅里叶变换获得 $X(e^{j\omega})$ 和 $H(e^{j\omega})$，再做一个对位相乘 $Y(e^{j\omega}) = X(e^{j\omega})H(e^{j\omega})$，再做傅里叶反变换即可获得卷积 $y[n] = x[n]*h[n]$，这样做，避免了直接卷积。
- 不是所有的 LTI 系统都存在频率响应，一般只考虑稳定的频率响应

**相乘性质**：若 $s[n] \leftrightarrow S(e^{j\omega}),\, p[n] \leftrightarrow P(e^{j\omega})$，则 $\displaystyle s[n]p[n] \leftrightarrow \frac{1}{2\pi} \int_{2\pi}S(e^{j\theta})T(e^{j(\omega - \theta)})\mathrm d\theta = \frac{1}{2\pi} S(e^{j\omega}) \otimes T(e^{j\omega})$ （周期卷积）
- 信号的相乘，可以视作一个信号（调制信号）控制另一个信号（载波）的幅度
- 通常而言，载波信号的频率比调制信号的频率明显高很多。载波信号适于传输信息，调制信号是原始的信息波形，二者相乘即可将我们的信息放在载波上来传送。
- 对于正弦幅度调制，由于 $\cos \omega_0 t \leftrightarrow \pi[\delta(\omega - \omega_0) +\delta(\omega + \omega_0)]$，卷积后，相当于把调制信号的频谱移到载频的位置。

**对偶性**：
- 若 $x[n] \leftrightarrow a_k$，则 $\displaystyle a_n \leftrightarrow \frac{1}{N}x[-k]$.
- 若 $x[n] \leftrightarrow X(e^{j\omega})$，则 $\displaystyle X(e^{jt}) \leftrightarrow x[-k]$.

# 5.8 由线性常系数差分方程表征的系统

对于线性常系数差分方程表征的 LTI 系统 $$\sum_{k = 0}^N a_k y[n - k] = \sum_{k = 0}^M b_k x[n - k]$$
我们将其进行傅里叶变换，得到 $$\sum_{k = 0}^N a_k e^{-jk\omega} Y(e^{j\omega}) = \sum_{k = 0}^M b_k e^{-jk\omega} X(e^{j\omega})$$
得到 LTI 系统的频率响应是一个 *有理函数*（可写成两个多项式相除） $$H(j\omega) = \frac{Y(j\omega)}{X(j\omega)} = \frac{\sum_{k = 0}^M b_k e^{-jk\omega}}{\sum_{k = 0}^N a_k e^{-jk\omega}}$$

# Conclusion

![](attachments/Pasted%20image%2020260417164057.png)
![](attachments/Pasted%20image%2020260417164109.png)
![](attachments/Pasted%20image%2020260417164120.png)
![](attachments/Pasted%20image%2020260417164132.png)