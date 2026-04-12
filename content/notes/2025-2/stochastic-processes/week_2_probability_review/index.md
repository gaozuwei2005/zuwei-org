---
title: 随机过程 | Week 2 概率论复习
date: 2026-03-13
summary: 随机变量函数分布、全期望公式、特征函数、矩母函数、概率母函数、中心极限定理
---

# 随机向量函数的分布

设连续型随机向量 $\boldsymbol X = (X_1, X_2,\cdots, X_n)^T$，以及一一映射的函数 $T: \mathbb R^n \to \mathbb R^n$，且 $T, T^{-1}$ 均可微，则 $\boldsymbol Y = T(\boldsymbol X)$ 的联合概率密度函数为 $$f_\boldsymbol Y(y_1, y_2, \cdots, y_n) = f_\boldsymbol X (x_1, x_2, \cdots, x_n) \left|\frac{\partial(x_1,x_2,\cdots, x_n)}{\partial(y_1,y_2,\cdots, y_n)}\right|$$
$$\frac{\partial (x_1, \cdots, x_n)}{\partial (y_1, \cdots, y_n)}  
=  \det \begin{pmatrix}  
\frac{\partial x_1}{\partial y_1} & \cdots & \frac{\partial x_1}{\partial y_n} \\\\  
\vdots & \ddots & \vdots \\\\  
\frac{\partial x_n}{\partial y_1} & \cdots & \frac{\partial x_n}{\partial y_n}  \end{pmatrix}$$
即逆变换 $\boldsymbol x  = T^{-1}(\boldsymbol y)$ 的 Jacobi 矩阵的行列式。

# 一些额外补充

- **全期望公式**：$E(E(X\mid Y)) = E(X)$
- 协方差矩阵 $\boldsymbol \Sigma_{\boldsymbol X}$ 是对称非负定矩阵

# 特征函数

**特征函数**：对于任意随机变量 $X$，它的特征函数为 $$\phi_X(\omega) = E(e^{i\omega X}) = \int_{-\infty}^{+\infty} e^{i\omega x} f_X(x) \mathrm dx$$
由于 $|e^{i\omega X}| = 1$，因此上述积分是收敛的，因此特征函数一定存在。

**特征函数的性质**：
- $\phi_{a + bX}(\omega) = e^{ja\omega} · \phi_X(b\omega)$
- 若 $X_1, X_2, \cdots,X_n$ 相互独立，则 $\displaystyle \phi_{X_1+X_2+\cdots+X_n}(\omega) = \prod_{i = 1}^n\phi_X(\omega)$
- $n$ 阶矩：$\displaystyle E[X^n] = \frac{\phi_X^{(n)}(0)}{i^n}$
	- $\phi_X'(\omega) = [E(e^{i\omega X})]' = E(iXe^{i\omega X}) = iE(Xe^{i\omega X})$，则 $\phi'_X(0) = i E(X)$
	- $\phi''_X(\omega) = [iE(Xe^{i\omega X})]' = i^2 E(X^2e^{i\omega X})$，则 $\phi''_X(0) = i^2 E(X)$
	- 以此类推
- 概率分布与特征函数一一对应【？】

**常见分布的特征函数**：
- 离散型随机变量
  - 二项分布：$\displaystyle \phi_X(\omega) = (p e^{i\omega} + q)^n$
  - 几何分布：$\displaystyle \phi_X(\omega) = \frac{p e^{i\omega}}{1 - q e^{i\omega}}$
  - 泊松分布：$\displaystyle \phi_X(\omega) = e^{\lambda (e^{i\omega} - 1)}$

- 连续型随机变量
  - 均匀分布 $U(a,b)$：$\displaystyle \phi_X(\omega) = \frac{e^{i\omega b} - e^{i\omega a}}{i\omega(b-a)}$
  - 指数分布：$\displaystyle \phi_X(\omega) = \frac{\lambda}{\lambda - i\omega}$
  - 正态分布 $N(\mu,\sigma^2)$：$\displaystyle \phi_X(\omega) = e^{i\omega\mu - \frac{\sigma^2\omega^2}{2}}$


# 矩母函数

**矩母函数**（MGF）定义为 $M_X(t)=E(e^{tX})$

只要它在 $t=0$ 附近存在，就可以用来生成矩：$E[X^n]=M_X^{(n)}(0).$


**与特征函数的关系**：

$$\phi_X(\omega)=M_X(i\omega), \qquad M_X(t)=\phi_X(-it)$$


**常见分布的矩母函数**：

- $B(n,p)$：$M_X(t)=(pe^t+q)^n$
- $P(\lambda)$：$M_X(t)=\exp\!\bigl(\lambda(e^t-1)\bigr)$
- $N(\mu,\sigma^2)$：$M_X(t)=\exp\!\left(\mu t+\frac{1}{2}\sigma^2 t^2\right)$
- $\mathrm{Exp}(\lambda)$：$M_X(t)=\frac{\lambda}{\lambda-t},\qquad t<\lambda.$

矩母函数的优点是“直接给矩”，但缺点是并不总存在；相比之下，特征函数总是存在，因此更适合做极限定理和分布收敛的证明。

# 概率母函数（PGF）

**概率母函数**适用于非负整数值随机变量 $X$，定义为

$$G_X(s)=E(s^X)=\sum_{k=0}^{\infty} P(X=k)s^k.$$


**性质**：

- 若 $X,Y$ 独立，则 $G_{X+Y}(s)=G_X(s)G_Y(s).$

- 若 $X$ 取值于非负整数，则 $E(X)=G_X'(1), \qquad E[X(X-1)] = G_X''(1).$


**常见分布的概率母函数**：

- 二项分布 $B(n,p)$:  $G_X(s)=(q+ps)^n.$

- 几何分布 $G(p)$：$G_X(s)=\frac{ps}{1-qs},\qquad |s|<\frac{1}{q}.$

- 泊松分布 $P(\lambda)$: $G_X(s)=\exp\!\bigl(\lambda(s-1)\bigr).$


# 中心极限定理（CLT）

设 $X_1,X_2,\cdots$ 为一列独立同分布随机变量，且

$$E(X_k)=\mu,\qquad \mathrm{Var}(X_k)=\sigma^2<\infty.$$

定义标准化和

$$S_n=\frac{\sum_{k=1}^n X_k-n\mu}{\sigma\sqrt n}.$$

则当 $n\to\infty$ 时，

$$S_n \xrightarrow{d} N(0,1).$$


**用特征函数证明的思路**：

令

$$Y_k=\frac{X_k-\mu}{\sigma},$$

   则 $E(Y_k)=0$，$\mathrm{Var}(Y_k)=1$。

记 $Y=Y_1$ 的特征函数为 $\phi_Y(t)$。在 $t=0$ 附近作展开，可得

   $$\phi_Y(t)=1-\frac{t^2}{2}+o(t^2).$$

因为

   $$S_n=\frac{1}{\sqrt n}\sum_{k=1}^n Y_k,$$

   所以其特征函数为

   $$\phi_{S_n}(t)=\left[\phi_Y\!\left(\frac{t}{\sqrt n}\right)\right]^n.$$

代入展开式：

$$\phi_Y\!\left(\frac{t}{\sqrt n}\right)  =1-\frac{t^2}{2n}+o\!\left(\frac{1}{n}\right),$$

因而

$$\phi_{S_n}(t)\to e^{-t^2/2}.$$

而 $e^{-t^2/2}$ 正是 $N(0,1)$ 的特征函数。由 Lévy 连续性定理可知

$$S_n \xrightarrow{d} N(0,1).$$


