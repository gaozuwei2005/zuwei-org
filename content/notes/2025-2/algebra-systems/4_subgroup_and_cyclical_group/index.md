---
title: 代数结构 | Week 4 子群和循环群
date: 2026-03-27
summary: 子群、生成子群、循环群
---

# 子群

**子群**：一个群的子集，但是关于原来的群的运算也满足群的条件，称为 $H \le G$.

$H\subseteq G$ 关于 $G$ 的运算构成群当且仅当：
- $H$ 对 $G$ 的运算封闭
- $G$ 的单位元属于 $H$
- 存在逆元：$\forall a \in H,\  a^{-1}\in H$

派生概念：真子群、平凡子群、非平凡子群、中心

子群的交与并：
- 若 $H\le G,\  K\le G$，则 $H\cap K\le G$
- 若 $H \cup K \le G$，当且仅当 $H \subseteq K \lor K\subseteq H$

# 生成子群

**生成子群**：对于群的一个子集，包含这个子集的最小的子群就是生成子群。（有点像闭包的定义），记为 $\langle S\rangle$.
- 一个子集的生成子群总是包含它的子群的子集
- $\langle S \rangle = \bigcap \\\{H \mid S\subseteq H \land H \le G\\\}$
- **循环群**：若 $\exists a \in G,\  G = \langle a \rangle$，则 $G$ 是由 $a$ 生成的循环群
- 空集的生成子群是单位元本身：$\langle \emptyset \rangle = \\\{e\\\}$

# 循环群

**循环群**：若 $\exists a \in G,\  G = \langle a \rangle$，则 $G$ 是由 $a$ 生成的循环群
- $\langle a^{-1}\rangle = \langle a \rangle$
- 群与阶：
	- 对于有限群 $|G| = |a|$、
	- 对于无限群可以直接取对数 $a^k=a^l\Leftrightarrow k=l$
	- 对于 $n$ 阶循环群 $a^k=a^l \Leftrightarrow n \mid (k - l)$.

派生概念：生成元、无限循环群、$n$ 阶循环群

常见的循环群的例子：
- 整数加群： $\langle \mathbb Z, + \rangle = \langle 1 \rangle = \langle -1 \rangle$
- 模 $m$ 加群：$\langle \mathbb Z_m, \oplus_m\rangle = \langle 1 \rangle$
- 模 $m$ 乘法下的可逆元素 $\gcd(m,x) = 1$：$U(m)$，如 $U(5) = \langle 2\rangle = \langle 3\rangle$
	- 当 $m = 1,2,4,p^k,2^k$ 时 $U(m)$ 才是循环群
	- $|U(m)| = \varphi(m)$
	- $U(m)$ 的生成元个数为 $\varphi(\varphi(m))$.
- 克莱因斯坦群：$\\\{e, a, b, c\\\}$，每个元素的逆元是自身，每两个元素乘积等于第三个元素

**生成元**：
- 对于无限循环群 $G = \langle a \rangle$，生成元只有两个 $a,\  a^{-1}$.
- 对于 $n$ 阶循环群 $G = \langle a \rangle$，生成元有 $\varphi(n)$ 个，且生成元必为 $\forall r,\  a^r, s.t.(n, r) = 1$. 证明 $$|a^r| = n \quad\Leftrightarrow\quad \frac{n}{(n, r)} = n \quad\Leftrightarrow\quad (n, r) = 1$$
- 对于 $n$ 阶循环群 $G =\langle a\rangle$，$\langle a^r \rangle = \langle a^{(n, r)}\rangle$

循环群的子群：
- 循环群的任意子群都是循环群。
- 对于无限循环群，它的全部子群集合为 $\\\{ \langle a^d \rangle \mid d = 0, 1, 2, \cdots \\\}$
- 对于 $n$ 阶循环群，它的全部子群集合为 $\\\{ \langle a^d \rangle \mid d  \mid n\\\}$

# Conclusion

群：
- 定义、逆元、消去律、重要例子（模加群、$U(m)$、置换群）
- 群元素、阶、阶的性质（$a^m = e \Leftrightarrow n \mid m$，$|a^r| = \frac{n}{(n, r)}$）
- 子群：封闭+单位元+逆元、$\forall a,b\in H,\ ab^{-1}\in H / a^{-1}b \in H$
- 循环群：$\langle a \rangle = \\\{ a^k \mid k \in \mathbb  Z\\\}$，找所有生成元，
	- 有限群 $a^r$ 是生成元 $\Leftrightarrow (n,r) = 1$，全部子群集合为 $\\\{ \langle a^d \rangle \mid d  \mid n\\\}$
	- 无限群 $a, a^{-1}$ 是生成元，全部子群集合为 $\\\{ \langle a^d \rangle \mid d = 0, 1, 2, \cdots \\\}$

