---
title: 解析几何 | Week 6 平面、点面关系、面面关系、直线
date: 2025-10-14
summary: 平面方程、点面关系、面面关系、空间直线方程
---


# 3.1 平面的方程

平面上的**一点**和与此平面平行的**两个不共线向量**决定一张平面。
那么每个平面上的点可以唯一地表示为坐标 $(u, v)$.

|           |                                                                                                                          一点与两方位向量                                                                                                                          |                                                                                                                                                                              三点式                                                                                                                                                                               |                                           截距式                                           |
| :-------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------: |
| **向量式方程** |                                                                                           $\boldsymbol r = \boldsymbol r_0 + u \boldsymbol a + v \boldsymbol b$                                                                                            |                                                                                                                        $\boldsymbol r = \boldsymbol r_1 + u(\boldsymbol r_2 - \boldsymbol r_1) + v(\boldsymbol r_3 - \boldsymbol r_1)$                                                                                                                         | 取三点式中的 $\boldsymbol r_1(a, 0, 0), \boldsymbol   r_2(0, b, 0), \boldsymbol r_3(0, 0, c)$ |
| **坐标式方程** |                                                                           $\begin{cases} x = x_0 + ux_1 + vx_2 \\\\ y = y_0 + uy_1 + vy_2 \\\\ z = z_0 + uz_1 + vz_2\end{cases}$                                                                           |                                                                                          $\displaystyle \begin{cases} x = x_1 + u(x_2 - x_1) + v(x_3 - x_1) \\\\ y = y_1 + u(y_2 - y_1) + v(y_3 - y_1) \\\\ z = z_1 + u(z_2 - z_1) + v(z_3 - z_1) \\\\  \end{cases}$                                                                                           |                                                                                         |
| **点位式方程** |                                  混合积 $(\boldsymbol r - \boldsymbol r_0, \boldsymbol a, \boldsymbol b) = 0$ 即<br>$\begin{vmatrix} x - x_0 & y - y_0 & z - z_0 \\\\ x_1 & y_1 & z_1 \\\\ x_2 & y_2 & z_2 \end{vmatrix} = 0$                                  | 混合积 $(\boldsymbol{r}-\boldsymbol{r}_1,\boldsymbol{r}_2-\boldsymbol{r}_1,\boldsymbol{r}_3-\boldsymbol{r}_1) = 0$，<br>即 $\begin{vmatrix}x-x_1 & y-y_1 & z-z_1\\\\x_2-x_1 & y_2-y_1 & z_2-z_1\\\\x_3-x_1 & y_3-y_1 & z_3-z_1\end{vmatrix}=0$ 或 $\begin{vmatrix}x & y & z & 1\\\\x_1 & y_1 & z_1 & 1\\\\x_2 & y_2 & z_2 & 1\\\\x_3 & y_3 & z_3 & 1\end{vmatrix}=0$ |             $\begin{vmatrix}x-a & y & z\\\\-a&b&0\\\\-a&0&c\end{vmatrix}=0$             |
| **一般式方程** | 点位式方程展开得到 $A x + B y + C z + D = 0\ (ABC \ne 0)$<br>$$A =\begin{vmatrix}y_1 & z_1\\\\y_2 & z_2\end{vmatrix},B =\begin{vmatrix}z_1 & x_1\\\\z_2 & x_2\end{vmatrix},C =\begin{vmatrix}x_1 & y_1\\\\x_2 & y_2\end{vmatrix}$$$$D = - (A x_0 + B y_0 + C z_0)$$ |                                                                                                                                                                                                                                                                                                                                                                |   **截距式方程** $\displaystyle \frac{x}{a} + \frac{y}{b} + \frac{z}{c} = 1\ (abc \ne 0)$    |


**一般式方程转点位式方程**：不妨设 $A \ne 0$，则整体除以 $A$ 得到 $x + B y + C z + D = 0$，那么就有 $\displaystyle \begin{vmatrix}x + D & y & z \\\\ B & -1 & 0 \\\\ C & 0 & -1\end{vmatrix} = 0$，其中取的三点为 $\boldsymbol M_0 (-D, 0, 0), \boldsymbol a(B, -1, 0), \boldsymbol b(C, 0, -1)$.


**定理**：空间任意平面的方程是三元一次方程，任意一个三元一次方程表示空间的一个平面。
- 若 $D = 0$，等价于平面通过原点；
- 若 $A, B, C$ 有一个为 $0$，等价于平面平行于或者通过某个坐标轴；
- 若 $A, B, C$ 有两个为 $0$，等价于平面平行于或者就是某个坐标平面。


**点法式方程**：给定空间一点 $\boldsymbol r_0(x_0, y_0, z_0)$ 和法向量 $\boldsymbol n\{A, B, C\}$，可唯一确定过 $\boldsymbol r_0$ 且与 $\boldsymbol n$ 垂直的平面。

