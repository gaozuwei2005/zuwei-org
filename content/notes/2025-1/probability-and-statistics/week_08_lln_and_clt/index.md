---
title: 概率论与数理统计 | Week 8 大数定律、中心极限定理
date: 2025-11-05
summary: 随机序列的收敛性、大数定律、中心极限定理
---


# 5.0 随机序列的收敛性

**随机变量序列**：$\{X_n\} = X_1, X_2, X_3, \cdots$，每个元素都是随机变量。

**相互独立的随机变量序列**：随机变量序列中，元素间相互独立。

**依概率收敛**：若随机变量序列 $\{X_n\}$ 对任意 $\epsilon > 0$ 有 $$\displaystyle \lim_{n \to \infty} P\{|X_n - X| < \epsilon\} = 1$$则称 $\{X_n\}$ 依概率收敛于 $X$，记作 $X_n \xrightarrow{P} X$ 或 $X_n - X \xrightarrow{P} 0$

**函数依概率收敛**：若 $X_n \xrightarrow{P} a, Y_n \xrightarrow{P} b$，且 $g(x, y)$ 在 $(a,b)$ 连续，则 $g(X_n, Y_n) \xrightarrow{P} g(a,b)$.

# 5.1 大数定律（LLN）


| 名称          | 前提                                                                                                | 结论                                                                                   | 备注                                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| 伯努利大数定律     | $n_A$ 是 $n$ 次独立重复试验中事件 $A$ 发生的次数，且 $A$ 发生的概率为 $p$                                                 | $$\frac{n_A}{n} \xrightarrow{P} p$$                                                  | 可以用频率近似代替概率（**依概率稳定**）。<br>频率与概率有较大偏差 $\displaystyle \left\lvert\frac{n_A}{n} - p\right\rvert \ge \epsilon$ 是小概率事件。 |
| 切比雪夫大数定律    | 相互独立的随机变量序列 $\{X_n\}$ 中，每个随机变量具有**相同的数学期望 $E(X_k) = \mu$ 和方差 $D(X_k) = \sigma^2$**                | $$\frac{1}{n} \sum_{k = 1}^n X_k \xrightarrow{P} \mu$$                               | 说明算术平均值是依照项数增加依概率收敛的意义下，逼近某个常数。<br>                                                                                 |
| 辛钦大数定律      | 相互独立的随机变量序列 $\{X_n\}$ 中，每个随机变量**独立同分布**，且 $E(X_k) = \mu$                                          | $$\frac{1}{n} \sum_{k = 1}^n X_k \xrightarrow{P} \mu$$                               |                                                                                                                     |
| 切比雪夫大数定律弱化1 | 相互独立的随机变量序列 $\{X_n\}$ 中，每个随机变量数学期望 $E(X_k) = \mu_k$ ，且方差**有界** $D(X_k) = \sigma_k^2 \le \sigma^2$ | $$\frac{1}{n} \sum_{k = 1}^n X_k \xrightarrow{P}\frac{1}{n} \sum_{k = 1}^n \mu_k$$   |                                                                                                                     |
| 切比雪夫大数定律弱化2 | 随机变量序列 $\{X_n\}$                                                                                  | $$\lim_{n \rightarrow\ \infty}\frac{1}{n^2} D\left( \sum_{k = 1}^n X_k \right) = 0$$ |                                                                                                                     |

## 5.2 中心极限定理（CLT）

**林德贝格-列维中心极限定理（The Lindberg-Levy Central Limit Theorem）**：设独立同分布的随机变量 $X_1, X_2, \cdots,$ 具有期望和有限方差 $E(X_k) = \mu,\ D(X_k) = \sigma^2 > 0$，那么他们的标准化变量 $$Y_n = \frac{\displaystyle\sum_{k = 1}^n X_k - n\mu}{\sqrt{n} \sigma}$$ 在 $n$ 充分大时满足标准正态分布 $Y_n \sim N(0,1)$ 即 $$\lim_{n \to \infty} P\{Y_n \le x\} = \int_{-\infty}^x \frac{1}{\sqrt{2\pi}} e^{-\frac{t^2}{2}} \mathrm dt = \Phi(x)$$
或可以写成 $\overline{X} \sim N(\mu, \sigma^2 / n)$.

**棣莫佛-拉普拉斯中心极限定理（De Moffle-Laplace's Central Limit Theorem）**：随机变量都是伯努利分布，当 $n$ 充分大时，有 $$b(n,p) \xrightarrow{n \to \infty} N(np, np(1 - p))$$
**李雅普诺夫中心极限定理（Lyapunov's Central Limit Theorem）**：设独立随机变量 $X_1, X_2, \cdots,$ 具有期望和有限方差 $E(X_k) = \mu_k,\ D(X_k) = \sigma_k^2 > 0$，并且 *Lyapunov 条件* 成立，即 $$\exists \delta >0,\ \lim_{n \to \infty} \frac{1}{B^{2 + \delta}} \sum_{k = 1}^n E\left\\{ |X_k - \mu_k|^{2 + \delta} \right\\} = 0,\ 其中\ B_n^2 = \sum_{k=1}^n \sigma_k^2$$ 那么在 $n$ 充分大时，其标准化变量是正态分布 $$Y_n = \frac{\displaystyle \sum_{k = 1}^n X_k - \sum_{k = 1}^n \mu_k}{B_n},\quad \lim_{n \to \infty} Y_n \sim N(0, 1)$$
在 $n$ 充分大时，总和也是一个正态分布 $\displaystyle \sum_{k = 1}^n X_k \sim N\left(\sum_{k = 1}^n\mu_k,B_n^2\right)$.

**大数定律和中心极限定理的关系**：
- 大数定律给出无穷多次试验的平均接近均值
- 中心极限定理给出无穷多次试验的平均在均值附近呈正态分布，方差趋向于 $0$。