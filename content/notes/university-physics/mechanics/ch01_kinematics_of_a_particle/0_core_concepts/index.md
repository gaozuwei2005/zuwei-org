---
title: 大学物理 | 1.0 核心知识
date: 2024-12-31
summary: 参考系、质点、加速度、匀加速运动、抛体运动、圆周运动、相对运动
---

# 1.1 参考系

**运动的相对性**：物体运动的形式随参考物的不同而不同。

一个坐标系和**一套同步的钟**(为防止高速运动时钟不同步)，构成一个坐标系。

# 1.2 质点的位矢、位移的速度

$\Delta \boldsymbol{r}$ 不等同于 $\Delta r$。前者是位移矢量，后者是位矢长度差（标量）。

我们可以用瞬时路程代替瞬时位移大小，来计算瞬时速度：$\displaystyle v = \lim_{\Delta t \to 0} \frac{|\Delta \boldsymbol{r}|}{\Delta t} = \lim_{\Delta t \to 0} \frac{\Delta s}{\Delta t}$

# 1.3 加速度

求导和积分是 $r \leftrightarrow v \leftrightarrow a$ 之间的渠道。

对于一个矢量，有两种表示方式：第一种是用分量式 $\boldsymbol{i}, \boldsymbol{j}, \boldsymbol{k}$，第二种是大小和夹角 $|\boldsymbol{r}|, \theta$。依据题目来选择。

# 1.4 匀加速运动

$r = r_0 + v_0t + \dfrac{1}{2}at^2$

$v^2 - v_0^2 = 2ax$

无初速的变形：$a = \dfrac{v^2}{2x}$，$x = \dfrac{v^2}{2a}$，$t = \sqrt{\dfrac{2h}{g}}$.

# 1.5 抛体运动

分量式：$x = v_0\cos \theta t$，$y = v_0\sin \theta t - \dfrac{1}{2} gt^2$

到最高点时间：$T = \dfrac{2v_0\sin \theta}{g}$，最大高度 $Y = \dfrac{v_0^2 \sin^2 \theta}{2g}$，当 $\theta = 45 ^\circ$ 时最大。

抛体轨道函数：$y = x \tan \theta - \dfrac{1}{2} \dfrac{gx^2}{v_0^2 \cos^2 \theta}$.

# 1.6 圆周运动

圆周运动中线速度、角速度和周期关系：$v = \omega R$, $T = \dfrac{2 \pi}{\omega} = \dfrac{2 \pi R}{v}$.

角速度也是有方向的，四指旋向转动方向的右手螺旋定责可得角速度的方向。且有 $\boldsymbol{v} = \boldsymbol{\omega} \times \boldsymbol{R}$.

圆周运动的加速度可视做切向加速度和法向加速度的合成：$\boldsymbol{a} = \boldsymbol{a}_t + \boldsymbol{a}_n$, $a = \sqrt{a_t^2 + a_n^2}$.

切向加速度代表速率变化快慢，可引出角加速度：$a_t = \dfrac{\mathrm d v}{\mathrm dt} = R \alpha$，方向与线 / 角速度方向相同。

法向加速度的大小通过圆内偏角等腰三角形和速度偏角等腰三角形相似得出：$a_n = \dfrac{v^2}{R} = \omega^2 R$，方向指向圆心，与速度方向垂直。

# 1.7 相对运动

$\boldsymbol{r}\_{AB}, \boldsymbol{v}\_{AB}, \boldsymbol{a}\_{AB}$：物体 $A$ 在 $B$ 为参考系的位移、速度、加速度。

连带式：$\boldsymbol{r}\_{SE} = \boldsymbol{r}\_{SV} + \boldsymbol{r}\_{VE}$

伽利略速度变换：$\boldsymbol{r}\_{SE} = \boldsymbol{r}\_{SV} + \boldsymbol{r}\_{VE}$

加速度变换：$\boldsymbol{a}\_{SE} = \boldsymbol{a}\_{SV} + \boldsymbol{a}\_{VE}$