---
title: 解析几何 | Cheatsheet
date: 2026-01-13
summary: 【最后通牒】共线与共面、向量的乘积、平面与直线的方程、点线面的关系、曲面、二次曲面、直母线、二次曲线的性质
---


# 共线与共面
- 三个点 $(x_1, y_1, z_1), (x_2, y_2, z_2),  (x_3, y_3, z_3)$ 共线 $\Leftrightarrow$ $\displaystyle \frac{x_2 - x_1}{x_3 - x_1} = \frac{y_2 - y_1}{y_3 - y_1} = \frac{z_2 - z_1}{z_3 - z_1}$
- 三个非零向量 $\\\{x_1, y_1, z_1\\\}, \\\{x_2, y_2, z_2\\\},  \\\{x_3, y_3, z_3\\\}$ 共面 $\Leftrightarrow$ $\begin{vmatrix}x_1&y_1&z_1\\\\x_2&y_2&z_2\\\\x_3&y_3&z_3\\\\\end{vmatrix}=0$
- 四个点 $(x_1, y_1, z_1), (x_2, y_2, z_2),  (x_3, y_3, z_3), (x_4, y_4, z_4)$ 共面 $\Leftrightarrow$ $\begin{vmatrix}x_2-x_1&y_2-y_1&z_2-z_1\\\\x_3-x_1&y_3-y_1&z_3-z_1\\\\x_4-x_1&y_4-y_1&z_4-z_1\\\\\end{vmatrix}=0$

# 向量的乘积
- 柯西不等式：$\displaystyle \left(\sum_{i = 1}^n a_i b_i\right)^2 \le \sum_{i = 1}^n a_i^2 \sum_{i = 1}^n b_i^2$
- $(\boldsymbol a \times \boldsymbol b)^2 + (\boldsymbol a·\boldsymbol b)^2 = |\boldsymbol a|^2 |\boldsymbol b|^2$
- $\boldsymbol a \times \boldsymbol b = \begin{vmatrix}\boldsymbol i & \boldsymbol j & \boldsymbol k \\\\ x_1 & y_1 & z_1 \\\\ x_2 & y_2 & z_2\end{vmatrix}$.
- 用坐标计算混合积：![](attachments/Pasted-image-20250923113325.png)

# 平面与直线的方程

**平面的方程**：
- 向量式方程：$\boldsymbol r = \boldsymbol r_0 + u \boldsymbol a + v \boldsymbol b$
- 点位式方程：$(\boldsymbol r - \boldsymbol r_0, \boldsymbol a, \boldsymbol b) = \begin{vmatrix} x - x_0 & y - y_0 & z - z_0 \\\\ x_1 & y_1 & z_1 \\\\ x_2 & y_2 & z_2 \end{vmatrix} = 0$
- 截距式方程：$\displaystyle \frac{x}{a} + \frac{y}{b} + \frac{z}{c} = 1\ (abc \ne 0)$
- 向量式点法式方程：$\boldsymbol n · (\boldsymbol r - \boldsymbol r_0) = 0$
- 坐标式点法式方程：$A (x - x_0) + B(y - y_0) + C(z - z_0) = 0$
- 向量式法式方程：$\boldsymbol n_0 · (\boldsymbol r - p \boldsymbol n_0) = 0$，即 $\boldsymbol n^0·\boldsymbol r - p = 0$
- 坐标式法式方程：$x \cos \alpha + y \cos \beta + z \cos \gamma - p = 0$

**直线的方程**：
- 向量式参数方程：$\boldsymbol r = \boldsymbol r_0 + t \boldsymbol v$
- 坐标式参数方程：$\begin{cases} x = x_0 + t X \\\\ y = y_0 + tY \\\\ z = z_0 + tZ \end{cases}$
- 标准方程 / 对称式方程 / 点向式方程：$\displaystyle \frac{x - x_0}{X} = \frac{y - y_0}{Y} = \frac{z - z_0}{Z}$
- 一般方程：$\begin{cases} A_1x + B_1y + C_1z + D_1 = 0 \\\\ A_2x + B_2y + C_2z + D_2 = 0 \end{cases}$
- 射影式方程：$\begin{cases}x = az + c \\\\ y = bz + d\end{cases}$

