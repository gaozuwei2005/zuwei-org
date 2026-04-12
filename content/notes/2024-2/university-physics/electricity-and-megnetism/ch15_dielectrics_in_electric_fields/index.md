---
title: 大学物理 | Ch15 静电场中的电介质
date: 2025-04-09
summary: 电介质、电容器
---

## 电介质
- 电介质使板间电压减小的比率 $\displaystyle U = \frac{U_0}{\epsilon_r}$，其中 $\epsilon_r$ 称为**相对介电常数**。真空、氦、空气的$\epsilon_r \approx 1$. 
- 电介质分子分为极性分子和非极性分子。极性分子正负电荷中心不重合，在电场中具有固有电矩和感生电矩，非极性分子在电场中具有感生电矩。感生电矩比固有电矩小得多。
- 电介质的极化：电介质的表面出现面束缚电荷的现象。电介质的极化导致导致板间电压减小。
- **电极化强度**：单位体积内分子的电矩矢量和 $\displaystyle \boldsymbol P = \frac{\sum \boldsymbol p_i}{\Delta V}$，单位 $C / m^2$。对于非极性电介质，有 $\boldsymbol P = n \boldsymbol p$.
- 当电场 $\boldsymbol E$ 不太强时，各向同性电介质的电极化强度与电场强度成正比 $\boldsymbol P = \epsilon_0(\epsilon_r - 1) \boldsymbol E$.
- 面束缚电荷密度取决于电极化强度的表面法向分量 $\displaystyle \sigma = \frac{\mathrm dq}{\mathrm dS} = P \cos \theta = \boldsymbol P · \boldsymbol e_n$.，可以得到 $\displaystyle q_{out} = \oint_S \mathrm d q_{out} = \oint_S \boldsymbol P · \mathrm d\boldsymbol S$，且 $q_{in} = -q_{out}$.
- **介电强度**：电介质的绝缘性能稳定状态能承受的最大电场强度。
- **D 的高斯定律**：任意封闭曲面的电位移通量等于封闭面包围的自由电荷的代数和：$\displaystyle \oint_S (\epsilon_0 \boldsymbol E + \boldsymbol P)·\mathrm d \boldsymbol S = \sum q_{0in}$（由高斯定律和束缚电荷密度公式合并而来），其中**电位移** $\boldsymbol D = \epsilon_0 \boldsymbol E + \boldsymbol P = \epsilon_0 \epsilon_r \boldsymbol E = \epsilon E$，单位 $C / m^2$。
## 电容器
- 两个相对的带等量异号电荷 $\pm Q$ 以及一定电压 $U = \varphi_+ - \varphi_-$ 的金属板。
- **电容**：$\displaystyle C = \frac{Q}{U}$，和电容器本身性质有关，单位法(拉)，$F = C / V$
- 若已知平行板电容器的电荷 $Q$，则 $\displaystyle C = \frac{Q}{U} = \frac{Q}{Ed} = \frac{Q}{\frac{Qd}{\epsilon_0 \epsilon_r S}} = \frac{\epsilon_0 \epsilon_r S}{d}$.（D 的高斯定律）
- 已知电容器的电荷，求电容器的电容，则应当先利用 D 的高斯定律求出任意一点电场强度，再求出两板间电压。
- 孤立导体的电容：孤立导体和无限远处的导体构成的电容器的电容。例如导体球的电容为 $C = 4 \pi \epsilon_0 R$.
- 电容器的并联：电压相等，电量相加，$\displaystyle C = \sum C_i$
- 电容器的串联：电量相等，电压相加：$\displaystyle \frac{1}{C} = \sum \frac{1}{C_i}$
- **电容器的能量**：利用放电时的做功来推导，$\displaystyle E = - \int \mathrm dA = \int_Q^0 \frac{q}{C} \mathrm dq = \frac{1}{2} \frac{Q^2}{C} = \frac{1}{2} Q U$
- **电场能量体密度**：利用平行板电容器的性质，$\displaystyle w_e = \frac{W}{Sd} = \frac{1}{Sd} \frac{(\epsilon ES)^2}{\frac{\epsilon S}{d}} = \frac{1}{2} \epsilon E^2 = \frac{1}{2} \boldsymbol D · \boldsymbol E$
- 能量密度积分求总能量：$\displaystyle W = \int w_e \mathrm dV = \int \frac{\epsilon E^2}{2} \mathrm dV$.