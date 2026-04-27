---
title: 信号与系统 | Week 8 傅里叶变换的应用
date: 2026-04-24
summary: 时域和频域特性、滤波器、采样定理、通信系统、信号调制
---

# CH6 时域和频域特性

## 6.1~6.2 傅里叶变换的模和相位表示

对于傅里叶变换可以表示为模-相位表示：$|X(j\omega)|e^{j\angle X(j\omega)}$（离散时间同理），因此信号的失真包括幅度失真和相位失真。

$$x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} |X(j \omega)| e^{j (\omega t + \phi_X(\omega))} \mathrm d \omega$$

 如果相位特性只是一个线性相移时如 $H(j\omega) = e^{-j\omega t_0}$，信号将只会发生时间延迟而未丢失任何信息。$$H(j \omega) = ke^{-j\omega t_0}\ (\text{for CTFT}) \quad H(e^{j\omega}) = ke^{-j\omega n_0}\ (\text{for DTFT})$$$$h(t) = k\delta(t - t_0)\ (\text{for CTFT}) \quad h[n] = k\delta[n - n_0]\ (\text{for DTFT})$$
如果相位特性是非线性的，那么将会导致不同频率的分量叠加，变成和原来信号很不相同的信号波形。

不失真系统：在被传输信号的带宽范围内满足不失真条件。

全通系统：系统的幅频特性是常数。

# 6.3 理想频率选择性滤波器

![](attachments/Pasted%20image%2020260421103541.png)

问题：
- 无限长的冲激响应
- 非因果，无法真正实时实现
- 产生振铃现象

在实际上只能做近似低通，避免此类麻烦。

# CH7 采样

在日常生活中，常用离散时间信号表示连续时间信号。

# 7.1 采样定理

一般情况下，从连续时间信号采样所得到的样本序列不能唯一地代表原来的连续时间信号。

**采样的数学模型**：
- 时域上：$x_p(t) = x(t) · p(t)$
- 频域上：$\displaystyle X_p(j\omega) = \frac{1}{2\pi} X(j\omega)*P(j\omega)$
- 对于理想采样，$p(t)$ 是均匀冲激串 $$p(t) = \sum_{n = -\infty}^{\infty} \delta(t - nT)\quad x_p(t) = \sum_{n = -\infty}^{\infty} x(nT) \delta(t - nT)$$ $$X_p(j\omega) = \frac{1}{T} \sum_{k = -\infty}^{\infty} X(j(\omega - k \omega_s))$$

![](attachments/Pasted%20image%2020260421104829.png)


在时域对连续时间信号进行理想采用相当于对连续时间信号的频谱以 $\omega_s$ 为周期进行无限周期延拓。

因此，我们要求 $X_p(j\omega)$ 周期性延拓的时候不能产生频谱混叠。如果最高频率分量为 $\omega_M$，那么采样间隔应当满足 $\omega_s > 2 \omega_M$.

**Nyquist, 奈奎斯特采样定理**：对带限于最高频率 $\omega_M$ 的连续时间信号 $x(t)$，如果以 $\omega_S > 2 \omega_M$ 的频率进行理想采样，那么 $x(t)$ 可以唯一地由样本 $x(nT)$ 来确定

![](attachments/Pasted%20image%2020260421111441.png)

**零阶保持采样**：我们在理想采样后，级联一个零阶保持系统，这样就能让离散的信号连接起来。

![](attachments/Pasted%20image%2020260421112216.png)

如果要恢复为原信号，需要级联系统 $H_r(j\omega)$，使得等效为理想低通滤波器。

$$H_0(j\omega)H_r(j\omega) = H(j\omega) = \begin{cases}T,&|\omega| < \omega_ c \\ 0,& |\omega| > \omega_c\end{cases}$$

$$H_r(j\omega) = \frac{H(j\omega)}{2 \sin (\omega T / 2)} e^{j \frac{\omega T}{2}}$$

## 7.2 利用内插从样本重建信号

*To be completed*


## 7.3 欠采样的效果—频谱混叠

如果不满足采样定理的要求，就会在 $x(t)$ 的频谱周期延拓时，出现频谱混叠的现象。

