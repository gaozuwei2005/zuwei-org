---
title: 数学分析 | Ch16 偏导数和全微分
date: 2025-03-28
summary: 偏导数、全微分、空间法向量与法平面
---

## 偏导数
- 偏导数：$f(x,y)$ 在 $(x_0, y_0)$ 关于 $x$ 的偏导数或全微商。$\displaystyle \left. \frac{\partial f}{\partial x} \right|\_{(x\_0, y\_0)} = f\_x(x\_0, y\_0) = \lim\_{\Delta x \to 0} \frac{\Delta\_x f(x\_0, y\_0)}{\Delta x}$
- 偏导数是曲面平行于某一条坐标轴曲线的斜率
- 二元函数在两点的偏导数存在不能推出函数在该点连续，只能说明曲面上过一点的两条曲线有切线
- 高阶偏导数：$\displaystyle \frac{\partial^2 u}{\partial x^2}, \frac{\partial^2 u}{\partial x \partial y}, \frac{\partial^2 u}{\partial y \partial x}, \frac{\partial^2 u}{\partial y^2}$，以此类推还有三阶以上等等
- 若 $f_{xy}(x, y), f_{yx}(x, y)$ 都连续，那么 $f_{xy}(x, y) = f_{yx}(x, y)$（写成极限形式后，由微分中值定理转换成误差量，令 $\Delta x \to 0, \Delta y \to 0$，误差量 $\to 0$）
- 复合函数链式法则：对于 $u = f(\varphi(s, t), \phi(s, t))$，则 $\displaystyle \frac{\partial u}{\partial s} = \frac{\partial f}{\partial x} \frac{\partial x}{\partial s} + \frac{\partial u}{\partial y}\frac{\partial y}{\partial s}$
- **方向导数**：多元函数上一点在某射线上的偏导，计算：$\displaystyle \frac{\partial f(P_0)}{\partial l} = \frac{\partial P_0}{\partial x} \cos \alpha + \frac{\partial P_0}{\partial y} \cos \beta + \frac{\partial P_0}{\partial z} \cos \gamma$（令 $\Delta x = \rho \cos \alpha, \Delta y = \rho \cos \beta, \Delta z = \rho \cos \gamma$，并对 $\rho$ 求导 即可）
- **泰勒公式**：对于二元函数 $f(x, y)$，对 $(x_0, y_0)$ 进行展开，构造函数 $\varphi(t) = f(x_0 + t \Delta x, y_0 + t \Delta y), t \in [0, 1]$，则
$$\begin{aligned}
\frac{\mathrm d^n}{\mathrm d t^n} f(x_0 + t \Delta x, y_0 + t \Delta y) &= \sum_{k = 0}^n \binom{n}{k} \frac{\partial^n f}{\partial x^k \partial y^{n - k}} (\Delta x)^k (\Delta y)^{n - k} \\\\
&= \left (\frac{\partial}{\partial x} \Delta x + \frac{\partial}{\partial y} \Delta y \right)^n f(x_0 + t \Delta x, y_0 + \Delta y)
\end{aligned}$$
故泰勒公式为
$$\begin{aligned}
f(x_0 + \Delta x, y_0 + \Delta y) =& \sum_{k = 0}^n \frac{1}{k!} \left (\frac{\partial}{\partial x} \Delta x + \frac{\partial}{\partial y} \Delta y \right)^n f(x_0, y_0) + \\\\
& \frac{1}{(n + 1)!} \left(\frac{\partial}{\partial x} \Delta x + \frac{\partial}{\partial y} \Delta y \right)^{n + 1} f(x_0 + \theta \Delta x, y_0 + \theta \Delta y), (\theta \in (0, 1)) \\\\
=& f(x_0, y_0) + \\\\
& f_x(x_0, y_0) \Delta x + f_y(x_0, y_0) \Delta y + \\\\
& \frac{1}{2} \left[ f_{xx}(x_0, y_0) \Delta x^2 + 2 f_{xy}(x_0, y_0) \Delta x \Delta y + f_{yy} (x_0, y_0) \Delta y^2 \right] + \cdots
\end{aligned}$$
## 全微分
- 全微分：若 $\Delta z = A \Delta x + B \Delta y + o (\rho)$ 其中 $A,B$ 与 $\Delta x, \Delta y$ 无关，$\rho = \sqrt{(\Delta x)^2 + (\Delta y)^2}$ 那么函数在 $(x_0, y_0)$ 可微。
- 切平面：$f(x_0, y_0) + A(x - x_0) + B(y - y_0) = 0$ 是 $z = f(x,y)$ 在 $(x_0, y_0)$ 上的切平面。
- 若 $f(x, y)$ 在 $(x_0, y_0)$ 可微，则 $f(x, y)$ 在 $(x_0, y_0)$ 连续（$\displaystyle \lim_{\Delta x \to 0 \atop \Delta y \to 0} A \Delta x + B \Delta y + o (\rho) = 0$）
- 若 $f(x, y)$ 在 $(x_0, y_0)$ 可微，则 $f(x, y)$ 在 $(x_0, y_0)$ 的两个偏导都存在，且 $\Delta z = f_x(x_0, y_0) \Delta x + f_y(x_0, y_0) \Delta y$（单独令 $\Delta x \to 0$ 或 $\Delta y \to 0$ 可得）
- $n$ 元函数全微分 $\displaystyle \mathrm du = \frac{\partial u}{\partial x_1} \mathrm d x_1 + \frac{\partial u}{\partial x_2} \mathrm d x_2 + \cdots + \frac{\partial u}{\partial x_n} \mathrm d x_n$.
- 若 $u = f(x, y)$ 在 $(x_0, y_0)$ 的邻域内存在偏导数，且 $f_x(x, y), f_y(x, y)$ 在 $(x_0, y_0)$ 连续，那么 $f(x, y)$ 在 $(x_0, y_0)$ 可微。（ $\Delta f(x_0, y_0)$ 可以用两次微分中值定理来近似，$\Delta f(x_0, y_0) = (A + \alpha) \Delta x + (B + \beta) \Delta y$，证明误差量 $\alpha \Delta x + \beta \Delta y \to 0$）
## 空间切向量与法平面
### 空间曲线
- 若已知空间曲线的切向量 $\boldsymbol \tau (x_0, y_0, z_0) = (A, B, C)$，那么切线方程就为 $\displaystyle \frac{x - x_0}{A} = \frac{y - y_0}{B} = \frac{z - z_0}{C}$，法平面方程就为 $A (x - x_0) + B (y - y_0) + C (z - z_0) = 0$
- 若已知曲线参数方程 $L : x = x(t), y = y(t), z = z(t), \alpha \le t \le \beta$，那么切向量就为 $\pm (x'(t_0), y'(t_0), z'(t_0)))$（写出割线向量，除以参数变化量 $\to 0$）
- 若已知曲线方程 $L : y = y(x), z = z(x)$，可以视作 $x$ 为参数，切向量为 $\pm (1, y'(t_0), z'(t_0))$
- 若已知曲线方程 $L : \begin{cases} F(x, y, z) = 0 \\\\ G(x, y, z) = 0\end{cases}$，那么分别对 $x$ 求导得到 $\begin{cases} F_x + F_y y' + F_z z' = 0 \\\\ G_x + G_y y' + G_z z' = 0 \end{cases}$，求解线性方程组（可利用 Cramer's Rule）可得到 $y', z'$，则切向量为 $\pm (1, y'(t_0), z'(t_0))$.
### 空间曲面
- 若已知空间曲面的法向量 $\boldsymbol n(x_0, y_0, z_0) = (A, B, C)$，那么切平面方程就为 $A (x - x_0) + B (y - y_0) + C (z - z_0) = 0$，法线方程就为 $\displaystyle \frac{x - x_0}{A} = \frac{y - y_0}{B} = \frac{z - z_0}{C}$.
- 若已知曲面方程 $\pi : F(x, y, z) = 0$，我们让 $x = x(t), y = y(t), z = z(t)$ 并对 $t$ 求导，可得到法向量 $\boldsymbol n = \pm (F_x, F_y, F_z)_{P}$
- 若已知曲面方程 $\pi : z = f(x, y)$，则可化作 $f(x, y) - z = 0$，法向量为 $\boldsymbol{n} = \pm (F_x, F_y, -1)_{P}$
- 若已知曲面方程 $\displaystyle \pi : \begin{cases}  x = x(u, v) \\\\ y = y(u, v) \\\\ z = z(u, v) \end{cases}$，我们将 $x, y$ 视作中间变量，求 $\displaystyle \frac{\partial z}{\partial u}, \frac{\partial z}{\partial v}$，用 Cramer's Rule 可得 $\displaystyle \boldsymbol n = \left . \pm \left ( \frac{\partial (y, z)}{\partial (u, v)},  \frac{\partial (z, x)}{\partial (u, v)}, \frac{\partial (x, y)}{\partial (u, v)}\right ) \right |_P$