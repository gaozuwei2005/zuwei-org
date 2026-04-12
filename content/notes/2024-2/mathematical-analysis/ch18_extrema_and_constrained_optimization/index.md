---
title: 数学分析 | Ch18 极值与条件极值
date: 2025-04-07
summary: 极值、条件极值
---

## 极值
- 定义：在邻域内的函数值都小于等于该点函数值。
- 必要条件：若存在对某变量 $x$ 的偏导，那么必有 $f_x(P_0) = 0$.
- 充分条件：若邻域内存在二阶连续偏导，且 $f_x(P_0) = f_y(P_0) = 0$，那么计算 $\displaystyle D = \left | \begin{matrix} a_{11} & a_{12} \\\\ a_{12} & a_{22} \\\\ \end{matrix}\right |$，则
	- $D > 0$：若 $a_{11} > 0$（或者 $a_{22} > 0$），那么 $f$ 在 $P_0$ 取极大值；若 $a_{11} < 0$（或者 $a_{22} < 0$），那么 $f$ 在 $P_0$ 取极小值。
	- $D < 0$：$P_0$ 不是 $f$ 的极值点。
	- $D = 0$：无法通过此方法判定是否为极值点。
	- 证明方法：利用泰勒公式得到
$$\begin{aligned}
\lim_{\rho \to 0} \Delta f(x_0, y_0) 
	&= \lim_{\rho \to 0} f(x_0 + \Delta x, y_0 + \Delta y) - f(x_0, y_0) \\\\
	&= \lim_{\rho \to 0} \frac{1}{2} d^2 f(x_0, y_0) + o(\rho^2) \\\\
	&= \frac{1}{2} \lim_{\rho \to 0} f_{xx}(x_0, y_0) \Delta x^2 + 
		2 f_{xy} (x_0, y_0) \Delta x \Delta y + 
		f_{yy} (x_0, y_0) \Delta y^2 \\\\
	&= \left [ \begin{matrix} \Delta x & \Delta y \end{matrix} \right] 
		\left [ \begin{matrix} f_{xx} & f_{xy} \\\\ f_{xy} & f_{yy} \end{matrix} \right]
		\left [ \begin{matrix} \Delta x \\\\ \Delta y \end{matrix} \right]
\end{aligned}$$
这是关于 $\Delta x, \Delta y$ 的二次型，分成 $D$ 正定、负定、半正定、半负定等来考虑。
- 最小二乘法：让 $\displaystyle f(a, b) = \sum_{i = 1}^n (a x_i + b - y_i) ^ 2$，对 $a, b$ 求偏导可得 $\begin{cases} (\boldsymbol x, \boldsymbol x) a + (\boldsymbol x, \boldsymbol e) b =  (\boldsymbol x, \boldsymbol y) \\\\ (\boldsymbol x, \boldsymbol e) a + (\boldsymbol e, \boldsymbol e) b = (\boldsymbol e, \boldsymbol y)\end{cases}$，对其求解可得 $\hat a, \hat b$，得到拟合直线。
- 多元函数的最值：要么是内点的极值点，要么是边界点。
## 条件极值
- 拉格朗日乘数法：若要求 $P$ 在满足 $F = 0, G = 0, \cdots$ 等条件下 $f(P)$ 的极值，则定义 $L = f + \lambda_1 F + \lambda_2 G + \cdots$，求解方程组 $\displaystyle \begin{cases} L_x(P) = L_y(P) = \cdots = 0 \\\\ F(P) = G(P) = \cdots = 0 \end{cases}$  的解可得稳定点，再判别其是否为条件极值点即可。
- 若 $P_0$ 是拉格朗日函数的稳定点，那么
	- 若 $\mathrm d^2L(P_0) < 0$，那么 $f$ 在 $P_0$ 取条件极小；
	- 若 $\mathrm d^2L(P_0) > 0$，那么 $f$ 在 $P_0$ 取条件极大；