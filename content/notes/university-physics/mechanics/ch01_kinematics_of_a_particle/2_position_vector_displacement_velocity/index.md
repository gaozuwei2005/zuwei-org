---
title: 大学物理 | 1.2 质点的位矢、位移和速度
date: 2024-11-19
summary: 位矢、位移、速度
---

## 位矢

> **位矢（也称位置矢量、径矢）**：从原点指向质点位置的有向线段，同时也是位置坐标。
>
> **质点的运动函数 / 方程**：
> 
> - 位矢式：$\boldsymbol{r} = \boldsymbol{r}(t)$
>
> - 坐标形式 / 分量式：$x = x(t), y = y(t), z = z(t)$.

以 $\boldsymbol{i,j,k}$ 为三个单位矢量，则

$$\boldsymbol{r}(t) = x(t)\boldsymbol{i} + y(t)\boldsymbol{j} + z(t)\boldsymbol{k}$$

$$r = |\boldsymbol{r}| = \sqrt{x^2 + y^2 + z^2}$$

三个分量式消去参数 $t$，可得轨迹方程。

## 位移

### 位移的定义

> **位移（位移矢量）**：一段时间内位置的改变（位矢的改变）。
> $$\Delta \boldsymbol{r} = \boldsymbol{r}(t + \Delta t) - \boldsymbol{r} (t)$$

而 $\Delta r = \Delta |\boldsymbol{r}|$，是指一段时间内**位矢长度（到原点距离）的改变**。

两种量的模的对比：

- **位移的模**：$|\Delta \boldsymbol{r}| = |\boldsymbol{r}(t + \Delta t) - \boldsymbol{r} (t)| = \sqrt{\Delta x^2 + \Delta y^2 + \Delta z^2}$
- **位矢差的模**：$\Delta r = \Delta |\boldsymbol{r}| = \sqrt{x'^2 + y'^2 + z'^2} - \sqrt{x^2 + y^2 + z^2}$
- 当 $\Delta \boldsymbol{r}$ 的反向延长线过原点时，$|\Delta \boldsymbol{r}| = \Delta r$；当 $\Delta \boldsymbol{r}$ 的延长线过原点时，$|\Delta \boldsymbol{r}| = - \Delta r$；

### 位移的特点

- **位移与路径无关，只由始末位置决定。** 位移等于末位矢减去初位矢。
- **位移反映了运动的矢量性和叠加性。** 总位移等于各段分位移之和。
- **位移与参考点的关系**：
  - 当新参考点与原来相对静止时，唯一不变；
  - 当新参考点在 $\Delta t$ 时间内与原参考点位移为 $\Delta \boldsymbol{d}$，那么新位移为 $\Delta \boldsymbol{r'} = \Delta \boldsymbol{r} - \Delta \boldsymbol{d}$.
  - 特别地，当 $\Delta \boldsymbol{d} = \Delta \boldsymbol{r}$，时，新位移 $\boldsymbol{r'} = \boldsymbol{0}$.

## 速度

> **平均速度**： $\overline{\boldsymbol{v}} = \frac{\Delta \boldsymbol{r}}{t} = \frac{\Delta x}{\Delta t} \boldsymbol{i} + \frac{\Delta y}{\Delta t} \boldsymbol{j} + \frac{\Delta z}{\Delta t} \boldsymbol{k}$.
>
> 平均速度大小：$|\overline{\boldsymbol{v}}| = \sqrt{\frac{\Delta x}{\Delta t} + \frac{\Delta y}{\Delta t} + \frac{\Delta z}{\Delta t}}$.

> **瞬时速度（速度）**：$\boldsymbol{v} = \lim\limits_{\Delta t \to 0} \frac{\Delta \boldsymbol{r}}{\Delta t} = \frac{\mathrm{d} \boldsymbol{r} }{\mathrm{d} t}$.
>
> 对 $\Delta, \mathrm{d}$ 的区分：$\Delta x$ 表示 $x$ 的变化量，可大可小；$\mathrm{d}$ 表示微分，是无穷小量，$\Delta x \to 0 = \mathrm{d} x$。
> 
> **瞬时速度的方向**：沿着该时刻质点所在运动轨道的**切线**，指向运动的**前方**。

瞬时速度的分解：

$$\boldsymbol{v} = \frac{\mathrm{d} \boldsymbol{r} }{\mathrm{d} t} = \frac{\mathrm{d} (x \boldsymbol{i} + y \boldsymbol{j} + z \boldsymbol{k}) }{\mathrm{d} t} = v_x \boldsymbol{i} + v_y \boldsymbol{j} + v_z \boldsymbol{k} = \boldsymbol{v_x} + \boldsymbol{v_y} + \boldsymbol{v_z}$$

**质点的速度是各分速度的矢量和。（微分的可加性）**

**速度单位**：$m/s, km/h$

> **瞬时速率（速率）**：表示速度的大小。
>
> $$v = |\boldsymbol{v}| = \lim\limits_{\Delta t \to 0} \left|\frac{\Delta \boldsymbol{r}}{\Delta t}\right| = \lim\limits_{\Delta t \to 0} \frac{\left|\Delta \boldsymbol{r}\right|}{\Delta t} = \sqrt{v_x^2 + v_y^2 + v_z^2}$$

若 $v$ 为负，常用于直线运动，表示反方向运动，此时已经是矢量。

> **路程 $\Delta s$**：在 $\Delta t$ 时间内质点沿轨道经过的程度（轨迹长度）。

**路程 $\Delta s$ 与位移 $\Delta \boldsymbol{r}$** 的区别：

- 路程是标量，无方向，与中间过程有关。
- 位移是矢量，有方向，只与始末点有关，与中间过程无关。
- $|\Delta \boldsymbol{r}| \le \Delta s$.
  - 位移的模是两点间最短的路程。
  - 当质点做方向不变的直线运动时，二者取等。
  - $\lim\limits_{\Delta t \to 0} \Delta s = |\Delta \boldsymbol{r}|$，或者 $\mathrm{d} s = |\mathrm{d} \boldsymbol{r}|$

**瞬时速率等于路程、位移对时间的的导数：**

$$v = |\boldsymbol{v}| = \frac{|\mathrm{d}\boldsymbol{r}|}{\mathrm{d} t} = \frac{\mathrm{d} s}{\mathrm d t}$$


> **平均速率**：瞬时速率的平均值，路程与时间的比值。路程随时间的平均变化率。
>
> $$\overline v = \int v \mathrm d t = \frac{\Delta s}{\Delta t}$$