**向量式点法式方程**：$\boldsymbol n · (\boldsymbol r - \boldsymbol r_0) = 0$

**坐标式点法式方程**：$A (x - x_0) + B(y - y_0) + C(z - z_0) = 0$

因此一般式方程中的一次项系数就是法向量的坐标分量.
如何求法向量：
- 若已知平面上三点，则求差向量并求叉积
- 若已知平行面，则取相同法向量
- 若已知垂直面，则法向量与垂直面的法向量垂直，即点积为 $0$.

**法式方程**：在点法式方程中，$\boldsymbol n$ 取单位向量 $\boldsymbol n^0\{\cos \alpha, \cos \beta, \cos \theta\}$ ，$\boldsymbol r_0$ 取平面与法向量的垂足，并令 $\boldsymbol r_0 = p \boldsymbol n^0$.

**向量式法式方程**：因此形式变成 $\boldsymbol n_0 · (\boldsymbol r - p \boldsymbol n_0) = 0$，即 $\boldsymbol n^0·\boldsymbol r - p = 0$

**坐标式法式方程**：$x \cos \alpha + y \cos \beta + z \cos \gamma - p = 0$

显然可见，一个平面只有一种法式方程的表示形式，但可能有无穷多种点法式方程的表示形式。

**一般式方程转法式方程**：除以法式化因子 $\lambda = - \operatorname{sign}(D) \sqrt{A^2 + B^2 + C^2}$ 即可，其中要使得常数项为**负数**。

# 3.2 平面与点的相关位置

**点与平面的距离**：一点与平面上的点的最短距离，即一点到其对平面作垂线的垂足的距离。

**离差**：一点 $P$ 对平面作垂线的垂足 $M$ 到该点的向量 $\overrightarrow{MP}$ ，在平面的单位法向量的射影。
- 离差的计算：
	- 向量式：$\delta = \boldsymbol n^0 · \overrightarrow{MP} = \boldsymbol n^0 (\overrightarrow{OP} - \overrightarrow{OM}) = \boldsymbol n^0 · \overrightarrow{OP} - p$
	- 坐标式：若已知法式方程以及 $P(x, y, z)$ 则 $\delta = x \cos \alpha + y \cos \beta + z \cos \gamma - p$
- 若 $P$ 位于 $\boldsymbol n^0$ 指向的半空间，则离差 $\delta = \left|\overrightarrow{MP}\right| > 0$；
- 若 $P$ 不位于 $\boldsymbol n^0$ 指向的半空间，则离差 $\delta = -\left|\overrightarrow{MP}\right| < 0$；
- 若 $P$ 在平面上，则离差 $\delta = 0$.
- **离差的绝对值为点到平面的距离**。
- 若两点在平面一侧，则离差符号相同；若两点在平面异侧，则离差符号相反。

**点与平面一般方程的距离**：先将一般方程转法式方程（除以法式化因子），再计算离差，则 $$\begin{aligned}d &= |\delta| = |x \cos \alpha + y \cos \beta + z \cos \gamma - p|\\\\&=\frac{|Ax_0+By_0+Cz_0+D|}{\sqrt{A^2+B^2+C^2}}\end{aligned}$$
如果只知道一般方程，只计算 $Ax_0 + B_y + Cz_0 + D$，结合法式化因子，也由其正负判断在哪个半空间。

# 3.3 两平面的相关位置

| 两平面位置 | 判断方法（向量）                                          | 判断方法（参数）                                                                                |
| ----- | ------------------------------------------------- | --------------------------------------------------------------------------------------- |
| 相交    | $\boldsymbol n_1 \nparallel \boldsymbol n_2$      | $A_1 : B_1 : C_1 \ne A_2 : B_2 : C_2$                                                   |
| 平行    | $\boldsymbol n_1 // \boldsymbol n_2, p_1 \ne p_2$ | $\displaystyle \frac{A_1}{A_2} = \frac{B_1}{B_2} = \frac{C_1}{C_2} \ne \frac{D_1}{D_2}$ |
| 重合    | $\boldsymbol n_1 // \boldsymbol n_2,\ p_1 = p_2$  | $\displaystyle \frac{A_1}{A_2} = \frac{B_1}{B_2} = \frac{C_1}{C_2} = \frac{D_1}{D_2}$   |
| 垂直    | $\boldsymbol n_1 · \boldsymbol n_2 = 0$           | $A_1A_2 + B_1B_2 + C_1C_2 = 0$                                                          |

**两平面夹角**：平面夹角一般取 $[0, \pi]$，有两种互补的角，其余弦值互为相反数 $$\pm \cos \angle(\boldsymbol n_1, \boldsymbol n_2) = \pm \frac{A_1A_2 + B_1B_2 + C_1C_2}{\sqrt{A_1^2+B_1^2+C_1^2}\sqrt{A_2^2+B_2^2+C_2^2}}$$

