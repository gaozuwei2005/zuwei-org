---
title: 解析几何 | Week 8 线线关系、平面束
date: 2025-10-28
summary: 线线位置关系、直线夹角、异面直线距离、公垂线方程、平面束
---


# 3.7 空间两直线的相关位置

两直线关系：共面（相交、平行、重合）、异面

## 空间两直线的位置关系

两直线 $l_1 : \boldsymbol r = M_1 + t \boldsymbol v_1$，$l_2 : \boldsymbol r = M_2 + t \boldsymbol v_2$，它们的关系取决于 $\boldsymbol v_1,\ \boldsymbol v_2,\ \overrightarrow{M_1M_2}$.

| $l_1,\ l_2$ 位置关系 | $\boldsymbol v_1,\ \boldsymbol v_2,\ \overrightarrow{M_1M_2}$ 位置关系            | 计算方法                                                                                                                                                                                            |
| ---------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 共面               | 共面                                                                            | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2}) = \left\lvert\begin{matrix} x_2  - x_1 & y_2 - y_1 & z_2 - z_1 \\\\ X_1 & Y_1 & Z_1 \\\\ X_2 & Y_2 & Z_2 \end{matrix}\right\rvert = 0$ |
| 相交               | 三向量共面，且 $\boldsymbol v_1, \boldsymbol v_2$ 相交                                 | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1 \ne X_2:Y_2:Z_2.$                                                                                                  |
| 平行               | 三向量共面，且 $\boldsymbol v_1 // \boldsymbol v_2$，但与 $\overrightarrow{M_1M_2}$ 不平行 | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1$ $=$ $X_2:Y_2:Z_2$ $\ne$ $(x_2-x_1):(y_2-y_1):(z_2-z_1)$                                                           |
| 重合               | 三向量共面，且 $\boldsymbol v_1 // \boldsymbol v_2 // \overrightarrow{M_1M_2}$       | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2})=0,\ X_1:Y_1:Z_1$ $=$ $X_2:Y_2:Z_2$ $=$ $(x_2-x_1):(y_2-y_1):(z_2-z_1)$                                                             |
| 异面               | 异面                                                                            | $(\boldsymbol v_1, \boldsymbol v_2, \overrightarrow{M_1M_2}) \ne 0$                                                                                                                             |

## 空间两直线的夹角

**两直线夹角余弦**：为其方向向量的夹角余弦 $$\pm\cos\angle(l_1, l_2)
= \pm
\frac{X_1 X_2 + Y_1 Y_2 + Z_1 Z_2}
{\sqrt{X_1^2 + Y_1^2 + Z_1^2}\,\sqrt{X_2^2 + Y_2^2 + Z_2^2}}$$
因此若两直线垂直，等价于 $X_1 X_2 + Y_1 Y_2 + Z_1 Z_2 = 0$.


## 异面直线的距离和公垂线方程

**两直线的距离**：空间上两直线的点之间的最短距离。

**两异面直线的公垂线**：与两条异面直线都 *垂直相交* 的直线。两交点之间线段的长为公垂线的长。

**定理**：两异面直线的距离等于公垂线的长。

理解：对于两直线 $l_1, l_2$，公垂线为 $l_0$，那么 $\forall M_1 \in l_1,\ M_2 \in l_2,\ \left|proj_{l_0} \overrightarrow{M_1M_2}\right| = \left|\overrightarrow{N_1N_2}\right|$，投影长度必然比原向量短。

**异面直线距离公式**：$\displaystyle d = \frac{\left|\overrightarrow{M_1M_2} · (\boldsymbol v_1 \times \boldsymbol v_2)\right|}{\left|\boldsymbol v_1 \times \boldsymbol v_2\right|} = \frac{\left|(\overrightarrow{M_1M_2}, \boldsymbol v_1, \boldsymbol v_2)\right|}{\left|\boldsymbol v_1 \times \boldsymbol v_2\right|}$

直观理解：距离（高）等于平行六面体体积除以底面面积 ![](attachments/Pasted-image-20251028105131.png)

**公垂线方程**：对于 $M_1$ 与向量 $\boldsymbol v_1, \boldsymbol v_1 \times \boldsymbol v_2$ 生成的平面 $\pi_1$ 和 $M_2$ 与向量 $\boldsymbol v_2, \boldsymbol v_1 \times \boldsymbol v_2$ 生成的平面 $\pi_2$ ，他们的交线就是公垂线。![](attachments/Pasted-image-20251028111548.png)

因此公垂线的方程为
$$l_0 : \begin{cases}\pi_1 :
\begin{vmatrix}
x - x_1 & y - y_1 & z - z_1 \\\\
X_1 & Y_1 & Z_1 \\\\
X & Y & Z
\end{vmatrix}
= 0\\\\\pi_2 :
\begin{vmatrix}
x - x_2 & y - y_2 & z - z_2 \\\\
X_2 & Y_2 & Z_2 \\\\
X & Y & Z
\end{vmatrix}
= 0\end{cases}
$$

其中$\quad\vec{v}_1 = \{X_1, Y_1, Z_1\}, \quad\vec{v}_2 = \{X_2, Y_2, Z_2\}, \quad\vec{v}_1 \times \vec{v}_2 = \{X, Y, Z\}$。

# 3.8 平面束

**有轴平面束**：空间中通过同一条直线的所有平面的集合叫做有轴平面束，那条直线叫做平面束的轴。

**有轴平面束的方程**：若平面束的轴为 $\begin{cases} A_1x + B_1y + C_1z + D_1 = 0 \\\\ A_2x + B_2y + C_2z + D_2 = 0 \end{cases}$，则有轴平面束的方程为 $$l(A_1x + B_1y + C_1z + D_1) + m(A_2x + B_2y + C_2z + D_2) = 0$$

其中 $l, m$ 是不全为零的任意实数。


**平行平面束**：空间中平行于同一个平面的集合叫做平行平面束。

**平行平面束的方程**：如果两个平面
$$\pi_1 : A_1x + B_1y + C_1z + D_1 = 0$$
$$\pi_2 : A_2x + B_2y + C_2z + D_2 = 0$$

为平行平面，即 $\displaystyle \frac{A_1}{A_2} = \frac{B_1}{B_2} = \frac{C_1}{C_2}$，那么平行平面束的方程为 $$l(A_1x + B_1y + C_1z + D_1) + m(A_2x + B_2y + C_2z + D_2) = 0$$

表示平行平面束，平面束里的任意一个平面都和平面 $\pi_1$ 或 $\pi_2$ 平行，其中 $l, m$ 是不全为零的任意实数，且 $\displaystyle -\frac{l}{m} \ne\frac{A_1}{A_2} =\frac{B_1}{B_2} =\frac{C_1}{C_2}$.

这种方法只是为了和有轴平面束的推导相统一。

**另一种更直接的方式**：平行于平面 $\pi: Ax + By + Cz + D = 0$ 的所有平面为 $Ax + By + Cz + t = 0$，其中 $t$ 为任意实数。