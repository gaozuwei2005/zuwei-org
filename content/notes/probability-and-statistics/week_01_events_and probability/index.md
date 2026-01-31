---
title: 概率论与数理统计 | Week 1 事件与概率
date: 2025-09-10
summary: 随机试验、随机事件、频率与概率、古典概型、条件概率、独立性
---

# 1.1 随机试验
随机试验的**特点**：
- 相同条件，重复进行
- 能明确所有可能结果，且不止一个
- 结果未知
# 1.2 样本空间、随机事件
**样本点**：每种结果

**样本空间**：所有样本点的集合

**随机事件**：随机试验的结果，用大写字母表示

随机事件是样本空间的一个子集。

样本空间是**必然事件**，空集是**不可能事件**，只含一个样本点的集合是**基本事件**。

**【事件的关系可用集合语言表达】**

相等 $A=B$

包含 $A\subset B$、和事件 $A\cup B$、积事件 $A\cap B$

差事件 $A - B$、逆事件/对立事件 $\overline{A}$、互不相容事件/互斥事件 $A \cap B = \emptyset$
![](attachments/Pasted-image-20250910150030.png)
运算规律：交换律、结合律、**分配律**（和对积、积对和均可）、**德摩根律**

和、积可拓展到 有限个 或 _可列个_

# 1.3 频率与概率

**频率** $\displaystyle f_n(A) = \frac{n_A}{n}$，频数为 $n_A$

**概率** $P(A) = \displaystyle \lim_{n \to \infty} f_n(A)$

**概率的公理化定义：**（公理，无需证明）
- 非负性：$0 \le P(A)$
- 规范性：$P(S) = 1$
- 可列可加性：无穷个两两互不相容事件 $\displaystyle P\left(\bigcup_{i = 1}^\infty A_i\right) = \sum_{i = 1}^\infty P(A_i)$

**概率的性质**：
- 不可能事件 $P(\emptyset) = 0$
	- 证明：$P(\emptyset \cap \emptyset) = 2P(\emptyset) = P(\emptyset)$，因此 $P(\emptyset) = 0$
- 有限可加性：$n$ 个两两互不相容事件 $\displaystyle P\left(\bigcup_{i = 1}^n A_i\right) = \sum_{i = 1}^n P(A_i)$
	- 证明：在可列可加性中，令后缀事件均为空集
- 若  $A\subset B$，则 $P(B) - P(A) = P(B-A), P(B)\ge P(A)$
	- 证明：用 $A$ 和 $B-A$ 的可加性
- $P(A) \le 1$
- 逆事件概率：$P(\overline A) = 1 - P(A)$
- 加法公式：$P(A\cup B) = P(A) + P(B) - P(AB)$
	- 证明：$A \cup B = A \cap (B - AB)$，用可加性

# 1.4 等可能概型（古典概型）
等可能概型/古典概型 的**特点**：
- 样本点数有限
- 基本事件可能性相同

$\displaystyle P(A) = \frac{k}{n} = \frac{\text{A包含的基本事件数}}{\text{基本事件总数}}$

古典概率常用**排列组合**计算

**几何概型**：
- 有无穷多个等可能结果的随机试验。
- 样本空间是某区域，实验结果落在度量相同的区域是等可能的
- $\displaystyle P(A) = \frac{m(A)}{m(S)}$

# 1.5 条件概率
**条件概率**：$\displaystyle P(B|A) = \frac{P(AB)}{P(A)}$，其中 $P(A) > 0$

对于古典概型问题，是容易理解的：$\displaystyle P(B|A) = \frac{AB 包含的基本事件数}{A 包含的基本事件数} = \frac{P(AB)}{P(A)}$

条件概率是一种概率，符合**公理化定义**：

对于所有条件概率 $P(·|A)$ 有
- 非负性：$P(B|A) \ge 0$
- 规范性：$P(S|A) = 1$
- 可列可加性：无穷个两两互不相容事件 $\displaystyle P\left(\left.\bigcup_{i = 1}^\infty A_i \right| A \right) = \sum_{i = 1}^\infty P(A_i | A)$

**乘法公式**：$P(AB) = P(A)P(B|A)$

推广：$P(ABC) = P(A)P(B|A)P(C|AB)$，依次类推


**全概率公式**：若 $S$ 能够划分成两两不相容的事件 $B_1, B_2, \cdots, B_n$，且 $P(B_i) > 0$，那么 $$P(A) = \sum_{i  = 1}^n P(B_i)P(A|B_i)$$
证明：利用有限可加性，以及乘法公式可以得出。

直观理解：$B_i$ 是导致 $A$ 的多种原因，那么 $A$ 是各个原因引起 $A$ 发生的概率之和。

**贝叶斯公式**：若 $S$ 能够划分成两两不相容的事件 $B_1, B_2, \cdots, B_n$，且 $P(B_i) > 0$，那么对于任意事件 $P(A) > 0$ 有 $$P(B_k | A) = \frac{P(B_kA)}{P(A)} = \frac{P(B_k)P(A|B_k)}{\displaystyle \sum_{i  = 1}^n P(B_i)P(A|B_i)}$$
理解：
- $P(B_k)$ 是先验概率，是对其可能性的初始认识；
- $P(B_k | A)$ 是后验概率，是知道新的信息后，对其可能性的重新估计。

# 1.6 独立性

**独立**：两事件相互独立，若 $P(AB) = P(A)P(B)$

理解：$\displaystyle P(A) = \frac{P(AB)}{P(B)} = P(A|B)$，即 $B$ 发生与否，对 $A$ 无影响，符合直觉。

对于四对事件 $A, B; A, \overline{B}; \overline{A}, B; \overline{A}, \overline{B}$，其中一对独立，其他三对都独立
- 可以用独立的定义来证明。

**多事件两两独立**：三事件两两独立，若 $\begin{cases}P(AB) = P(A)P(B) \\\\ P(AC) = P(A)P(C) \\\\ P(BC) = P(B)P(C) \end{cases}$.

**多事件相互独立**：三事件相互独立，若 $\begin{cases}P(AB) = P(A)P(B) \\\\ P(AC) = P(A)P(C) \\\\ P(BC) = P(B)P(C) \\\\ P(ABC) = P(A)P(B)P(C)\end{cases}$.

两两独立是相互独立的**必要不充分条件**。

$n$ 个事件相互独立，满足任意抽出子集事件，其积事件的概率都等于各事件的概率乘积。