---
title: 解析几何 | Week 4 曲线、曲面
date: 2025-09-28
summary: 曲线方程、曲面方程
---


# 2.1 平面曲线的方程
**曲线的一般方程**：$F(x, y) = 0$ 或 $y = f(x)$

**曲线的参数方程**：$\boldsymbol r = \boldsymbol r(t),\ a \le t \le b$，或 $\begin{cases}x = x(t)\\\\y = y(t)\end{cases}, a \le t \le b$

可以将向径表示成若干容易求解的向量相加，这样就容易求出点的参数方程。

一般方程与参数方程之间的转化注意点：
- 曲线的一般方程能够转化成参数方程
- 将参数方程不一定能转化成一般方程
- 同一条曲线(一般方程)可以有多种不同形式的参数方程
- 参数方程与一般方程互化时，必须保证两种形式等价

# 2.2 曲面的方程
**曲面的方程的表达**：
- $F(x, y, z) = 0$ 或 $z = f(x, y)$
- $\boldsymbol r = \boldsymbol r (u, v) = x(u,v)\boldsymbol e_1 + y(u, v)\boldsymbol e_2 + z(u,v) \boldsymbol e_3$
- $\begin{cases}x = x(u, v)\\\\y = y(u, v)\\\\z = z(u, v)\end{cases},\\ a \le u \le b, c \le v \le d$

**常见坐标系**：
- 直角坐标系：$x, y, z$
- 球坐标系：$\displaystyle \rho = \sqrt{x^2 + y^2 + z^2},\ \varphi = \arcsin \frac{z}{\sqrt{x^2 + y^2 + z^2}},\ \theta = \arcsin \frac{y}{\sqrt{x^2 + y^2}}$
- 柱坐标系：$\displaystyle \rho = \sqrt{x^2 + y^2},\ \varphi = \arcsin \frac{y}{x^2 + y^2},\ u = z$

**球面方程**：
- $(x - a)^2 + (y - b)^2 + (z - c)^2 = r^2$
- $x^2 + y^2 + z^2 + 2gxy + 2hyz + 2kzx + l= 0$，其中满足 $\Delta = g^2 + h^2 + k^2 - l > 0$
	- 三元二次方程表示球面，当且仅当二次项系数相等，且交叉项消失，且判别式大于零
	- $\Delta = 0$ 表示空间一点（点球），$\Delta < 0$ 无实图形（虚球面）
- $\displaystyle \begin{cases}x = r\cos\theta\cos\varphi\\\\y = r\cos\theta\sin\varphi\\\\z = r\sin\theta\end{cases},\\ -\frac{\pi}{2} \le \theta \le \frac{\pi}{2},\\ -\pi < \varphi \le \pi$

**截痕法**：随着某一个坐标变化（如竖坐标 $z$），看截出来的平面是什么形状

**柱面**：如果曲面中缺了一个变量如 $z$，而变为 $F(x, y) = 0$，则是平行于 $z$ 轴沿着平面的曲线移动而成的面。形成柱面的直线叫做它的 **母线**。平面的曲线叫做 **准线**。

**二次曲面**：![](attachments/Pasted-image-20250930104908.png)

# 2.3 空间曲线方程

**空间曲线的方程表达**：
- 看作两个曲面的交线：$\begin{cases} F(x, y, z) = 0 \\\\ G(x, y, z) = 0 \end{cases}$
- 向量式参数方程：$\boldsymbol r = \boldsymbol r(t) = x(t) \boldsymbol i + y(t) \boldsymbol j + z(t) \boldsymbol k$
- 坐标式参数方程：$\begin{cases}x = x(t)\\\\y = y(t)\\\\z = z(t)\end{cases}, a \le t \le b$


**空间曲线在坐标面的上的投影**：例如要求在 $xOy$ 上的投影曲线，则先由 $\begin{cases} F(x, y, z) = 0 \\ G(x, y, z) = 0 \end{cases}$ 消去 $z$ 得到投影柱面 $H(x, y) = 0$，那么投影曲线则为 $\begin{cases}H(x, y) = 0\\\\z = 0\end{cases}$.

