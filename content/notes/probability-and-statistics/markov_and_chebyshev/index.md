---
title: 概率论与数理统计 | 马尔科夫不等式和切比雪夫不等式
date: 2026-01-10
summary: 专项补习：马尔科夫不等式、切比雪夫不等式
---


# 1. Markov 不等式（马尔可夫）

若 $Y\ge 0$，且 $E(Y)<\infty$，则对任意 $a>0,\ P(Y\ge a)\le \frac{E(Y)}{a}$.

## 一行证明模板
$$
E(Y)=E\big(Y\mathbf 1_{Y\ge a}\big)+E\big(Y\mathbf 1_{Y<a}\big)
\ge E\big(Y\mathbf 1_{Y\ge a}\big)\ge aP(Y\ge a).
$$
## 变形招式

- $Y=(X-\mu)^2\ge 0$
- $Y=|X|^p\ge 0$
- $Y=e^{tX}\ge 0$（这会通往 Chernoff，但期末一般不深究）

# 2. Chebyshev 不等式（切比雪夫）

若 $E(X)=\mu$，$D(X)=\sigma^2<\infty$，则对任意 $\varepsilon>0$：
$$
P(|X-\mu|\ge \varepsilon)\le \frac{\sigma^2}{\varepsilon^2}.
$$
## 关键理解
它就是 Markov 在
$Y=(X-\mu)^2,\quad a=\varepsilon^2$
上的直接应用：

$$
P(|X-\mu|\ge \varepsilon)
= P\big((X-\mu)^2\ge \varepsilon^2\big)
\le \frac{E[(X-\mu)^2]}{\varepsilon^2}
= \frac{\sigma^2}{\varepsilon^2}.
$$

# 弱大数定律

设 $X_1,\dots,X_n$ 独立同分布，$E(X_i)=\mu$，$D(X_i)=\sigma^2$， 则
$$
E(\bar X)=\mu,\qquad D(\bar X)=\frac{\sigma^2}{n}.
$$
## 用 Chebyshev 证明 LLN
$$
P(|\bar X-\mu|\ge \varepsilon)\le \frac{D(\bar X)}{\varepsilon^2}
=\frac{\sigma^2}{n\varepsilon^2}\to 0.
$$

# 最容易犯的 5 个坑

1) **Markov 的前提必须是非负**：要么题目给 $X\ge0$，要么自己构造 $Y\ge0$（比如平方、绝对值、指数）。  
2) **Chebyshev 必须方差有限**（题目一般会给或默认）。  
3) 上界**可以大于 1**，不矛盾，只是很松。  
4) $P(|X-\mu|\ge \varepsilon)$ 用 Chebyshev；$P(X\ge a)$ 且非负用 Markov。  

# Conclusion

- **Markov**：$Y\ge0\Rightarrow P(Y\ge a)\le \frac{E(Y)}a$  
- **Chebyshev**：$P(|X-\mu|\ge \varepsilon)=P((X-\mu)^2\ge \varepsilon^2)\le \frac{\sigma^2}{\varepsilon^2}$
- **LLN**：$D(\bar X)=\sigma^2/n\Rightarrow P(|\bar X-\mu|\ge \varepsilon)\le \sigma^2/(n\varepsilon^2)\to0$
