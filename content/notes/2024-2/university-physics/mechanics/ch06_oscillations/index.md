---
title: 大学物理 | Ch6 振动
date: 2024-12-24
summary: 简谐运动（描述、动力学、能量）、阻尼运动、受迫振动、振动、简谐运动的合成
---

# 6.1 简谐运动的描述

**简谐运动**：$x = A \cos(\omega t + \varphi)$.（一般是 $\cos$）

**角频率、周期和频率**：$\displaystyle\omega  = \frac{2\pi}{T},\  \nu = \frac{1}{T}, \ \omega = 2\pi \nu$

**速度**：$\displaystyle v = \frac{\mathrm dx}{\mathrm dt} = -\omega A\sin(\omega t + \varphi) = \omega A \cos \left(\omega t + \varphi + \frac{\pi}{2}\right)$

**加速度**：$\displaystyle a = \frac{\mathrm d^2 x}{\mathrm dt^2} = - \omega^2 A \cos(\omega t + \varphi) = \omega^2 A \cos(\omega t + \varphi + \pi) = - \omega^2 x$

**位移、速度和加速度最大值**：$v_{m} = \omega A,\quad a_m = \omega^2 A$

**相量图**：注明 $A, \omega, \varphi$，其中 $\omega$ 包括大小和方向。

**相差**：$\Delta \varphi$，可调成 $(-\pi, \pi]$，相位差为 $0$ 称之同相，相位差为 $\pi$ 称之反相。相值大的是超前振动，相值小的是落后振动。

# 6.2 简谐运动的动力学

**回复力**：$F = m \dfrac{\mathrm d^2 x}{\mathrm dx^2} = -kx = - m\omega^2 x$。

微分方程 $a = \dfrac{\mathrm d^2 x}{\mathrm dx^2} = -\dfrac{k}{m} x$ 的解是三角函数 $x = A\cos(\omega t + \varphi)$。因此，只要合外力满足 $F = - k x$，那么一定物体一定做简谐运动。

**固有角频率**：$\displaystyle \omega = \sqrt\frac{k}{m}$，**固有周期**：$\displaystyle T = 2 \pi \sqrt\frac{m}{k}$

**幅值**：$\displaystyle A = \sqrt{x_0^2 + \frac{v_0^2}{\omega^2}}$，其中初位移 $x_0 = A\cos \varphi$，初速度 $v_0 = - \omega A \sin \varphi$。

**初相**：$\displaystyle \varphi = \arctan \left(- \frac{v_0}{\omega x_0}\right)$，一般 $\varphi$ 在 $(-\pi, \pi]$ 内有两个值，需要代入到初始条件中确定。

# 6.3 简谐运动的能量

简谐运动的能量：$\displaystyle E = \frac{1}{2} kA^2$.

$$\begin{aligned}
E &= \frac{1}{2}mv^2 + \frac{1}{2}kx^2 \\\\
&= \frac{1}{2} m [- \omega A \sin(\omega t + \varphi)]^2 + \frac{1}{2} m \omega ^2 [A \cos(\omega t + \varphi)]^2 \\\\
&= \frac{1}{2} m \omega^2 A^2 \\\\
&= \frac{1}{2} k A^2
\end{aligned}$$

弹簧势能和振子动能对时间的平均值：

$\displaystyle \overline{E_p} = \frac{1}{2} \int_0^T \frac{1}{2} kx^2 \mathrm dt = \frac{1}{2} \int_0^T \frac{1}{2} k[A\cos(\omega t + \varphi)]^2 \mathrm dt = \frac{1}{4} kA^2 = \frac{1}{2} E$

$\displaystyle \overline{E_k} = \frac{1}{2} \int_0^T \frac{1}{2} mv^2 \mathrm dt = \frac{1}{2} \int_0^T \frac{1}{2} m [\omega A \sin(\omega t + \varphi)]^2 \mathrm dt = \frac{1}{4} kA^2 = \frac{1}{2} E$

# 6.4 阻尼运动

**阻尼力**： $f = - \gamma v = - \gamma \dfrac{\mathrm dx}{\mathrm dt}$

那么**运动方程**为 $\displaystyle a = m \dfrac{\mathrm d^2 x}{\mathrm dt^2} = - k x - \gamma \dfrac{\mathrm dx}{\mathrm dt}$（常系数二阶线性齐次常微分方程）

**固有角频率** $w_0 = \sqrt{\dfrac{k}{m}}$ 和**阻尼系数** $\beta = \dfrac{\gamma}{2m}$，那么运动方程可以重写为 $\displaystyle \dfrac{\mathrm d^2 x}{\mathrm dt^2} + 2 \beta \dfrac{\mathrm dx}{\mathrm dt} + \omega_0^2 x = 0$

**欠阻尼 / 无阻尼**：当阻尼作用较小 $\beta < \omega_0$ 时，$x = A_0 e^{- \beta t} \cos (\omega t + \varphi_0)$，其中 $\omega = \sqrt{\omega_0^2 - \beta^2}$.

