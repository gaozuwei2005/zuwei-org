---
title: 代数结构 | Week 1 前置知识
date: 2026-03-06
summary: 等价关系、集合等势运算及其性质、代数概念
---


# 等价关系

**等价关系**：笛卡尔积 $A \times A$ 的子集且满足自反性、对称性、传递性的关系。

衍生概念：等价类、商集、集合划分

- 非空集合 $A$ 的等价关系与它的 **划分** 有一一对应关系。
- 非空集合 $A$ 的等价关系与 **以 $A$ 为定义域的满函数** 有一一对应关系。

**模 $m$ 整数同余关系**：
- 描述：$R:\,a \equiv b \pmod m$。
- 模 $m$ 剩余类 $\overline{a}$：同余关系下的等价类 $[a]_R$，其中 $a$ 是 *该等价类中最小自然数*
- 商集为 $\mathbb Z_m$

大小为 $n$ 的集合 $A$ 上的等价关系总个数，即它的划分数为 $\displaystyle \sum_{i = 1}^n B(n, i)$，其中 $\displaystyle B(n + 1, m) = \sum_{k = 0}^n \binom{n}{k} B(k, m - 1)$.

# 集合等势

**等势**：对于集合 $A, B$，若存在它们之间的双函数，则称它们等势，记作 $A \approx B$.

集合等势可以视作是所有集合组成的集合上的 *等价关系*，具有自反性、对称性、传递性。

重要的集合等势的例子：
- $\mathbb N \approx \mathbb Z$
- $\mathbb R \approx (0, 1)$
- $\wp (A) \approx 2^A = \{f \mid f : A \to 2\}$

**康托尔定理**：对于任意集合 $A$，不存在 $A$ 到它的幂集 $\wp(A)$ 的满函数。

该定理在有限集上显然，在无限集上可以用二难推理来证明。

康托尔定理的证明：构造 $B = \{a \in A \mid a \notin f(a)\}$，它没有原像，因为如果有 $f(b) = B$，则 $b$ 是否在集合中均会导致矛盾 $$b \in f(b) \Leftrightarrow b \in B \Leftrightarrow b \notin f(b)$$这说明了无限的量度是分等级的，并且可以有无穷多的层次。$$|A| < |\wp(A)| < |\wp(\wp(A))| < \cdots$$
**归纳集**：对空集和后继封闭的集合，$\emptyset \in A,\, a \in A \Rightarrow a^+ = a \cup \{a\} \in A$

**有穷集**：与自然数 $\{0, 1, 2, \cdots n\}$ 等势的集合。有穷集不与它的任何真子集等势。

**无穷集**：和它的某个真子集等势的集合。

**可数集**：有穷集或者与自然数集等势的集合。
- 例子：自然数集、整数集、有理数集、正整数对集合、自然数对集合

**不可数集**：与自然数集不等势的无穷集。
- 例子：实数集

# 运算及其性质

运算的 *严格* 定义：
- **二元运算**：形如 $f:\, S\times S\to S$ 的函数
- **$n$ 元运算**：形如 $f:\, S^n \to S$ 的函数
- 零元运算 / 常量运算：集合 $S$ 的元素

**运算的封闭性**：集合 $S$ 对运算 $f$ 封闭，则
- 从函数看：$f:\, S\times S \to S$ 是 $S$ 的运算
- 从一阶逻辑看：$\forall t_1,t_2 \in S,\ f(t_1,t_2) \in T$

运算的可能满足的性质：
- 一个运算：
	- 交换律、结合律
	- 幂等律：$a \circ a = a$
	- 消去律：$a \circ b = a \circ c \to b = c,\ b \circ a = c \circ a \to b  = c$
- 两个运算之间：
	- 分配律：包括左分配、右分配
	- 吸收律：$a \circ (a \star b) = a$
- 特殊元素：
	- 单位元：$e \circ a = a$
	- 零元 / 吸收元：$z \circ a = z$
	- 逆元：$a \circ a^{-1} = e$

# 代数概念

