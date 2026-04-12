---
title: 离散数学 | 计数 | Week 15 递推
summary: 常系数线性齐次递推、常系数线性非齐次递推、主定理
date: 2025-12-15
toc: true
---


**常系数 $k$ 阶线性递推关系式**：$\displaystyle a_n = F(n) + \sum_{i = 1}^k c_i a_{n - i}$.

若 $F(n) = 0$，则为齐次递推；若 $F(n) \ne 0$，则为非齐次递推；

# 常系数线性齐次递推求解

**特征方程**：$\displaystyle x^k = \sum_{i = 1}^k c_i x^{k - i}$.

由代数基本定理知，该方程在复数域内有 $k$ 个可重根，假设有 $t$ 个不同根 $r_{1 \cdots t}$，重数分别为 $m_{1 \cdots t}$，则 $$a_n = \sum_{i = 1}^t r_i^n \sum_{j = 0}^{m_i - 1} \beta_{i, j} n^{j}$$
其中 $\beta_{i,j}$ 由将 $a_{1, 2, \cdots k}$ 代入以上方程求解线性方程组得到。

如果 $k$ 个根都不相同，则 $\displaystyle a_n = \sum_{i = 1}^t \beta_i r_i^n$.

# 常系数线性非齐次递推求解

先求出伴随特征方程 $\displaystyle x^k = \sum_{i = 1}^k c_i x^{k - i}$ 的根，

假设有 $t$ 个不同根 $r_{1 \cdots t}$，重数分别为 $m_{1 \cdots t}$，则齐次通解为 $$a_n^{(h)} = \sum_{i = 1}^t r_i^n \sum_{j = 0}^{m_i - 1} \beta_{i, j} n^{j}$$
然后如果 $\displaystyle F(n) = s^n \sum_{i = 0}^t b_i n^i$，为「多项式 $\times$ 常数指数」的形式，那么
- 如果 $s$ 不是伴随特征方程的根，则解的形式与 $F$ 相同 $\displaystyle a_n^{(p)} =s^n \sum_{i = 0}^t p_i n^i$.
- 如果 $s$ 是伴随特征方程的根，且重数为 $m$，则解需额外乘上 $n^m$，得 $\displaystyle a_n^{(p)} =n^ms^n \sum_{i = 0}^t p_i n^i$.
- 以上公式的 $p_i$ 需要代入 $a_{1, 2, \cdots, t}$ 求解线性方程组来决定。


最后 $$a_n = a^{(h)} + a^{(p)} = \sum_{i = 1}^t r_i^n \sum_{j = 0}^{m_i - 1} \beta_{i, j} n^{j} +n^ms^n \sum_{i = 0}^t p_i n^i$$

# 主定理

分治算法的时间复杂度通常可用递推关系式 $f(n) = af(n / b) + O(n^d)$ 来表示，其中 $a \ge 1, \ b > 1, d \ge 0$，那么 $$f(n) = af(n / b) + O(n^d) = \begin{cases}O(n^d),& a < b^d \\\\ O(n^d \log n),& a = b^d \\\\ O(n^{\log_b a}), & a > b^d\end{cases}$$
