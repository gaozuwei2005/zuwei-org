---
title: 大学物理 | 3.4 质心
date: 2024-11-24
summary: 质心、重心
---

> **质心**：质点系（离散质点系）中一个特殊的点，其位矢为
>
> $$\boldsymbol{r_C} = \frac{\sum_{i} m_i\boldsymbol{r_i}}{\sum_{i} m_i} = \frac{\sum_{i} m_i\boldsymbol{r_i}}{m}$$
>
> 对于连续物体，质心位矢可用积分得到
>
> $$\boldsymbol{r_C} = \frac{\int \boldsymbol{r} \mathrm d m}{\int \mathrm d m} = \frac{\int \boldsymbol{r} \mathrm d m}{m}$$

以上定义式都可写成分量式。

**物理意义**：对各个质点进行加权平均，权重为质量越重的质点，就越有话语权。

质量均匀对称体，其质心在**几何中心**上。

把质点系的一部分看成质量集中的单一质点，计算总共质点系的质心时，这一部分就可以用单一质点来计算。

对于空心的体，可以用减法求质心。

> **重心**：各质点所受重力的合力的作用点。
>
> $$\boldsymbol{r}\_{C,\boldsymbol{g}} = \frac{\sum\_{i} m_i  \boldsymbol{gr\_i}}{\sum\_{i} m\_i\boldsymbol{g}}$$
>
>
> 在均匀重力场中，重心和质心重合。原因是各处 $\boldsymbol{g}_i$ 均相等
>
> $$\boldsymbol{r}\_{C,\boldsymbol{g}} = \frac{\sum\_{i} m_i  \boldsymbol{r\_i}}{\sum_\{i} m\_i} = \boldsymbol{r}\_C$$