---
title: 信号与系统 | Week 4 傅里叶级数表示
date: 2026-03-24
summary: LTI 系统对复指数信号的响应、连续时间周期信号的傅里叶级数表示、离散时间周期信号的傅里叶级数表示、傅里叶级数与 LTI 系统的关系、滤波器
---

# 3.1 引言

周期信号可以分解为成谐波关系的复指数信号的线性组合。

LTI 系统对于复指数信号的响应具有特殊的简单形式。

# 3.2 LTI 系统对复指数信号的响应

对于复指数信号 $e^{st} / z^n$ 的响应，只是在前面多乘了一个常数 $H(s) / H(z)$.

因此我们称 $e^{st} / z^n$ 是一切 LTI 系统的 **特征函数**，对应的特征值为 $H(s) / H(z)$.

$$T\\\{e^{st}\\\} = \int_{-\infty}^{+\infty} e^{s(t-\tau)}h(\tau) \mathrm d\tau = e^{st} \int_{-\infty}^{+\infty} e^{-s\tau}h(\tau) \mathrm d\tau = H(s) e^{st}$$
$$T\\\{z^n\\\} = \sum_{k} z^{n-k}h[k]  = z^n \sum_k z^{-k} h[k] = H(z) z^n$$

因此我们希望把任意信号分解为 $$x(t) = \sum_k a_k e^{s_kt}, \quad x[n] = \sum_k a_k z_k^n$$

# 3.3 连续时间周期信号的傅里叶级数表示

## 3.3.1 连续时间傅里叶级数

**成谐波关系的复指数信号集**：$\\\{\varphi_k(t)\\\} = \\\{e^{jk\omega_0t}\\\},\quad k = 0, \pm 1, \pm 2, \cdots$
- 每个信号的基波频率为 $k|\omega_0|$，均为 $|\omega_0|$ 的整数倍，因此称它们为 *成谐波关系*
- 公共周期：$\displaystyle T_0 = \frac{2\pi}{\omega_0}$
- 直流分量：$k = 0$；基波分量：$k = \pm 1$；二次谐波分量：$k = \pm 2$；
- 这些信号彼此独立

**连续时间傅里叶级数**：成谐波关系的复指数信号的线性组合 $$x(t) = \sum_k a_k e^{jk\omega_0t},\quad k = 0, \pm 1, \pm 2,\cdots$$
傅里叶级数也以 $\displaystyle T = \frac{2\pi}{|\omega_0|}$ 为周期。


## 3.3.2 频谱表示法

将傅里叶级数表示为频谱图：

![](attachments/Pasted%20image%2020260324113736.png)

## 3.3.3 系数的确定

对于 $\displaystyle x(t) = \sum_k a_k e^{jk\omega_0t},\quad k = 0, \pm 1, \pm 2,\cdots$，它的每一项系数为 $$a_k = \frac{1}{T} \int_t^{t + T} x(t) e^{-jk\omega_0 t}\mathrm dt$$
其中 $[t, t+ T]$ 的位置无特定要求。

特别地，直流分量 $\displaystyle a_0 = \frac{1}{T} \int_t^{t + T} x(t)\mathrm dt$.

# 3.4 连续时间傅里叶级数的收敛

在误差能量最小的准则下，傅里叶级数是对周期信号的最佳近似。

**平方可积条件**：对于能量有限的信号 $\displaystyle \int_T|x(t)|^2\mathrm dt < \infty$，则 $a_k$ 必然存在，并且 $x(t)$ 与傅里叶级数表示没有能量上的差别。

**Dirichlet 条件**：
- 信号在任何周期内信号绝对可积 $$|a_k| \le \frac{1}{T}\int_T |x(t)e^{-jk\omega_0t}|\mathrm dt = \frac{1}{T}\int_T |x(t)|\mathrm dt < \infty$$
- 有限长区间内，只有有限个极值点
- 有限长区间内，只有有限个间断点且函数值有限。此时傅里叶级数收敛于间断点两边值的平均

**Gibbs 现象**：在间断点的傅里叶级数不可避免地产色产生震荡和超量。并且随着项数越多震荡频率越高，并向间断点处压缩，

# 3.6  离散时间周期信号的傅里叶级数表示

**离散时间傅里叶级数**：$$x[n] = \sum_{k = \langle N\rangle} a_k e^{j \frac{2\pi}{N} kn}$$
其中的项数只有 $N$ 个。

如果改变了区间，那么系数的变换是按照周期性变化规律的：$a_{k+N} = a_k$.

**系数的确定**：$$a_k = \frac{1}{N} \sum_{n = \langle N\rangle} x[n] e^{-j\frac{2\pi}{N} kn}$$

**收敛性**：离散时间傅里叶级数由于是有限和式，所以必然收敛。

# 3.8 傅里叶级数与 LTI 系统

连续时间 LTI 系统的频率响应：$$H(j\omega) = \int_{-\infty}^{+\infty} h(t) e^{-j\omega t}\mathrm dt$$
离散时间 LTI 系统的频率响应：$$H(e^{j\omega}) = \sum_{n} h(t) e^{-j\omega n}$$
$$x(t)=\sum_{k=-\infty}^{\infty} a_k e^{jk\omega_0 t}\;\Longrightarrow\;y(t)=\sum_{k=-\infty}^{\infty} a_k H(jk\omega_0)e^{jk\omega_0 t}$$

$$x[n]=\sum_{k=\langle N\rangle} a_k e^{j\frac{2\pi}{N}kn}\;\Longrightarrow\;y[n]=\sum_{k=\langle N\rangle} a_k \!\left(e^{j\frac{2\pi}{N}k}\right)e^{j\frac{2\pi}{N}kn}$$


# 3.9~3.11 滤波

**滤波**：改变信号中各频率分量的相对大小，或消除某些频率分量的过程。

滤波的分类：频率成形滤波器（改变信号频谱形状）、频率选择性滤波器（消除某些特定频率）

常见滤波器：低通滤波器、高通滤波器、带通滤波器

对于离散时间滤波器，只需要其中 $N$ 个系数即可

对于微分、差分方程，它们也可以视作是广义上的滤波器。
- 对于微分方程：令 $x(t) = e^{j\omega t}$，$y(t) = H(j\omega)e^{j\omega t}$
- 对于差分方程：令 $x[n] = e^{j \omega n}$，$y[n] = H(e^{j\omega})e^{j\omega n}$

解出对应的 $H$ 之后，就可以画出它的频谱图和相位图，并分析它作为滤波器的特点。
