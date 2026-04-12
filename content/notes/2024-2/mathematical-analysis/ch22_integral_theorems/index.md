---
title: 数学分析 | Ch22 各种积分的联系
date: 2025-04-28
summary: 格林公式、高斯公式、斯托克斯公式、平面线积分与路径无关、空间线积分与路径无关
---

## 各种积分的联系
- **格林公式**：设 $D$ 是逐段光滑闭曲线 $L$ 围成的平面闭区域，且 $P(x, y), Q(x, y)$ 有一阶连续偏导数，那么有 $\displaystyle \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right)\mathrm dx \mathrm dy = \oint_L P \mathrm dx + Q \mathrm dy$，其中 $L$ 的方向是逆时针方向。（先证明凸区域 $\displaystyle \int_c^d \mathrm dy \int_{x_1(y)}^{x_2(y)} \frac{\partial Q}{\partial x} \mathrm dx$ 拆成上下二型曲线积分之差从而得证，然后同理另一维也成立，然后用若干直线把一般区域划分为凸区域）
	- 便于记忆的形式：$\displaystyle \iint_D \begin{vmatrix} \displaystyle \frac{\partial}{\partial x} & \displaystyle \frac{\partial}{\partial y} \\\\ \displaystyle P & \displaystyle Q \\\\ \end{vmatrix} \mathrm dx \mathrm dy = \oint_L P \mathrm dx + Q \mathrm dy$
	- 单独变分的形式：$\displaystyle \oint_L P \mathrm dx = - \iint_D \frac{\partial P}{\partial y} \mathrm dx \mathrm dy, \oint_L Q\mathrm dy = \iint_D \frac{\partial Q}{\partial x} \mathrm dx \mathrm dy$
	- 格林公式建立了平面区域重积分与区域边界第二型积分的联系，可以看作是牛顿-莱布尼兹公式的二维推广。
	- 平面区域面积：$\displaystyle |D| = \iint_D \mathrm dx \mathrm dy = \frac{1}{2} \oint_L x \mathrm dy - y \mathrm dx = \oint_L x \mathrm dy = - \oint_L y \mathrm dx$.
- **高斯公式**：设 $V$ 是分片光滑的双侧封闭曲面 $S$ 围成的空间闭区域，且三元函数 $P, Q, R$ 在 $V, S$ 上有一阶连续偏导数，那么 $\displaystyle \iiint_V \left( \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z} \right) \mathrm dx \mathrm dy \mathrm dz = {\rlap { \mspace{1mu} \boldsymbol{\bigcirc}}{ \rlap {\int}{\ \int}}}\_S P \mathrm dy \mathrm dz + Q \mathrm dz \mathrm dx + R \mathrm dx \mathrm dy$，其中 $S$ 的方向为外侧。（先证明投影面相同的区域将$\displaystyle \iint_D \mathrm dx \mathrm dy \int_{z_1(x, y)}^{z_2(x, y)} \frac{\partial R}{\partial z} \mathrm dz$  拆成上下二型曲面积分而得证，同理另两维也成立，然后用若干光滑曲面将一般区域划分为投影面相同的区域）
	- 转换为第一型曲面积分：$\displaystyle \iiint_V \left( \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z} \right) \mathrm dx \mathrm dy \mathrm dz = {\rlap { \mspace{1mu} \boldsymbol{\bigcirc}}{ \rlap {\int}{\;\int}}}_S (P \cos \alpha + Q \cos \beta + R \cos \gamma) \mathrm dS$，其中 $\boldsymbol n = (\cos \alpha, \cos \beta, \cos \gamma)$ 是 $S$ 指向 $V$ 外部的单位法向量。
	- 高斯公式建立了三维区域重积分与区域边界第二型曲面积分的关系，可以看作是牛顿-莱布尼兹公式的三维推广。
- **斯托克斯公式**：设 $S$ 是光滑曲线 $L$ 围成的光滑曲面，且三元函数 $P, Q, R$ 在 $S, L$ 上有一阶连续偏导数，那么 $\displaystyle \iint_S \left( \frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z} \right) \mathrm dy \mathrm dz + \left( \frac{\partial P}{\partial z} - \frac{\partial R}{\partial x} \right) \mathrm dz \mathrm dx + \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) \mathrm dx \mathrm dy = \oint_L P \mathrm dx + Q \mathrm dy + R \mathrm dz$，其中 $S$ 的侧和 $L$ 的方向按照右手法则，四指为 $L$，大拇指为 $S$。（先证明平面函数积分，用格林公式转化 $\displaystyle \oint_l P(x, y, z(x, y)) \mathrm dx = - \iint_{\sigma_{xy}} \left(\frac{\partial P}{\partial y} - \frac{\partial P}{\partial z} \frac{\cos \beta}{\cos \gamma}\right) \mathrm dx\mathrm dy$，然后利用 $\displaystyle \frac{\partial z}{\partial y} = -\frac{\cos \beta}{\cos \gamma}, \mathrm dx \mathrm dy = \mathrm  dS \cos \gamma \mathrm dz \mathrm dx = \mathrm  dS \cos \beta$ 代换可得 $\displaystyle \iint_S \frac{\partial P}{\partial z}\mathrm dz \mathrm dx -  \frac{\partial P}{\partial y}\mathrm dz \mathrm dy$，然后对另两维同理，相加即可）
	- 分量公式：
		- $\displaystyle \oint_L P \mathrm dx = \iint_S \frac{\partial P}{\partial z}\mathrm dz \mathrm dx -  \frac{\partial P}{\partial y}\mathrm dz \mathrm dy$
		- $\displaystyle \oint_L Q \mathrm dy = \iint_S \frac{\partial Q}{\partial x}\mathrm dx \mathrm dy -  \frac{\partial Q}{\partial z}\mathrm dy \mathrm dz$
		- $\displaystyle \oint_L R \mathrm dz = \iint_S \frac{\partial R}{\partial y}\mathrm dy \mathrm dz -  \frac{\partial R}{\partial y}\mathrm dz \mathrm dx$
	- 便于记忆的形式：$\displaystyle \oint_L P \mathrm dx + Q \mathrm dy + R \mathrm dz = \iint_S \begin{vmatrix} \mathrm dy \mathrm dz & \mathrm dz \mathrm dx & \mathrm dx \mathrm dy \\\\ \displaystyle \frac{\partial}{\partial x} & \displaystyle \frac{\partial}{\partial y} & \displaystyle \frac{\partial}{\partial z} \\\\ P & Q & R \\\\\end{vmatrix} = \iint_S \begin{vmatrix} \cos \alpha & \cos \beta & \cos \gamma \\\\ \displaystyle \frac{\partial}{\partial x} & \displaystyle \frac{\partial}{\partial y} & \displaystyle \frac{\partial}{\partial z} \\\\ P & Q & R \\\\\end{vmatrix} \mathrm dS$
	- 格林公式是斯托克斯公式的特殊情形，当 $\mathrm dz = 0$.
	- 斯托克斯公式建立了空间曲面第二型曲面积分与边界曲线第二型曲线积分的联系，也是牛顿-莱布尼兹公式的三维推广。
