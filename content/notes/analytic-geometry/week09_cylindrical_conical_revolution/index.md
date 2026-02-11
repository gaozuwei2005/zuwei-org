---
title: 解析几何 | Week 9 柱面、锥面、旋转曲面
date: 2025-11-04
summary: 柱面、锥面、旋转曲面的方程
---


# 4.1 柱面

**柱面**：平行于定**方向**且与一条**准线**相交的一族平行直线所生成的曲面。
- 其中每条平行直线都是柱面的**母线**。
- 准线并不唯一，只需要和每条平行直线都相交即可。

**柱面方程**：给定准线方程 $\begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和方向向量 $\boldsymbol r\\\{X, Y, Z\\\}$，那么母线族方程为 $$\frac{x - x_0}{X} = \frac{y - y_0}{Y} = \frac{z - z_0}{Z},\ s.t. \begin{cases}F_1(x_0, y_0, z_0) = 0 \\\\ F_2(x_0, y_0, z_0) = 0\end{cases}$$
消去 $x_0, y_0, z_0$ 即可得到柱面方程是三元方程 $F(x, y, z) = 0$.

**圆柱面方程**：给定中轴线 $\boldsymbol v\\\{X, Y, Z\\\}$、轴线上一点 $\boldsymbol M_0(x_0, y_0, z_0)$ 以及半径 $r$，那么柱面方程为 $$\begin{aligned} r = \frac{|\overrightarrow{M_1M_0} \times \boldsymbol v|}{|\boldsymbol v|} =\frac{\sqrt{\begin{vmatrix}y_0 - y_1 & z_0 - z_1\\\\Y & Z\end{vmatrix}^2
+\begin{vmatrix}z_0 - z_1 & x_0 - x_1\\\\Z & X\end{vmatrix}^2
+\begin{vmatrix}x_0 - x_1 & y_0 - y_1\\\\X & Y\end{vmatrix}^2}
}{\sqrt{X^2 + Y^2 + Z^2}}\\\\
\begin{vmatrix}y_0 - y_1 & z_0 - z_1\\\\Y & Z\end{vmatrix}^2
+\begin{vmatrix}z_0 - z_1 & x_0 - x_1\\\\Z & X\end{vmatrix}^2
+\begin{vmatrix}x_0 - x_1 & y_0 - y_1\\\\X & Y\end{vmatrix}^2
= (X^2 + Y^2 + Z^2)r^2\end{aligned}$$
**柱面的充分判定**：只用两个变量表示的方程表示的是一个柱面，该柱面与所缺失的变量对应的坐标轴平行。例如，$F(x,y) = 0$ 的柱面对应准线为 $\begin{cases}F(x, y) = 0 \\\\ z = 0\end{cases}$，方向向量为 $r\\\{0, 0, 1\\\}$.

**二次柱面**：与 $xOy$ 坐标面交线为椭圆、双曲线或抛物线的柱面。
![](attachments/Pasted-image-20251104104614.png)

**射影柱面**：一条空间曲线可以用两个射影柱面的交来表示，如 $\begin{cases}F_1(x, y) = 0 \\\\ F_2(x, z) = 0\end{cases}$.

# 4.2 锥面

**锥面**：过一**顶点**且与一条**准线**相交的一族直线所生成的曲面。
- 其中每条直线都是锥面的**母线**。
- 准线并不唯一，只需要和每条直线都相交即可。

**锥面的方程**：给定准线方程 $\begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和顶点 $\boldsymbol A(x_0, y_0, z_0)$，那么母线族方程为 $$\frac{x - x_0}{x - x_1} = \frac{y - y_0}{y - y_1} = \frac{z - z_0}{z - z_1},\ s.t. \begin{cases}F_1(x_1, y_1, z_1) = 0 \\\\ F_2(x_1, y_1, z_1) = 0\end{cases}$$
消去 $x_1, y_1, z_1$ 即可得到柱面方程是三元方程 $F(x, y, z) = 0$.

**圆锥面的方程**：给定顶点 $\boldsymbol A(x_0, y_0, z_0)$、轴线法向量 $\boldsymbol n$，以及母线与轴线的夹角（半顶角）为 $\alpha$，那么圆锥面方程为 $$\cos \alpha = \pm \frac{\overrightarrow{AM} ·\boldsymbol n}{|\overrightarrow{AM}|·|\boldsymbol n|}$$
**锥面的充分判定**：一个关于 $x, y, z$ 的齐次方程总是表示顶点在 $(0, 0, 0)$ 的锥面。
- 原因：若 $k$ 次齐次方程 $F(x, y, z) = 0$，则 $F(tx, ty, tz) = t^k F(x, y, z) = 0$.
**锥面的充分判定 2**：一个关于 $x - x_0, y - y_0, z - z_0$ 的齐次方程总是表示顶点在 $(x_0, y_0, z_0)$ 的锥面。

# 4.3 旋转曲面

**旋转曲面 / 回转曲面**：曲线 $\Gamma$ 绕着 **(旋转)轴** $l$ 旋转一周形成的曲面。
- 每条曲线 $\Gamma$ 都是该曲面的母线。
- 母线上每个点旋转时都形成一个圆，那么每个圆都称为 **纬圆 / 纬线**。
- 以 $l$ 为界的每个 *半平面* 与曲面交成一条曲线，称为曲面的 **经线**，注意经线不一定就是母线。

**旋转曲面的方程**：给定母线方程 $\Gamma : \begin{cases}F_1(x, y, z) = 0 \\\\ F_2(x, y, z) = 0\end{cases}$ 和旋转轴 $\displaystyle l : \frac{x-x_0}{X} = \frac{y-y_0}{Y} = \frac{z-z_0}{Z}$，我们取母线上一点 $\boldsymbol M_1 (x_1,y_1,z_1)$，那么纬圆族的方程为 $$\begin{cases} X(x - x_1) + Y(y - y_1) + Z(z - z_1) = 0 \\\\ (x - x_0)^2 + (y - y_0)^2 + (z - z_0)^2 = (x_1 - x_0)^2 + (y_1 - y_0)^2 + (z_1 - z_0)^2 \end{cases},\ s.t.  \begin{cases}F_1(x_1, y_1, z_1) = 0 \\\\ F_2(x_1, y_1, z_1) = 0\end{cases}$$
消去 $x_1, y_1, z_1$ 即可得到三元方程 $F(x, y, z) = 0$.
