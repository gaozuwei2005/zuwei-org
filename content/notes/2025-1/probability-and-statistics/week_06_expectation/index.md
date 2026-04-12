---
title: 概率论与数理统计 | Week 6 随机变量函数的分布、期望
date: 2025-10-29
summary: 两个随机变量的函数的分布、数学期望
---


# 3.5 两个随机变量的函数的分布

对于两个随机变量 $X, Y$，已知它们的联合分布，则它们的函数的分布为：

| 类型                                  | 分布                                                                                                                                                               |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 和分布 $Z = X+Y$                       | 离散：$\displaystyle P\\{Z = r\\} = \sum_{i = 0}^r a_i b_{r - i}$<br>连续：$\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} f(z - y, y) \mathrm dy$<br>（或写成 $x$ 为被积变量） |
| 商分布 $\displaystyle Z = \frac{X}{Y}$ | $\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} \lvert y\rvert f(zy,y)\mathrm dy$                                                                               |
| 差分布 $Z = X - Y$                     | $\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} f(z + y, y) \mathrm dy$<br>（或写成 $x$ 为被积变量）                                                                      |
| 积分布 $Z = XY$                        | $\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} f\left(x ,\frac{z}{x}\right)\frac{1}{\lvert x\rvert}\mathrm dy$                                                 |
| 最大值分布 $M = \max(X,Y)$               | $F_M(z) = P\\{X \le z, Y \le z\\} = F(z, z)$                                                                                                                     |
| 最小值分布 $N = \min(X,Y)$               | $F_N(z) = P\\{X \ge z, Y \ge z\\} = 1 - F_X(z) - F_Y(z) + F(z,z)$                                                                                                |

一般函数：若要求 $Z = g(X,Y)$ 的密度，可以选取新的变量向量 $(Z, Y)$，将原变量表示为 $$X = h(Z, Y),\quad Y = Y$$
那么雅各比矩阵为 $\begin{bmatrix} \partial h/\partial z & \partial h/\partial y \\ 0 & 1 \end{bmatrix}$，行列式为 $\partial h / \partial z$.

因此 $\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} \left|\frac{\partial h}{\partial z}\right| f(h(z,y),y)\mathrm dy$.


