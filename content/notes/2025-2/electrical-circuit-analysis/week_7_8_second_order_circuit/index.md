---
title: 电路基础 | Week 7+8 二阶电路
date: 2026-04-17
summary: 初始值和终值的确定，无源激励 RLC 串联电路
---


# 8.1 引言

需要用二阶微分方程表征其特征的电路就叫二阶电路。

通常会有两个（无法等效合并的）非线性元件。

![](attachments/Pasted%20image%2020260414091346.png)

# 8.2 初始值和终值的确定

需要获得 $\displaystyle v(0), i(0), \frac{\mathrm dv(0)}{\mathrm dt}, \frac{\mathrm di(0)}{\mathrm dt}, i(\infty), v(\infty)$.

对于电容 $v_c(0^+) = v_c(0^-)$；对于电感 $i_L(0^+) = i_L(0^-)$.

对于电感，由 $\displaystyle v = L\frac{\mathrm di}{\mathrm dt}$  得到 $\displaystyle \frac{\mathrm di(0)}{\mathrm dt} = \frac{v(0)}{L}$.

对于电容，由 $\displaystyle i = C\frac{\mathrm dv}{\mathrm dt}$ 得到 $\displaystyle \frac{\mathrm dv(0)}{\mathrm dt} = \frac{i(0)}{C}$.

# 8.3 无源激励 RLC 串联电路

![](attachments/Pasted%20image%2020260417153254.png)

列 KVL 可得二阶常系数齐次微分方程 $$Ri + L \frac{\mathrm di}{\mathrm dt} + \frac{1}{C}\int_{-\infty}^t i \mathrm dt = 0 \quad \Rightarrow \quad \frac{\mathrm d^2 i}{\mathrm dt^2} + \frac{R}{L} \frac{\mathrm di}{\mathrm dt} + \frac{i}{LC} = 0\quad \text{或}\quad \frac{\mathrm d^2 v}{\mathrm dt^2} + \frac{R}{L}\frac{\mathrm dv}{\mathrm dt} + \frac{v}{LC} = 0$$
特征方程 $$s^2 + \frac{R}{L}s + \frac{1}{LC} = 0$$
令 $\displaystyle \alpha = \frac{R}{2L}\ (Np/s),\ \omega_0 = \sqrt{\frac{1}{LC}}\ (rad/s)$，则 $$s_{1,2} = -\alpha \pm \sqrt{\alpha^2 - \omega_0^2}\quad (Np/s)$$
- **过阻尼** $\alpha > \omega_0$：则 $s_{1,2} = -\alpha \pm \sqrt{\alpha^2 - \omega_0^2}$，得到 $i(t) = A_1e^{s_1t} + A_2e^{s_2t}$，用初值列方程得到系数 $A_1, A_2$ 即可
- **临界阻尼** $\alpha = \omega_0$：则 $s = -\alpha$，得到 $i(t) = (A_2 + A_1t) e^{-\alpha t}$，用初值列方程得到系数 $A_1, A_2$ 即可
- **欠阻尼** $\alpha < \omega_0$：则令阻尼频率 $\omega_d = \sqrt{\omega_0 - \alpha^2}$，那么 $s_{1,2} = -\alpha \pm j \omega_d$，得到 $i(t) = A_1 e^{s_1t} + A_2e^{s_2t} = e^{-at} (A_1\cos\omega_dt + A_2\sin\omega_dt) = K e^{-at} \cos(\omega_dt + \theta)$，其中 $\displaystyle K = \sqrt{A_1^2 + A_2^2},\ \theta = -\arctan \frac{A_2}{A_1}$.

![](attachments/Pasted%20image%2020260417154924.png)

