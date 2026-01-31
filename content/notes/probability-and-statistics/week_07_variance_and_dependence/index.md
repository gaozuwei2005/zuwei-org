---
title: 概率论与数理统计 | Week 7 期望、方差、协方差、相关系数
date: 2025-10-31
summary: 期望、方差、协方差、相关系数、矩/协方差矩阵
---


# 4.1 数学期望 (con'd)

**二维随机变量的数学期望**：
- 离散型随机变量：若 $(X,Y)$ 的联合概率分布为 $P\{X = x_i, Y = y_j\} = p_{ij},\ i, j = 1, 2, \cdots$，则 $$E(X) = \sum_{i}\sum_{j} x_i p_{ij}\qquad E(Y) = \sum_{i}\sum_{j} y_i p_{ij}$$
- 连续性随机变量：若 $(X,Y)$ 的概率密度函数为 $f(x,y)$，则 $$E(X) = \int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty} xf(x,y) \mathrm dx \mathrm dy\qquad E(Y) = \int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty} yf(x,y) \mathrm dx \mathrm dy$$

**二维随机变量函数的数学期望**：
- 离散型随机变量：若 $(X,Y)$ 的联合概率分布为 $P\{X = x_i, Y = y_j\} = p_{ij},\ i, j = 1, 2, \cdots$，且有 $$\sum_{i}\sum_{j} |g(x_i,y_j)|p_{ij} < +\infty$$则 $Z = g(x,y)$ 的数学期望为 $$E(Z) = \sum_{i}\sum_{j} g(x_i, y_j) p_{ij}$$
- 连续性随机变量：若 $(X,Y)$ 的概率密度函数为 $f(x,y)$，且有 $$\int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty} |g(x, y)|f(x,y) \mathrm dx \mathrm dy$$ 收敛，则 $Z = g(X,Y)$ 的数学期望为 $$E(Z) = \int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty} g(x, y)f(x,y) \mathrm dx \mathrm dy$$

**数学期望的性质**：
- **常数**：$E(C) = C$
- **线性性**：$\displaystyle E(kX) = kE(X),\quad E(X+Y) = E(X)+E(Y),\quad E\left(\sum_{i}c_iX_i\right)=\sum_i c_iE(X_i)$
- **乘积**：
	- 若 $X,Y$ 独立，则 $E(XY)=E(X)E(Y)$
	- 若 $X_1,X_2,\cdots,X_n$ 相互独立，则 $\displaystyle E\left(\prod_i X_i\right) = \prod_i E(X_i)$

# 4.2 方差
**一维随机变量的方差**：对于随机变量 $X$，若 $E[(X - E(X))^2]$  存在，则称其为 $X$ 的方差，记为 $D(X)$ 或 $Var(X)$，该数值刻画了随机变量的取值对于数学期望的**离散程度**。

**标准差 / 均方差**：$\sigma(X) = \sqrt{D(X)}$.


**方差计算**：
- 离散型随机变量：$\displaystyle D(X) = \sum_{k}[x_k - E(X)]^2p_k$
- 连续性随机变量：$\displaystyle D(X) = \int_{-\infty}^{+\infty} [x - E(X)]^2 f(x) \mathrm dx$
- **方差简化公式**：（几乎任何情况都能用）$$\begin{aligned}D(X) &= E[(X - E(X))^2] \\\\&= E[X^2 - 2XE(X) + E^2(X)] \\\\&= E(X^2) - 2E^2(X) + E^2(X) \\\\&= E(X^2)-E^2(X)\end{aligned}$$
**常见一维随机变量的期望和方差**：

|              分布               |                                        分布律 / 概率密度函数                                         |            期望            |              方差               |
| :---------------------------: | :-----------------------------------------------------------------------------------------: | :----------------------: | :---------------------------: |
|            0-1 分布             |      $$\displaystyle P\\{X = i\\} = \begin{cases}p,& i = 1\\\\1-p, & i=0\end{cases}$$       |       $$E(X) = p$$       |       $$D(X) = p(1-p)$$       |
|   二项分布<br>$X \sim b(n, p)$    | $$\displaystyle P\\{X = k\\} = \binom{n}{k} p^k (1 - p)^{n - k},\quad k = 0, 1, \cdots, n$$ |      $$E(X) = np$$       |      $$D(X) = np(1-p)$$       |
| 泊松分布<br>$X \sim \pi(\lambda)$ |       $$P\\{X = k\\} = e^{-\lambda} \frac{\lambda^k}{k!},\quad k = 0 , 1, 2,\cdots$$        |    $$E(X) = \lambda$$    |      $$D(X) = \lambda$$       |
|    均匀分布<br>$X \sim U(a,b)$    |  $$f(x) = \begin{cases}\dfrac{1}{b -a},& a < x < b \\\\ 0,& \text{otherwise}\end{cases}$$   | $$E(X) = \frac{a+b}{2}$$ | $$D(X) = \frac{(b-a)^2}{12}$$ |
|             指数分布              |  $$f(x) = \begin{cases}\dfrac{e^{-x/\theta}}{\theta},& x > 0 \\\\ 0,& x \le 0\end{cases}$$  |    $$E(X) = \theta$$     |      $$D(X) = \theta^2$$      |
| 正态分布<br>$X = N(\mu,\sigma^2)$ |         $$f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{ -\frac{(x - \mu)^2}{2\sigma^2} }$$         |      $$E(X) = \mu$$      |      $$D(X) = \sigma^2$$      |

