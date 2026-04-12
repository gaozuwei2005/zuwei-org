---
title: 大学物理 | Ch12 静电场
date: 2025-03-26
summary: 电荷、库仑定律、电场、高斯定律
---


## 电荷
- 同种电荷相斥，异种电荷相吸。电子、质子、中子
- 电量：$Q / q$，单位库(仑)，符号为 $C$，有代数正负
- 电荷的量子性：电荷量是基本单元的整数倍。$e = 1.602 \times 10^{-19} C$。夸克或反夸克的电荷大小缩小到 $\frac{e}{3}$
- 宏观上，电荷可视做连续分布在带电体上。
- 点电荷：带电体的形状和电荷分布无关紧要，将带电体看作带点的点。
- 电荷守恒定律：系统内电荷数的代数和不变。
- 电荷的相对论不变性：电荷的电量与参考系和运动状态无关。
## 库仑定律
- 库仑定律：电荷 $q_2$ 受电荷 $q_1$ 的作用力 $\displaystyle \mathbf F\_{21} = \frac{kq\_1q\_2}{r\_{21}^2} \mathbf{e}\_{r21} = \frac{q\_1q\_2}{4 \pi \epsilon\_0 r\_{21}^2} \mathbf{e}\_{r21}$，其中 $k \approx 9 \times 10^9 N·m^2/C^2, \epsilon_0 \approx 8.85 \times 10^{-12} C^2/(N·m^2)$
- 静电力的叠加原理：电荷系对某一点电荷的总电力为 $\displaystyle F = \sum_{i  = 1}^n \frac{qq_i}{4 \pi \epsilon_0 r_i^2} \mathbf e_{r_i}$
## 电场
- 电场强度：$\displaystyle \mathbf E = \frac{\mathbf F}{q}$，单位 $V/ m = N/C$，那么有 $\mathbf F = q \mathbf E$.
- 电场叠加原理：电荷系在某一点的电场为 $\displaystyle \mathbf E = \sum_{i = 1}^n \mathbf E_i$
- 电力作用方式：$\text{电荷} \Leftrightarrow \text{电场} \Leftrightarrow \text{电荷}$。电场和磁场已被证明是一种客观实在。
- 点电荷电场：$\displaystyle \mathbf E = \frac{q}{4 \pi \epsilon_0 r^2} \mathbf e_r$，正电荷沿径矢方向，负电荷指向中心。电场具有球对称性
- 点电荷系场强：$\displaystyle \mathbf E = \sum_{i = 1}^n \frac{q_i}{4 \pi \epsilon_0 r^2} \mathbf e_{r_i}$，带电体场强 $\displaystyle \mathrm d\mathbf E = \frac{\mathrm dq}{4 \pi \epsilon_0 r^2} \mathbf e_r$，$\displaystyle \mathbf E = \int \frac{\mathrm dq}{4 \pi \epsilon_0 r^2} \mathbf e_r$
- 电偶极子场强：$\displaystyle \boldsymbol E = E_+ + E_- = \frac{q\boldsymbol r_+}{4 \pi \epsilon_0 r_+^3} + \frac{-q\boldsymbol r_-}{4 \pi \epsilon_0 r_-^3} \approx \frac{-q \boldsymbol l}{4 \pi \epsilon_0 r^3} = \frac{- \boldsymbol p}{4 \pi \epsilon_0 r^3}$，其中电矩 $\boldsymbol p = q \boldsymbol l$（从负指向正）
- 电偶极子在均匀电场中所受力矩：$\boldsymbol M = \boldsymbol r_+ \times q\boldsymbol E + \boldsymbol r_- \times (-q \boldsymbol E) = q \boldsymbol l \times \boldsymbol E = \boldsymbol p \times \boldsymbol E$，与支点位置无关。
- 电场线：电场中的假想曲线，曲线疏密代表场强大小，曲线方向代表场强方向。
## 高斯定律
- 电通量：场强对面积的积分 $\displaystyle \mathrm d \Phi_e = \mathbf E \mathrm · d\boldsymbol S = E \mathrm dS \cos \theta$，$\displaystyle \Phi_e = \oint_S \mathbf E · \mathrm d\boldsymbol S$，电通量是电场线条数。
- 高斯定律：静电场内通过任意曲面的电通量等于封闭面内电量除以 $\epsilon_0$：$\displaystyle \Phi_e = \frac{q}{\epsilon_0}$
- 库仑定律和高斯定律二者等价。高斯定律是电场基本规律，库仑定律是关于静电场的规律。
- 常借助电场分布的对称性，利用高斯定律计算场强数值。
- 均匀带电球面：$\displaystyle E_{in} = 0, E_{ex} = \frac{\frac{q}{\epsilon_0}}{4 \pi r^2}= \frac{q}{4 \pi \epsilon_0 r^2}$
- 均匀带电球体：$\displaystyle E_{in} = \frac{\frac{\rho · \frac{4}{3} \pi r^3}{\epsilon_0}}{4 \pi r^2} = \frac{\rho}{3 \epsilon_0} r, E_{ex} = \frac{q}{4 \pi \epsilon_0 r^2}$，其中 $\rho$ 为电荷体密度.
- 无限长均匀带电直线 / 圆柱壳：$\displaystyle E = \frac{\frac{\lambda l}{\epsilon_0}}{2 \pi r l} = \frac{\lambda}{2 \pi \epsilon_0 r}$，方向垂直于带电直线，其中 $\lambda$ 为电荷线密度
- 无限长均匀带电平面：$\displaystyle E = \frac{\frac{\sigma\Delta S}{\epsilon_0}}{2\Delta S} = \frac{\sigma}{2 \epsilon_0}$，方向垂直于带电平面，其中 $\sigma$ 为电荷面密度