**代数**：一个集合以及这个集合上的一些运算 $\mathcal A = (A, f_1, f_2, \cdots, f_k)$。
- 该集合为代数的 *基集*。

**子代数**：对于两个代数 $\mathcal A = (A, f_1, f_2, \cdots, f_k),\, \mathcal B = (B, f_1, f_2, \cdots, f_k)$，若 $A \subseteq B$，则称 $\mathcal A$ 是 $\mathcal B$ 的子代数。此时子代数对于原代数的所有运算都 *封闭*。

可置换：对于代数结构 $\mathcal A = (A)$，$n$ 元运算 $f$，和一个等价关系 $\sim$，若对于任意 $a_1 \sim b_1,\, a_2 \sim b_2,\, \cdots,\, a_n \sim b_n$ 则 $f(a_1, a_2, \cdots, a_n) \sim f(b_1, b_2, \cdots, b_n)$，那么称 $\sim$ 与运算 $f$ 可置换。直观上讲，*可置换* 指的是运算前后能够保持等价关系。

**同余关系**：对于代数结构 $\mathcal A = (A, f_1, f_2, \cdots, f_k)$ 和一个等价关系 $\sim$，若对于任意运算 $f$ 和 $\sim$ 都可以置换，则称 $\sim$ 是同余关系。

**商代数**：对于代数结构 $\mathcal A = (A, f_1, f_2, \cdots, f_k)$ 和一个等价关系 $R$，我们对于*基集关于这个同余关系的商集* $A / R$ 定义同类型的代数系统 $\mathcal A / R = (A/R, f_1, f_2, \cdots, f_k)$。我们称该代数系统为 $\mathcal A$ 关于 $R$ 的商代数。
- 在运算的时候，等价类商代数的结果，等于等价类的代表作原代数运算的结果所在的等价类 $$f_i([a_1]_R, [a_2]_R, \cdots, [a_{n_i}]_R) = \left[f_i(a_1, a_2, a_3, \cdots, a_{n_i})\right]_R$$
- 商代数的例子：$[2]_5 \otimes_{\equiv_5} [3]_5 = [2 * 3]_5 = [1]_5$

代数的同类型：对于两个代数，如果它们所配备的运算个数相同，并且每个运算对应位置一致，每个运算的元数一一对应地相同，那么我们称两个代数是同类型的。

**代数同态**：对于两个同类型的代数 $\mathcal A= (A, f_1, f_2, \cdots, f_k)$ 和 $\mathcal B = (B, g_1, g_2, \cdots, g_k)$ 的基集的函数 $h: A \to B$，若有 $$\forall a, b \in A,\, h(f_i(a_1, a_2, \cdots, a_{n_i})) = g_i(h(a_1), h(a_2), \cdots, h(a_{n_i}))$$ 则称该函数与代数的所有运算 *可交换*，并且称该函数 $f$ 为 *代数同态*。
- 该定义直观上指，先运算后映射，与先映射后运算的结果相同。
- **单同态**：属于单函数的代数同态。*单同态与子代数一一对应*。
- **满同态**：属于满函数的代数同态。*满同态与商代数一一对应*。
- **代数同构**：若两个代数 $\mathcal A,\mathcal B$ 存在属于 *双函数* 的代数同态，则称这两个代数 *同构*，记作 $\mathcal A \cong \mathcal B$。

**代数同态基本定理**：对于两个代数 $\mathcal A = (A, f_1, f_2, \cdots, f_k)$ 和 $\mathcal B = (B, g_1, g_2, \cdots, g_k)$，若存在代数同态 $\varphi: A \to B$，我们定义一个 *核关系*（这种关系显然为等价关系） $$\ker \varphi = \{(a, a') \in A \times A \mid \varphi(a) = \varphi(a')\}$$
并定义令一个代数 $\varphi(\mathcal A) = (\text{Im } \varphi, g_1, g_2, \cdots, g_k) \le \mathcal B$，那么有 $$\mathcal A / \ker \varphi \cong \varphi(\mathcal A).$$
