---
title: 大学物理 | 1.7 相对运动
date: 2024-11-24
summary: 伽利略速度变换
---


## 伽利略速度变换

### 下标

在位移下标中，**第一个字母代表运动物体，第二个字母代表参考物**。如 $\boldsymbol{r}_{SE}$ 表示地面参考系中小球的位移。

- $S$：Sphere 小球；
- $V$：Vehicle 小车；
- $E$：Earth 地面。

### 推导
  
在参考系 $E$（地面参考系）中，

$$\Delta \boldsymbol{r} = \Delta \boldsymbol{r}\_{SE} = \Delta \boldsymbol{r}\_{SV} + \Delta \boldsymbol{r}\_{VE}$$

在参考系 $V$（小车参考系）中，

$$\Delta \boldsymbol{r'} = \Delta \boldsymbol{r}_{SV}$$

故

$$\Delta \boldsymbol{r} = \Delta \boldsymbol{r'} + \Delta \boldsymbol{r}_{VE}$$

两边同除 $\Delta t$ 并令 $\Delta t \to 0$ 得

$$\boldsymbol{v} =  \boldsymbol{v'} + \boldsymbol{v}_{VE} = \boldsymbol{v'} + \boldsymbol{u}$$

- $\boldsymbol{v}$：绝对速度
- $\boldsymbol{v'}$：相对速度
- $\boldsymbol{u}$：牵连速度

> **伽利略速度变换**：绝对速度 $=$ 相对速度 $+$ 牵连速度
>
> **推论**：若两参考系间相对静止，则 $\boldsymbol{u} = \boldsymbol{0}, \boldsymbol{v} = \boldsymbol{v'}$，即质点在两参考系中速度相同。

两边同除 $\Delta t$ 并令 $\Delta t \to 0$ 得

$$\boldsymbol{a} = \boldsymbol{a'} + \boldsymbol{a_0}$$

> **伽利略加速度变换**：绝对加速度 $=$ 相对加速度 $+$ 牵连加速度
>
> **推论**：若两参考系间相对运动为匀速直线运动，则 $\boldsymbol{a_0} = \boldsymbol{0}, \boldsymbol{a} = \boldsymbol{a'}$，即质点在两参考系中加速度相同。

说明：

- 速度的变换不等同于速度的合成。前者在两个不同参考系下讨论，后者在同一参考系下讨论。
- 伽利略速度变换只适用于两参考系相对速度**远小于真空光速**的情形。

