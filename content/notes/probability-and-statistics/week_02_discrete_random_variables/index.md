---
title: 概率论与数理统计 | Week 2 离散型随机变量
date: 2025-09-17
summary: 两点分布、二项分布、泊松分布、超几何分布、几何分布、
---
# 2.1 随机变量
**随机变量**：映射 $X : S \to \mathbb R$，其中 $S$ 是样本空间。那么 $X = X(e),\ (e \in S)$ 为随机变量.

随机变量常用大写字母，随机变量的某个取值为小写字母。

$\\{e | X \in L\\}$ 表示使得 $X(e) \in L$ 的所有样本点组成的事件。

*可简写为 $\{X \in L\}$，如 $\{X = 2\}$，$\{Y \ge 100\}$ 等*

$P\\{X \in L\\}$ 表示使得 $X(e) \in L$ 的所有样本点组成的事件的概率。


分类：离散型随机变量、连续型随机变量

# 2.2 离散型随机变量及其分布律

**离散型随机变量**：随机变量的取值是 有限多个 或 可列无穷多个。

**离散型随机变量的分布律**：对于 $X$ 的一切可能值 $x_k\ (k = 1, 2, \cdots)$，则 $$P\{X = x_k\} = p_k$$ 为 $X$ 的分布律。

特点：$p_k \ge 0$，$\displaystyle \sum_{k} p_k = 1$

分布律的表示方法：公式法、列表法

如何研究分布律：先考虑能取什么值，再考虑每种取值的概率

## 0-1 分布 / 两点分布 / 伯努利分布
**伯努利分布**：$P\{X = 1\} = p,\ P\{X = 0\} = 1 - p$

**伯努利试验**：只有两种互逆的结果的试验

## 二项分布
**$\boldsymbol n$ 重伯努利试验**：将伯努利试验 _独立、重复_ 地进行 $n$ 次。

**二项分布**：$n$ 重伯努利试验中，对于感兴趣的事件 $A$ 有 $P(A) = p$，则 $A$ 的发生总次数 $X$ 服从 参数为 $n, p$ 的二项分布，记作 $X \sim b(n, p)$，分布律为
$$P\{X = k\} = \binom{n}{k} p^k (1 - p)^{n - k},\quad k = 0, 1, \cdots, n$$
0-1 分布是 $n = 1$ 的二项分布。

二项分布随 $k$ 的**趋势**：先增后减，在 $k \in [(n + 1)p - 1, (n + 1) p] \cap \mathbb N$ 的概率达到顶峰
![](attachments/Pasted-image-20250917154804.png)

![](attachments/Pasted-image-20250917155147.png)

## 泊松 (Poisson) 分布

**泊松分布**：$X$ 满足参数为 $\lambda > 0$ 的泊松分布，则记 $X \sim \pi(\lambda)$，其分布律为 $$P\{X = k\} = e^{-\lambda} \frac{\lambda^k}{k!},\quad k = 0 , 1, 2,\cdots$$
**物理意义**：
- 每次试验结果为“发生”或“未发生”、各次试验独立（多重伯努利试验）
- 试验次数可认为是无限多次 $(n \to +\infty)$
- 事件在一个短区间内发生两次或以上的概率可忽略
- 事件在一个短区间内发生的概率与区间长度成正比

二项分布随 $k$ 的**趋势**：先增后减，在 $k \in [\lambda - 1, \lambda] \cap \mathbb N$ 的概率达到顶峰
![](attachments/Pasted-image-20250919164900.png)

**泊松定理**：在二项分布 $X \sim b(n, p)$ 中，令 $np = \lambda$，则有 $$\lim_{n \to \infty} P\{X = k\} = \lim_{n \to \infty} \binom{n}{k} p^k (1 - p)^{n - k} = \frac{\lambda^k e^{-\lambda}}{k!}$$
证明：将 $p = \frac{\lambda}{n}$，然后用泰勒级数转化。推导过程比较复杂。

所以*泊松分布是对二项分布无限细分的时候的极限。*

当 $n \ge 20$，$p \le 0.05$ 时，可以用泊松分布 $\pi(np)$ 来近似二项分布 $b(n, p)$

## 超几何分布
**超几何分布**：设有产品 $N$ 件， 其中次品 $D$ 件， 其余为正品， 从中随机地抽取 $n$ 件，则抽到的次品数 $X$ 服从超几何分布，分布律为
$$P\{X = k\} = \frac{\binom{D}{k} \binom{N - D}{n - k}}{\binom{N}{n}},\quad \max(0, n - N + D) \le k \le \min(n, D)$$
当 $N \gg n$ 时近似于二项分布。

## 几何分布
**几何分布**：某事件发生概率为 $p$，重复试验直至发生的次数 $X$ 服从几何分布，分布律为
$$P\{X = k\} = (1 - p)^{k - 1} p,\quad k = 1, 2, \cdots$$

**无记忆性**：若在前 $m$ 次试验，那么在此条件下，事件发生所需要再试验的次数也服从同一几何分布， 该分布与 $m$ 无关 $$P\{X = m + k  \mid X > m\} = P\{X = k\}$$
# 2.3 随机变量的分布函数

**分布函数**：若 $X$ 是 _随机变量_，则其分布函数为 $$F(x) = P\{X \le x\},\ -\infty < x < \infty$$
由定义可以推出：
- $P\{a < X \le b\} = F(b) - F(a)$
- $P\{X > a\} = 1 - F(a)$

离散型随机变量的分布函数：$\displaystyle F(x) = \sum_{x_k \le x} p_k$
图像**特点**：
- 左侧为 $0$，右侧为 $1$，且中间为左闭右开水平线的分段函数
- 在每个 $X$ 的取值发生跳变

随机变量的分布函数的**充分必要条件**：
- 非负性：$F(x) \ge 0$
- 单调不减性：$\forall x_1 < x_2,\ F(x_1) \le F(x_2)$
- 规范性：$\displaystyle F(- \infty) = \lim_{x \to -\infty} F(x) = 0,\ F(+ \infty) = \lim_{x \to +\infty} F(x) = 1$
- 右连续性：$\displaystyle \lim_{x \to x_0^{+}} F(x) = F(x_0)$

## 2.4 连续型随机变量及其概率密度

**连续性随机变量**：若 $X$ 为随机变量，如果存在非负函数 $f(x)$ 满足 $$P\{a < X \le b\} = \int_a^b f(x) \mathrm dx$$ 则称 $X$ 为连续型随机变量，$f(x)$ 是 $X$ 的概率密度函数。

由定义可以得出：
- $\displaystyle F(x) = \int_{-\infty}^x f(t) \mathrm dt$
- $\displaystyle f(x) = \lim_{\Delta x \to 0^+} \frac{\int_x^{x + \Delta x} f(t) \mathrm dt}{\Delta x}$，若 $f(x)$ 在 $x$ 连续，则 $f(x) = F'(x)$
- $P\{X = a\} = 0$
	- 概率为 $0$ 的事件不一定是不可能事件
	- 概率为 $1$ 的事件不一定是必然事件
- $\displaystyle \int_{-\infty}^{\infty} f(t) \mathrm dt = 1$

**判定是否为概率密度函数的条件**：
1. $f(x) \ge 0$
2. $\displaystyle \int_{-\infty}^{+\infty} f(x) \mathrm dx= 1$
