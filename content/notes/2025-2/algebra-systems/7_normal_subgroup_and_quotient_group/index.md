---
title: 代数结构 | Week 7+8 正规子群和商群
date: 2026-04-17
summary: 正规子群、商群
---

# 正规子群

**正规子群**：左陪集和右陪集相等的子群，即 $H \le G,\ \forall a \in G,\ aH = Ha$. 我们记作 $H \trianglelefteq G$.
- 单位元子群 $\{e\}$ 和群 $G$ 本身都是正规子群，称为平凡正规子群。
- 交换群的任意子群都是正规子群（由于 $ab = ba$）
- 若 $H \le G,\ K \le G$，而 $H \trianglelefteq G$ 且 $H \subseteq K$，则 $H \trianglelefteq K$.
- 若 $H \le G,\ \forall a \in G,\ \exists b \in G,\  aH = Hb$ 则 $H \trianglelefteq G$.

**正规子群的判定**：对于 $H \le G$，下面是判定 $H \trianglelefteq G$ 的等价条件
- $\forall a \in G,\ aH = Ha$
- $\forall a \in G,\ aNa^{-1} = N$
- $\forall a \in G,\ aNa^{-1} \subseteq N$
- $\forall a \in G,\ \forall h \in H,\ aha^{-1}\in H$

**正规子群的性质**：
- 若 $H \trianglelefteq G,\ K \trianglelefteq G$，则 $H \subseteq K \trianglelefteq G$，且 $HK \trianglelefteq G$.
- 只有两个陪集的子群一定是正规子群，因为它的不等陪集只能是另外一个。
- 如果群 $G$ 的子群 $H$ 不与 $G$ 的任意其他子群等势，则 $H$ 是 $G$ 的正规子群！

# 商群

**商群**：对于正规子群 $N$，我们依照它的陪集定义等价类 $G / N = \{Na \mid a \in G\}$，则我们定义等价类之间的运算类似于 $G$ 中的二元运算，则 $G/N$ 也构成群：$$\forall a, b,\ Na \circ Nb = Nab$$
- 满足结合律 $(Na\circ Nb)\circ Nc = Na \circ (Nb \circ Nc)$
- 存在单位元 $N$.
- 存在逆元 $Na \circ Na^{-1} = N$

**商群的性质**：
- 若 $H \trianglelefteq G$，且 $G$ 是交换群，则 $G/H$ 也是交换群
- 