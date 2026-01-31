---
title: 概率论与数理统计 | Week 10~13 参数估计
date: 2025-11-12
summary: 点估计、区间估计、估计量的评选标准
---



**参数估计问题**：通过样本估计总体的某些参数或分布函数。

# 7.1 点估计

**点估计问题**：已知总体分布函数为 $F(x; \theta)$，其中 $\theta$ 未知。要根据样本 $X_1, X_2, \cdots, X_n$ 对 $\theta$ 估计。
## 7.1.1 矩估计法

**矩估计法**：对于连续性随机变量 $X$，其概率密度为 $f(x; \theta_1, \theta_2, \cdots, \theta_k)$，并且样本的 $l$ 阶矩 $\mu_l = E(X^l)$ 是关于 $\theta_1, \theta_2, \cdots, \theta_k$ 的函数，即 $$E(X^l) = \int_{-\infty}^{+\infty} x^l f(x; \theta_1, \theta_2, \cdots, \theta_k) \mathrm dx = \mu_l(\theta_1, \theta_2, \cdots, \theta_k)$$ 存在，那么如果求出样本的各阶矩 $A_l \ (l = 1,2, \cdots, k)$（称之为**矩估计值**），那么求解方程组 $$\begin{cases} \mu_l(\theta_1, \theta_2, \cdots, \theta_k) = A_l& l = 1, 2, \cdots, k\end{cases}$$
  即可求出各个**矩估计量** $\hat{\theta_1}, \hat{\theta_2}, \cdots,\hat{\theta_n}$。
  
（对于离散型随机变量也成立）

矩估计法的优点：简单易行，无需知道总体是什么分布。
矩估计法的缺点：没有利用总体分布类型的信息。

## 7.1.2 最大似然法

最大似然估计法的基本思想：选择能使结果有最大可能性的参数。

**似然函数**：记似然函数为参数使得取到样本（各个样本值相互独立）的联合概率（对于离散型随机变量）或联合密度（对于连续性随机变量）为 $$L(\theta) = \prod_{i = 1}^n f(x_i; \theta)$$
实际上，一般对于似然函数取对数 $$\ln L(\theta) = \sum_{i = 1}^n \ln f(x_i; \theta)$$

**最大似然估计法**：参数的近似取使得该样本概率最大的参数 $\displaystyle\hat \theta = \arg \max_{\theta \in \Theta} L(\theta)$.

$\hat \theta (x_1, x_2, \cdots, x_n)$ 是最大似然估计值，$\hat \theta (X_1, X_2, \cdots, X_n)$ 是最大似然估计量。

如果 $\theta$ 是连续凸函数，那么可以对其求导 $\displaystyle \frac{\mathrm d \ln L(\theta)}{\mathrm d \theta} = 0$，求解该方程即可得到 $\hat \theta$.

# 7.3 估计量的评选标准

## 7.3.1 无偏性

思想：希望估计值的期望值等于位置参数的真值。

**无偏估计量**：满足 $E(\hat \theta) = \theta$ 的参数估计量。

## 7.3.2 有效性

思想：希望估计值的方差越小越好。

**有效**：对于两个 $\theta$ 的估计量 $\hat \theta_1,\ \hat \theta_2$，若 $D(\hat \theta_1) \le D(\hat \theta_2)$，则称 $\hat \theta_1$ 较 $\hat \theta_2$ 有效。

## 7.3.3 相合性

**相合估计量**：对于 $\theta$ 的估计量 $\hat \theta$，若 $\displaystyle \forall \epsilon > 0,\ P\{|\hat\theta - \theta| < \epsilon\} = 1$，即 $\hat\theta \xrightarrow{P} \theta$，则称 $\hat \theta$ 是 $\theta$ 的相合估计量。

*矩估计法与最大似然估计法一般都具有相合性。*

若 $\displaystyle\lim_{n \to \infty} D(\hat \theta) = 0$，则 $\hat \theta$ 是 $\theta$ 的相合估计量。

# 7.4 区间估计

**区间估计**：对于 $X$ 的分布函数 $F(x; \theta)$，给定 $\alpha\ (0 < \alpha < 1)$，如果有两个统计量 $\underline{\theta}(X_1, \cdots, X_n),\ \overline{\theta}(X_1, \cdots, X_n)$ 使得 $$P\{\underline{\theta}(X_1, \cdots, X_n) < \theta < \overline{\theta}(X_1, \cdots, X_n)\} = 1 - \alpha$$ 其中  $(\underline \theta, \overline \theta)$ 为 $\theta$ 的双侧 $1 - \alpha$ 置信区间（双侧置信下限到双侧置信上限）.

**置信水平**：样本算出的置信区间包含带估计参数真实值 $\theta$ 的**概率**，这里为 $1 - \alpha$.

