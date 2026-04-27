---
title: 数学分析 | Ch16 偏导数和全微分
date: 2026-04-25
summary: 偏导数、全微分、空间法向量与法平面
---

## 偏导数

偏导数：$f(x,y)$ 在 $(x_0, y_0)$ 关于 $x$ 的偏导数或全微商，固定一个维度。$\displaystyle \left. \frac{\partial f}{\partial x} \right|\_{(x_0, y_0)} = f_x(x_0, y_0) = \lim_{\Delta x \to 0} \frac{\Delta_x f(x_0, y_0)}{\Delta x}$

偏导数是曲面平行于某一条坐标轴曲线的斜率


![](attachments/Pasted%20image%2020260425095222.png)

$f(x) = |x|$ 求导后是 $\operatorname{sgn} x$.
只看那个截面的二维曲线的斜率，所以会分成很多种情况。
二者之一为零，变成绝对值函数。二者均为零，则变成了常值函数 $0$.

只看截出来的曲线的情况，忽视其他的！


二元函数在两点的偏导数存在不能推出函数在该点连续，只能说明曲面上过一点的两条曲线有切线，无法反映曲面的连续性。


**高阶偏导数**：$\displaystyle \frac{\partial^2 u}{\partial x^2}, \frac{\partial^2 u}{\partial x \partial y}, \frac{\partial^2 u}{\partial y \partial x}, \frac{\partial^2 u}{\partial y^2}$，以此类推还有三阶以上等等


**二阶偏导连续则偏导顺序可交换**：若 $f_{xy}(x, y), f_{yx}(x, y)$ 都连续，那么 $f_{xy}(x, y) = f_{yx}(x, y)$
证明：写成极限形式后，可以发现只是求极限顺序不同，由微分中值定理转换成误差量，令 $\Delta x \to 0, \Delta y \to 0$，误差量 $\to 0$）


**复合函数链式法则**：对与可微函数 $u = f(\varphi(s, t), \phi(s, t))$，并且 $\varphi$ 和 $\phi$ 可求偏导，则 $\displaystyle \frac{\partial u}{\partial s} = \frac{\partial f}{\partial x} \frac{\partial x}{\partial s} + \frac{\partial u}{\partial y}\frac{\partial y}{\partial s}$
证明：写成微分形式，然后将 $\Delta x$ 和 $\Delta y$ 换成关于 $s$ 的形式，求极限。

涉及多元中间变量的链式法则：
![](attachments/Pasted%20image%2020260425132026.png)

Computational Graph.
![](attachments/Pasted%20image%2020260425132215.png)

![](attachments/Pasted%20image%2020260425132514.png)

先列计算图，然后代入原来的方程求解。

如果函数以隐函数的形式表示，那么也可以直接对两边求偏导，然后解方程。
![](attachments/Pasted%20image%2020260425140040.png)

如果函数以方程组的形式表示，那么也可以对于某个变元求偏导，然后解方程：
![](attachments/Pasted%20image%2020260425140522.png)
![](attachments/Pasted%20image%2020260425140531.png)

先设出我们所需的目标方程，再对这个方程进行求偏导。

- **方向导数**：多元函数上一点在某射线上的偏导，计算：$\displaystyle \frac{\partial f(P_0)}{\partial l} = \frac{\partial P_0}{\partial x} \cos \alpha + \frac{\partial P_0}{\partial y} \cos \beta + \frac{\partial P_0}{\partial z} \cos \gamma$

利用全微分，然后令 $\Delta x = \rho \cos \alpha, \Delta y = \rho \cos \beta, \Delta z = \rho \cos \gamma$



**泰勒公式**：对于二元函数 $f(x, y)$，对 $(x_0, y_0)$ 进行展开，构造函数 $\varphi(t) = f(x_0 + t \Delta x, y_0 + t \Delta y), t \in [0, 1]$，则
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

微分是自变量的改变量的线性函数。
微分与函数真实改变量之差是比自变量该变量更高阶的无穷小量。
微分是函数该变量的线性主要部分。

**全微分**：若 $\Delta z = A \Delta x + B \Delta y + o (\rho)$ 其中 $A,B$ 与 $\Delta x, \Delta y$ 无关（但可以和 $x, y$ 有关），$\rho = \sqrt{(\Delta x)^2 + (\Delta y)^2}$ 那么函数在 $(x_0, y_0)$ 可微。

本质上可以选择其他等价的距离尺度例如 $|\Delta x| + |\Delta y|$，$\max\\\{|x|, |y|\\\}$，只不过 $\rho = \sqrt{(\Delta x)^2 + (\Delta y)^2}$ 是最自然的欧氏距离。

这里微分与函数的全改变量之差是比 $\rho$ 更高阶的无穷小量。这里的 $\rho$ 可以同时衡量 $\Delta x$ 和 $\Delta y$ 的总变化量。


全微分的式子可以改写成**切平面**：$z = f(x_0, y_0) + A(x - x_0) + B(y - y_0)$ 是 $z = f(x,y)$ 在 $(x_0, y_0)$ 上的切平面。这个平面在 $P_0$ 处和曲面十分密切。


**可微必连续**：若 $f(x, y)$ 在 $(x_0, y_0)$ 可微，则 $f(x, y)$ 在 $(x_0, y_0)$ 连续
证明：$\displaystyle \lim_{\Delta x \to 0 \atop \Delta y \to 0} A \Delta x + B \Delta y + o (\rho) = 0$
可微是比连续更加强的条件。可微不仅要求函数值不跳变，还要求函数在该点附近有稳定的线性近似.