## 积分与路径无关
- **平面线积分与路径无关**：假设函数 $P(x, y), Q(x, y)$ 在平面单连通区域 $D$ 上有连续偏导数，那么下列四断言等价：
	- 闭合曲线积分为零：沿 $D$ 中任意逐段光滑闭曲线 $L$ 有 $\displaystyle \oint_L P\mathrm dx + Q \mathrm dy = 0$.
	- 路径无关：沿 $D$ 中任意逐段光滑闭曲线 $L$ 有 $\displaystyle \int_L P\mathrm dx + Q \mathrm dy$ 与路径无关，只与 $L$ 的起点和终点有关。
	- 存在某个定义在 $D$ 上的函数 $u$ 使得其全微分 $\mathrm du = P \mathrm dx + Q \mathrm dy$.
	- 在 $D$ 内每一点有 $\displaystyle \frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}$

证明：
（$1 \to 2$）对于两条不同路径，一条正向另一条反向形成闭曲线，其积分为 $0$，从而两路径积分相等。
（$2 \to 3$）构造 $\displaystyle u(x, y) = \int_{(x_0, y_0)}^{(x, y)} P \mathrm dx + Q \mathrm dy$.，那么对于各变分的偏导，有 $\displaystyle u(x + \Delta x, y) - u(x, y) = \int_{(x, y)}^{(x + \Delta x, y)} P \mathrm dx + Q \mathrm dy = P(\xi, y) \Delta x$，取极限除以变分则为 $P(x, y)$，对于变分 $y$ 同理。
（$3 \to 4$）显然。
（$4 \to 1$）对于任意一个单连通区域内的光滑闭曲线，由格林公式有 $\displaystyle \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right)\mathrm dx \mathrm dy = \oint_L P \mathrm dx + Q \mathrm dy = 0$.
如果 $D$ 是复连通区域，那么 $1, 2, 3$ 是等价的，但是 $4$ 只是必要的。

- **奇点**：使 $\displaystyle \frac{\partial Q}{\partial x} \ne \frac{\partial P}{\partial y}$ 的点。那么
	- 不包含奇点的闭曲线积分为零。
	- 循环常数：环绕某一个奇点的任意两条简单闭曲线 $L_1, L_2$ 正向的积分相等，这个值就是该奇点的循环常数。
	- 环绕某一个节点正向 $n$ 圈，负向 $m$ 圈的闭曲线积分为循环常数的 $(n_1 - n_2)$ 倍。
	- 包含若干个奇点的闭曲线积分为这些奇点的循环常数之和。
	- 循环常数的计算，通常取竖直线和水平线积分之和。
- **空间线积分与路径无关**：假设三元函数 $P, Q, R$ 在空间单连通区域 $V$ 上有连续偏导数，那么下面四断言等价：
	- 闭合曲线积分为零：沿 $V$ 中任意逐段光滑闭曲线 $L$ 有 $\displaystyle \oint_L P \mathrm dx + Q \mathrm dy + R \mathrm dz = 0$.
	- 路径无关：沿 $V$ 中任意逐段光滑闭曲线 $L$ 有 $\displaystyle \int_L P \mathrm dx + Q \mathrm dy + R \mathrm dz$. 与路径无关，只与 $L$ 的起点和终点有关。
	- 存在某个定义在 $V$ 上的函数 $u$ 使得其全微分 $\mathrm du = P \mathrm dx + Q \mathrm dy + R \mathrm dz$.
	- 在 $D$ 内每一点有 $\displaystyle \frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x},  \frac{\partial Q}{\partial z} = \frac{\partial R}{\partial y},  \frac{\partial R}{\partial x} = \frac{\partial P}{\partial z}$，或者写成 $\begin{vmatrix} \boldsymbol i & \boldsymbol j & \boldsymbol k \\\\ \displaystyle \frac{\partial}{\partial x} & \displaystyle \frac{\partial}{\partial y} & \displaystyle \frac{\partial}{\partial z} \\\\ P & Q & R \\\\\end{vmatrix} = \boldsymbol 0$.
证明：与平面的类似，在（$4 \to 1$）的证明过程中需要用到斯托克斯公式。