因此阻尼系数 $\beta$ 越大，周期 $\displaystyle T = \frac{2 \pi}{\sqrt{\omega_0^2 - \beta^2}}$ 越大。无阻尼的周期（固有周期 $\displaystyle T_0 = \frac{2 \pi}{\omega_0}$）最短。

**能量衰减**：在弱阻尼（$\beta \ll \omega_0$） 时，由于振幅 $A_0 e^{-\beta t}$ 不断减小，那么能量有 $E \approx E_0 e^{-2\beta t}$。

**时间常量（鸣响时间）**：阻尼振动能量减小到原始能量的 $\dfrac{1}{e}$ 所经过的时间：$\tau = \dfrac{1}{2\beta} = \dfrac{2m}{\gamma}$.

**品质因数（Q 值）**：用鸣响时间的振动次数来比较振动的优劣：$Q = 2\pi \dfrac{\tau}{T} = \omega \tau$.

**过阻尼**：当阻尼作用过大时，物体将从原来远平衡位置的状态慢慢回到平衡位置，而不具有任何周期性。

**临界阻尼**：系统还是一次性回到平衡状态，但所用时间比过阻尼的情况更短。施加临界阻尼可以让物体以最短时间回到平衡位置。

# 6.5 受迫振动 共振

**受迫振动**：振动系统在周期性外力作用下补充能量的振动。

受迫振动的**运动方程**：$\displaystyle m \frac{\mathrm d^2 x}{\mathrm dt^2} = - kx - \gamma \dfrac{\mathrm dx}{\mathrm dt} + H \cos \omega t$. 其中 $H \cos \omega t$ 是周期性外力。

令 $\displaystyle \omega_0^2 = \frac{k}{m},\ 2 \beta = \frac{\gamma}{m},\ h = \frac{H}{m}$，上式变为

$$\displaystyle \frac{\mathrm d^2 x}{\mathrm dt^2} + 2 \beta \dfrac{\mathrm dx}{\mathrm dt} + \omega_0^2 x = h \cos \omega t$$

该微分方程的解为

$$x = A_0 e^{-\beta t} \cos(\sqrt{\omega_0^2 - \beta^2}\ t + \varphi_0) + A\cos(\omega t + \varphi)$$

因此受迫振动是由两个振动合成的，第一个振动会迅速减弱直至可以忽略不计。后一项表示的是受迫振动达到稳定状态时的等幅振动。

等幅振动角频率就是驱动力的角频率，振幅为

$$A = \frac{h}{\sqrt{(\omega_0^2 - \omega^2)^2 + 4 \beta^2 \omega^2}}$$

当 $\omega = \sqrt{\omega_0^2 - 2\beta^2}$ 时，$A$ 达到最大振幅 $A = \dfrac{h}{2\beta\sqrt{\omega_0^2 - \beta^2}}$.

稳态受迫振动与驱动力的相位差

$$\varphi = \arctan \frac{-2\beta\omega}{\omega_0^2 - \omega^2}$$

**共振**：在弱阻尼即 $\beta \ll \omega_0$ 的情况下，若驱动力频率等于振动频率的固有频率时，振幅达到最大值。

# 6.6 同一直线上同频率的简谐运动的合成

同频率简谐运动的合运动表达式为 $x = A \cos(\omega t + \varphi)$

合振幅为 $A = \sqrt{A_1^2 + A_2^2 + 2A_1A_2\cos(\varphi_1 - \varphi_2)}$

初相为 $\tan \varphi = \dfrac{A_1\sin\varphi_1 + A_2\sin\varphi_2}{A_1\cos\varphi_1 + A_2\cos\varphi_2}$

同两振动同相时，有 $A = A_1 + A_2$，振幅最大。

同两振动反相时，有 $A = |A_1 - A_2|$，振幅最小。

# 6.7 同一直线上不同频率的简谐运动的合成

对于两个同振幅、同频率的简谐运动，它们的合成可以使用和差化积得到

$$x = 2A \cos\frac{\omega_2-\omega_1}{2}t \cos\left( \frac{\omega_1+\omega_2}{2}t + \varphi \right)$$

如果两个简谐运动的角速度相差很小 $\omega_2 - \omega_1 \ll \omega_1 + \omega_2$，也就是第二个三角函数的变化比第一个三角函数的变化要快得多，因此，该合运动可以看作是振幅为 $\left| 2A \cos \dfrac{\omega_2 - \omega_1} t \right|$，角频率为 $\dfrac {\omega_1 + \omega_2}{2}$ 的谐振动。

这一种合振动会有忽强忽弱的现象，我们称之为 **拍**，单位时间内振动加强或减弱的次数称为**拍频**。

$$\nu = 2 \times \frac{1}{2 \pi} \left( \frac{\omega_2 - \omega_1}{2} \right) = \nu_2 - \nu_1$$