---
title: 代数结构 | Week 6 子群的陪集
date: 2026-04-10
summary: 子集乘积、子集陪集、拉格朗日定理
---

# 子集乘积

**子集乘积**：
- $A, B\subseteq G,\  AB=  \\\{ab \mid a \in A, b \in B\\\}$
- $A = \\\{g\\\}$，则 $gB = \\\{gb \mid b \in B\\\}$
- $B =  \\\{g\\\}$，则 $Ag = \\\{ag \mid a \in A\\\}$

**子集乘积的性质**：
- 若 $G$ 是交换群，则 $AB = BA$，否则一般不满足该性质。
- 子集乘积一般不满足交换律，也一般不满足消去律
- 满足结合律：$A(BC) = (AB)C$
- 若 $gA = gB$ 或 $Ag = Bg$，则 $A = B$
	- 证明：存在逆元 $g^{-1}$，则 $g^{-1}gA = g^{-1}gB$ 即 $A = B$.
- 若 $H$ 是子群则 $HH = H$.
	- 证明：$\forall a\in H,b\in H, ab \in H$ 则 $HH=H$.
- 若 $A\le G, B\le G$，若 $AB \le G$ 当且仅当 $AB = BA$
	- 必要性证明：$x \in AB$，那么 $x = ab,\  ab, b^{-1}a^{-1} \in AB$，而 $b^{-1}a^{-1} \in BA$，故 $ab \in BA$，得到 $AB \subseteq BA$，交换方向同理，故二者相等。
	- 充分性证明：$x,y \in AB$，那么 $x = ab, y = a'b'$，故 $xy^{-1} = a(bb'^{-1})a \in ABA = A(BA) = A(AB) = AB$，因此 $AB$ 是子群。

# 子群陪集

左陪集：$H \le G,\  aH = \\\{ah\mid h \in H\\\}$

右陪集：$H \le G,\  Ha = \\\{ha \mid h \in H\\\}$

陪集是对群的划分，$H$ 是一个代表的等价类/划分，每个配集相当于是和 $H$ 相似的集合。

**子群陪集的性质**：（下面只讨论右陪集，而左陪集是完全一致的）
- $H \le G,\  a \in Ha$
- $H\le G$，那么 $Ha \le G$ 当且仅当 $Ha \in H$ 当且仅当 $a \in H$.
- $H \le G$，那么 $Ha = Hb$ 当且仅当 $ab^{-1}\in H$
	- 充分性证明：$x \in Ha$ 那么 $h \in H,\  x = ha$，令 $h' = hab^{-1}$（需要有 $ab^{-1}\in H$），则 $x = h'b\in Hb$，故 $Ha \in Hb$，反向同理可证。
	- 必要性证明：$x \in Ha$ 那么 $h \in H,\  x = ha$，$x \in Hb$ 那么 $h' \in H,\  x = h'b$，那么 $ha = h'b$ 即 $ab^{-1} = h^{-1}h\in H$.
- 子群的所有右陪集构成的集合族是一个划分 $G \backslash H$，因此这些陪集两两不交。
- 正规子群：$\forall a \in G,\  aH = Ha$

（还漏了一些后面的性质，要补上）

# 拉格朗日定理

陪集等势：$H\le G,\  |Ha| = |H| = |aH|$
- 证明：群的运算满足消去律，所以 $x,y\in H, x\ne y \Leftrightarrow xa \ne ya$，所以配集大小不变。

子群的指标：$[G:H]$，即子群陪集的个数

**拉格朗日定理**：$H\le G$，那么 $|G| = |H|· |G:H|$，即群的阶等于子群的阶 和 子群陪集个数 的乘积。

推论 1：$n$ 阶有限群 $G$ 中，每个元素 $a$ 的阶 $|a|$ 是 $n$ 的 因子
- 证明：$\langle a\rangle \le G$，则 $|\langle a \rangle| \mid n$

推论 2（费马小定理）：对于素数 $p$，若 $a \perp p$，则 $a^{p - 1} \equiv 1 \pmod p$