# 3.4 空间直线的方程

## 空间直线的标准方程（始点与方向向量）

**向量式参数方程**：$\boldsymbol r = \boldsymbol r_0 + t \boldsymbol v$

**坐标式参数方程**：$\begin{cases} x = x_0 + t X \\\\ y = y_0 + tY \\\\ z = z_0 + tZ \end{cases}$

以上，其中 $t$ 是参数，$\boldsymbol v$ 是方向向量。


消去参数 $t$ 可以得到 **标准方程 / 对称式方程 / 点向式方程**：$\displaystyle \frac{x - x_0}{X} = \frac{y - y_0}{Y} = \frac{z - z_0}{Z}$

其中 $X, Y, Z$ 及其成比例的一组数称为直线 $l$ 的**方向数**。

当方向数中的某些量为 $0$ 时，仍然写成分式形式，如：
- $\displaystyle \frac{x - x_0}{0} = \frac{y - y_0}{Y} = \frac{z - z_0}{Z}$，表示 $\displaystyle x = x_0,\ \frac{y - y_0}{Y} = \frac{z - z_0}{Z}$
- $\displaystyle \frac{x - x_0}{0} = \frac{y - y_0}{0} = \frac{z - z_0}{Z}$，表示 $x = x_0,\ y = y_0$.


方向角可以通过方向数计算：$$\cos \alpha = \pm \frac{X}{\sqrt{X^2 + Y^2 + Z^2}},\cos \beta = \pm \frac{Y}{\sqrt{X^2 + Y^2 + Z^2}},\cos \gamma = \pm \frac{Z}{\sqrt{X^2 + Y^2 + Z^2}}$$
前面的正负号要看方向角和向量是不是同向。

如果直接取方向向量 $\boldsymbol v_0 = \{ \cos \alpha, \cos \beta, \cos \gamma\}$，则 $\boldsymbol r = \boldsymbol r_0 + t \boldsymbol v_0$，则 $|t|$ 恰好是对应点到 $\boldsymbol r_0$ 的距离。

## 空间直线的一般方程（两平面交线）

空间直线可以看成两平面的交线 $\begin{cases} A_1x + B_1y + C_1z + D_1 = 0 \\\\ A_2x + B_2y + C_2z + D_2 = 0 \end{cases}$

前提条件是两平面不平行：$\boldsymbol n_1 \times \boldsymbol n_2 = \left\\\{ \left|\begin{matrix} B_1 & C_1 \\\\ B_2 & C_2 \end{matrix}\right|, \left|\begin{matrix} C_1 & A_1 \\\\ C_2 & A_2 \end{matrix}\right|, \left|\begin{matrix} A_1 & B_1 \\\\ A_2 & B_2 \end{matrix}\right|\right\\\} \ne \boldsymbol 0$

**标准方程转一般方程**：不妨设方向向量中 $Z \ne 0$，那么可写成 $$\begin{cases} \displaystyle \frac{x - x_0}{X} = \frac{z - z_0}{Z} \\\\ \displaystyle \frac{y - y_0}{Y} = \frac{z - z_0}{Z} \end{cases}$$
**一般方程转标准方程**：由于 $\boldsymbol n_1 \times \boldsymbol n_2 = \left\\\{ \begin{vmatrix} B_1 & C_1 \\\\ B_2 & C_2 \end{vmatrix}, \begin{vmatrix} C_1 & A_1 \\\\ C_2 & A_2 \end{vmatrix}, \begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix}\right\\\} \ne \boldsymbol 0$，因此必有不为零的分量，这对应于矩阵相容。不妨设 $\begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix} \ne 0$ ，相当于解关于 $x, y$ 的方程组 $$\begin{cases} A_1x + B_1y = -C_1z - D_1 \\\\ A_2x + B_2y = -C_2z - D_2 \end{cases}$$得到（不用记，只要知道是求解线性方程组即可） $$x = \frac{\begin{vmatrix} B_1 & C_1 \\\\ B_2 & C_2 \end{vmatrix}}{\begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix}} z + \frac{\begin{vmatrix} B_1 & D_1 \\\\ B_2 & D_2 \end{vmatrix}}{\begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix}},\quad y = \frac{\begin{vmatrix} C_1 & A_1 \\\\ C_2 & A_2 \end{vmatrix}}{\begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix}} z + \frac{\begin{vmatrix} D_1 & A_1 \\\\ D_2 & A_2 \end{vmatrix}}{\begin{vmatrix} A_1 & B_1 \\\\ A_2 & B_2 \end{vmatrix}}$$
为了简便，也就是说我们已经得到参数形式 $$\begin{cases}x=\alpha t + \beta \\\\ y = \gamma t + \delta \\\\ z = t\end{cases}$$
容易得到标准方程 $$\frac{x - \beta}{\alpha} = \frac{y - \delta}{\gamma} = \frac{z}{1}$$