置信水平和估计精度的关系：
- 置信水平 $\uparrow$，置信区间长度 $\uparrow$，参数估计精度 $\downarrow$.
- 置信水平 $\downarrow$，置信区间长度 $\downarrow$，参数估计精度 $\uparrow$.

# 7.5 正态总体均值与方差的区间估计

**求置信区间的一般步骤**：
1. 寻找参数 $\theta$ 的良好的点估计 $T(X_1, X_2, \cdots, X_n)$（无偏、有效、相合）
2. 寻找待估参数 $\theta$ 与估计量 $T$ 的已知分布的函数 $W(T, \theta)$，称为**枢轴量**。
3. 根据 $W(T, \theta)$ 的分布，确定 $(a,b)$ 使得 $P\{a < W < b\} = 1 - \alpha$
4. 等价变形 $a < W < b$ 得到 $\underline{\theta} < \theta < \overline{\theta}$.

**正态总体均值、方差的置信区间（置信度 $1-\alpha$）：**

大量引用了 [Week 9 样本及抽样分布](../week_09_sampling_distributions) 的内容。

| 类型         | 待估参数                                          | 参数前提                                              | 点估计                                 | 枢轴量及其分布                                                                                                                                                                                                                  | 置信区间                                                                                                                                    |
| ---------- | --------------------------------------------- | ------------------------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| **一个正态总体** | $\displaystyle \mu$                           | $\displaystyle \sigma^2$ 已知                       | $\overline X$                       | $\displaystyle Z=\frac{\overline{X}-\mu}{\sigma/\sqrt{n}}\sim N(0,1)$                                                                                                                                                    | $\displaystyle \left( \overline{X}\pm \frac{\sigma}{\sqrt{n}} z_{\alpha/2} \right)$                                                     |
|            | $\displaystyle \mu$                           | $\displaystyle \sigma^2$ 未知                       | $\overline{X}$                      | $\displaystyle t=\frac{\overline{X}-\mu}{S/\sqrt{n}}\sim t(n-1)$                                                                                                                                                         | $\displaystyle \left( \overline{X}\pm \frac{S}{\sqrt{n}} t_{\alpha/2}(n-1) \right)$                                                     |
|            | $\displaystyle \sigma^2$                      | $\displaystyle \mu$ 未知                            | $S^2$                               | $\displaystyle \chi^2=\frac{(n-1)S^2}{\sigma^2}\sim \chi^2(n-1)$                                                                                                                                                         | $\displaystyle \left( \frac{(n-1)S^2}{\chi^2_{\alpha/2}(n-1)},\ \frac{(n-1)S^2}{\chi^2_{1-\alpha/2}(n-1)} \right)$                      |
| **两个正态总体** | $\displaystyle \mu_1-\mu_2$                   | $\displaystyle \sigma_1^2,\sigma_2^2$ 已知          | $\overline{X} - \overline{Y}$       | $\displaystyle Z=\frac{(\overline{X}-\overline{Y})-(\mu_1-\mu_2)}{\sqrt{\sigma_1^2/n_1+\sigma_2^2/n_2}}\sim N(0,1)$                                                                                                      | $\displaystyle \left( \overline{X}-\overline{Y}\pm z_{\alpha/2}\sqrt{\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2}} \right)$            |
|            | $\displaystyle \mu_1-\mu_2$                   | $\displaystyle \sigma_1^2=\sigma_2^2=\sigma^2$ 未知 | $\overline{X} - \overline{Y}$       | $\displaystyle t=\frac{(\overline{X}-\overline{Y})-(\mu_1-\mu_2)}{S_w\sqrt{\displaystyle\frac{1}{n_1}+\frac{1}{n_2}}}\sim t(n_1+n_2-2)$<br>其中 $\displaystyle S_w = \sqrt{\frac{(n_1-1)S_1^2 + (n_2-1)S_2^2}{n_1+n_2-2}}$ | $\displaystyle \left( \overline{X}-\overline{Y} \pm t_{\alpha/2}(n_1+n_2-2)\ S_w \sqrt{\frac{1}{n_1}+\frac{1}{n_2}} \right)$            |
|            | $\displaystyle \frac{\sigma_1^2}{\sigma_2^2}$ | $\displaystyle \mu_1,\mu_2$ 未知                    | $\displaystyle \frac{S_1^2}{S_2^2}$ | $\displaystyle F=\frac{S_1^2/\sigma_1^2}{S_2^2/\sigma_2^2}\sim F(n_1-1,n_2-1)$                                                                                                                                           | $\displaystyle \left( \frac{S_1^2}{S_2^2} \frac{1}{F_{\alpha/2}(n_1-1,n_2-1)},\ \frac{S_1^2}{S_2^2} F_{\alpha/2}(n_2-1, n_1-1) \right)$ |