**可微必有各方向偏导**：若 $f(x, y)$ 在 $(x_0, y_0)$ 可微，则 $f(x, y)$ 在 $(x_0, y_0)$ 的两个偏导都存在，且 $\Delta z = f_x(x_0, y_0) \Delta x + f_y(x_0, y_0) \Delta y$
证明：单独令 $\Delta y = 0,\ \Delta x \to 0$ 或 $\Delta x = 0,\ \Delta y \to 0$ 可得
可微是比可求偏导更强的条件。$\mathrm dx = f_x \mathrm dx + f_y\mathrm dy$


**邻域内各方向有连续偏导必可微**：若 $u = f(x, y)$ 在 $(x_0, y_0)$ 的邻域内存在偏导数，且 $f_x(x, y), f_y(x, y)$ 在 $(x_0, y_0)$ 连续，那么 $f(x, y)$ 在 $(x_0, y_0)$ 可微。
证明：用中间量做桥梁 $(x_0,y_0) - (x_0 + \Delta x, y_0) - (x_0 + \Delta x, y_0 + \Delta y)$.
$\Delta f(x_0, y_0)$ 可以用两次微分中值定理来近似，在这个时候，真实增量可以写成 $\Delta f = A\Delta x + B\Delta y + \alpha \Delta x + \beta \Delta y$.

从弱到强：连续、可偏导、可微、各方向有连续偏导
但连续和可偏导之间不存在强弱关系。

$n$ 元函数全微分 $\displaystyle \mathrm du = \frac{\partial u}{\partial x_1} \mathrm d x_1 + \frac{\partial u}{\partial x_2} \mathrm d x_2 + \cdots + \frac{\partial u}{\partial x_n} \mathrm d x_n$.

二阶全微分：是自变量的改变量的二次函数。
![](attachments/Pasted%20image%2020260425115509.png)
n 阶全微分：
![](attachments/Pasted%20image%2020260425115702.png)

复合函数的全微分具有形式不变性：
![](attachments/Pasted%20image%2020260425132915.png)

**做题思路**：

**求全微分**：如果有全微分，那么 $\mathrm dx = f_x \mathrm dx + f_y\mathrm dy$，所以转化为求各方向的偏导。

**问是否有可微性**：
- 首先看有没有偏导，如果没有就肯定没有全微分。
- 然后，我们假设它有全微分，那么就可以写成 $\Delta z = f_x(x_0, y_0) \Delta x + f_y(x_0, y_0) \Delta y + M$，我们需要看后面剩下的余项是否真的是高阶小量 $o(\rho)$ ，因此看 $\displaystyle \lim_{\Delta x \to 0, \Delta y \to 0} \frac{M}{\sqrt{(\Delta x)^2 + (\Delta y)^2}} = 0$ 是否成立.

![](attachments/Pasted%20image%2020260425112129.png)

## 空间切向量与法平面
### 空间曲线

若已知空间曲线的切向量 $\boldsymbol \tau (x_0, y_0, z_0) = (A, B, C)$，那么切线方程就为 $\displaystyle \frac{x - x_0}{A} = \frac{y - y_0}{B} = \frac{z - z_0}{C}$，法平面方程就为 $A (x - x_0) + B (y - y_0) + C (z - z_0) = 0$

若已知曲线参数方程 $L : x = x(t), y = y(t), z = z(t), \alpha \le t \le \beta$，那么切向量就为 $\pm (x'(t_0), y'(t_0), z'(t_0)))$（写出割线向量，除以参数变化量 $\to 0$）

若已知曲线方程 $L : y = y(x), z = z(x)$，可以视作 $x$ 为参数，切向量为 $\pm (1, y'(t_0), z'(t_0))$

若已知曲线方程 $L : \left\\\{ \begin{aligned} F(x, y, z) = 0 \\\\ G(x, y, z) = 0\end{aligned}\right.$，那么分别对 $x$ 求导得到 $\left \\\{ \begin{aligned} F_x + F_y y' + F_z z' = 0 \\\\ G_x + G_y y' + G_z z' = 0 \end{aligned} \right .$，求解线性方程组（可利用 Cramer's Rule）可得到 $y', z'$，则切向量为 $\pm (1, y'(t_0), z'(t_0))$.

### 空间曲面
若已知空间曲面的法向量 $\boldsymbol n(x_0, y_0, z_0) = (A, B, C)$，那么切平面方程就为 $A (x - x_0) + B (y - y_0) + C (z - z_0) = 0$，法线方程就为 $\displaystyle \frac{x - x_0}{A} = \frac{y - y_0}{B} = \frac{z - z_0}{C}$.

若已知曲面方程 $\pi : F(x, y, z) = 0$，我们让 $x = x(t), y = y(t), z = z(t)$ 并对 $t$ 求导，可得到法向量 $\boldsymbol n = \pm (F_x, F_y, F_z)_{P}$


若已知曲面方程 $\pi : z = f(x, y)$，则可化作 $f(x, y) - z = 0$，法向量为 $\boldsymbol{n} = \pm (F_x, F_y, -1)_{P}$


若已知曲面方程 $\displaystyle \pi : \left \\\{ \begin{aligned} x = x(u, v) \\\\ y = y(u, v) \\\\ z = z(u, v) \end{aligned} \right .$，我们将 $x, y$ 视作中间变量，求 $\displaystyle \frac{\partial z}{\partial u}, \frac{\partial z}{\partial v}$，用 Cramer's Rule 可得 $\displaystyle \boldsymbol n = \left . \pm \left ( \frac{\partial (y, z)}{\partial (u, v)},  \frac{\partial (z, x)}{\partial (u, v)}, \frac{\partial (x, y)}{\partial (u, v)}\right ) \right |_P$
