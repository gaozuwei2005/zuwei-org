---
title: 离散数学 | 集合、关系和函数 | Week 10 关系
summary: 定义与表示、运算、性质
date: 2025-11-10
toc: true
---


# 关系的定义和表示

**笛卡尔积**：两集合中所有元素构成的有序对的集合 $A \times B = \{\langle a, b \rangle \mid a \in A \land b \in B\}$。

- 笛卡尔积不满足交换律，也不满足结合律。
- 若 $|A| = n, |B| = m$ 则 $|A \times B| = nm$.

**二元关系**：集合 $A$ 到 $B$ 的二元关系 $R$ 为笛卡尔积 $A \times B$ 的子集，即 $R\subseteq A \times B$.
- $A = B$ 则称 $R$ 为 $A$ 上的二元关系
- $\langle a,b \rangle \in R$ 记为 $a\ R\ b$，$\langle a,b \rangle \notin R$ 记为 $a\ \not R\ b$，

**二元关系的表示**：类似于集合的表示。
- 元素枚举法
- 性质概括法
- 归纳定义法
- 关系图：
	- 对于 $A$ 到 $B$ 的二元关系，用一个二分图表示，左列点是 $A$ 的元素，右列点是 $B$ 的元素。若 $\langle a,b \rangle \in R$ 则连边 $a \to b$.
	- 对于 $A$ 上的二元关系，用一个图表示，点是 $A$ 的元素，若 $\langle a,b \rangle \in R$ 则连边 $a \to b$. 可能会有环。
- 关系矩阵：对于 $A$ 到 $B$ 的二元关系，其中 $|A| = n, |B| = m$，那么构建 $n \times m$ 的矩阵 $M$，其中 $m_{ij} = [\langle a_i,b_j \in R\rangle]$.

**特殊关系**：
- 空关系：$\emptyset \subseteq A \times B$.
- 全关系：$A \times B \subseteq A \times B$
- 恒等关系 / 对角关系：$\Delta = \{\langle a, a \rangle \mid a \in A\} \subseteq A \times A$

# 关系的运算

**类似于集合**：集合并、集合交、集合差、集合补

**逆关系**：对于二元关系 $R \subseteq A \times B$，定义逆关系 $R^{-1} = \{\langle b,a\rangle\mid\langle a,b \rangle\in R\} \subseteq B \times A$

逆关系的基本性质：
- $(R^{-1})^{-1} = R$
- 保持子集关系：若 $R \subseteq S$ 则 $R^{-1} \subseteq S^{-1}$
- 对并、交运算的分配：$(R \cup S)^{-1} = R^{-1} \cup S^{-1}$，$(R \cap S)^{-1} = R^{-1} \cap S^{-1}$


**关系复合**：对于二元关系 $R \subseteq A \times B$ 和 $S \subseteq B \times C$，定义关系复合 $S\circ R = \{\langle a, c \rangle \mid \exists b \in B (\langle a,b \rangle \in R \land \langle b,c \rangle \in S)\}$
- 注意前面是 $S$，后面是 $R$，通常称为**逆序复合**，先写外层再写内层。
- 理解：关系的传递。
- 关系复合可以用关系矩阵的**逻辑积** $R \odot S$ 表示，其中 $$(R \odot S)_{ij} = \bigvee_k (r_{ik} \land s_{kj})$$
关系复合的性质：
- 结合律：$T \circ (S \circ R) = (T \circ S) \circ R$
- 单位元：$\Delta \circ R = R \circ \Delta = R$
- 保持子集关系：若 $R \subseteq S \land T \subseteq W$，则 $T \circ R \subseteq W \circ S$
- 与关系逆关系：$(R \circ S)^{-1} = S^{-1} \circ R^{-1}$
- **对集合并的分配律**：*可由存在量词对析取分配证明*
	- $T \circ (R \cup S) = (T \circ R) \cup (T \circ S)$
	- $(R \cup S) \circ T = (R \circ T) \cup (S \circ T)$
- **对集合交不满足分配律**，只有子集关系：原因是存在量词对合取不满足分配
	- $T \circ (R \cap S) \subseteq (T \circ R) \cap (T \circ S)$
	- $(R \cap S) \circ T \subseteq (R \circ T) \cap (S \circ T)$

# 关系的性质

**关系性质的形式化表达**：

| **性质** |                                        **元素考察法定义**                                        | 性质概括法定义                              | 关系矩阵特征             |
| :----: | :---------------------------------------------------------------------------------------: | ------------------------------------ | ------------------ |
|  自反性   |                           $$\forall a \in A,\ ((a, a) \in R)$$                            | $$\Delta_A \subseteq R$$             | 对角线均为 $1$          |
|  反自反性  |                          $$\forall a \in A,\ ((a, a) \notin R)$$                          | $$R \cap \Delta_A = \emptyset$$      | 对角线均为 $0$<br>（无自环） |
|  对称性   |             $$\forall a,\ b \in A, ((a, b) \in R \rightarrow (b, a) \in R)$$              | $$R = R^{-1}$$                       | 关于对角线对称<br>（无向图）   |
|  反对称性  |     $$\forall a,\ b \in A \, ((a, b) \in R \land (b, a) \in R \rightarrow (a = b))$$      | $$R \cap R^{-1} \subseteq \Delta_A$$ | 关于对角线相反<br>（有向图）   |
|  传递性   | $$\forall a,\ b,\ c \in A \, ((a, b) \in R \land (b, c) \in R \rightarrow (a, c) \in R)$$ | $$R \circ R \subseteq R$$            | 闭包<br>             |

满足某性质的集合通过关系运算后，是否能保持性质：

| 关系运算         | 自反性 | 反自反性 | 对称性 | 反对称性 | 传递性 | 理解                     |
| ------------ | --- | ---- | --- | ---- | --- | ---------------------- |
| 关系逆 $R^{-1}$ | 是   | 是    | 是   | 是    | 是   | 逆运算不改变关系本质，只改变方向，性质都保持 |
| 集合交 $R∩S$    | 是   | 是    | 是   | 是    | 是   | 交集保持所有好性质              |
| 集合并 $R∪S$    | 是   | 是    | 是   | 否    | 否   | 并集加入新边，破坏反对称和传递        |
| 集合差 $R-S$    | 否   | 是    | 是   | 是    | 否   | 差集删掉一些边，自反性和传递性破坏      |
| 关系复合 $R∘S$   | 是   | 否    | 否   | 否    | 否   | 关系复合形成复杂结构，性质基本无法保持    |
