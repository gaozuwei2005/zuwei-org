---
title: 概率论与数理统计 | Week 9 样本及抽样分布
date: 2025-11-05
summary: 随机样本、抽样分布（卡方分布、t分布、F分布）
---


# 6.1 随机样本

**总体**：研究对象的全体，可以用一个随机变量 $X$ 或其分布来描述。

**个体**：总体中的每个对象。

**样本**：根据一定规则抽取的部分个体可看做 $n$ 维随机变量 $(X_1, X_2, \cdots, X_n)$.

抽样的目的：通过观察样本推断总体分布以及各种特征。

**样本容量**：样本包含的个体数目。

**简单随机样本**：$n$ 维随机变量 $(X_1, X_2, \cdots, X_n)$ 满足以下特点：
- 独立性：$X_1, X_2, \cdots, X_n$ 相互独立；
- 代表性：$X_i$ 与 $X$ 具有相同分布。
- 分布函数：$\displaystyle F(x_1, x_2, \cdots, x_n) = \prod_{i = 1}^n F(x_i),\ \displaystyle f(x_1, x_2, \cdots, x_n) = \prod_{i = 1}^n f(x_i)$

# 6.3 抽样分布

**统计量**：关于样本的一个 $n$ 元函数 $g(X_1, X_2, \cdots, X_n)$.

**抽样分布**：统计量的分布。

**常用统计量：** （下面的期望方差，统一假设 $\\{X_i\\}_{i = 1}^n$ 独立同分布，且 $E(X) = \mu,\ D(X) = \sigma^2$，那么有 $E(X^2) = \sigma^2 + \mu^2$）

|     统计量名称     |                                                            公式                                                             |                                           期望                                            |                    方差                    |
| :-----------: | :-----------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------: | :--------------------------------------: |
|     样本均值      |                                      $$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$$                                      | $$E(\overline{X}) = \mu$$ $$E\left(\overline{X}^2\right) = \frac{\sigma^2}{n} + \mu^2$$ | $$D(\overline{X}) = \frac{\sigma^2}{n}$$ |
|     样本方差      | $$S^2 = \frac{1}{n - 1} \sum_{i=1}^n (X_i - \bar{X})^2 = \frac{1}{n - 1} \left( \sum_{i=1}^n X_i^2 - n\bar{X}^2 \right)$$ |                                  $$E(S^2) = \sigma^2$$                                  |                                          |
|     样本标准差     |                                                    $$S = \sqrt{S^2}$$                                                     |                                   $$E(S) \ne \sigma$$                                   |                                          |
| 样本 $k$ 阶（原点）矩 |                             $$A_k = \frac{1}{n} \sum_{i=1}^n X_i^k \quad (k = 1, 2, \cdots)$$                             |                                   $$E(A_k) = E(X^k)$$                                   |     $$D(A_k) = \frac{1}{n} D(X^k)$$      |
|  样本 $k$ 阶中心矩  |                       $$B_k = \frac{1}{n} \sum_{i=1}^n (X_i - \bar{X})^k \quad (k = 1, 2, \cdots)$$                       |      $$E(B_1) = 0$$$$E(B_2) = \frac{n - 1}{n} E(S^2) = \frac{n - 1}{n} \sigma^2$$       |                                          |

样本来估计总体方差时，样本均值 $\overline{X}$ 是“计算出来的”，它消耗了一个自由度。

为了让样本方差成为总体方差的**无偏估计**，必须除以 $n−1$。

## 三大分布重点内容（$\bigstar$ 务必记住）

