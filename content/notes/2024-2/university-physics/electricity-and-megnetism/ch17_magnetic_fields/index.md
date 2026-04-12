---
title: 大学物理 | Ch17 磁场
date: 2025-04-18
summary: 磁场、毕奥萨瓦尔定理、安培环路定理
---

## 磁场
- 磁力是运动电荷之间相互作用的表现。
- 产生磁力的场叫做磁场。
- 磁感应强度：若已知检验电荷的速度 $\boldsymbol v$ 和受到的磁力 $\boldsymbol F$，那么 $\boldsymbol B$ 满足 $\boldsymbol F = q \boldsymbol v \times \boldsymbol B$.（洛伦兹力），单位 $T$，特斯拉。
- 磁感应强度满足叠加原理：$\boldsymbol B = \sum \boldsymbol B_i$
- 磁感线：类比电场中引入电场线的方法引入磁感线。
- 磁通量：通过某一面积的磁通量 $\displaystyle \Phi = \int_S \boldsymbol B · \mathrm d\boldsymbol S$，单位 $Wb = T·m^2$，韦伯。
## 毕奥-萨瓦尔定律
- 恒定磁场：电流元 $\boldsymbol I\mathrm d\boldsymbol l$ 产生的磁场。
- 毕奥萨瓦尔定律：电流元在某一点的磁场为 $\displaystyle \mathrm d\boldsymbol B = \frac{\mu_0}{4\pi} \frac{\boldsymbol I\mathrm d\boldsymbol l\times \boldsymbol e_r}{r^2}$，其中真空磁导率 $\displaystyle \mu_0 = \frac{1}{\epsilon_0 c^2} = 4 \pi \times 10^{-7} N/A^2$，那么 $\displaystyle B = \int_l \frac{\mu_0 I \mathrm dl \sin \theta}{4 \pi r^2}$.（用电流求磁场分布）
- 无限长直电流的磁感应强度 $\displaystyle B = \frac{\mu_0 I}{2 \pi r}$.
- 磁通连续定理（磁场的高斯定律）：通过任意封闭曲面的磁通量等于 $0$. $\displaystyle \oint_S \boldsymbol B· \mathrm d\boldsymbol S = 0$，这是因为所有电流元的磁场都是封闭同心圆。
- 磁通连续反映了没有磁极或磁单极子存在.
## 安培环路定理
- 安培环路定理：磁感应强度的线积分等于路径包围的电流之和的 $\mu_0$ 倍：$\displaystyle \oint_C \boldsymbol B· \mathrm d\boldsymbol r = \oint_C B r \mathrm d\alpha = \oint_C \frac{\mu_0 I}{2 \pi r} r \mathrm d\alpha = \mu_0 \sum I_{in}$
	- 这里指的包围是指与环路向铰链的电流，如果铰链多次，则要算多次。
	- 当电流方向与环路绕行方向满足右手螺旋定则时为正，否则为负。
- 当闭合路径不包围电流时，磁感应强度的环路积分为零。
- 无限长圆柱面电流的磁场分布：设计同轴封闭圆柱面，磁场只有切向分量， $\displaystyle B_{ex} = \frac{\mu_0 I}{2 \pi r}, B_{in} = 0$
- 通电螺线环的磁场分布：设计同心圆，那么 $\displaystyle B_{in} = \frac{\mu N I}{2 \pi r}, B_{ex} = 0$.
- 无限大平面电流的磁场分布：设计跨过平面的矩形环路，那么 $\displaystyle B = \frac{\mu_0 \lambda l}{2l} = \frac{\mu_0 \lambda}{2}$.
- 广义安培环路定理：$\displaystyle \oint_C \boldsymbol B · \mathrm d \boldsymbol r = \mu_0\left(I_{c, in} + \epsilon_0 \frac{\partial \boldsymbol E}{\partial t}\right) · \mathrm d \boldsymbol S$
	- 其中后者表示的是变化的电场 $\displaystyle \mu_0 \epsilon_0 \frac{\mathrm d \Omega_e}{\mathrm dt} = \mu_0 \epsilon_0 \frac{\mathrm d}{\mathrm dt} \int_S \boldsymbol E· \mathrm d \boldsymbol S = \mu_0 \epsilon_0 \frac{\partial \boldsymbol E}{\partial t} \int_S · \mathrm d \boldsymbol S$
	- 该定理表明，变化的电场会产生磁场
	- $\displaystyle I_{c, in} + \epsilon_0 \frac{\partial \boldsymbol E}{\partial t}$ 中，前者是环路电流，后者是位移电流，两项之和为全电流。