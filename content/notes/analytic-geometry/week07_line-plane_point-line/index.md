---
title: 解析几何 | Week 7 线面关系、点线关系
date: 2025-11-03
summary: 线面关系、点线关系
---


# 3.5 直线与平面的相对位置

给定直线 $l$ 的始点 $\boldsymbol M_0 (x_0, y_0, z_0)$ 和方向向量 $\boldsymbol v\{X, Y, Z\}$，以及平面 $\Pi$ 的法向量 $\boldsymbol n\{A, B, C\}$ 和平面一般方程 $Ax + B y + Cz + D = 0$，那么有

| 线面关系 | 判断方法（向量）                                                         | 判断方法（参数）                                         |
| ---- | ---------------------------------------------------------------- | ------------------------------------------------ |
| 相交   | $\boldsymbol v \not\perp \boldsymbol n$                          | $AX+BY+CZ\ne0$                                   |
| 平行   | $\boldsymbol v \perp \boldsymbol n,\ \boldsymbol M_0 \notin \Pi$ | $AX+BY+CZ = 0$<br>$Ax_0 + By_0 + Cz_0 + D \ne 0$ |
| 线在面上 | $\boldsymbol v \perp \boldsymbol n,\ \boldsymbol M_0 \notin \Pi$ | $AX+BY+CZ = 0$<br>$Ax_0 + By_0 + Cz_0 + D = 0$   |
| 垂直   | $\boldsymbol v // \boldsymbol n$                                 | $A_1 : B_1 : C_1 = A_2 : B_2 : C_2$              |

**求直线和平面的交点**：将直线坐标参数方程 $\begin{cases} x = x_0 + t X \\\\ y = y_0 + tY \\\\ z = z_0 + tZ \end{cases}$ 代入平面一般式求解。

**求直线和平面夹角**：一般取 $\displaystyle  0 \le \varphi \le \frac{\pi}{2}$，那么 $$\displaystyle \begin{aligned}\sin \varphi &= |\cos \angle(\boldsymbol v, \boldsymbol n)|\\\\&= \frac{|AX+BY+CZ|}{\sqrt{A^2+B^2+C^2}·\sqrt{X^2+Y^2+Z^2}}\end{aligned}$$
# 3.6 空间直线与点的相关位置
给定直线的始点 $\boldsymbol M_0 (x_0, y_0, z_0)$ 和方向向量 $\boldsymbol v\{X, Y, Z\}$，那么点 $\boldsymbol M(x_1, y_1, z_1)$ 到直线的距离可以通过计算 $\overrightarrow{M_1M_0}$ 与 $\boldsymbol v$ 的叉积得到：$$\begin{aligned} d &= \frac{|\overrightarrow{M_1M_0} \times \boldsymbol v|}{|\boldsymbol v|} \\\\&=\frac{\sqrt{\begin{vmatrix}y_0 - y_1 & z_0 - z_1\\\\Y & Z\end{vmatrix}^2
+\begin{vmatrix}z_0 - z_1 & x_0 - x_1\\\\Z & X\end{vmatrix}^2
+\begin{vmatrix}x_0 - x_1 & y_0 - y_1\\\\X & Y\end{vmatrix}^2}
}{\sqrt{X^2 + Y^2 + Z^2}}\end{aligned}$$
