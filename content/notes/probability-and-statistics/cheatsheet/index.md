---
title: 概率论与数理统计 | Cheatsheet
date: 2026-01-06
summary: 【最后通牒】高斯积分、函数分布、期望与方程、两大不等式、LLN&CLT、抽样分布、区间估计、假设检验
---


# 高斯积分

1. $\displaystyle \int_{0}^{+\infty} e^{-u^2} \mathrm du = \frac{\sqrt{\pi}}{2}$
2. $\displaystyle \int_0^{+\infty} e^{-\frac{x^2}{b}} \mathrm dx = \frac{\sqrt \pi}{2} · \sqrt{b}$
3. 遇到 $\displaystyle \int x^n e^{-\frac{x^2}{b}} \mathrm dx$ 的形式，拆成 $x^{n - 1} · \left( x e^{-\frac{x^2}{b}}\right)$ 的形式，后面可以积分
   $\displaystyle \int x e^{-\frac{x^2}{b}} \mathrm dx = -\frac{b}{2} e^{-\frac{x^2}{b}}$
   所以用分部积分来降次，直到降为 $n = 0$，再用高斯公式。
# 连续型随机变量的函数分布



**单变量**：要求 $Y = g(X)$ 的密度
$$f_Y(y)=\sum_{x:\,g(x)=y}f_X\big(x(y)\big)\,\left|\frac{dx(y)}{dy}\right|=\sum_{x:\,g(x)=y}\frac{f_X(x)}{|g'(x)|}$$
如果导数 $g'(x)$ 为零（只是有限个），那么可以不用管。


**双变量**：要求 $Z = g(X,Y)$ 的密度，可以选取新的变量向量 $(Z, Y)$，将原变量表示为 $$X = h(Z, Y),\quad Y = Y$$
那么雅各比矩阵为 $\begin{bmatrix} \partial h/\partial z & \partial h/\partial y \\\\ 0 & 1 \end{bmatrix}$，行列式为 $\partial h / \partial z$.
因此 $\displaystyle f_Z(z) = \int_{-\infty}^{+\infty} \left|\frac{\partial h}{\partial z}\right| f(h(z,y),y)\mathrm dy$.

# E & D

|              分布               |                                            分布律                                            |            期望            |              方差               |
| :---------------------------: | :---------------------------------------------------------------------------------------: | :----------------------: | :---------------------------: |
|  0-1 分布<br>$X \sim b(1, p)$   |      $$\displaystyle P\{X = i\} = \begin{cases}p,& i = 1\\\\1-p, & i=0\end{cases}$$       |       $$E(X) = p$$       |       $$D(X) = p(1-p)$$       |
|   二项分布<br>$X \sim b(n, p)$    | $$\displaystyle P\{X = k\} = \binom{n}{k} p^k (1 - p)^{n - k},\quad k = 0, 1, \cdots, n$$ |      $$E(X) = np$$       |      $$D(X) = np(1-p)$$       |
| 泊松分布<br>$X \sim \pi(\lambda)$ |       $$P\{X = k\} = e^{-\lambda} \frac{\lambda^k}{k!},\quad k = 0 , 1, 2,\cdots$$        |    $$E(X) = \lambda$$    |      $$D(X) = \lambda$$       |
|             几何分布              |                 $$P\{X = k\} = (1 - p)^{k - 1} p,\quad k = 1, 2, \cdots$$                 |  $$E(X) = \frac{1}{p}$$  | $$D(X) = \frac{1 - p}{p^2}$$  |
|    均匀分布<br>$X \sim U(a,b)$    |     $$f(x) = \begin{cases}\dfrac{1}{b -a},& a < x < b \\\\ 0,& otherwise\end{cases}$$     | $$E(X) = \frac{a+b}{2}$$ | $$D(X) = \frac{(b-a)^2}{12}$$ |
|             指数分布              | $$f(x) = \begin{cases}\dfrac{e^{-x/\theta}}{\theta},& x > 0 \\\\ 0,& x \le 0\end{cases}$$ |    $$E(X) = \theta$$     |      $$D(X) = \theta^2$$      |
| 正态分布<br>$X = N(\mu,\sigma^2)$ |        $$f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{ -\frac{(x - \mu)^2}{2\sigma^2} }$$        |      $$E(X) = \mu$$      |      $$D(X) = \sigma^2$$      |
# Morkov, Chebyshev, LLN

- **Markov**：若 $Y\ge0$，则 $P(Y\ge a)\le \frac{E(Y)}a$  
- **Chebyshev**：若 $D(X)<\infty$，则 $P(|X-\mu|\ge \varepsilon)=P((X-\mu)^2\ge \varepsilon^2)\le \frac{\sigma^2}{\varepsilon^2}$
- **LLN 的证明**：$D(\bar X)=\sigma^2/n\Rightarrow P(|\bar X-\mu|\ge \varepsilon)\le \sigma^2/(n\varepsilon^2)\to0$

# CLT

**林德贝格-列维中心极限定理**：设独立同分布的随机变量 $X_1, X_2, \cdots,$ 具有期望和有限方差 $E(X_k) = \mu,\ D(X_k) = \sigma^2 > 0$，那么他们的标准化变量 $$Y_n = \frac{\displaystyle\sum_{k = 1}^n X_k - n\mu}{\sqrt{n} \sigma} \sim N(0,1)$$ 或可以写成 $\overline{X} \sim N(\mu, \sigma^2 / n)$.

**棣莫佛-拉普拉斯中心极限定理**：随机变量都是伯努利分布，当 $n$ 充分大时，有 $$b(n,p) \xrightarrow{n \to \infty} N(np, np(1 - p))$$
# 抽样分布

|       分布类型        | 来源结构                                                                                                                    | 性质与公式                                                                                                                                                                                                                   | 上 $\alpha$ 分位点         |
| :---------------: | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| $\chi^2$ 分布（卡方分布） | 相互独立的随机变量 $X_i \sim N(0,1)$<br>，那么   <br>$$\chi^2 = \sum_{i = 1}^n X_i^2 \sim \chi^2(n)$$                               | **期望与方差**：若 $\chi^2 \sim \chi^2(n)$，则 $$E(\chi^2) = n,\ D(\chi^2) = 2n$$**可加性**：若相互独立的 $Y_i \sim \chi^2(n_i)\ (i = 1, 2, \cdots m)$，则 $$\displaystyle \sum_{i = 1}^m Y_m \sim \chi^2\left( \sum_{i = 1}^m n_i \right)$$ | $$\chi_\alpha^2(n)$$   |
|      $t$ 分布       | 若相互独立的 $X \sim N(0, 1),\ Y \sim \chi^2(n)$，则 $$\displaystyle T = \frac{X}{\sqrt{Y/n}} \sim t(n)$$                       | **对称性**：$t$ 分布关于 $t = 0$ 对称，即 $$t_{1 - \alpha}(n) = - t_{\alpha}(n)$$**极限是正态分布**：$$n \to \infty,\ t(n) \to N(0, 1)$$                                                                                                    | $$t_{\alpha}(n)$$      |
|      $F$ 分布       | 设 $X \sim \chi^2(n_1)$，$Y \sim \chi^2(n_2)$，$X, Y$ 独立，那么 $$\displaystyle F = \frac{X / n_1}{Y / n_2} \sim F(n_1, n_2)$$ | **倒数性质**：若 $F \sim F(n_1, n_2)$，则 $$\frac{1}{F} \sim F(n_2, n_1)$$$$F_{1-\alpha}(n_1,n_2) = \frac{1}{F_{\alpha}(n_2,n_1)}$$                                                                                             | $$F_\alpha(n_1, n_2)$$ |

# 区间估计

| 类型         | 待估参数                                          | 参数前提                                              | 点估计                                 | 枢轴量及其分布                                                                                                                                                                                                                  | 置信区间                                                                                                                                    |
| ---------- | --------------------------------------------- | ------------------------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| **一个正态总体** | $\displaystyle \mu$                           | $\displaystyle \sigma^2$ 已知                       | $\overline X$                       | $\displaystyle Z=\frac{\overline{X}-\mu}{\sigma/\sqrt{n}}\sim N(0,1)$                                                                                                                                                    | $\displaystyle \left( \overline{X}\pm \frac{\sigma}{\sqrt{n}} z_{\alpha/2} \right)$                                                     |
|            | $\displaystyle \mu$                           | $\displaystyle \sigma^2$ 未知                       | $\overline{X}$                      | $\displaystyle t=\frac{\overline{X}-\mu}{S/\sqrt{n}}\sim t(n-1)$                                                                                                                                                         | $\displaystyle \left( \overline{X}\pm \frac{S}{\sqrt{n}} t_{\alpha/2}(n-1) \right)$                                                     |
|            | $\displaystyle \sigma^2$                      | $\displaystyle \mu$ 未知                            | $S^2$                               | $\displaystyle \chi^2=\frac{(n-1)S^2}{\sigma^2}\sim \chi^2(n-1)$                                                                                                                                                         | $\displaystyle \left( \frac{(n-1)S^2}{\chi^2_{\alpha/2}(n-1)},\ \frac{(n-1)S^2}{\chi^2_{1-\alpha/2}(n-1)} \right)$                      |
| **两个正态总体** | $\displaystyle \mu_1-\mu_2$                   | $\displaystyle \sigma_1^2,\sigma_2^2$ 已知          | $\overline{X} - \overline{Y}$       | $\displaystyle Z=\frac{(\overline{X}-\overline{Y})-(\mu_1-\mu_2)}{\sqrt{\sigma_1^2/n_1+\sigma_2^2/n_2}}\sim N(0,1)$                                                                                                      | $\displaystyle \left( \overline{X}-\overline{Y}\pm z_{\alpha/2}\sqrt{\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2}} \right)$            |
|            | $\displaystyle \mu_1-\mu_2$                   | $\displaystyle \sigma_1^2=\sigma_2^2=\sigma^2$ 未知 | $\overline{X} - \overline{Y}$       | $\displaystyle t=\frac{(\overline{X}-\overline{Y})-(\mu_1-\mu_2)}{S_w\sqrt{\displaystyle\frac{1}{n_1}+\frac{1}{n_2}}}\sim t(n_1+n_2-2)$<br>其中 $\displaystyle S_w = \sqrt{\frac{(n_1-1)S_1^2 + (n_2-1)S_2^2}{n_1+n_2-2}}$ | $\displaystyle \left( \overline{X}-\overline{Y} \pm t_{\alpha/2}(n_1+n_2-2)\ S_w \sqrt{\frac{1}{n_1}+\frac{1}{n_2}} \right)$            |
|            | $\displaystyle \frac{\sigma_1^2}{\sigma_2^2}$ | $\displaystyle \mu_1,\mu_2$ 未知                    | $\displaystyle \frac{S_1^2}{S_2^2}$ | $\displaystyle F=\frac{S_1^2/\sigma_1^2}{S_2^2/\sigma_2^2}\sim F(n_1-1,n_2-1)$                                                                                                                                           | $\displaystyle \left( \frac{S_1^2}{S_2^2} \frac{1}{F_{\alpha/2}(n_1-1,n_2-1)},\ \frac{S_1^2}{S_2^2} F_{\alpha/2}(n_2-1, n_1-1) \right)$ |

# 假设检验

![](attachments/Pasted-image-20260104205511.png)