**方差的性质**：
- **常数**：$D(C) = 0$
- **线性变换**：$D(CX) = C^2D(X),\quad D(X+ C) = D(X)$
- **随机变量相加**：$$\begin{aligned} D(X+Y)&=E[(X+Y-E(X+Y))^2]\\&=E\{[(X - E(X) ) + (Y - E(Y))]^2\} \\&=E[(X - E(X))^2] + E[(Y - E(Y))^2] + 2E[(X - E(X))(Y - E(Y))] \\&= D(X) + D(Y) + 2Cov (X, Y)\end{aligned}$$
  其中 $Cov(X,Y)$ 指两变量的协方差。
  当 $X, Y$ 相互独立，协方差为零，则 $D(X+Y) = D(X)+D(Y)$
- $D(X) = 0 \Leftrightarrow P\{X = E(X)\} = 1$
- **切比雪夫不等式**：$$P\left\{|X - E(X)| \ge \epsilon\right\} \le \frac{D(X)}{\epsilon^2}$$
  当方差越小，则随机变量取值在期望附近的概率越大。

# 4.3 协方差和相关系数

**协方差 (Covariance)**：随机变量 $X,Y$ 的协方差为 $$Cov(X,Y) = E\{[X - E(X)][Y - E(Y)]\}$$


协方差的**性质**：
- 交换律：$Cov(X,Y) = Cov(Y,X)$
- 线性性：$Cov(aX,bY) = abCov(X,Y),\quad Cov(X_1+X_2, Y) = Cov(X_1,Y)+Cov(X_2,Y)$
- $Cov(X,X) = E(X^2) - E^2(X) = D(X)$

协方差计算公式：
$$\begin{aligned} Cov(X,Y)&=E\{[X - E(X)][Y - E(Y)]\}\\\\&=E(XY) - E(X)E(Y)-E(Y)E(X) + E(X)E(Y)\\\\&=E(XY)-E(X)E(Y)\end{aligned}$$
因此若 $X,Y$ 独立，则 $Cov(X,Y) = 0$

**相关系数**：假设随机变量 $X,Y$ 的 $D(X) > 0, D(Y) >0$，则 $$\rho_{XY} = \frac{Cov(X,Y)}{\sqrt{D(X)}\sqrt{D(Y)}}$$
相关系数与线性拟合的关系：$$\begin{aligned}\min_{a, b} E\{[Y - (aX + b)]^2\} &= (1 - \rho_{XY}^2)D(Y) \\\\&=D[Y - (aX+b)] + E^2[Y - (aX+ b)]\end{aligned}$$
**相关系数的性质**：
- $|\rho_{XY}| \le 1$
- $|\rho_{XY}| = 1 \Leftrightarrow \exists a, b,\ P\{Y = aX+b\} = 1$
	- $\rho_{XY} = 1 \Leftrightarrow a > 0$
	- $\rho_{XY} = -1 \Leftrightarrow a < 0$
- $X, Y$ 相互独立 $\Rightarrow \rho_{XY} = 0$

对于二维正态分布随机变量 $X,Y$，相互独立 $\Leftrightarrow \rho = 0$

# 4.4 矩、协方差矩阵

|              定义               |                                                                                                                                              公式                                                                                                                                               |
| :---------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|          $k$ 阶（原点）矩           |                                                                                                                                           $E(X^k)$                                                                                                                                            |
|           $k$ 阶中心矩            |                                                                                                                                      $E\{[X - E(X)]^k\}$                                                                                                                                      |
|       $k + l$ 阶混合（原点）矩        |                                                                                                                                         $E\{X^kY^l\}$                                                                                                                                         |
|        $k + l$ 阶混合中心距         |                                                                                                                               $E\{[X - E(X)]^k [Y - E(Y)]^l\}$                                                                                                                                |
|      $(X_1, X_2)$ 的协方差矩阵      |                                                                                                           $\begin{bmatrix}D(X_1)&Cov(X_1,X_2)\\\\Cov(X_1,X_2)&D(X_2)\end{bmatrix}$                                                                                                            |
| $(X_1,X_2,\ldots,X_n)$ 的协方差矩阵 | $$\begin{bmatrix}D(X_1) & \mathrm{Cov}(X_1,X_2) & \cdots & \mathrm{Cov}(X_1,X_n)\\\\\mathrm{Cov}(X_2,X_1) & D(X_2) & \cdots & \mathrm{Cov}(X_2,X_n)\\\\\vdots & \vdots & \ddots & \vdots\\\\\mathrm{Cov}(X_n,X_1) & \mathrm{Cov}(X_n,X_2) & \cdots & D(X_n)\end{bmatrix}$$<br>协方差矩阵是**对称矩阵**。 |

