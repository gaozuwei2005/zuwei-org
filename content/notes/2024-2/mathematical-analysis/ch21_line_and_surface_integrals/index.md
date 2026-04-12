---
title: 数学分析 | Ch21 曲线积分和曲面积分
date: 2025-04-21
summary: 曲线积分（第一型、第二型）、曲面积分（第一型、第二型）
---

## 曲线积分
### 第一型曲线积分（无方向）
- 定义：黎曼和：$\displaystyle \int_L f(x, y, z) \mathrm ds = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i, \eta_i, \zeta_i) \Delta s_i$，其中 $(\xi_i, \eta_i, \zeta_i) \in \Delta s_i$
- 若 $L: \displaystyle \begin{cases} x = x(t) \\\\ y = y(t) \\\\ z = z(t)\end{cases} , \alpha \le t \le \beta$，那么 $\displaystyle \int_L f(x, y, z) \mathrm ds = \int_{\alpha}^{\beta} f(x(t), y(t), z(t)) \sqrt{x'^2(t) + y'^2(t) + z'^2(t)} \mathrm dt$（先将参数方程转换为本性方程，然后求积分，方向向量长度就是对应的变化率，可理解为 $\displaystyle \mathrm ds = \sqrt{x'^2(t) + y'^2(t) + z'^2(t)} \mathrm dt$）
### 第二型曲线积分（有方向）
- 定义：
	- 分量黎曼和：$\displaystyle \int_{L} f(x, y, z) \mathrm dx = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i, \eta_i, \zeta_i) \Delta x_i$，其中 $(\xi_i, \eta_i, \zeta_i) \in \Delta s_i$
	- 黎曼内积和：设向量函数 $\boldsymbol F(x,y,z) = (P(x,y,z), Q(x,y,z), R(x,y,z))$，那么 $$\displaystyle \begin{aligned} &\lim_{\lambda \to 0} \boldsymbol \sum_{i = 1}^n \boldsymbol F(\xi_i, \eta_i, \zeta_i) · \Delta \boldsymbol s_i \\\\ =& \lim_{\lambda \to 0} \sum_{i = 1}^n P(\xi_i, \eta_i, \zeta_i) \Delta x_i + Q(\xi_i, \eta_i, \zeta_i) \Delta y_i + R(\xi_i, \eta_i, \zeta_i) \Delta z_i \\\\ =& \int_L P(x, y, z) \mathrm dx + Q(x, y, z) \mathrm dy + R(x, y, z) \mathrm dz\end{aligned}$$
	- 如果曲线方向改变，积分将取相反数。
	- 闭曲线的积分号要写成 $\displaystyle \oint$，此时积分与起点无关，只与方向有关