|       分布类型        | 来源结构                                                                                                                    | 性质与公式                                                                                                                                                                                                                   | 上 $\alpha$ 分位点         |
| :---------------: | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| $\chi^2$ 分布（卡方分布） | 相互独立的随机变量 $X_i \sim N(0,1)$<br>，那么   <br>$$\chi^2 = \sum_{i = 1}^n X_i^2 \sim \chi^2(n)$$                               | **期望与方差**：若 $\chi^2 \sim \chi^2(n)$，则 $$E(\chi^2) = n,\ D(\chi^2) = 2n$$**可加性**：若相互独立的 $Y_i \sim \chi^2(n_i)\ (i = 1, 2, \cdots m)$，则 $$\displaystyle \sum_{i = 1}^m Y_m \sim \chi^2\left( \sum_{i = 1}^m n_i \right)$$ | $$\chi_\alpha^2(n)$$   |
|      $t$ 分布       | 若相互独立的 $X \sim N(0, 1),\ Y \sim \chi^2(n)$，则 $$\displaystyle T = \frac{X}{\sqrt{Y/n}} \sim t(n)$$                       | **对称性**：$t$ 分布关于 $t = 0$ 对称，即 $$t_{1 - \alpha}(n) = - t_{\alpha}(n)$$**极限是正态分布**：$$n \to \infty,\ t(n) \to N(0, 1)$$                                                                                                    | $$t_{\alpha}(n)$$      |
|      $F$ 分布       | 设 $X \sim \chi^2(n_1)$，$Y \sim \chi^2(n_2)$，$X, Y$ 独立，那么 $$\displaystyle F = \frac{X / n_1}{Y / n_2} \sim F(n_1, n_2)$$ | **倒数性质**：若 $F \sim F(n_1, n_2)$，则 $$\frac{1}{F} \sim F(n_2, n_1)$$$$F_{1-\alpha}(n_1,n_2) = \frac{1}{F_{\alpha}(n_2,n_1)}$$                                                                                             | $$F_\alpha(n_1, n_2)$$ |
## $\chi^2$ 分布（卡方分布）

**卡方分布**：对于相互独立的随机变量 $X_1,X_2, \cdots, X_n$，$X_i \sim N(0, 1)\ (i = 1, 2, \cdots n)$，那么 $\displaystyle \chi^2 = \sum_{i = 1}^n X_i^2$ 服从自由度为 $n$ 的 $\chi^2$ 分布，记为 $\chi^2 \sim \chi^2(n)$，概率密度为 $$f(y;n) =  \begin{cases}\displaystyle \frac{1}{2^{n/2}\Gamma(n/2)}·y^{n/2-1}e^{-y/2},& y>0 \\\\ 0,&y\le 0\end{cases}\qquad \text{where}\ \ \Gamma(\alpha) = \int_0^{+\infty} x^{\alpha - 1}e^{-x}\mathrm dx.$$
**$\Gamma(\alpha)$ 的性质：**
- $\displaystyle\Gamma\left(\frac{1}{2}\right) = \sqrt{\pi}$
- $\Gamma(1) = 1$
- $\forall \alpha > 0,\ \Gamma(\alpha+1) = \alpha \Gamma(\alpha)$
- $\forall n \in \mathbb N^*,\ \Gamma(n) = (n -1)!$

**$\chi^2$ 分布的性质：**
- **期望与方差**：若 $\chi^2 \sim \chi^2(n)$，则 $E(\chi^2) = n,\ D(\chi^2) = 2n$
- **可加性**：
	- 若相互独立的 $Y_1 \sim \chi^2(n_1),\ Y_2 \sim \chi^2(n_2)$，则 $Y_1+Y_2 \sim \chi^2(n_1+n_2)$
	- 若相互独立的 $Y_i \sim \chi^2(n_i)\ (i = 1, 2, \cdots m)$，则 $\displaystyle \sum_{i = 1}^m Y_m \sim \chi^2\left( \sum_{i = 1}^m n_i \right)$
- **上 $\alpha$ 分位点**：记为 $\chi_\alpha^2(n)$ ，使得 $\displaystyle \int_{\chi_\alpha^2(n)}^{+\infty} f(y;n)\mathrm dy = \alpha$.
	- $\displaystyle \lim_{n \to \infty} X_{\alpha}^2(n) = \frac{1}{2}\left(z_{\alpha} + \sqrt{2n-1}\right)^2$
- 对于满足卡方分布的变量做了「非 i.i.d 加法」的任何其他运算（数乘、数加、开方、平方、对数等等），**结果不再满足卡方分布**。

## $t$ 分布

**$t$ 分布**：若相互独立的 $X \sim N(0, 1),\ Y \sim \chi^2(n)$，则 $\displaystyle T = \frac{X}{\sqrt{Y/n}}$ 服从自由度为 $n$ 的 $t$ 分布，记作 $T\sim t(n)$.

