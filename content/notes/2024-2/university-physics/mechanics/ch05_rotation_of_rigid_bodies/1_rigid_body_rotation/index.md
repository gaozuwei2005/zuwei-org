---
title: 大学物理 | 5.1 刚体转动的描述
date: 2024-11-22
summary: 刚体、平动、转动
---


## 刚体

> **刚体**：受力时不改变形状和体积的物体。

固体的理想化模型：无穷多质量微元（质元）组成的质点系。外力作用下，各个微元相对位置不变。

## 刚体运动

刚体运动分为平动和转动。

### 平动的定义

> **平动**：刚体中任意两个质点的连线在运动中始终保持平行。

### 转动的定义

> **转动**：只研究**定轴转动**（转轴位置和方向固定、各质元角量相同）

> **转动平面**：垂直于转轴的平面。
>
> 刚体中各质元都在转动平面内，绕着转动平面和转轴交点，做圆周运动。

> **角位移**：
>
> $$\mathrm d\theta = \frac{\mathrm ds}{r} = \theta(t + \mathrm dt) - \theta (t)$$

> **角速度**：和圆周运动相似。
>
> $$\boldsymbol{\omega} = \frac{\mathrm d \theta}{\mathrm dt}$$


> **角加速度**：
>
> $$\alpha = \frac{\mathrm d \omega}{\mathrm dt} = \frac{\mathrm d^2 \theta}{\mathrm dt^2}$$


以上均为矢量，其方向是由右手螺旋法则确定。



- **角量与线量的关系**：

$$\boldsymbol{v} = \boldsymbol{w} \times \boldsymbol{r}$$

$$\boldsymbol{a} = \boldsymbol{a}_t + \boldsymbol{a}_n = \boldsymbol\alpha \boldsymbol{r} + \boldsymbol{\omega}^2 \boldsymbol{r}$$

- **匀加速转动**：类似于匀加速直线运动，有三条基本公式.

$$\begin{aligned}
\omega &= \omega_0 + \alpha t \\\\
\theta &= \theta_0 + \frac{1}{2} \alpha t^2 \\\\
\omega^2 - \omega_0^2 &= 2 \alpha (\theta - \theta_0) \\\\
\end{aligned}$$

一般可以把运动分解为：绕每一转轴的转动 $+$ 随着转轴的平动。（单质点只有平动）

刚体的任意运动，均可分解为整体随刚体任意一点的平动加绕着该点的转动。为了分解能量方便，一般取质心。