# 点、直线、平面的关系

**点与平面一般方程的距离**：先将一般方程转法式方程（除以法式化因子），再计算离差，则 $$\begin{aligned}d &= |\delta| = |x \cos \alpha + y \cos \beta + z \cos \gamma - p|\\\\&=\frac{|Ax_0+By_0+Cz_0+D|}{\sqrt{A^2+B^2+C^2}}\end{aligned}$$

| 面面关系 | 判断方法（向量）                                          | 判断方法（参数）                                                                                |
| ---- | ------------------------------------------------- | --------------------------------------------------------------------------------------- |
| 相交   | $\boldsymbol n_1 \nparallel \boldsymbol n_2$      | $A_1 : B_1 : C_1 \ne A_2 : B_2 : C_2$                                                   |
| 平行   | $\boldsymbol n_1 // \boldsymbol n_2, p_1 \ne p_2$ | $\displaystyle \frac{A_1}{A_2} = \frac{B_1}{B_2} = \frac{C_1}{C_2} \ne \frac{D_1}{D_2}$ |
| 重合   | $\boldsymbol n_1 // \boldsymbol n_2,\ p_1 = p_2$  | $\displaystyle \frac{A_1}{A_2} = \frac{B_1}{B_2} = \frac{C_1}{C_2} = \frac{D_1}{D_2}$   |
| 垂直   | $\boldsymbol n_1 · \boldsymbol n_2 = 0$           | $A_1A_2 + B_1B_2 + C_1C_2 = 0$                                                          |

**两平面夹角**：平面夹角一般取 $[0, \pi]$，有两种互补的角，其余弦值互为相反数 $$\pm \cos \angle(\boldsymbol n_1, \boldsymbol n_2) = \pm \frac{A_1A_2 + B_1B_2 + C_1C_2}{\sqrt{A_1^2+B_1^2+C_1^2}\sqrt{A_2^2+B_2^2+C_2^2}}$$

| 线面关系 | 判断方法（向量）                                                         | 判断方法（参数）                                         |
| ---- | ---------------------------------------------------------------- | ------------------------------------------------ |
| 相交   | $\boldsymbol v \not\perp \boldsymbol n$                          | $AX+BY+CZ\ne0$                                   |
| 平行   | $\boldsymbol v \perp \boldsymbol n,\ \boldsymbol M_0 \notin \Pi$ | $AX+BY+CZ = 0$<br>$Ax_0 + By_0 + Cz_0 + D \ne 0$ |
| 线在面上 | $\boldsymbol v \perp \boldsymbol n,\ \boldsymbol M_0 \notin \Pi$ | $AX+BY+CZ = 0$<br>$Ax_0 + By_0 + Cz_0 + D = 0$   |
| 垂直   | $\boldsymbol v // \boldsymbol n$                                 | $A_1 : B_1 : C_1 = A_2 : B_2 : C_2$              |

**求直线和平面夹角**：一般取 $\displaystyle  0 \le \varphi \le \frac{\pi}{2}$，那么 $$\displaystyle \begin{aligned}\sin \varphi &= |\cos \angle(\boldsymbol v, \boldsymbol n)|\\\\&= \frac{|AX+BY+CZ|}{\sqrt{A^2+B^2+C^2}·\sqrt{X^2+Y^2+Z^2}}\end{aligned}$$
**点线距离**：给定直线的始点 $\boldsymbol M_0 (x_0, y_0, z_0)$ 和方向向量 $\boldsymbol v\\\{X, Y, Z\\\}$，那么点 $\boldsymbol M(x_1, y_1, z_1)$ 到直线的距离可以通过计算 $\overrightarrow{M_1M_0}$ 与 $\boldsymbol v$ 的叉积得到：$$d = \frac{|\overrightarrow{M_1M_0} \times \boldsymbol v|}{|\boldsymbol v|} $$
两直线 $l_1 : \boldsymbol r = M_1 + t \boldsymbol v_1$，$l_2 : \boldsymbol r = M_2 + t \boldsymbol v_2$，它们的关系取决于 $\boldsymbol v_1,\ \boldsymbol v_2,\ \overrightarrow{M_1M_2}$.

