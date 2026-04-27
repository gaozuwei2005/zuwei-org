---
title: 电路基础 | Week 9 正弦量与向量
date: 2026-04-24
summary: 正弦量、相量、电路元件的相量关系
---

正弦量是有正弦或余弦函数形式的信号，正弦电流通常称为交流电。本章主要讨论的是正弦稳态响应。

# 9.2 正弦量

**正弦交流电压**：$v(t) = V_m \sin (\omega t + \psi)$.

**正弦交流电流**：$i(t) = I_m \sin(\omega t + \psi)$

相关概念：
- 振幅 $V_m$、角频率 $\omega$、初相角 $\psi$、辐角 $\omega t+\psi$、
- 周期 $\displaystyle T = \frac{2\pi}{\omega}$、频率 $\displaystyle f = \frac{1}{T} = \frac{\omega}{2\pi}$

**相位差**：对于 $v_1(t) = V_1\sin(\omega_1 t + \psi_1),\ v_2(t) = V_2\sin(\omega_2 t + \psi_2)$

![](attachments/Pasted%20image%2020260424144829.png)

# 9.3 相量

相量是一个复数，能表示正弦量的幅度和相位。但不能体现其角频率。

表达方式：$z = x + jy = r \angle \upphi = r e^{j\upphi}$，分别对应坐标式、极坐标式、指数式
- $r = \sqrt{x^2 + y^2}, \upphi = \arctan \frac{y}{x}$
- $x = r\cos\upphi,\ y = r\sin\upphi$
- $e^{j\upphi} = \cos\upphi + j\sin\upphi$

![](attachments/Pasted%20image%2020260424145711.png)



![](attachments/Pasted%20image%2020260424145803.png)


**相量表示法**：

对于 $v(t) = V_m \cos(\omega t + \phi) = \mathbf{Re}(V_m e^{j(\omega t + \phi)}) = \mathbf{Re}(V_m e^{j\phi} · e^{j\omega t}) = \mathbf{Re}(\overrightarrow{\boldsymbol V} · e^{j \omega t})$

我们记 $\overrightarrow{\boldsymbol V} = V_me^{j\phi} = V_m\angle \phi$ 是正弦量的向量表示法。 $v(t)$ 是 $\overrightarrow{\boldsymbol V} · e^{j \omega t}$ 在实轴上的投影。

- 一阶导数：时域 $\displaystyle \frac{\mathrm dv(t)}{\mathrm dt}$，相当于频域 $j \omega \boldsymbol{V}$.
- 一阶积分：时域 $\displaystyle \int v \mathrm dt$，相当于频域 $\displaystyle \frac{\boldsymbol V}{j \omega}$.

# 9.4 电路元件的相量关系

纯电阻 $R$ ：$\boldsymbol V = R\boldsymbol I$，对应阻抗为 $Z = R$

电感 $L$：$\boldsymbol V = j\omega L\boldsymbol I$，对应阻抗为 $Z = j\omega L$

电容 $C$：$\displaystyle \boldsymbol V = \frac{\boldsymbol I}{j\omega C} = \frac{-j\boldsymbol I}{\omega C}$，对应阻抗为 $\displaystyle Z = \frac{1}{j\omega C}$.


![](attachments/Pasted%20image%2020260424154841.png)