**独立的正态分布的随机变量的和分布**：  
- 若$X_1 \sim N(\mu_1, \sigma_1^2), X_2 \sim N(\mu_2, \sigma_2^2)$，且 $X_1, X_2$ 独立，则 $X_1 + X_2 \sim N(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$
- 对于多个独立正态变量，有 $\displaystyle \sum_{i = 1}^n a_iX_i \sim N\left( \sum_{i = 1}^n a_i\mu_i, \sum_{i = 1}^n a_i^2\sigma_i^2\right)$
- 对于多个同正态分布变量，有 $\displaystyle \overline{X} = \sum_{i = 1}^n X_i \sim N\left( \mu, \frac{\sigma^2}{n} \right)$

**独立的随机变量的最值分布**：  
- $M = \max(X_1, X_2, \cdots, X_n)$ 的分布函数为 $\displaystyle F_M(z) = \prod_{i = 1}^n F_{X_i}(z)$
- $N = \min(X_1, X_2, \cdots, X_n)$ 的分布函数为 $\displaystyle F_N(z) = 1 - \prod_{i = 1}^n (1 - F_{X_i}(z))$
- 若随机变量是同分布的，则 $F_M(z) = F^n(z),\ F_N(z) = 1 - (1 - F(z))^n$

# 4.1 数学期望

**离散型随机变量的数学期望**：对于离散型随机变量 $X$，对应分布律为 $P\{X = x_k\} = p_k,\ k = 1, 2, \cdots$，则 $X$ 的数学期望 $E(x)$ 为 $$E(X) = \displaystyle \sum_{k = 1}^\infty x_k p_k$$其中要满足该级数 **绝对收敛**。

数学期望是常数而非变量，体现了随机变量的平均值。

**重要离散型随机变量的数学期望**：

| 类型     | 参数 / 分布律                                                                       | 期望                                                                                                                                                                             |
| ------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0-1 分布 | $\displaystyle P\\{X = i\\} = \begin{cases}p,& i = 1\\\\1-p, & i=0\end{cases}$ | $E(X) = p$                                                                                                                                                                     |
| 二项分布   | $X \sim b(n, p)$                                                               | $\displaystyle \begin{aligned}E(X) &= \sum_{k = 0}^n k \binom{n}{k} p^k(1-p)^{n-k} \\\\&=np\sum_{k = 1}^n \binom{n-1}{k-1} p^{k-1}(1-p)^{n-k} \\\\&=np\end{aligned}$           |
| 泊松分布   | $X \sim \pi(\lambda)$                                                          | $\begin{aligned}E(X) &=\sum_{k=0}^\infty k\frac{\lambda^k}{k!}e^{-\lambda}\\\\&=\lambda e^{-\lambda} \sum_{k=0}^\infty \frac{\lambda^{k-1}}{(k-1)!}\\\\&=\lambda\end{aligned}$ |

**一维连续型随机变量的数学期望**：对于连续型随机变量 $X$，对应密度函数为 $f(x)$，则 $$E(X) = \int_{-\infty}^{\infty} xf(x)\mathrm dx$$其中要满足该积分 **绝对收敛**。

**重要离散型随机变量的数学期望**：

| 类型   | 参数 / 分布律                                                                                | 期望                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---- | --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 均匀分布 | $f(x) = \begin{cases}\dfrac{1}{b -a},& a < x < b \\\\ 0,& otherwise\end{cases}$         | $\displaystyle E(x) = \int_a^b \frac{x}{b-a}\mathrm dx = \frac{a+b}{2}$                                                                                                                                                                                                                                                                                                                                                                                    |
| 指数分布 | $f(x) = \begin{cases}\dfrac{e^{-x/\theta}}{\theta},& x > 0 \\\\ 0,& x \le 0\end{cases}$ | $\begin{aligned} E(x)&=\int_0^\infty \frac{xe^{-x/\theta}}{\theta}\mathrm dx \\\\&= -\int_0^{\infty} x\mathrm de^{-x/\theta} \\\\&= \left.-xe^{-x/\theta}\right\vert_0^\infty + \int_0^\infty e^{-x/\theta}\mathrm dx\\\\&=\theta \end{aligned}$                                                                                                                                                                                                           |
| 正态分布 | $X \sim N(\mu,\sigma^2)$                                                                | $$\begin{aligned}<br>E(X)<br>&= \int_{-\infty}^{\infty}<br>x \cdot \frac{1}{\sqrt{2\pi}\sigma}<br>e^{-\frac{(x-\mu)^2}{2\sigma^2}} \, dx \\\\<br>&= \int_{-\infty}^{\infty}<br>\frac{\sigma t + \mu}{\sqrt{2\pi}}<br>e^{-\frac{t^2}{2}} \, dt \qquad (t = \tfrac{x-\mu}{\sigma})\\\\<br>&= \mu<br>\end{aligned}$$<br>其中带 $\sigma t$ 的部分，由于是奇函数，因此积分为零<br>带 $\mu$ 的部分，有 $\displaystyle \int_{-\infty}^{\infty} e^{-\frac{t^2}{2}} \mathrm dt = \sqrt{2\pi}$ |

**一维随机变量函数的数学期望**：对于两个随机变量有 $Y = g(X)$，其中 $g$ 是连续函数，则
- 若 $X$ 是离散型随机变量，则 $\displaystyle E(Y) = E[g(X)] = \sum_{k = 1}^\infty g(x_k) p_k$，其中要满足级数绝对收敛；
- 若 $X$ 是连续型随机变量，则 $\displaystyle E(Y) = E[g(X)] = \int_{-\infty}^{+\infty} g(x)f(x)\mathrm dx$，其中要满足积分绝对收敛。