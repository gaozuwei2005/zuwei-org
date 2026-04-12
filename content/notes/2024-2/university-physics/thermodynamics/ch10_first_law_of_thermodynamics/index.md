---
title: 大学物理 | Ch10 热力学第一定律
date: 2025-03-12
summary: 热力学第一定律、热容、绝热过程、循环过程
---

## 热力学第一定律
- 外力对气体做功是宏观功，热传递是微观功或热量
- $\triangle$ **热力学第一定律**：系统内能变化等于外界对系统做功与热传递之和 $\Delta E = A' + Q$
- $\triangle$ 热一的另一表述：系统吸热用于内能增加和对外做功：$Q = \Delta E + A$，其中 $A = -A'$
- 准静态过程：过程的任意时刻，系统无限接近平衡态（微小变化所需时间远大于弛豫时间）
- 平衡态可以用状态参量表示，准静态过程可以用过程曲线表示
- $\triangle$ 无摩擦准静态过程中，系统对外界做功 $\mathrm dA = p\mathrm dV$，$\displaystyle A = \int_{V_1}^{V_2} p \mathrm dV$，为 $p-V$ 图过程曲线下有向面积
## 热容
- 固体和液体吸收热量 $Q = cm\Delta T$，相变时吸收热量为潜热（熔化热、汽化热）
- $\triangle$ 理想气体定体摩尔热容 $\displaystyle C\_{V, m} = \frac{1}{\nu}\left(\frac{\mathrm dQ}{\mathrm dT}\right)\_V = \frac{i}{2}R$，定压摩尔热容 $\displaystyle C\_{p, m} = \frac{1}{\nu}\left(\frac{\mathrm dQ}{\mathrm dT}\right)\_p = \frac{i + 2}{2} R$
- $\triangle$ 迈耶公式 $C_{p, m} - C_{V, m} = R$，比热比 $\displaystyle \gamma = \frac{C_{p, m}}{C_{V,m}} = \frac{i + 2}{i}$
- $\triangle$ 单原子分子 $i = 3$，双原子分子 $i = 5$，多原子分子 $i = 6$
- $\triangle$ 气体内能改变 $\displaystyle \Delta E = \nu C_{V,m} \Delta T$，气体吸收热量 $\displaystyle Q = \nu C_{*, m} \Delta T$
## 绝热过程
- 绝热过程：系统和外界无热量交换条件下的过程。若过程进行很快来不及热量交换，也可近似看作绝热过程。此时内能增量等于外界对气体做功：$Q = 0, \Delta E = A'$.
- $\triangle$ 泊松公式：准静态绝热过程中，需要满足 $\displaystyle \frac{\mathrm dp}{p} + \gamma \frac{\mathrm dV}{V} = 0$，或者 $p V^\gamma = C_1$。用理想气体状态方程可得过程方程： $TV^{\gamma - 1} = C_2$，$p^{\gamma - 1}T^{- \gamma} = C_3$.
- $\triangle$ 准静态绝热过程对外做功 $\displaystyle A = \int_{V_1}^{V_2} p\mathrm dV = \frac{1}{\gamma - 1} (p_1V_1 - p_2V_2)$.
- 绝热线比等温线陡，是因为等温条件下气体会与外界热量交换，分子平均动能不变；而绝热过程中外界做功还会增大气体分子平均动能，从而使得气体压强增大更多。
- 绝热自由膨胀：理想气体在真空中自由膨胀达到新的平衡态的过程。此时过程绝热且不做功，故 $\Delta E = 0$。绝热自由膨胀是非准静态过程，只能说明始末态温度相等。
## 循环过程
- 循环过程：系统经历一系列变化又回到初始状态的整个过程：$\Delta E  = 0, Q = A$.
- 在 $p-V$ 图当中，若气体顺时针循环，则称正循环（热循环）；若气体逆时针循环，则称逆循环（制冷循环）
- 循环过程中工质吸收减去放出的热量 $A = Q_1- Q_2$。相当于 $p - V$ 图上闭合曲线面积。
- $\triangle$ 效率：循环过程净功与高温吸热的比率 $\displaystyle \eta = \frac{A}{Q_1} = 1 - \frac{Q_2}{Q_1}$.
- $\triangle$ 卡诺循环：工质只和两个恒温热库交换热量的循环过程，效率为 $\displaystyle \eta = 1 - \frac{T_2}{T_1}$。在实际生产中，常提高高温热库的温度 $T_2$ 来提高效率。
- 热力学温标：$\displaystyle \frac{Q_1}{Q_2} = \frac{T_1}{T_2}$
- 制冷循环：工质从低温热库吸热和外界对其做的功以热量形式传给高温热库的循环。
- $\triangle$ 制冷系数 $\displaystyle w = \frac{Q_2}{A}  = \frac{Q_2}{Q_1 - Q_2}$，若为卡诺制冷循环，则 $\displaystyle w = \frac{T_2}{T_1 - T_2}$