| $l_1,\ l_2$ 位置关系 | $\boldsymbol v_1,\ \boldsymbol v_2,\ \overrightarrow{M_1M_2}$ 位置关系            | 计算方法                                                                                                                                                                                            |
| ---------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 共面               | 共面                                                                            | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2}) = \left\lvert\begin{matrix} x_2  - x_1 & y_2 - y_1 & z_2 - z_1 \\\\ X_1 & Y_1 & Z_1 \\\\ X_2 & Y_2 & Z_2 \end{matrix}\right\rvert = 0$ |
| 相交               | 三向量共面，且 $\boldsymbol v_1, \boldsymbol v_2$ 相交                                 | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1 \ne X_2:Y_2:Z_2.$                                                                                                  |
| 平行               | 三向量共面，且 $\boldsymbol v_1 // \boldsymbol v_2$，但与 $\overrightarrow{M_1M_2}$ 不平行 | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1$ $=$ $X_2:Y_2:Z_2$ $\ne$ $(x_2-x_1):(y_2-y_1):(z_2-z_1)$                                                           |
| 重合               | 三向量共面，且 $\boldsymbol v_1 // \boldsymbol v_2 // \overrightarrow{M_1M_2}$       | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1$ $=$ $X_2:Y_2:Z_2$ $=$ $(x_2-x_1):(y_2-y_1):(z_2-z_1)$                                                             |
| 异面               | 异面                                                                            | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2}) \ne 0$                                                                                                                             |

**两直线夹角余弦**：为其方向向量的夹角余弦 $$\pm\cos\angle(l_1, l_2)
= \pm
\frac{X_1 X_2 + Y_1 Y_2 + Z_1 Z_2}
{\sqrt{X_1^2 + Y_1^2 + Z_1^2}\,\sqrt{X_2^2 + Y_2^2 + Z_2^2}}$$
因此若两直线垂直，等价于 $X_1 X_2 + Y_1 Y_2 + Z_1 Z_2 = 0$.

**异面直线距离公式**：$\displaystyle d = \frac{\left|\overrightarrow{M_1M_2} · (\boldsymbol v_1 \times \boldsymbol v_2)\right|}{\left|\boldsymbol v_1 \times \boldsymbol v_2\right|} = \frac{\left|(\overrightarrow{M_1M_2}, \boldsymbol v_1, \boldsymbol v_2)\right|}{\left|\boldsymbol v_1 \times \boldsymbol v_2\right|}$

**异面直线公垂线的方程**：$\begin{cases}\pi_1 :\begin{vmatrix}x - x_1 & y - y_1 & z - z_1 \\\\X_1 & Y_1 & Z_1 \\\\X & Y & Z\end{vmatrix}= 0\\\\\pi_2 :\begin{vmatrix}x - x_2 & y - y_2 & z - z_2 \\\\X_2 & Y_2 & Z_2 \\\\X & Y & Z\end{vmatrix}= 0\end{cases}$

# 曲面

**柱面方程**：给定准线方程 $\begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和方向向量 $\boldsymbol r\\\{X, Y, Z\\\}$，那么母线族方程为 $$\frac{x - x_0}{X} = \frac{y - y_0}{Y} = \frac{z - z_0}{Z},\ s.t. \begin{cases}F_1(x_0, y_0, z_0) = 0 \\\\ F_2(x_0, y_0, z_0) = 0\end{cases}$$
消去 $x_0, y_0, z_0$ 即可得到柱面方程是三元方程 $F(x, y, z) = 0$.

