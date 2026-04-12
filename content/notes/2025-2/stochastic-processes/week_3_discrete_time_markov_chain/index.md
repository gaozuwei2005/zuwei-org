---
title: 随机过程 | Week 3~6 离散时间 Markov 链
date: 2026-04-10
summary: 定义与例子、状态分类及性质、极限分布与平稳分布
---

# 定义与例子

**离散时间马尔科夫链**：具有可数样本空间 $\mathcal E$，$X_k$ 只与 $X_{k - 1}$ 的取值有关的随机过程 $X_n$，形式化理解：
- 下一步只看当前：
$$P(X_{k_{m+1}}\in A\mid X_{k_m},X_{k_{m-1}},\dots,X_{k_1})=P(X_{k_{m+1}}\in A\mid X_{k_m})$$
- 未来任意一步，只看当前，不必再看更早的过去：
$$P(X_{n+1}\in A\mid X_n,X_{n-1},\dots,X_0)=P(X_{n+1}\in A\mid X_n)$$
- 给定当前状态，则将来的状态与过去的状态独立：$$P(C\mid BA) = P(C\mid B) \Leftrightarrow P(CA|B) = P(C|B)P(A|B)$$
**齐次马尔科夫链**：$n$ 步状态转移概率不依赖于时刻，只依赖于时间间隔 $n$，即 $$P(X_{k + n} = j \mid X_k = i) = p_{ij}^{(n)}$$
- 一步转移概率：$p_{ij} = P(X_{k + 1} = j \mid X_k = i)$
- **Chapman-Kolmogorov (C-K) 方程**：$n$ 步转移概率完全由 $p_{ij}$ 完全决定 $$p_{ij}^{(n + m)} = \sum_{k \in \mathcal E} p_{ik}^{(n)} p_{kj}^{(m)}$$
- CK 方程的证明：$$\begin{aligned}p_{ij}^{(n + m)}  &= P(X_{l + n + m} = j \mid X_{l} = i) \\ &= \sum_{k \in \mathcal E}P(X_{l + n} = k \mid X_{l} = i) · P(X_{l + n +m}=j \mid X_{l + n} = k, X_k = i) \\ &= \sum_{k \in \mathcal E} P(X_{l + n} = k \mid X_{l} = i) ·P(X_{l + n +m}=j \mid X_{l + n} = k) \\&=\sum_{k \in \mathcal E} p_{ik}^{(n)} p_{kj}^{(m)}\end{aligned}$$
- CK 方程可以写成矩阵形式称为**状态转移概率矩阵** ${\boldsymbol P}^{(n + m)} = {\boldsymbol P}^{(n)}{\boldsymbol P}^{(m)}$，$\boldsymbol P^{(n)} = \boldsymbol P^{n}$
	- 该矩阵的每一行的总和均为 $1$
- 从 CK 方程可以推出有限维联合分布：$$P(X_0 = i_0, X_1 = i_1,\cdots,X_m=i_m) = p_0(i_0)·p_{i_0i_1}·p_{i_1i_2}\cdots p_{i_{m-1}i_m}$$
- **递推函数表示**：$X_{n + 1} = f(X_n, Z_{n + 1})$，其中 $\{Z_i\}_{n = 1}^{\infty}$ 独立同分布与 $X_0$ 独立。
- **状态转移图表示**：节点表示状态，带权有向边表示转移情况及其概率。

# 状态分类及性质

**可达**：状态的可达性，$i \to j$，当且仅当 $\exists n > 0, p_{ij}^{(n)} > 0$。具有传递性

派生概念：不可达 $i \not\to j$，用状态图可以清晰的看出可达性

**相通**：两个状态相互可达，$p_{ij}^{(m)},\, p_{ji}^{(n)}$
- 是一种等价关系，满足自反、对称、传递

**闭集**：集合中的状态无法跳出，$S \subseteq \mathcal E$，$\forall i \in S,j \not\in S$，则 $i \not \to j$，则称 $S$ 是闭集

派生概念：吸收态（单状态闭集）

**不可约**：没有闭的真子集的状态空间，则称其不可约。
- 不可约的集合中任意两个状态都互通。

**状态的周期**：每个状态转移回本身的所有步长的最大公约数 $$d_i = \gcd \{n \ge 1:p_{ii}^{(n)} > 0\}$$
派生概念：周期态（$d_i > 1$）、非周期态（$d_i = 1$）

- 周期与相通的关系：若 $i \leftrightarrow j$，则 $d_i = d_j$


