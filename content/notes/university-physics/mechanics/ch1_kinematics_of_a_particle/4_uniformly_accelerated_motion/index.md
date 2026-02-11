---
title: 大学物理 | 1.4 匀加速运动
date: 2024-11-21
summary: 加速度的定义、微积分知识
---


## 匀加速运动

### 匀加速运动的定义及向量式

> **匀加速运动**：加速度的 **大小和方向** 都不随时间改变的运动。（加速度为常矢量）

**速度公式**：

$$\mathrm d \boldsymbol{v} = \boldsymbol{a} \mathrm dt$$

两边积分得到

$$\int_{\boldsymbol{v_0}}^{\boldsymbol{v}} \mathrm d \boldsymbol{v} = \int_{0}^{\mathrm t} \boldsymbol{a} \mathrm dt$$

$$\boldsymbol{v} - \boldsymbol{v_0} = \boldsymbol{a}t$$

$$\boldsymbol{v} = \boldsymbol{v_0} + \boldsymbol{a}t$$

> 积分知识：$\int \mathrm dx = x + C$.

**位矢公式**：

$$\mathrm d\boldsymbol{r} = \boldsymbol{v} \mathrm dt$$

两边积分得到

$$\int_{\boldsymbol{r_0}}^{\boldsymbol{r}} \mathrm d\boldsymbol{r} = \int_{0}^{t} \boldsymbol{v} \mathrm dt= \int_{0}^{t} (\boldsymbol{v_0} +\boldsymbol{a}t) \mathrm dt$$

$$\boldsymbol{r} - \boldsymbol{r_0} = \boldsymbol{v_0} t + \frac{1}{2} \boldsymbol{a} t^2$$

$$\boldsymbol{r} = \boldsymbol{r_0} + \boldsymbol{v_0} t + \frac{1}{2} \boldsymbol{a} t^2$$

> 积分知识：$\int x \mathrm dx = \frac{1}{2} x^2 + C$.

### 常用分量式

- 速度分量式：

$$v_x = v_{0x} + a_xt$$
$$v_y = v_{0y} + a_yt$$
$$v_z = v_{0z} + a_zt$$

- 位矢分量式：

$$x = x_0 + v_{0x}t + \frac{1}{2}a_xt^2$$
$$y = y_0 + v_{0y}t + \frac{1}{2}a_yt^2$$
$$z = z_0 + v_{0z}t + \frac{1}{2}a_zt^2$$

注意，各分量系数可正可负。

## 匀加速直线运动

> **匀加速直线运动**：加速度为常矢量，且与初速度共线的运动。

**速度**：$v = v_0 + at$

**位矢**：$x = x_0 + v_0 t + \frac{1}{2} at^2$

联立两式，消去 $t$，得到速度与位置的关系：

$$v^2 - v_0^2 = 2a(x - x_0)$$

## 自由落体运动

> **自由落体运动**：只有重力作用，加速度为 $\boldsymbol{a} = \boldsymbol{g}$ 初速度为 $\boldsymbol{0}$ 的匀加速直线运动。
>
> 地面表面 $|\boldsymbol{g}| \approx 9.8 m/s^2$

若以起点为原点，取 $y$ 轴向下为正方向，则

$$\begin{aligned}
v &= gt \\
y &= \frac{1}{2} gt^2 \\ 
v^2 &= 2gy
\end{aligned}$$