**圆柱面方程**：给定中轴线 $\boldsymbol v\\\{X, Y, Z\\\}$、轴线上一点 $\boldsymbol M_0(x_0, y_0, z_0)$ 以及半径 $r$，那么柱面方程为 $$r = \frac{|\overrightarrow{M_1M_0} \times \boldsymbol v|}{|\boldsymbol v|}$$
**锥面的方程**：给定准线方程 $\begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和顶点 $\boldsymbol A(x_0, y_0, z_0)$，那么母线族方程为 $$\frac{x - x_0}{x - x_1} = \frac{y - y_0}{y - y_1} = \frac{z - z_0}{z - z_1},\ s.t. \begin{cases}F_1(x_1, y_1, z_1) = 0 \\\\ F_2(x_1, y_1, z_1) = 0\end{cases}$$
消去 $x_1, y_1, z_1$ 即可得到柱面方程是三元方程 $F(x, y, z) = 0$.

**圆锥面的方程**：给定顶点 $\boldsymbol A(x_0, y_0, z_0)$、轴线法向量 $\boldsymbol n$，以及母线与轴线的夹角（半顶角）为 $\alpha$，那么圆锥面方程为 $$\cos \alpha = \pm \frac{\overrightarrow{AM} ·\boldsymbol n}{|\overrightarrow{AM}|·|\boldsymbol n|}$$
**旋转曲面的方程**：给定母线方程 $\Gamma : \begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和旋转轴 $\displaystyle l : \frac{x-x_0}{X} = \frac{y-y_0}{Y} = \frac{z-z_0}{Z}$，我们取母线上一点 $\boldsymbol M_1 (x_1,y_1,z_1)$，那么纬圆族的方程为 $$\begin{cases} X(x - x_1) + Y(y - y_1) + Z(z - z_1) = 0 \\\\ (x - x_0)^2 + (y - y_0)^2 + (z - z_0)^2 = (x_1 - x_0)^2 + (y_1 - y_0)^2 + (z_1 - z_0)^2 \end{cases},\ s.t.  \begin{cases}F_1(x_1, y_1, z_1) = 0 \\\\ F_2(x_1, y_1, z_1) = 0\end{cases}$$
消去 $x_1, y_1, z_1$ 即可得到三元方程 $F(x, y, z) = 0$.

如果旋转曲面上的母线，且旋转轴为坐标轴的时候，它的方程可以简化为二元函数。
- 如 $F(x, \pm \sqrt{y^2 + z^2}) = 0$ 绕着 $x$ 轴旋转。
- 如果绕着某个坐标轴旋转，只需将曲线方程保留和旋转轴同名坐标，其余两坐标平方和的正负平方根代替方程中的另一个坐标。

# 二次曲面

