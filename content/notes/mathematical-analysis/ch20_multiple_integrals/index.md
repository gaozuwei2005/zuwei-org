---
title: 数学分析 | Ch20 重积分
date: 2025-04-18
summary: 定义、性质、化为累次积分、变量代换、曲面面积
---

## 定义
对于有界闭区域 $D$，将任意曲线网将其分成若干可求面积的区域 $\Delta \sigma_1, \Delta \sigma_2, \cdots, \Delta \sigma_n$，任取 $(\xi_i, \eta_i) \in \Delta \sigma_i$，令 $\displaystyle \lambda = \max_{1 \le i \le n} \{ d_i \}$，则
$$\iint_D f(P) \mathrm d\sigma = \iint_D f(x, y) \mathrm dx \mathrm dy = \lim_{\lambda\to 0} f(\xi_i, \eta_i) \Delta \sigma_i$$
## 性质
- 可积性：逐段光滑曲线围成的有界闭区域（或只有若干间断光滑曲线）上的连续函数可积。
- 线性性：满足数乘、加减、积分限加减
- 单调性：若 $f(P) \le g(P)$，那么 $\displaystyle \iint_D f(P) \mathrm d\sigma \le \iint_D g(P) \mathrm d\sigma$.
- 绝对值可积：$\displaystyle \left | \iint_D f(P) \mathrm d\sigma \right | \le \iint_D |f(P)| \mathrm d\sigma$
- 积分中值定理：有界闭区域 $D$ 上的连续函数满足 $\exists P_0 \in D$，满足 $\displaystyle \iint_D f(P) \mathrm d\sigma = f(P_0) |D|$
## 化为累次积分
### 二重积分
- $\displaystyle \iint_D f(x, y) \mathrm dx \mathrm dy = \int_a^b \mathrm dx \int_c^d f(x, y) \mathrm dy = \int_c^d \mathrm dy \int_a^b f(x, y) \mathrm dx$（用平行于坐标轴的直线网来划分区域）
- $\displaystyle \iint_D f(x, y) \mathrm dx \mathrm dy = \int_a^b \mathrm dx \int_{y_1(x)}^{y_2(x)} f(x, y) \mathrm dy = \int_c^d \mathrm dy \int_{x_1(y)}^{x_2(y)} f(x, y) \mathrm dx$（构造延拓函数，使区域变为矩形，且让原区域外的函数值为 $0$）
### 三重积分
- $\displaystyle \iiint_V f(x, y, z) \mathrm dx \mathrm dy \mathrm dz = \int_a^b \mathrm dx \int_c^d \mathrm dy \int_e^f f(x, y, z) \mathrm dz= \int_a^b \mathrm dx \int_{c(x)}^{d(x)} \mathrm dy \int_{e(x, y)}^{f(x, y)} f(x, y, z) \mathrm dz$（此处 $x, y, z$ 的积分顺序可以调换）
- $\displaystyle \iiint_V f(x, y, z) \mathrm dx \mathrm dy \mathrm dz = \int_e^f \mathrm dz \iint_{D_z} f(x, y, z) \mathrm dx \mathrm dy = \iint_D \mathrm dx \mathrm dy \int_{e(x, y)}^{f(x, y)} f(x, y, z) \mathrm dz$（此处各变元的积分顺序可以调换）
## 变量代换
- $\displaystyle \iint_D f(x, y) \mathrm dx \mathrm dy = \iint_{\Delta} f(\varphi(u, v), \psi(u, v)) |J(u, v)| \mathrm du \mathrm dv$，其中 $\displaystyle J(u, v) = \frac{\partial(x, y)}{\partial (u, v)} = \left | \begin{matrix} \displaystyle \frac{\partial \varphi}{\partial u} & \displaystyle \frac{\partial \varphi}{\partial v} \\\\ \displaystyle \frac{\partial \phi}{\partial u} & \displaystyle \frac{\partial \phi}{\partial v} \\\\\end{matrix}\right |$，$J(u, v)$ 可以理解为复合变换之后的面积变化率。
	- 普通变换：$\displaystyle \begin{cases} x = \phi(u, v) \\\\ y = \psi(u, v)\end{cases} \Rightarrow \mathrm dx \mathrm dy = J(u, v) \mathrm du \mathrm dv$
	- 极坐标变换：$\displaystyle \begin{cases} x = r \cos \theta \\\\ y = r \sin \theta\end{cases} \Rightarrow \mathrm dx \mathrm dy = \left | \begin{matrix} \displaystyle \cos \theta & \displaystyle -r \sin \theta \\\\ \displaystyle \sin \theta & \displaystyle r \cos \theta \\\\\end{matrix}\right | \mathrm dr \mathrm d\theta = r \mathrm dr \mathrm d\theta$（圆环面积等于弧长乘半径差）
	- 广义坐标轴变换：$\displaystyle \begin{cases} x = ar \cos \theta \\\\ y = br \sin \theta\end{cases} \Rightarrow \mathrm dx \mathrm dy = \left | \begin{matrix} \displaystyle a\cos \theta & \displaystyle -ar \sin \theta \\\\ \displaystyle b\sin \theta & \displaystyle br \cos \theta \\\\\end{matrix}\right | \mathrm dr \mathrm d\theta = abr \mathrm dr \mathrm d\theta$（椭圆面积）
