---
title: 大学物理 | 3.8 质点系的角动量定理
date: 2024-11-28
summary: 质点系的角动量定理、质点系的角动量守恒定律、轻绳与轻杆
---

## 质点系的角动量定理

质点系对某点的总角动量为

$$\boldsymbol{L} = \sum_i \boldsymbol{L}_i = \sum_i \boldsymbol{r}_i \times \boldsymbol{p}_i$$

两边对时间求导，并记 $\boldsymbol{F}\_i, \boldsymbol{f}\_{ij}$ 分别为质点 $i$ 受到的外力和第 $j$ 个质点对它的内力 $(j \ne i)$。

$$\begin{aligned}
\frac{\mathrm d\boldsymbol{L}}{\mathrm dt} &= \sum\_i \boldsymbol{M}_i \\\\
&= \sum\_i \boldsymbol{r}\_i \times \left( \boldsymbol{F\_i} + \sum\_{j \ne i} \boldsymbol{f}\_{ij} \right) \\\\
&= \sum\_i \boldsymbol{r}\_i \times \boldsymbol{F\_i} + \sum\_{i \ne j}  (\boldsymbol{r}\_i \times \boldsymbol{f}\_{ij} + \boldsymbol{r}\_j \times \boldsymbol{f}\_{ji}) \\\\
&= \sum\_i \boldsymbol{r}\_i \times \boldsymbol{F\_i} + \sum\_{i \ne j} -(\boldsymbol{r}\_i - \boldsymbol{r}\_j) \times \boldsymbol{f}\_{ij}
 \end{aligned}$$

由于 $(\boldsymbol{r}\_i - \boldsymbol{r}\_j)$ 与  $\boldsymbol{f}\_{ij}$ 反向平行，故此处叉乘为 $\boldsymbol{0}$，因此有以下定理：

> **质点系的角动量定理**：一个质点系对于某定点所受的合外力矩等于质点系对该点的总角动量对时间的导数。
>
> $$\frac{\mathrm d \boldsymbol{L}}{\mathrm d t} = \boldsymbol{M}$$

## 质点系的角动量守恒定律

> **质点系的角动量守恒定律**：当质点对某顶点的合外力矩为 $\boldsymbol{0}$ 时，该质点系对该顶点的角动量将保持不变
>
> $$ \boldsymbol{M} = \boldsymbol{0} \Leftrightarrow \boldsymbol{L} = const$$

### 固定转轴圆盘的运动

一般而言，对于固定转轴的圆盘。如果质心在圆心转轴上，由于转轴固定，所以质心不动，一定有**动量守恒**，合外力为零。

$$\boldsymbol{F}_a + \sum_i \boldsymbol{F}_i = \boldsymbol{0}$$

其中 $\boldsymbol{F}_a$ 为转轴对系统施加的力。

若质点不在圆心上，那么圆盘转动相当于质心做圆周运动，因此**动量不守恒**。

对转轴的合力矩

$$\boldsymbol{M} = \boldsymbol{0} \times \boldsymbol{F}_a + \sum_i \boldsymbol{r}_i \times \boldsymbol{F}_i = \sum_i \boldsymbol{r}_i \times \boldsymbol{F}_i$$

因此，我们无需考虑转轴施加的力。只需将各质点的力矩相加看看是否为 $\boldsymbol{0}$，即可判断是否角动量守恒。

### 合外力为零与角动量守恒

- 若所有外力都共线，且合外力为零（如相互作用力），则这些外力对任何点的合外力矩均为 $\boldsymbol{0}$；
- 若质点系合外力为 $\boldsymbol{0}$，并不代表该质点系的合外力矩为 $\boldsymbol{0}$（作用点的位矢不一样）。
- 若质点系不受任何外力，则合外力矩一定为 $\boldsymbol{0}$。

## 轻绳与轻杆

- 轻绳只传递沿着其方向的张力（拉力）；
- 轻杆可传递沿着其方向的张力（拉力）和压力，还可以传递垂直于自身方向的切力（剪力）。
- 