| 类型        | 椭球面                                                                                                                                                                                                                  | 单叶双曲面                                                                                                                                                                                                            | 双叶双曲面                                                                                                                                                                                                            | 椭圆抛物面                                                                       | 双曲抛物面                                                                       |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 标准方程      | $\displaystyle \frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1$<br>$(a,\ b,\ c>0)$                                                                                                                           | $\displaystyle \frac{x^2}{a^2} + \frac{y^2}{b^2} - \frac{z^2}{c^2} = 1$<br>$(a,\ b,\ c>0)$<br>三个参数中两正一负                                                                                                          | $\displaystyle \frac{x^2}{a^2} + \frac{y^2}{b^2} - \frac{z^2}{c^2} = -1$<br>$(a,\ b,\ c>0)$<br>三个参数中两负一正                                                                                                         | $\displaystyle \frac{x^2}{a^2} + \frac{y^2}{b^2} = \pm 2z$<br>$(a,\ b > 0)$ | $\displaystyle \frac{x^2}{a^2} - \frac{y^2}{b^2} = \pm 2z$<br>$(a,\ b > 0)$ |
| 坐标面平行平面截线 | 例如与 $z = h$ 截取面，则截出的的曲线为 $$\begin{cases} \emptyset,& \lvert h\rvert > c \\\\(0, 0, \pm c), & \lvert h\rvert = c \\\\ 椭圆, & \lvert h\rvert < c\end{cases}$$                                                               | $x = x_0$：$\lvert x_0\rvert = a$ 截出交于 $(\pm a, 0, 0)$ 的双直线；其余均为双曲线<br>$y = y_0$：$\lvert y_0\rvert = b$ 截出交于 $(0, \pm b, 0)$ 的双直线；其余均为双曲线<br>$z = z_0$：椭圆                                                         | $x = x_0, y = y_0$ 截出的都是双曲线<br>$z = h$ 截出的曲线为<br>$$\begin{cases} \emptyset,& \|h\| < c \\\\(0, 0, \pm c), & \|h\| = c \\\\ 椭圆, & \|h\| > c\end{cases}$$                                                              | $x = x_0, y = y_0$ 截出的都是抛物线（且形状相同，与取值无关）<br>$z = z_0$ 截出的是椭圆                | $x = x_0, y = y_0$ 截出的都是抛物线（且形状相同，与取值无关）<br>$z = z_0$ 截出的是双曲线               |
| 三角函数参数方程  | $\displaystyle \begin{cases} x = a \cos\theta \cos\varphi \\\\ y = b\cos\theta \sin\varphi \\\\ z = c \sin \theta\end{cases}$<br>$\left( - \frac{\pi}{2} \le \theta \le \frac{\pi}{2}, \ 0 \le \varphi \le 2\pi \right)$ | $\displaystyle \begin{cases} x = a \sec\theta \cos\varphi \\\\ y = b\sec\theta \sin\varphi \\\\ z = c \tan \theta\end{cases}$<br>$\left( - \frac{\pi}{2} < \theta < \frac{\pi}{2}, \ 0 \le \varphi \le 2\pi \right)$ | $\displaystyle \begin{cases} x = a \tan\theta \cos\varphi \\\\ y = b\tan\theta \sin\varphi \\\\ z = c \sec \theta\end{cases}$<br>$\left( - \frac{\pi}{2} < \theta < \frac{\pi}{2}, \ 0 \le \varphi \le 2\pi \right)$ |                                                                             |                                                                             |

# 直母线

| **单叶双曲面的 u 族直线**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | **单叶双曲面的 v 族直线**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 考虑引入参数 $u$，可以将以上方程分解成三种直线：<br>$$\begin{aligned}(1)\quad & \begin{cases}\displaystyle\frac{x}{a} + \frac{z}{c} = u \left(1 + \frac{y}{b}\right) \\\\ \displaystyle\frac{x}{a} - \frac{z}{c} = \frac{1}{u} \left(1 - \frac{y}{b}\right)\end{cases} \\\\ \\\\(2)\quad & \begin{cases}\displaystyle\frac{x}{a} + \frac{z}{c} = 0\\\\\displaystyle1 - \frac{y}{b}=0\end{cases} \quad (i.e.\ u \to 0)\\\\ \\\\(3)\quad & \begin{cases}\displaystyle\frac{x}{a} - \frac{z}{c} = 0\\\\\displaystyle1 + \frac{y}{b}=0\end{cases}\quad (i.e.\ u \to \infty)\end{aligned}$$ | 考虑引入参数 $v$，可以将以上方程分解成三种直线：<br>$$\begin{aligned}(1)\quad & \begin{cases}\displaystyle\frac{x}{a} + \frac{z}{c} = v \left(1 - \frac{y}{b}\right) \\\\ \displaystyle\frac{x}{a} - \frac{z}{c} = \frac{1}{v} \left(1 + \frac{y}{b}\right)\end{cases} \\\\ \\\\(2)\quad & \begin{cases}\displaystyle\frac{x}{a} + \frac{z}{c} = 0\\\\\displaystyle1 + \frac{y}{b}=0\end{cases} \quad (i.e.\ v \to 0)\\\\ \\\\(3)\quad & \begin{cases}\displaystyle\frac{x}{a} - \frac{z}{c} = 0\\\\\displaystyle1 - \frac{y}{b}=0\end{cases}\quad (i.e.\ v \to \infty)\end{aligned}$$<br> |

