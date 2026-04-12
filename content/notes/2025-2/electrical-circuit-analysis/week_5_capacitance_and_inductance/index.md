---
title: 电路基础 | Week 5 电容和电感
date: 2026-03-31
summary: 电容、电容的串并联、电感、电感的串并联、积分器、差分器
---

# 6.1 引言

电容和电感是**储能器件**，能够储存和释放能量，具有记忆功能。

# 6.2 电容

电容包括*两个极板 + 中间的电介质*。

**电容器的电容量**：在数值上等于一个导电极板上的电荷量与两个极板之间的电压之比。

电容器的电容量的基本单位是法拉 $(F)$。在电路图中通常用字母 $C$ 表示电容元件。

$$C = \frac{Q}{U}\quad (F)$$

一般电容单位：$F = C/V,\ pF = 10^{-9}F, \mu F = 10^{-6}F$

**平行板电容器的电容**：$\displaystyle C = \frac{\epsilon A}{d}$，其中 $\epsilon$ 是介电常数，$A$ 是极板表面积，$d$ 是板间距离

**电容充放电**：电流与电压参考方向相同，充电；相反时，放电

![](attachments/Pasted%20image%2020260331081921.png)

**电容的伏安关系**：$$i = \frac{\mathrm dq}{\mathrm dt} = C \frac{\mathrm dv}{\mathrm dt} \quad \Longleftrightarrow\quad v = \frac{1}{C} \int_{t_0}^t i \mathrm dt + v(t_0)$$
- $i$ 与 $v$ 的瞬时变化量有关，而与 $v$ 的真实值无关
- 因此电容具有「**隔直流、通交流**」的动态特性。
- **记忆性**：$v$ 不仅与当前的电流有关，还与历史的情况有关。
- **连续性**：$v$ 是连续的，不会产生突变
- 初始电压为 $v(t_0)$ 的电容可等效成一个 $v_s = v(t_0)$ 的电压源和一个初始电压为 $0$ 而电容值相同的电容串联。
- **线性电容**：$C$ 不随电压改变，只由电容的材料决定。

**电容储存能量**：$$w = \frac{1}{2}Cv^2 = \frac{q^2}{2C}\quad (W)$$

# 6.3 电容的串并联

$N$ 个并联电容的等效电容是各个电容之和。$$C = C_1 + C_2 + \cdots + C_n$$
对于并联的电路，各支路的电压相同，各支路电荷量总和等于干路电荷量。

![](attachments/Pasted%20image%2020260331091401.png)

$N$ 个串联电容的等效电容的倒数等于各个电容的倒数之和。$$\frac{1}{C_{eq}} = \frac{1}{C_1} + \frac{1}{C_2} + \cdots + \frac{1}{C_N}$$
对于串联的电路，各电容电荷量相同，各电容电压总和等于总电路的电压。

![](attachments/Pasted%20image%2020260331091526.png)


# 6.4 电感

电感是 *导线绕成的线圈*。当线圈留过电流时则会形成磁场，储存磁场能量，满足右手螺旋定则。

电感：单位电流引起线圈的磁通量。

$$L = \frac{\Psi}{I}\quad (H)$$
螺线管的电感量：$$L = \frac{N^2\mu A}{l}$$
其中 $N$ 是匝数，$l$ 是长度，$A$ 是横截面积，$\mu$ 是磁导率。

**电感的伏安特性**：$$v = L\frac{\mathrm di}{\mathrm dt}\quad \Leftrightarrow \quad i = \frac{1}{L}\int_{t_0}^t v\mathrm dt + i_0$$
- 电感具有**记忆性**，$v$ 与 $i$ 的变化速度有关，与 $i$ 的实际大小无关
- 电感具有**连续性**，不能突变。

**电感的能量**：$$w = \frac{1}{2}Li^2$$
在直流电源下，电容视作为开路，电感视作为短路。

# 6.6 应用实例

## 6.6.1 积分器

![](attachments/Pasted%20image%2020260407081629.png)
将反向放大器的反馈电阻用电容取代后，即可得到**积分器**。

对节点 $a$ 分析，可以得到 $$\frac{-v_i}{R} + C \frac{\mathrm d (-v_o)}{\mathrm dt} = 0 \quad \Rightarrow \quad v_o(t) = - \frac{1}{RC} \int_0^{t} v_i(\tau) \mathrm d\tau$$
## 6.6.2 差分器

![](attachments/Pasted%20image%2020260407082052.png)

将反向放大器的输入阻抗用电容取代后，即可得到**积分器**。

对节点 $a$ 分析，可以得到 $$C \frac{\mathrm d(-v_i)}{\mathrm dt} - \frac{v_o}{R} = 0 \quad \Rightarrow \quad v_o = -RC \frac{\mathrm dv_i}{\mathrm dt}$$


# Conclusion

![](attachments/Pasted%20image%2020260407081308.png)