- $\displaystyle \iiint_V f(x, y, z) \mathrm dx \mathrm dy \mathrm dz = \iiint_{\Delta} f(x(u, v, w), y(u, v, w), z(u, v, w)) \left|\frac{\partial(x, y, z)}{\partial (u, v, w)}\right| \mathrm du \mathrm dv$，$J(u, v, w)$ 可以理解为复合变换之后的面积变化率。
	- 柱坐标变换：$\displaystyle \begin{cases} x = r \cos \theta \\\\ y = r \sin \theta \\\\ z = z\end{cases} \Rightarrow \mathrm dx \mathrm dy \mathrm dz= r \mathrm dr \mathrm d\theta \mathrm dz$（圆环面积等于弧长乘半径差）
	- 球坐标变换：$\displaystyle \begin{cases} x = r \cos \theta \sin \varphi \\\\ y = r \sin \theta \sin\varphi \\\\ z = r \cos \varphi\end{cases} \Rightarrow \mathrm dx \mathrm dy \mathrm dz= -r^2\sin\varphi \mathrm dr \mathrm d\theta \mathrm dz$（球环面积等于长乘宽乘高 $\mathrm dr · r \mathrm d \varphi · r \sin \varphi \mathrm d \theta$）
## 曲面面积
- 若曲面函数为 $z = f(x, y), (x, y) \in D$，那么考虑小区域切平面用投影计算并求和：$\displaystyle S = \lim_{\lambda \to 0} \sum_{i = 1}^n \Delta \sigma_i = \lim_{\lambda \to 0} \sum_{i = 1}^n \frac{\Delta D_i}{|\cos \gamma_i|} = \iint_D \sqrt{1 + f_x^2(x, y) + f_y^2(x, y)} \mathrm dx \mathrm dy$，其中 $\cos\gamma_i$ 是每一点的法向量 $\boldsymbol n_i = \pm(f_x(x, y), f_y(x, y), -1)$ 与 $z$ 轴的夹角余弦 $\displaystyle \cos \gamma_i = \frac{\pm 1}{\sqrt{1 + f_x^2(x, y) + f_y^2(x, y)}}$。
- 若曲面方程为 $\displaystyle \begin{cases} x = x(u, v) \\\\ y = y(u,v) \\\\ z = z(u, v)\end{cases} , (u, v) \in D$，那么我们沿用之前的做法，求每一点的法向量，$\displaystyle \boldsymbol n = \pm\left(\frac{\partial (y, z)}{\partial (u,v)}, \frac{\partial (z, x)}{\partial (u,v)}, \frac{\partial (x, y)}{\partial (u,v)}\right) = \pm \left(A, B, C\right) = \pm(\boldsymbol r_u \times \boldsymbol r_v)$，其中 $\displaystyle \boldsymbol r_u = \left(\frac{\partial x}{\partial u}, \frac{\partial y}{\partial u}, \frac{\partial z}{\partial u}\right),  \boldsymbol r_v = \left(\frac{\partial x}{\partial v}, \frac{\partial y}{\partial v}, \frac{\partial z}{\partial v}\right)$。那么 $\displaystyle S = \iint_U \frac{\mathrm dx \mathrm dy}{|\cos(\boldsymbol n, \boldsymbol z)|} = \iint_D \sqrt{A^2 + B^2 + C^2} \mathrm du \mathrm dv = \iint_D \sqrt{|\boldsymbol r_u|^2  |\boldsymbol r_v|^2 - (\boldsymbol r_u · \boldsymbol r_v)^2} \mathrm du \mathrm dv$