| **双曲抛物面的 u 族直线**                                                                                                                                    | **双曲抛物面的 v 族直线**                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 考虑引入参数 $u$<br>$$\begin{cases}\displaystyle \frac{x}{a} + \frac{y}{b} = 2u \\\\ \displaystyle u\left(\frac{x}{a} - \frac{y}{b}\right) = z\end{cases}$$ | 考虑引入参数 $v$<br>$$\begin{cases}\displaystyle \frac{x}{a} - \frac{y}{b} = 2u \\\\ \displaystyle u\left(\frac{x}{a} + \frac{y}{b}\right) = z\end{cases}$$ |
# 二次曲线的性质

**与直线参数方程联立**：
$$\Phi(X,Y)\cdot t^{2}
+2[\,F_{1}(x_{0},y_{0})\cdot X+F_{2}(x_{0},y_{0})\cdot Y\,]t
+F(x_{0},y_{0})=0$$
$$\Delta = [\,F_{1}(x_{0},y_{0})\cdot X + F_{2}(x_{0},y_{0})\cdot Y\,]^{2} - \Phi(X,Y)\cdot F(x_{0},y_{0})$$

| 二次项系数             | 判别式                                                                             | 交点情况       |
| ----------------- | ------------------------------------------------------------------------------- | ---------- |
| $\Phi(X,Y) \ne 0$ | $\Delta > 0$                                                                    | 两个不同的实交点   |
|                   | $\Delta = 0$                                                                    | 两个相互重合的实交点 |
|                   | $\Delta < 0$                                                                    | 两个共轭的虚交点   |
| $\Phi(X,Y) = 0$   | $F_{1}(x_{0},y_{0})\cdot X+F_{2}(x_{0},y_{0})\cdot Y \ne 0$                     | 唯一实交点      |
|                   | $F_{1}(x_{0},y_{0})\cdot X+F_{2}(x_{0},y_{0})\cdot Y \ne 0,\ F(x_0, y_0) \ne 0$ | 无交点        |
|                   | $F_{1}(x_{0},y_{0})\cdot X+F_{2}(x_{0},y_{0})\cdot Y = F(x_0, y_0) = 0$         | 直线在二次曲线上   |

**渐近方向**：$\Phi(X,Y)\equiv \begin{bmatrix}X & Y\end{bmatrix} \begin{bmatrix}a_{11} & a_{12}\\\\ a_{12} & a_{22} \end{bmatrix} \begin{bmatrix}X \\\\ Y\end{bmatrix} \equiv a_{11}X^{2}+2a_{12}XY+a_{22}Y^{2} = 0$

**通过渐近方向判断二次曲线类型**：$\Delta = (2a_{12})^2 - 4a_{11}a_{22} = -4I_2 = -4 \begin{vmatrix} a_{11} & a_{12} \\\\ a_{12} & a_{22} \end{vmatrix}$
- 若 $I_2 > 0$，则有一对共轭虚渐近方向，没有实渐近方向，称该二次曲线为椭圆型。
- 若 $I_2 = 0$，则有一对重合的实渐近方向，称该二次曲线为抛物型。
- 若 $I_2 < 0$，则有一对不重合的实渐近方向，称该二次曲线为双曲型。


