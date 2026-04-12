---
title: 离散数学 | 计数 | Week 13+14 排列组合计数
summary: 加乘原理、容斥原理、鸽笼原理、排列组合、组合恒等式、排列与组合的生成
date: 2025-12-01
toc: true
---


# 加乘原理

**加法原理**：若集合 $S$ 可被划分为集合族 $\mathcal{F}=\{S_1, S_2, \dots, S_n\}$，也即 $\mathcal{F}$ 是 $S$ 的一个划分，集合 $S$ 的元素个数等于这些子集合元素个数之和，即：
$$  
|S| = |S_1| + |S_2| + \cdots + |S_n|.  
$$


**乘法原理**：若集合 $S$ 的每个元素都是由 $n$ 元组 $\langle s_1, s_2, \dots, s_n \rangle$，每个元素 $s_i$ 可能有 $m_i$ 种取值，且对所有 $i < n$，无论 $s_i$ 取 $m_i$ 种值中的哪一个，$s_{i+1}$ 都有 $m_{i+1}$ 种可能取值。则集合 $S$ 的元素个数为  $|S| = m_1 m_2 \cdots m_n$ 或  $|S| = m_1 \times m_2 \times \cdots \times m_n$.

**减法原理：** 若 $U$ 是包含 $S$ 的更大集合，可看作全集，$U - S = \overline{S}$，那么 $|S| = |U| - |U-S|$。减法原理是加法原理的补原理。  

当 $|U|$ 和 $|U-S|$ 的计算比 $|S|$ 更简单时适合用减法原理。  

**除法原理：** 若存在满函数 $f: S \to T$，且 $T$ 的每个元素在 $f$ 下恰好有 $k$ 个原像，则  
$|T| = |S|/k$。

**一一对应原理：** 若集合 $S$ 和 $T$ 之间存在双射，则 $|S| = |T|$。

# 容斥原理

对于有限集合 $A_1, A_2, \dots, A_n$，其并集的大小可由容斥原理给出：

**一般形式：**
$$\left|\bigcup_{i=1}^n A_i\right|= \sum_{1 \le i \le n} |A_i|- \sum_{1 \le i < j \le n} |A_i \cap A_j|+ \sum_{1 \le i < j < k \le n} |A_i \cap A_j \cap A_k|- \cdots+ (-1)^{n-1} \left|A_1 \cap A_2 \cap \cdots \cap A_n\right|.$$

**三集合情形：**
$$|A \cup B \cup C|= |A| + |B| + |C|- |A \cap B| - |B \cap C| - |A \cap C|+ |A \cap B \cap C|.$$

**两集合情形：**
$$|A \cup B| = |A| + |B| - |A \cap B|.$$

# 鸽笼原理

**鸽笼原理**：$k + 1\ (k \in N^*)$ 只鸽子放到 $k$ 个鸽笼里，则存在鸽笼至少有两个鸽子。

**广义鸽笼原理**：将 $N$ 个物体放到 $k$ 个盒子当中，则存在鸽笼至少有 $\lceil N / k \rceil$ 个鸽子。

# 排列与组合

**排列**：$\displaystyle P_n^r = \frac{n!}{(n - r)!} = \underbrace{n · (n - 1) · \cdots (n - r + 1)}_{r\ 个}$

**组合**：$\displaystyle C_n^r = \binom{n}{r} = \frac{n!}{r! (n - r)!}$


**可重排列**：$\displaystyle \frac{(m_1 + m_2 + \dots + m_n)!}{m_1! · m_2!  \cdots  m_n!}$


**可重组合**：$\displaystyle \binom{n + r - 1}{r}$.

# 常见组合恒等式

- **吸收 / 提取恒等式**：

$$\binom n m = \dfrac{n}{m} \binom {n-1} {m-1} = \dfrac{m}{n-m + 1} \binom{n}{m - 1}$$

- **列求和 / 上指标求和**：即枚举最后一个元素的位置。

$$\sum_{i=0}^m \binom{n+i} n = \binom{n+m+1}{n+1}$$

- **斜线求和**：下指标对称一下就变成列求和。

$$\sum_{i=0}^m \binom{n+i} i = \dbinom {n+m+1} m$$

- **三项式恒等式**：求集合的子集的子集个数，相当于求集合的子集的超集个数。

$$\binom n r \binom r k = \binom n k\dbinom {n-k} {r-k}$$

- **下指标卷积 / 范德蒙德卷积**：即枚举左半部分选了多少个元素。

$$\sum_{k=0}^n \dbinom n i \dbinom m {k-i} = \dbinom{n+m} k$$

还有另一种：

$$\sum_{k} \binom n {a-k} \binom m {b+k} = \binom {n+m} {a+b}$$

- **下指标点积**：是范德蒙德卷积的特例。第二个组合数的下指标对称一下即可。

$$\sum_{i=0}^n \binom n i \binom m i = \binom {n+m} m$$

- **上指标卷积**：它等价于在中间插入一个分隔符，然后就变成 $(n+1)$ 个物品选择 $(a+b+1)$ 个物品的方案数和。**注意不要和下指标卷积混淆！** 上指标卷积的上下指标与下指标卷积相比均多加了个 $1$。

$$\sum_{i=0}^n \binom i a \binom {n-i} b = \binom {n+1}{a+b+1}$$
# 排列与组合的生成

**下一个全排列构造方法**：对于 $a = a_1a_2\cdots a_n$ 的下一个串
- 找到极长递减后缀，使得 $a_{i + 1}a_{i + 2}\cdots a_n$ 是递减序列。
- 找到 $a_{i + 1},a_{i + 2},\cdots, a_n$ 中比 $a_i$ 大且最小的数 $a_j$.
- 那么将 $a_j$ 放到第 $i$ 位，其余递增排列即可。

**下一个 r - 组合构造方法**：对于 $a = a_1 a_2 \cdots a_r$ （递增）的下一个组合
- 找到极长后缀，使得 $\forall i < j \le r,\ a_j = n - r + j$。
- 将所有 $j \in [i, r]$ 替换为 $a_i + 1, a_i + 2, \cdots, a_i + r - i + 1$.

