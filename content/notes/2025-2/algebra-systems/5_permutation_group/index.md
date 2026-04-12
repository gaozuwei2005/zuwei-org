---
title: 代数结构 | Week 5 置换群
date: 2026-04-03
summary: 置换群
---


# 置换群

**$n$ 元置换**：在 $S = \\\{1, 2, \cdots, n\\\}$ 上的任何双函数 $\sigma: S \to S$，称为 $n$ 元置换 $$\sigma = \begin{pmatrix} 1 &2 & \cdots & n \\\\ \sigma(1) & \sigma(2) & \cdots & \sigma(n)\end{pmatrix}$$
- 置换的乘积：对应函数的复合 $\sigma \circ \tau$，注意是先做后面的置换再做前面的置换
- 衍生概念：恒等置换、逆置换

**$n$ 元对称群**：所有 $n$ 元置换关于置换乘法构成的群，记为 $S_n$

**$n$ 元置换群**：$S_n$ 的任意子群。

**$k$ 阶轮换**：对于 $n$ 元置换 $S$，若存在 $i_j \in S, j = 1, \cdots k$ 若 $$\sigma(i_1)=  i_2,\  \sigma(i_2)=  i_3,\  \cdots ,\ \sigma(i_{k - 1}) = i_k,\  \sigma(i_k)= i_1$$
- 衍生概念：对换、恒等轮换、不相交的轮换
- 不相交的轮换的乘积可交换：$\sigma\tau=\tau\sigma$
- 每个置换可以表示为一些不相交的轮换的乘积，每个不相交的轮换对应一个简单环
- 每个置换可以表示为一些对换的乘积，其中 $(i_1i_2i_3\cdots i_k)=(i_1i_2)(i_2i_3)\cdots(i_{k-1}i_k)$

# Conclusion

置换群：
- 置换乘积
- 写出不相交轮换和对换