**中心**：$\begin{cases}F_1(x_0, y_0) \equiv a_{11}x+a_{12}y+a_{13} = 0 \\\\ F_2(x_0, y_0) \equiv a_{12}x+a_{22}y+a_{23} = 0\end{cases}$

| 中心类型   | 判别法                                                                                       | 类型                                                                  |
| ------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| 中心二次曲线 | $I_2 \ne 0$，方程有唯一解                                                                        | 椭圆型、双曲型（包括双曲线和双直线）                                                  |
| 无心二次曲线 | $I_2 = 0$，且 $\frac{a_{11}}{a_{12}} = \frac{a_{12}}{a_{22}} \ne \frac{a_{13}}{a_{23}}$，无解  | 抛物型                                                                 |
| 线心二次曲线 | $I_2 = 0$，且 $\frac{a_{11}}{a_{12}} = \frac{a_{12}}{a_{22}} = \frac{a_{13}}{a_{23}}$，无穷多组解 | 单直线 $(ax + by + c)^2 = 0$<br>或双平行线 $(ax + by + c)(ax + by + d) = 0$ |

**渐近线**：过**二次曲线的中心**，且以**渐近方向为方向**的直线，是二次曲线的渐近曲线。

**正则点切线方程**：方向数满足 $F_{1}(x_{0},y_{0})\cdot X + F_{2}(x_{0},y_{0})\cdot Y = 0$，切线方程有多种形式如下
$$\begin{aligned}(1)\quad & \begin{cases}x = x_0 + F_2(x_0, y_0) t \\\\ y = y_0 - F_1(x_0, y_0) t\end{cases}\\\\(2)\quad &\frac{x - x_0}{F_2(x_0, y_0)} = \frac{y - y_0}{-F_1(x_0, y_0)}\\\\(3)\quad &(x-x_0)F_1(x_0, y_0) + (y - y_0)F_2(x_0, y_0) = 0\\\\(4)\quad & xF_1(x_0, y_0) + yF_2(x_0, y_0) + F_3(x_0, y_0)= 0\\\\(5)\quad & a_{11}x_0 x + a_{12}(x_0y + xy_0) + a_{22}y_0y + a_{13}(x+x_0) + a_{23}(y+ y_0) + a_{33} = 0\end{aligned}$$

**奇异点**：曲线上一点满足 $F(x_0, y_0) = 0,\ F_1(x_0, y_0) = F_2(x_0, y_0) = 0$，则过它的直线都是二次曲线的切线。

**平行弦对应直径**：平行弦的方向是**非渐近**方向数 $(X, Y)$（满足 $\Phi(X,Y) \ne 0$），弦中点满足的方程是直径 $XF_1(x, y) + YF_2(x, y) = 0$

**直径与曲线型**：
- 中心二次曲线的直径经过直径中心（如椭圆或双曲线），因为中心都满足 $F_1(x, y) = F_2(x, y) = 0$.
- 无心二次曲线的直径平行于曲线的渐近方向（如抛物线），方向数就是 $a_{22} : - a_{12}$ 或 $a_{12} : - a_{11}$.
- 线心二次曲线的直径就是曲线的中心直线。

**共轭方向**：
- $X':Y' = - (a_{12}X + a_{22}Y) : (a_{11}X + a_{12}Y)$
- $\begin{bmatrix}X & Y\end{bmatrix} \begin{bmatrix}a_{11} & a_{12} \\\\ a_{12} & a_{22} \end{bmatrix}\begin{bmatrix}X' \\\\ Y'\end{bmatrix}= a_{11}XX' + a_{12} (XY' + X'Y) + a_{22} YY' = 0$
- 平行弦弦方向和直径方向互为共轭方向

**共轭直径**：中心二次曲线的一对具有**相互共轭方向**的直径

**主方向**：
- $A^*$ 的特征值
- 主直径与垂直于主直径的方向都是二次曲线的主方向。

**主直径**：二次曲线中垂直于其共轭弦的直径。主直径是二次曲线的**对称轴**。