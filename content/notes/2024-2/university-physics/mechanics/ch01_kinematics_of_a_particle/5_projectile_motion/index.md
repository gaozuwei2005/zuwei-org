---
title: 大学物理 | 1.5 抛体运动
date: 2024-11-22
summary: 定义、分析、特征、竖直上抛运动
---


## 抛体运动的定义与分析

> **抛体运动**：从地面上某点向空中抛出的物体在空中的运动。
> 
> **抛体运动的一般简化假设**：
> 
> - 一般被抛物体速度较小，受风面积小，可忽略空气阻力；
> - 运动轨道一般在 $\boldsymbol{v_0}$ 和 $\boldsymbol{a} = -\boldsymbol{g}$ 张成的平面下研究。

令 $x_0 = y_0 = 0, v_{0x} = v_0 \cos \theta, v_{0y} = v_0 \sin \theta, a_x = 0, a_y = -g$，则有

$$\begin{aligned}
v_x &= v_0\cos \theta \\\\
v_y &= v_0\sin \theta - gt \\\\
x &= v_0t\cos \theta \\\\
v_y &= v_0t \sin \theta - \frac{1}{2}gt^2
\end{aligned}$$

抛体运动为竖直的匀加速运动与水平匀速运动的合运动。

## 抛体运动的特征

- **物体回落至原高度时间 $\boldsymbol T$**：令位移大小为 $0$，

    $$y = v_0 t\sin\theta - \frac{1}{2}gt^2 = 0$$

    $$\Rightarrow t_1 = 0 (舍), \ t_2 = T = \frac{2v_0\sin\theta}{g}$$

- **最大高度 $\boldsymbol Y$**：

    $$Y = \frac{v_{0y}^2}{2g} = \frac{v_0^2 \sin^2 \theta}{2g}$$

- **水平射程 $\boldsymbol X$**：

    $$X = v_0\cos\theta·T = v_0\cos\theta · \frac{2v_0\sin\theta}{g} = \frac{v_0 \sin2\theta}{g}$$

若 $v_0$ 固定，当 $\theta = 45^\circ$ 时，$X$ 取最大值；当 $\theta = 90^\circ$ 时（竖直上抛），$T$ 和 $Y$ 最大。

- **抛物线**：

    联立以上二式

    $$\begin{aligned}
    x &= v_0\cos\theta · t\\\\
    y &= v_0\sin\theta · t - \frac{1}{2} gt^2
    \end{aligned}$$

    可得

    $$y = x\tan\theta - \frac{g}{2v_0^2\cos^2\theta}·x^2$$

## 竖直上抛运动

> **抛体运动**：$\theta = 90^\circ$ 的抛体运动。

$$\begin{aligned}
v &= v_0 - gt \\\\
y &= y_0 + v_0t - \frac{1}{2}gt^2\\\\
v^2 &= v_0^2 - 2g(y - y_0)\\\\
\end{aligned}$$

## 矢量知识

> **叉乘**：两个矢量的叉乘 $\boldsymbol{c} = \boldsymbol{a} \times \boldsymbol{b}$。仍是矢量，大小为
> $$|\boldsymbol{c}| = |\boldsymbol{a}| |\boldsymbol{b}| \sin \theta$$
>
> 方向由 **右手螺旋法则** 确定：四指顺着 $\langle\boldsymbol{a}, \boldsymbol{b}\rangle$ 从 $\boldsymbol{a}$ 到 $\boldsymbol{b}$ 画圆弧，大拇指为 $\boldsymbol{c}$ 的方向。由此可知 $\boldsymbol{c} \perp \operatorname{Span}\\{\boldsymbol{a}, \boldsymbol{b}\\}$.

- 叉乘 **没有交换律**：$\boldsymbol{a} \times \boldsymbol{b} = - \boldsymbol{b} \times \boldsymbol{a}$
- 坐标式：$\boldsymbol{a} \times \boldsymbol{b} = (a_yb_z - a_zb_y)\boldsymbol{i} + (a_zb_x - a_xb_z) \boldsymbol{j} + (a_xb_y - a_yb_z)\boldsymbol{k}$
- 三个单位矢量，任两个单位向量的叉积等于另一个单位向量。
- 点乘和叉乘的计算优先级相同，高于加减。