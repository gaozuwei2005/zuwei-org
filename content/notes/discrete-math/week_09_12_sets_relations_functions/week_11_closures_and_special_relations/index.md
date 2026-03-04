---
title: 离散数学 | 集合、关系和函数 | Week 11 关系闭包、特殊关系
summary: 关系闭包、等价关系、偏序关系
date: 2025-11-17
toc: true
---


# 关系闭包
## 定义和基本性质

**关系的闭包**：包含一个关系且满足某个性质的最小关系。

| 类型   | 记号     | 特征                                                                                                                |
| ---- | ------ | ----------------------------------------------------------------------------------------------------------------- |
| 自反闭包 | $r(R)$ | $R \subseteq r(R) \ \land\  r(R) \text{ is reflective}\ \land\ \forall S \text{ is reflective},\ r(R)\subseteq S$ |
| 对称闭包 | $s(R)$ | $R \subseteq s(R) \ \land\  s(R) \text{ is symmetric}\ \land\ \forall S \text{ is symmetric},\ s(R)\subseteq S$   |
| 传递闭包 | $t(R)$ | $R \subseteq t(R) \ \land\  t(R) \text{ is transitive}\ \land\ \forall S \text{ is transitive},\ t(R)\subseteq S$ |

**基本性质**：
- $R$ 是自反/对称/传递关系，当且仅当 $r/s/t(R) = R$.
- **闭包保持子集关系**：若 $R \subseteq S$，则 $r/s/t(R)\subseteq r/s/t(S)$
- **闭包与关系并的关系**：
	- $r/s(R \cup S) = r/s(R) \cup r/s(S)$
	- $t(R) \cup t(S) \subseteq t(R\cup S)$
## 自反闭包的计算

只需添上所有对角线为 $1$ 即可：$r(R) = R \cup \Delta_A$.
## 对称闭包的计算

只需添上所有对称的 $1$ 即可：$s(R) = R \cup R^{-1}$.
## 传递闭包的计算

*（居然在高中学过）*

传递闭包问题：给出了若干个传递关系。现在需要求出任意两点 $x,y$ 能否从 $x$ 走到 $y$。

对问题进行考察，具有以下性质：
- 连通性：$(x,y) \in t(R)\ \Leftrightarrow \exists a_1 = x, a_2,\cdots, a_k = y\ (k \ge 2),\ \forall i = 1, 2, \cdots, k - 1,\  (a_i, a_{i + 1}) \in R$
- 枚举路径长度：$\displaystyle t(R) = \bigcup_{k = 1}^{\infty} R^k$，其中 $R^k = \underbrace{R \circ R \circ \cdots \circ R}_{k 个}$.
- 当 $|A| = n$ 时，路径长度最多为 $n$，即 $\displaystyle t(R) = \bigcup_{k = 1}^{n} R^k$.
### Floyd-Warshall 算法

设 $W_{ij}^{[k]} = 1$ 当且仅当从节点 $i$ 能经过所有中间结点都在 $[1, k]$ 中而到达 $j$。

**递推公式**：
- $W^{[0]} = R$，$W^{[n]} = t(R)$.
- 对于 $k > 0$，有 $W_{ij}^{[k]} = W_{ij}^{[k - 1]} \lor \left(W_{ik}^{[k - 1]} \land W_{kj}^{[k - 1]}\right)$.

**伪代码表示**：
```c++
for k = [1, n]
	for i = [1, n]
		for j = [1, n]
			w[i, j] = w[i, j] or (w[i, k] and w[k, j])
```

# 等价关系

**等价关系**：同时满足 *自反性、对称性、传递性* 的关系。（e.g. 数集上的相等关系）

描述了无向图的连通性。

**等价类**：对于非空集合 $A$ 上的 *等价关系* $R$，记 $a$ 所在的 $R$ 等价类为 $$[a]_R = \\\\\{b \in A \mid \langle a, b\rangle \in R\\\\\}$$
**商集**：$R$ 中所有等价类构成的集合为 $$A / R = \\\\\{[a]_R \mid a \in A\\\\\}$$
**等价类的基本性质**：
- 等价类非空：$\forall a \in A,\ [a]_R \neq \emptyset$
- 等价类要么相等要么不交：$[a]_R = [b]_R \Leftrightarrow \langle a, b \rangle \in R \qquad [a]_R \cap [b]_R = \emptyset \Leftrightarrow \langle a, b \rangle \notin R$
- 等价类广义并构成元素集：$\displaystyle \bigcup A / R = \bigcup_{a \in A} [a]_R = A$.

**划分**：集合族 $\mathcal F$ 是非空集合 $A$ 的 *划分* 当且仅当：
- 非空子集：$\forall S \in \mathcal F,\ S \ne \emptyset \land S \subseteq A$，每个 $S$ 称为 **划分块**。
- 两两不交：$\forall S_1, S_2 \in \mathcal F,\ S_1 \cap S_2 = \emptyset$。
- 覆盖集合：$\bigcup \mathcal F = A$。

每个等价类与其划分有**一一对应**关系。

# 偏序关系

**偏序关系**：同时满足 *自反性、反对称性、传递性* 的关系。（e.g. 数集上的小于等于关系）

描述了有向图的连通性。

**偏序集** $(A, \preccurlyeq)$：非空集合 $A$ 及其偏序关系 $\preccurlyeq$.

**可比**：若 $a \preccurlyeq b \lor b \preccurlyeq a$，则 $a$ 与 $b$ 可比，否则不可比。

**全序 / 线序**：任意两个元素都可比的偏序集。

**覆盖**：记 $a \preccurlyeq b \land a \ne b$  为 $a \prec b$，那么称 $a \prec b \land \lnot \exists c (a \prec c \land c \prec b)$ 为 $b$ 覆盖 $a$.

**哈斯图**：只包含 *覆盖边*，且被覆盖元素在下方，覆盖元素在上方。

偏序集的元素：
- 极大元（无后继）
- 最大元（其他均为其前继）
- 极小元（后前继）
- 最小元（其他均为其后继）

偏序集的子集：
- 上界（元素均为其前继）
- 上确界（最小的上界）
- 下界（元素均为其后继）
- 下确界（最大的下界）