- 若 $f(x, y, z)$ 定义域为光滑曲线段 $L: \displaystyle \begin{cases} x = x(t) \\\\ y = y(t) \\\\ z = z(t)\end{cases} , \alpha \le t \le \beta$，且 $L$ 不自交，那么 $\displaystyle \int_L f(x, y, z) \mathrm dx = \int_{\alpha}^{\beta} f(x(t), y(t), z(t)) x'(t) \mathrm dt$.（使用中值定理 $\Delta x(t\_i) = x'(\tau^\*\_i) \Delta t\_i$，然后证明 $\tau\_i$ 和 $\tau\_i^\*$ 很接近）
- 引入方向余弦，第二型曲线积分可以转变为第一型曲线积分：$\displaystyle \int_L P\mathrm dx + Q \mathrm dy + R \mathrm dz = \int_L [P \cos(\boldsymbol \tau, x) + Q \cos(\boldsymbol \tau, y) + R \cos(\boldsymbol \tau, z) ] \mathrm ds$，其中 $\boldsymbol \tau = (x'(s), y'(s), z'(s))$，或 $\displaystyle \int_L \boldsymbol F · \mathrm d\boldsymbol s = \int_{L} \boldsymbol F · \boldsymbol \tau \mathrm ds$.
## 曲面积分
### 第一型曲面积分（无方向）
- 定义：黎曼和：$\displaystyle \iint_S f(x, y, z) \mathrm dS = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i, \eta_i, \zeta_i) \Delta S_i$，其中 $(\xi_i, \eta_i, \zeta_i) \in \Delta S_i$
- 若 $S: z = z(x, y), (x, y) \in \Delta S$，那么 $\displaystyle \iint_S f(x, y, z) \mathrm ds = \iint_D f(x, y, z(x, y)) \sqrt{z_x^2(x, y) + z_y^2(x, y) + 1} \mathrm dx \mathrm dy$（先用中值定理 $\Delta S\_i = \sqrt{z\_x^2(\xi^\*\_i, \eta^\*\_i) + z\_y^2(\xi^\*\_i, \eta^\*\_i) + 1} \mathrm dx \mathrm dy$，然后用连续性证明 $f(\xi\_i, \eta\_i, z(\xi\_i, \eta\_i))$ 和 $f(\xi^\*\_i, \eta^\*\_i, z(\xi^\*\_i, \eta^\*\_i))$ 很接近）
- 若 $L: \displaystyle \begin{cases} x = x(u, v) \\\\ y = y(u, v) \\\\ z = z(u, v)\end{cases} , (u, v) \in D$，那么曲面面积元 $\mathrm dS = \sqrt{EG - F^2} \mathrm du \mathrm dv$
### 第二型曲面积分（有方向）
- 确定在曲面的哪一侧：
	- 若曲面为 $z = f(x, y), (x, y) \in D$，那么令 $\displaystyle p = \frac{\partial f}{\partial x}, q = \frac{\partial f}{\partial y}$，则每一点的法向量为 $\displaystyle (\cos \alpha, \cos \beta, \cos \gamma) = \pm \left ( \frac{-p}{\sqrt{1 + p^2 + q^2}}, \frac{-q}{\sqrt{1 + p^2 + q^2}}, \frac{1}{\sqrt{1 + p^2 + q^2}} \right )$，只要固定前面的正负号，就能确定曲面的一侧。
	- 若曲面为 $L: \displaystyle \begin{cases} x = x(u, v) \\\\ y = y(u, v) \\\\ z = z(u, v)\end{cases} , (u, v) \in D$，那么令 $\displaystyle A = \frac{\partial (y, z)}{\partial (u, v)}, B = \frac{\partial (x, z)}{\partial (u, v)}, C = \frac{\partial (x, y)}{\partial (u, v)}$，则每一点的法向量为 $\displaystyle (\cos \alpha, \cos \beta, \cos \gamma) = \pm \left ( \frac{A}{\sqrt{A^2 + B^2 + C^2}},  \frac{B}{\sqrt{A^2 + B^2 + C^2}}, \frac{C}{\sqrt{A^2 + B^2 + C^2}} \right )$，只要固定前面的正负号，就能确定曲面的一侧。
- 第二型曲面积分：
	- 分量黎曼和：$\displaystyle \iint_S f(x, y, z) \mathrm dx \mathrm dy = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i, \eta_i, \zeta_i) \cos \alpha_i \Delta S_i = \lim_{\lambda \to 0} \sum_{i = 1}^n f(\xi_i, \eta_i, \zeta_i) \cos \Delta D_i$，其中 $(\xi_i, \eta_i, \zeta_i) \in \Delta S_i$，$\Delta D_i$ 是 $\Delta S_i$ 对 $xy$ 平面的投影。
	- 流量：若曲面法向量函数 $\boldsymbol n(x,y,z) = (P(x,y,z), Q(x,y,z), R(x,y,z))$，那么流量为 $\displaystyle \iint_S P(x, y, z) \mathrm dy\mathrm dz + Q(x, y, z) \mathrm dz \mathrm dx + R(x, y, z) \mathrm dx \mathrm dy$
	- 如果换为另一侧计算，那么积分将取相反数。
- 将法向量提出来，就有 $\displaystyle \iint_S P\mathrm dy\mathrm dz + Q\mathrm dz \mathrm dx + R\mathrm dx \mathrm dy = \iint_S (P\cos\alpha + Q\cos\beta + R\cos \gamma) \mathrm dS$，转换为了第一型曲面积分.
- 在连续光滑曲面上，$S： z = z(x, y), (x, y) \in D$，那么 $\displaystyle \iint_S R(x, y, z) \mathrm dx \mathrm dy = \pm \iint_D R(x, y, z(x, y)) \mathrm dx \mathrm dy$
- 光滑曲面 $L: \displaystyle \begin{cases} x = x(u, v) \\\\ y = y(u, v) \\\\ z = z(u, v)\end{cases} , (u, v) \in D$，那么 $\displaystyle \iint_S R(x, y, z) \mathrm dx \mathrm dy = \pm \iint_D R(x(u, v), y(u, v) z(u, v)) \left| \frac{\partial(x, y)}{\partial (u, v)} \right| \mathrm du \mathrm dv$