**首达概率**：状态 $i$ 通过 $n$ 步第一次到达状态 $j$ 的概率 $$f_{ij}^{(n)} = P(X_n = j, X_{n-1}\ne j,\cdots,X_1\ne j \mid X_0 = i)$$
**常返态**：无论迟早总能返回到自身的状态 $$f_{ii} = \sum_{n = 1}^{\infty} f_{ii}^{(n)} = 1$$
派生概念：
- 瞬时态（滑过态、非常返态）：$\displaystyle f_{ii} = \sum_{n = 1}^{\infty} f_{ii}^{(n)} < 1$
- 正常返（返回期望时间收敛）：$\displaystyle \mu_i = \sum_{n = 1}^{\infty} nf_{ii}^{(n)} < \infty$
- 零常返（返回期望时间发散）：$\displaystyle \mu_i = \sum_{n = 1}^{\infty} nf_{ii}^{(n)} = \infty$

**常返性的判据：**
- 状态 $i$ 是常返态当且仅当 $\displaystyle \sum_{n = 0}^{\infty} p_{ii}^{(n)} = \infty$
- 状态 $i$ 是瞬时态当且仅当 $\displaystyle \sum_{n = 0}^{\infty} p_{ii}^{(n)}<\infty$

$\displaystyle p_{ij}^{(n)} = \sum_{k = 1}^n f_{ij}^{(k)} p_{jj}^{(n - k)}$，概率母函数 $P = 1 + FP \Leftrightarrow \displaystyle P = \frac{1}{1 - F}$，

对于平衡随机徘徊过程，在一维和二维下是常返的，在三维以上不常返。直观上是因为维数变大，走出去回归的概率越来越小。

对于一维平衡随机徘徊过程，是零常返的。对于二维的话，自然也是零常返的。


**$n$ 步转移概率的极限**：
- 瞬时态 / 零常返态的返回概率极限：$\displaystyle \lim_{n \to \infty} p_{ii}^{(n)} = 0$
- 非周期常返态的返回概率极限：$\displaystyle \lim_{n \to \infty} p_{ii}^{(n)} = \frac{1}{\mu_i}$
- 周期为 $d_i$ 的常返态的返回概率极限：$\displaystyle \lim_{n \to \infty} p_{ii}^{(nd_i)} = \frac{d_i}{\mu_i}$
- 瞬时态 / 零常返态的到达概率极限：$\displaystyle \forall i,\, \lim_{n \to \infty} p_{ij}^{(n)} = 0$
- 非周期正常返态的到达概率极限：$\displaystyle \forall i,\, \lim_{n \to \infty} p_{ij}^{(n)} = \frac{f_{ij}}{\displaystyle \sum_{n = 1}^{\infty} f_{ij}^{(n)}}$

**有限状态 Markov 链的常返性**：
- 有限状态 Markov 链一定存在正常返态
- 对于不可约的有限状态 Markov 链，所有状态都是正常返态


**非常返态分析**：为了计算从非常返态出发，进入常返态的概率及时间。
- 方法：单步递推

**对状态集合的分析**：
- 能否到达 $A$：$T_1^{\mathcal A} = \min \{X_n = S\mid X_0 = i\}$
- 平均要多久才能到达 $A$

# 3.3 极限分布与平稳分布

**极限分布**：对于状态空间的一个分布 $p_i$，满足非负性和归一性，并且使得 $$p_i = \lim_{n \to \infty} P(X_n = i) = \lim_{n \to \infty} \sum_{j \in \mathcal E} P(X_0 = j) p_{ji}^{(n)}$$

对于非常返态和零常返态 $j$，有 $\displaystyle \lim_{n \to \infty} P(X_n =j) = 0$，对于非周期正常返态有非零值，对于周期性正常返态，极限分布不存在。

对于可约的 Markov 链，概率极限分布通常是和状态初值有关。对于不可约的 Markov 链，通常和状态初值无关。

**平稳分布**：对于一步转移概率矩阵 $\boldsymbol P$，若存在概率分布 $\pi = \{\pi_0, \pi_1,\cdots\}$ （满足非负性和归一性）满足 $\boldsymbol \pi = \boldsymbol {\pi P}$，则称该概率分布为平稳分布或不变分布。
- 性质：若初始分布为 $\boldsymbol \pi$，则任意时刻分布均为 $\boldsymbol \pi$.
- 可以用线性方程组求解，这导致平稳分布可能不唯一。

**极限分布与平稳分布的关系**：
- 如果极限分布存在，那么它一定是平稳分布（由定义可以推出）
- 但是平稳分布不一定说明他就是极限分布
- 周期性 Markov 链没有极限，但是平稳分布可能存在
- 不可约零常返或瞬时 Markov 链，极限为零（不存在极限分布），但没有平稳分布。
- 对于 *有限状态、不可约、非周期* 的 Markov 链，极限分布和平稳分布完全等同