当 $\omega_0 < \omega_s < 2\omega_0$ 时将会产生频谱混叠，恢复的信号的周期将是 $w_s - w_0$.

![](attachments/Pasted%20image%2020260421114616.png)

# CH8 通信系统

通信系统的各个环节：

![](attachments/Pasted%20image%2020260421114640.png)

## 8.1 正弦幅度调制

幅度调制的数学模型是乘法器，$y(t) = x(t) · c(t)$，其中 $x(t)$ 是调制信号，$c(t)$ 是载波。调制信号改变了载波的各个位置的幅度，从而已调信号可以保存调制信号的信息。


![](attachments/Pasted%20image%2020260424164531.png)

当 $c(t) = \cos(\omega_c t + \theta_c)$ 时，称为正弦幅度调制。

**双边带调制**：如果令 $c(t) = \cos(\omega_c t)$，那么 $C(j\omega) = \pi [\delta(\omega - \omega_c) + \delta(\omega + \omega_c)]$，是两个冲击，幅度为 $\pi$.  那么已调信号的频谱为 $$Y(j\omega) = \frac{1}{2} [X(j(\omega - \omega_c)) + X(j(\omega + \omega_c))]$$
![](attachments/Pasted%20image%2020260424164814.png)

相当于将原信号的频谱分两半后，搬到正负对称高频边带的位置。

**同步解调**：我们将 $y(t)$ 再次与同频载波相乘，再通过低通滤波，即可得到原来的信号。

$$w(t) = y(t) \cos \omega_c t = x(t) \cos^2 \omega_c t =  \underbrace{\frac{1}{2} x(t)}_{目标信号} + \underbrace{\frac{1}{2} x(t)\cos 2 \omega_c t}_{干扰信号}$$
![](attachments/Pasted%20image%2020260424165152.png)

![](attachments/Pasted%20image%2020260424165410.png)

**载波相位的影响**：设调制时载波为 $c_1(t) = \cos(\omega_c t +\theta_c)$，解调时载波为 $c_1(t) = \cos(\omega_c t +\varphi_c)$，则

$$w(t) x(t) \cos^2 (\omega_c t + \theta_c) =  \underbrace{\frac{1}{2} x(t) \cos(\theta_c - \varphi_c)}_{目标信号} + \underbrace{\frac{1}{2} x(t)\cos (2 \omega_c t)}_{干扰信号}$$

## 8.3 频分多路复用

利用不同的载波可以将同一频段分别加载在不同频段，注意频段不能重合。$$w(t) = \sum_{k}x_k(t) ·\cos(w_k t)$$
![](attachments/Pasted%20image%2020260424173854.png)


在解调时，只需使用带通滤波器滤出一路信号，再进行解调即可。

## 8.4 单边带正弦幅度调制

双边带调制信号再经过一个低通滤波器，即可消除一半的边带，减少对频域的占用。

![](attachments/Pasted%20image%2020260424174102.png)

## 8.5 脉冲串作载波的幅度调制

用脉冲串作为载波信号：$$C(j\omega) = 2\pi \sum_{k = -\infty}^{\infty} a_k \delta(\omega - \frac{2\pi}{T}k)$$
那么已调信号为 $$Y(j\omega) = \sum_{k = -\infty}^{\infty} a_k X[j(\omega - \frac{2\pi}{T}k)]$$
信号可恢复要求 $\displaystyle 2\omega_M < \frac{2\pi}{T}$.

低通滤波器的截止频率 $W$ 满足：$\omega_M < W < \omega_c - \omega_M$.

![](attachments/Pasted%20image%2020260424174823.png)


时分多路复用：我们为每一路信号分配一个时隙，使得各路信号的时隙彼此不重叠则可以实现多路信号同时传送。

## 8.6 脉冲幅度调制

脉冲幅度调制实际上是零阶保持采样。

在每个时隙内只需要信号的一个样本值，只要各路信号时隙彼此不重叠即可实现时分多路复用。

![](attachments/Pasted%20image%2020260424175100.png)

![](attachments/Pasted%20image%2020260424175146.png)
