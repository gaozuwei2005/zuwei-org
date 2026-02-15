---
title: 大学物理 | 3.5 质心运动定理
date: 2024-11-25
summary: 质心的运动速度、质心运动定理
---


## 质心的运动速度

> **质心的运动速度**：对质心定义式两边除以 $\Delta t$ 并让 $\Delta t \to 0$，则可得到
>
> $$\boldsymbol{v}_c = \frac{\sum_i m_i \boldsymbol{v}_i}{m}$$

**物理意义**：质点系中各质点的速度以质量为权重的加权平均。

> **质心动量 $\boldsymbol{=}$ 系统总动量**
>
> 证明：由质心运动速度定义式可得：
> 
> $$m \boldsymbol{v}_C = \sum_i m_i \boldsymbol{v}_i$$
> 
> 相当于把总质量全部集中到质心，然后随质心一起运动。

若将每个质点的速度分解为

$$\boldsymbol{v}\_i = \boldsymbol{v}\_C + \boldsymbol{v}\_{iC}$$


$$\boldsymbol{p'} 
= \sum_i m\_i \boldsymbol{v}\_{iC} 
= \sum_i m\_i(\boldsymbol{v}\_{C} + \boldsymbol{v}\_{iC}) 
= m\boldsymbol{v}\_C + \sum\_i m_i\boldsymbol{v}\_{iC} 
= m\boldsymbol{v}\_C$$

故那么所有质点相对于质心的总动量为

$$\sum_i m_i\boldsymbol{v}_{iC} = \boldsymbol{0}$$

## 质心运动定理

> **质心运动定理**：系统所受合外力等于系统总质量乘质心加速度。

**证明**：对质心速度定义式两边对 $t$ 求导

$$m \boldsymbol{a}_C = \sum_i m_i\boldsymbol{a}_i = \sum_i \frac{\mathrm d (m_i \boldsymbol{v}_i)}{\mathrm dt} = \sum_i \frac{\mathrm d\boldsymbol{p}_i}{\mathrm dt} = \sum_i \boldsymbol{F}_i = \boldsymbol{F}$$