**$t(n)$ 分布的概率密度：** $$\quad f(t;n) = \frac{\Gamma\left(\frac{n+1}{2}\right)}{\sqrt{n\pi}\ \Gamma\left(\frac{n}{2}\right)} \left(1 + \frac{t^2}{n}\right)^{-\frac{n+1}{2}}, \quad -\infty < t < +\infty$$
$t$ 分布关于 $t = 0$ 对称。当 $n$ 充分大时，$t$ 分布近似于标准正态分布。

**上 $\alpha$ 分位点**：记作 $t_{\alpha}(n)$，使得 $\displaystyle\int_{t_{\alpha}(n)}^{\infty} f(t;n)\,dt = \alpha$.


## $F$ 分布

**定义：**  设 $X \sim \chi^2(n_1)$，$Y \sim \chi^2(n_2)$，且 $X, Y$ 独立，则称随机变量 $\displaystyle F = \frac{X / n_1}{Y / n_2}$  服从自由度 $(n_1, n_2)$ 的 $F$ 分布，记为 $F \sim F(n_1, n_2)$。 其中 $n_1$ 称为第一自由度，$n_2$ 称为第二自由度。

**概率密度**：
$$f(x; n_1, n_2) =
\begin{cases}
\dfrac{1}{B\left(\tfrac{n_1}{2}, \tfrac{n_2}{2}\right)}
\left(\dfrac{n_1}{n_2}\right)^{\tfrac{n_1}{2}}
x^{\tfrac{n_1}{2}-1}
\left(1+\dfrac{n_1}{n_2}x\right)^{-\tfrac{n_1+n_2}{2}},
& x>0,\\\\
0, & x \le 0
\end{cases}$$$$\text{where}\quad B(a,b) = \int_0^1 x^{a-1}(1-x)^{b-1}\,dx = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}, \quad (a, b > 0)$$

**上 $\alpha$ 分位点**：记作 $F_{\alpha}(n_1,n_2)$，使得 $\displaystyle\int_{F_{\alpha}(n_1,n_2)}^{\infty} f(x;n_1,n_2)\mathrm dx = \alpha$.

**性质：** 
- 若 $F \sim F(n_1, n_2)$，则 $1/F \sim F(n_2, n_1)$。
- $F_{1-\alpha}(n_1,n_2) = [F_{\alpha}(n_2,n_1)]^{-1}$

## 正态总体的样本均值与方差的分布

**定理：** 设 $(X_1, X_2, \cdots, X_n)$ 是总体 $N(\mu, \sigma^2)$ 的样本，$\bar{X}, S^2$ 分别是样本均值和样本方差，则有：
1.  $\displaystyle\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$
2.  $\displaystyle\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$
3.  $\bar{X}$ 和 $S^2$ 相互独立

**定理：** 设 $(X_1, \cdots, X_n)$ 是总体 $N(\mu, \sigma^2)$ 的样本，$\bar{X}$ 和 $S^2$ 分别是样本均值和样本方差，  
则有：$\displaystyle\frac{\bar{X} - \mu}{S / \sqrt{n}} \sim t(n-1)$.

**定理：** 设样本 $(X_1, \cdots, X_{n_1})$ 和 $(Y_1, \cdots, Y_{n_2})$ 分别来自总体 $N(\mu_1, \sigma_1^2)$ 和 $N(\mu_2, \sigma_2^2)$，并且它们相互独立，其样本方差分别为 $S_1^2, S_2^2$，则：
1. $\displaystyle F=\frac{S_1^2/\sigma_1^2}{S_2^2/\sigma_2^2}\sim F(n_1-1,n_2-1)$
2. $\displaystyle \frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2}}}\sim N(0,1)$
3. 当 $\sigma_1^2=\sigma_2^2=\sigma^2$ 时，$\displaystyle \frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{S_w\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}\sim t(n_1+n_2-2)$ 其中 $\displaystyle  S_w^2=\frac{(n_1-1)S_1^2+(n_2-1)S_2^2}{n_1+n_2-2},\quad S_w=\sqrt{S_w^2}$



