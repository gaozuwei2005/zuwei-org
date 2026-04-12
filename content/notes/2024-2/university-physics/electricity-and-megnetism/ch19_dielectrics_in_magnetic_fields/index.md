---
title: 大学物理 | Ch19 磁场中的电介质
date: 2025-05-07
summary: 磁介质、磁化、铁磁质
---

## 磁介质
- 磁介质对管内磁感应强度的影响为：相对磁导率 $\displaystyle \mu_r = \frac{B}{B_0}$，其中 $B, B_0$ 是同一电流下，管内为真空和磁介质时的磁感应强度。
- 抗磁质 $\mu_r$ 略小于 $1$，顺磁质 $\mu_r$ 略大于 $1$，铁磁质 $\mu_r$ 远大于 $1$ 且随 $B_0$ 大小发生变化。
- 圆电流的磁矩 $\boldsymbol m = IS \boldsymbol e_n$，其中 $\boldsymbol e_n$ 为圆面积正法线方向的单位矢量。
- 电子轨道磁矩为 $\displaystyle m = IS = \frac{ev}{2 \pi r} \pi r^2 = \frac{evr}{2} = \frac{eL}{2m_e}$.
- 一个分子的磁矩是其中所有电子的轨道磁矩、自旋磁矩以及核的自旋磁矩的矢量和。
- 在正常情况下，抗磁质的分子磁矩为零，顺磁矩的分子磁矩不为零，称为固有磁矩。铁磁质的原子内电子之间存在一种特殊的相互作用使他们有很强的磁性。
## 磁化
- 当顺磁质放入磁场中，磁场力矩会使分子磁矩偏向与外磁场一致（磁化），从而加强了外加磁场。
- 当抗磁质放入磁场中，每个电子和核会对原有磁矩产生与原方向相反的感生磁矩 $\Delta \boldsymbol m$，从而减弱了外加磁场。顺磁质的感生磁矩相比固有磁矩忽略不计。
- 磁介质表面会有一层束缚电流 / 磁化电流通过的现象称为磁化现象。顺磁质产生的磁化电流会加强磁介质的磁场（右手螺旋关系），抗磁质产生的磁化电流会减弱磁介质中的磁场（左手螺旋关系）。
- 磁化强度：$\displaystyle \boldsymbol M = \frac{\sum \boldsymbol m_i}{\Delta V}$，单位体积内分子磁矩的矢量和，单位 $A/ m$.
- 顺磁质和抗磁质的磁化强度随外磁场的增强而增大，近似于外磁场 $\boldsymbol B$ 成正比关系：$\displaystyle \boldsymbol M = \frac{\mu_r - 1}{\mu_0 \mu_r} \boldsymbol B$，其中 $\mu_r$ 是磁介质的相对磁导率。
- 闭合路径包围的总束缚电流等于磁化强度的闭合路径积分 $\displaystyle I = \oint_L \boldsymbol M · \mathrm d \boldsymbol r$.
- **H 的环路定理**：由 $\displaystyle \oint\_L \boldsymbol B · \mathrm d\boldsymbol r = \mu\_0 \left (\sum I\_{0in} + I'\_{in} \right )$，令磁场强度 $\displaystyle \boldsymbol H = \frac{\boldsymbol B}{\mu_0} - \boldsymbol M$，那么得到 $\displaystyle I_{0in} = \oint_L \boldsymbol H · \mathrm d \boldsymbol r$.
- 磁场强度 $\displaystyle \boldsymbol H = \frac{\boldsymbol B}{\mu_0} - \boldsymbol M = \frac{\boldsymbol B}{\mu_0 \mu_r} = \frac{\boldsymbol B}{\mu}$，单位 $A/m$，其中 $\mu$ 为磁介质的磁导率。
## 铁磁质
- 磁化曲线：通过改变 $I$ 得到 $H - B$ 曲线，以表示铁磁质的磁化特点。
- 起始磁化曲线：从没有磁化开始，逐渐增大 $I$ 得到的磁化曲线。
- 磁饱和状态：当 $H$ 到达某一个值之后，$B$ 几乎不再增大的状态，磁化强度达到最大值。
- 磁滞效应：当 $I$  减小为 $0$ 时，$B$ 仍然保持一定的值，称为剩磁。
- 矫顽力：使 $B$ 完全消失的反向电流对应的 $H_c$ 值。
- 磁滞回线：电流正向增大至磁场饱和，正向减小至电流为零，反向增大至磁场为零，反向增大至磁场饱和，反向减小至电流为零，正向增大至磁场为零，正向增大至磁场饱和。
- 软磁材料：$H_c$ 很小，常做变压器和电磁铁铁芯。
- 居里点：使铁磁材料变为顺磁质的高温温度。- 硬磁材料：$H_c$ 很大，常做永久磁体，电子记忆元件。

- 磁畴理论：铁磁体内包含无数个磁畴，磁畴内磁矩取向相同但相互无规则，而外加磁场时，磁矩与外加磁场相近的磁畴扩大，当饱和时所有磁畴指向同一方向。