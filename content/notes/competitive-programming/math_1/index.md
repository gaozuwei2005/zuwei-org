---
title: OI 笔记合集 | 数学1：组合计数、多项式、生成函数
date: 2021-12-02
summary: FFT、NTT、多项式导数与积分、泰勒级数、多项式牛顿迭代、多项式对指幂函数、多项式除法、朴素计算多项式、拉格朗日插值、生成函数、exp组合意义与欧拉变换、多项式恒等式、下降幂恒等式、斯特林数、伯努利数、分拆数、线性递推、Prufer序列、FMT、FWT、集合幂级数
---

本部分为 组合计数 / 多项式 / 生成函数 笔记。

## 快速傅里叶变换 $\mathbf {(FFT)}$

- 核心思想：系数表示---DFT $O(n\log n)$--->点值表示:$O(n)$ 求乘积---IDFT $O(n\log n)$--->系数表示

- 原理：分治。

- DFT/IDFT 只能使用单位根实现相互转化。

对于 $k<n/2$：

- $f\left(w_n^k\right)=fl\left(w_{n/2}^k\right)+w_{n}^k\times fr\left(w_{n/2}^k\right)$
- $f\left(w_n^{k+n/2}\right)=fl\left(w_{n/2}^k\right)-w_{n}^k\times fr\left(w_{n/2}^k\right)$

这种变换方式相当于最后将序列位置按照二进制翻转来放置。

DFT：$g[i]=f(w_{n}^i)$，做法以上；

IDFT：$n·f[i]=g(w_{n}^{-i})$，还是一样的形式，只不过最后系数要除以 $n$.

## 快速数论变换 $\mathbf {(NTT)}$

将 FFT 中的单位根改为原根的若干次方即可。由于这个单位根要满足 $0\sim n-1$ 次根互不相同，并且要满足 $w^n=1$（相当于转了一圈），所以选取 $G^{(p-1)/n}$ 作为单位根。

$g[i]=f(G^i)$，$n·f[i]=g(G^{-i})$。

- ### [原根表](https://www.cnblogs.com/zhylj/p/10167753.html)

## 多项式导数与积分

根据幂函数的导数与积分有

- 求导：

$$\dfrac{\mathrm d}{\mathrm dx} f(x)=\sum\limits_{i=0}i·f[i]·x^{i-1}$$

- 积分：

$$\int f(x)\mathrm dx=\sum\limits_{i=0}\dfrac{f[i]}{i}·x^{i+1}$$

时间复杂度 $O(n)$

## 泰勒级数

泰勒级数是一种将一个函数转化成幂级数（多项式）的形式的方法。

我们想得到这样的形式（$f(x)$ 在 $x=a$ 下的泰勒展开）：$f(x)=c_0+c_1(x-a)+c_2(x-a)^2+c_3(x-a)^3\dots$

- 求 $c_0$：显然有 $c_0=f(a)$；
- 求 $c_1$：取 $f(x)$ 的导数 $f'(x)=c_1+2c_2(x-a)+3c_3(x-a)^2+\dots$，那么 $c_1=f'(a)$；
- 求 $c_2$：再取导数 $f''(x)=2c_2+2\times3c_3(x-a)+3\times4c_4(x-a)^2+\dots$，那么 $c_2=f''(a)/2$。
- $\dots$

我们发现每次取导数的时候，幂次下放，导致最后得到的系数乘了阶乘，所以我们需要除以一个阶乘。即

$$f(x)=f(a)+\dfrac{f'(a)}{1!}·(x-a)+\dfrac{f''(a)}{2!}·(x-a)^2+\dfrac{f'''(a)}{3!}·(x-a)^3+\dots=\sum\limits_{i=0}^{+\infty}\dfrac{f^{(i)}(a)}{i!}(x-a)^i$$

- 麦克劳林级数：函数在 $x=0$ 处的泰勒级数，即

$$f(x)=\sum_{i=0}^{+\infty}\dfrac{f^{(i)}(0)}{i!}x^i$$

常用泰勒级数：

- $e^x=\sum\limits_{i=0}^{+\infty}\dfrac{x^i}{i!}$
- $\dfrac{1}{1-x}=\sum\limits_{i=0}^{+\infty} x^i$
- $\ln (1-x)=-\sum\limits_{i=1}^{+\infty}\dfrac{x^i}{i}$
- $\ln (1+x)=-\sum\limits_{i=1}^{+\infty}\dfrac{(-x)^i}{i}$

## 多项式牛顿迭代法

- 给定多项式 $g(x)$，求满足 $g(f(x))\equiv 0\pmod {x^n}$ 在 $\bmod {x^n}$ 下的 $f(x)$

考虑倍增法，首先当 $n=1$ 的时候我们可以求出 $g(f(x))\equiv0\pmod{x^1}$。

我们现在已经得到了 $\bmod {x^n}$ 下的解 $f_0(x)$，现在我们需要求 $\bmod {x^{2n}}$ 下的解 $f(x)$。

我们将 $g(f(x))$ 在 $f_0(x)$ 处进行泰勒展开：

$$\sum_{i=0}^{+\infty}\dfrac{g^{(i)}(f_0(x))}{i!}(f(x)-f_0(x))^i\equiv0\pmod{x^{2n}}$$

由于我们是在 $\bmod x^{2n}$ 意义下，所以 $\ge 2$ 的 $i$ 都会直接变为 $0$，因此有

$$g(f_0(x))+g'(f_0(x))(f(x)-f_0(x))\equiv0\pmod {x^{2n}}$$

解得 $f(x)\equiv f_0(x)-\dfrac{g(f_0(x))}{g'(f_0(x))}\pmod{x^{2n}}$

这种倍增的方法本质是半在线卷积。

### 多项式求逆

假设给定函数 $h(x)$，我们需要解方程 $g(f(x))=\dfrac{1}{f(x)}-h(x)\equiv0\pmod{x^{2n}}$

首先要满足 $[x^0]h(x)\neq 0$，否则不存在逆元。

那么我们有

$$
\begin{aligned}
f(x)&\equiv f_0(x)-\dfrac{\dfrac{1}{f_0(x)}-h(x)}{-\dfrac{1}{f_0^2(x)}}&\pmod {x^{2n}}\\\\
&\equiv2f_0(x)-f_0^2(x)·h(x)&\pmod {x^{2n}}\\\\
\end{aligned}
$$

每次迭代我们需要 $O(1)$ 次多项式乘法，时间复杂度 $T(n)=T\left(\dfrac{n}{2}\right)+O(n\log n)=O(n\log n)$。

### 多项式开根

假设给定函数 $h(x)$，我们需要解方程 $g(f(x))=f^2(x)-h(x)\equiv0\pmod{x^{2n}}$

首先要满足 $[x^0]h(x)>0$，否则我们要找到最低次项 $ax^i$ 满足 $a>0,2|i$，然后我们将 $h(x)$ 整体除以 $ax^i$，转化为前者的情况，最后再乘以 $\sqrt ax^{i/2}$。否则不存在 $\sqrt {h(x)}$。

那么我们有

$$
\begin{aligned}
f(x)&\equiv f_0(x)-\dfrac{f_0^2(x)-h(x)}{2f_0(x)}&\pmod {x^{2n}}\\\\
&\equiv\dfrac{f_0^2(x)+h(x)}{2f_0(x)}&\pmod {x^{2n}}\\\\
\end{aligned}
$$

每次迭代我们需要 $O(1)$ 次多项式求逆 + 多项式乘法，时间复杂度 $T(n)=T\left(\dfrac{n}{2}\right)+O(n\log n)=O(n\log n)$。

## 多项式对指幂函数

### 多项式对数函数 $\mathbf{ln}$

我们用麦克劳林级数定义多项式的对数函数

$$\begin{aligned}
\ln (1-f(x))&=-\sum_{i=1}^{+\infty}\dfrac{f^i(x)}{i}\\\\
\ln (1+f(x))&=-\sum_{i=1}^{+\infty}\dfrac{(-f(x))^i}{i}
\end{aligned}$$

其实用 $\ln f(x)$ 也能定义，[不过比较麻烦](https://www.zhihu.com/question/415271590)

$$\ln f(x)=-\sum_{i=1}^{+\infty}\dfrac{(1-f(x))^i}{i}$$

首先我们要满足 $[x^0]f(x)=1$，否则就不存在 $\ln f(x)$

对 $\ln f(x)$ 求导再积分，有

$$\begin{aligned}
\dfrac{\mathrm d}{\mathrm dx}\ln f(x)&\equiv \dfrac{f'(x)}{f(x)}&\pmod {x^n}\\\\
\ln f(x)&\equiv \int\dfrac{f'(x)}{f(x)}\mathrm dx&\pmod{x^n}
\end{aligned}$$

这也是计算很多式子的对数函数的常用方法：求导再积分。

求导积分时间复杂度均为 $O(n)$，求逆和乘法时间复杂度为 $O(n\log n)$，故总时间复杂度为 $O(n\log n)$。

### 多项式指数函数 $\mathbf{exp}$

我们用麦克劳林级数定义多项式的指数函数

$$\exp f(x)=e^{f(x)}=\sum_{i=0}^{+\infty}\dfrac{f^i(x)}{i!}$$

首先我们要满足 $[x^0]f(x)=0$，否则就不存在 $\exp f(x)$

假设给定函数 $h(x)$，我们需要解方程 $g(f(x))=\ln f(x)-h(x)\equiv0\pmod{x^{2n}}$

我们使用多项式牛顿迭代法，有

$$
\begin{aligned}
f(x)&\equiv f_0(x)-\dfrac{\ln f_0(x)-h(x)}{\dfrac{1}{f_0(x)}}&\pmod {x^{2n}}\\\\
&\equiv f_0(x)(1-\ln f_0(x)+h(x))&\pmod {x^{2n}}\\\\
\end{aligned}
$$

每次迭代我们需要 $O(1)$ 次多项式 $\ln$ + 多项式乘法，时间复杂度 $T(n)=T\left(\dfrac{n}{2}\right)+O(n\log n)=O(n\log n)$。常数非常大，有时候甚至可以视为 $O(n\log^2 n)$。

- 在计算若干个多项式乘积的时候，我们不妨对它们取 $\ln$（求导+积分），然后就变成了若干个多项式相加，这是容易的。最后再将他们和做一个 $\exp$ 即可。

$$\prod F_i=\exp\sum \ln F_i=\exp\sum\int \dfrac{F'_i}{F_i}\mathrm dx$$

### 多项式幂函数

- 当 $[x^0]f(x)=1$ 时，有 $f^k(x)=e^{k \ln f(x)}$；
- 当 $[x^0]f(x)\ne1$ 时，我们设 $f(x)$ 的最低次项为 $f_ix^i$，我们将 $f(x)$ 整体除以这个最低次项，然后再转化为第一种情况，最后再乘以 $f_i^kx^{ik}$。

$O(1)$ 次多项式 $\ln$ + 多项式 $\exp$，时间复杂度 $O(n\log n)$。

求多项式幂函数 $\approx$ 写一遍多项式全家桶。

## 多项式除法

- 给定多项式 $f(x),g(x)$，求商多项式 $q(x)$ 和余数多项式 $r(x)$ 满足 $f(x)=q(x)·g(x)+r(x)$，其中 $\deg f=\deg g+\deg q,\deg r<\deg q$

记 $n=\deg f,m=\deg g$。我们构造反转函数 $f^{rev}(x)=x^nf(1/x)$，即将 $f(x)$ 内的系数反转。

我们将 $x$ 替换为 $1/x$，并再在两边乘 $x^n$，在 $\bmod {x^{n-m+1}}$ 意义下可以得到

$$\begin{aligned}
x^nf(1/x)&\equiv x^{n-m}q(1/x)·x^mg(1/x)+x^{n-m+1}·x^{m-1}r(1/x)&\pmod {x^{n-m+1}}\\\\
f^{rev}(x)&\equiv q^{rev}(x)·g^{rev}(x)+x^{n-m+1}r^{rev}(x)&\pmod {x^{n-m+1}}\\\\
\dfrac{f^{rev}(x)}{g^{rev}(x)}&\equiv q^{rev}(x)&\pmod {x^{n-m+1}}\\\\
\end{aligned}
$$

我们做一次多项式求逆 + 多项式乘法即可求出 $q^{rev}(x)\to q(x)$，再算 $r(x)=f(x)-q(x)g(x)$ 用一次多项式乘法求出。

时间复杂度 $O(n\log n)$.

## 朴素地计算多项式全家桶

有时候我们 不需要 / 无法 使用多项式技术，但只要求 $O(n^2)$ 计算多项式全家桶。

- **朴素多项式乘法**

直接枚举：$h_i = \sum\limits_{j=0}^i f_j·g_{i-j}$.

- **朴素多项式求逆**

显然有 $F * H = \sum\limits_{i=0}^n \sum\limits_{j=0}^i f_i·h_{i-j}=1$

因此可以解得 $f_{0}=\dfrac{1}{h_0}, f_i = \dfrac{1}{h_0}\sum\limits_{j=0}^{i-1} f_j·h_{i-j}$ $(i>0)$，前提是 $h_0 \ne 0$.

- **朴素多项式除法**

由 $F * G = H$ 得到显然有 $F * G = \sum\limits_{i=0}^n \sum\limits_{j=0}^i f_i·g_{i-j} = \sum\limits_{i=0}^n h_i$

解得 $f_0 = \dfrac{h_0}{g_0}, f_i = \dfrac{1}{g_0}\sum\limits_{j=0}^{i-1} f_j·g_{i-j}$ $(i>0)$，前提是 $g_0 \ne 0$.

- **朴素多项式开根**

由 $F * F = H$ 得到 $\sum\limits_{i=0}^n \sum\limits_{j=0}^i f_i·f_{i-j} = \sum\limits_{i=0}^n h_i$

解得 $f_{0}=\sqrt{h_0},f_i=\dfrac{1}{2f_0} \left(h_i - \sum\limits_{j=1}^{i-1} f_j·f_{i-j}\right) (i>0)$，前提是 $h_0 > 0$（或者 $h_0$ 在模意义下有平方根）

- **朴素多项式对数函数**

因为 $\ln f(x)=\int \dfrac{f'(x)}{f(x)} \mathrm dx$，所以直接套用朴素多项式除法即可。

- **朴素多项式指数函数**

设 $G = \exp F$，则有

$$\begin{aligned}
G' &= F' \exp F \\\\
G' &= F' G \\\\
\[x^n\] G' &= \[x^n\](F'G) \\\\
\[x^n\] G' &= \sum_{i=0}^n \[x^i\]F'·\[x^{n-i}\]G \\\\
(n+1)\[x^{n+1}\] G &= \sum_{i=0}^n (i+1)\[x^{i+1}\]F·\[x^{n-i}\]G \\\\
\[x^n\] G &= \dfrac{1}{n} \sum_{i=1}^n i·\[x^i\]F·\[x^{n-i}\]G
\end{aligned}$$

边界为 $G[0]=1$.

- **朴素多项式快速幂**

方法一：按照字面意思模拟。时间复杂度 $O(n^2\log w)$，其中 $w$ 是指数大小。

方法二：由 $F^k = \exp k \ln F$，套用朴素多项式对数函数 + 指数函数，时间复杂度 $O(n^2)$.

方法三：

$$\begin{aligned}
G &= F^k \\\\
G' &= k F^{k-1} F'\\\\
G'F &= k F^k F' \\\\
G'F &= k G F' \\\\
\sum_{i=0}^n [x^i]G'·[x^{n-i}]F &= \sum_{i=0}^n k·[x^i]G·[x^{n-i}]F' \\\\
\sum_{i=0}^n \dfrac{1}{i+1}·[x^{i+1}]G·[x^{n-i}]F &= \sum_{i=0}^n \dfrac{k}{n-i+1}·[x^i]G·[x^{n-1+1}]F \\\\
\sum_{i=1}^{n+1} \dfrac{1}{i}·[x^i]G·[x^{n-i+1}]F &= \sum_{i=0}^n \dfrac{k}{n-i+1}·[x^i]G·[x^{n-1+1}]F \\\\
\end{aligned}$$

只有左边含 $x^{n+1}$ 项，因此使用类似多项式乘法即可。

以上所有多项式朴素算法均可以 **半在线** 地计算，并且 **对模数没有要求**。

## 多项式技巧

### 半在线卷积(分治 $\mathbf {FFT}$)

- 给定 $f_0$ 和 $g_{1\sim n}$，已知 $f_n=\sum\limits_{i=1}^n f_{n-i}g_i$，求 $f_{1\sim n}$。

由于计算 $f_i$ 就要知道 $f_{1\sim i-1}$ 的值，我们不可能一个一个算。所以考虑 cdq 分治。

我们假设我们已经算出了 $f_{1\sim mid}$ 的值，我们现在要计算 $f_{1\sim mid}$ 对 $f_{mid+1,r}$ 的贡献。

于是我们先计算 $f_{l\sim mid}*g_{1,r-l}$，然后将对应的位置加到 $f_{mid+1,r}$。这样左半边对右半边的贡献就做完了。

注意我们先递归 $[l,mid]$，计算贡献，再递归 $[mid+1,r]$。

时间复杂度 $T(n)=2T\left(\dfrac{n}{2}\right)+O(n\log n)=O(n\log^2 n)$.

当然，可以考虑其生成函数意义：$F=F*G+f_0$，解得 $F=\dfrac{f_0}{1-G}$，于是一次多项式求逆在 $O(n\log n)$ 的时间即可求得答案。

- 给定 $f_0$，已知 $f_n=\sum\limits_{i=1}^n f_{n-i}g_i$，而 $g_i=\sum\limits_{j|i}j·f_j$，求 $f_{1\sim n}$。

这个时候 $g$ 也不直接给你了，所以我们无法像上面那样直接用 $f_{l\sim mid}*g_{1,r-l}$。

- 若 $l=0$，则 $f_{0\sim mid}*g_{0\sim mid}\rightarrow f_{mid+1\sim r}$，显然此时 $f,g$ 在 $[0,mid]$ 的值都算出来了。
- 若 $l>0$，则我们做两次卷积：
	- $f_{l\sim mid}*g_{0\sim r-l}\rightarrow f_{mid+1,r}$
   - $f_{0\sim r-l}*g_{l\sim mid}\rightarrow f_{mid+1,r}$
   
然后走到底端 $[i,i]$  的时候，我们将所有 $g_{ik}(k\ge 1)$ 加上 $i·f_i$，这里的总复杂度是调和级数 $O(n\log n)$.

时间复杂度 $T(n)=2T\left(\dfrac{n}{2}\right)+O(n\log n)=O(n\log^2 n)$.

### 另一种分治 $\mathbf {FFT}$

- 已知多项式 $F_{1 \sim n} = a_ix + b_i$，求 $\prod\limits_{i=1}^n F_i = \prod\limits_{i=1}^n (a_ix + b_i)$.

从前往后求的话时间复杂度会退化为 $T(n) = T(n-1) + O(n) = O(n^2)$.（使用朴素多项式乘法）

我们可以考虑分成前半段和后半段分别求乘积，然后再把这两段的乘积用 $\text{FFT}$ 合并。

这样时间复杂度就为 $T(n) = 2T\left(\dfrac{n}{2}\right) + O(n\log n) = O(n\log^2 n)$.

### 多项式平移

- 已知多项式 $F(x)$，求 $F(x+c)$.

其实就是暴力拆乘方

$$\begin{aligned}
F(x+c) &= \sum_{i=0}^n f_i (x+c)^i 
= \sum_{i=0}^n f_i \sum_{j=0}^i \binom{i}{j} c^{i-j} x^j \\\\
[x^{j}] F(x+c) &= \sum_{i=j}^n f_i \binom{i}{j} c^{i-j} 
= \dfrac{1}{j!} \sum_{i=j}^n f_i·i!·\dfrac{c^{i-j}}{(i-j)!}
\end{aligned}$$

这是一个减法卷积，可以用 FFT 加速。

## 拉格朗日插值法

直接构造一个函数：

$$f(x)=\sum_{i=0}^n y_i\prod_{i\neq j} \dfrac{x-x_j}{x_i-x_j}$$

证明：考虑 $f(x_k)$ 中每个 $y_i$ 的系数。$k\neq i$ 时乘积式里存在 $x_k-x_k=0$；$k=i$ 时 $\prod\limits_{k\neq j} \dfrac{x_k-x_j}{x_k-x_j}=1$。

时间复杂度 $O(n^2)$.

如果我们均取 $0\sim n$ 作为 $x_i$，那么有 

$$\begin{aligned}
f(x)&=\sum_{i=0}^n y_i \prod_{i\neq j} \dfrac{x-j}{i-j}\\\\
	&=\sum_{i=0}^n y_i \left(\prod_{i\neq j} x-j\right)\left(\prod_{i\neq j}\dfrac{1}{i-j}\right)\\\\
   &=\sum_{i=0}^n y_i \times \dfrac{x^{\underline n}}{x-i} \times \dfrac{(-1)^{n-i}}{i!·(n-i)!} & (x>n)
\end{aligned}$$

我们可以直接预处理阶乘及其逆元做到 $O(n)$。

## 多项式快速求值与插值

### 多项式快速求值

- 给定一个多项式 $F$，求 $F(x_1),F(x_2),\dots,F(x_m)$.

考虑将 $F$ 表示为 $F = (x-x_i)·Q+r$ 的形式。也就是我们希望求得 $F$ 对 $x-x_i$ 取模的余数 $r$。那么此时 $F(x_i)=r$.

但是直接取模肯定是不行的。考虑分治，对于假设现在已经考虑到 $x_{l \sim r}$。

1. 将当前的 $F$ 对 $\prod\limits_{i=l}^r (x-x_i)$ 取模得到 $F = \prod\limits_{i=l}^r (x-x_i)·Q +R$，容易发现，$\forall i\in[l,r], F(x_i) = R(x_i)$，然后我们将 $F$ 替换为 $R$ 即可。
2. 递归 $x_{l \sim mid}$ 和 $x_{mid+1 \sim r}$ 继续处理。

容易发现，每次的步骤 1. 都让当前的 $F$ 的长度变为 $O(size)$。因此时间复杂度为 $T(n) = 2T\left(\dfrac{n}{2}\right) + O(n\log n) = O(n\log^2 n)$.

### 多项式快速插值

- 给定 $F(x_1),F(x_2),\dots,F(x_m)$，求 $F$.

使用拉格朗日插值法

$$\begin{aligned}
F &= \sum_{i=0}^n y_i\prod_{i\neq j} \dfrac{x-x_j}{x_i-x_j} \\\\
&= \sum_{i=0}^n \dfrac{y_i}{\prod\limits_{i\neq j} x_i-x_j} \prod_{i\neq j} x-x_j\\\\
\end{aligned}
$$

这样就有一个 $O(n^2)$ 的做法，先计算出 $\prod\limits_{i} x-x_i$，然后依次对 $x-x_i$ 进行 $O(n)$ 取模，然后再乘上 $\dfrac{y_i}{\prod\limits_{i\neq j} x_i-x_j}$ （暴力计算）即可。

考虑对于每个 $i$ 求出 $\prod\limits_{i\neq j} x_i-x_j$。我们可以先算出 $G = \prod\limits_{i=1}^n x-x_i$，然后计算 $\dfrac{G(i)}{x_i-x_i}$。

但是直接计算会变成 $\dfrac{0}{0}$。因此我们使用洛必达法则：

- 洛必达法则(L'Hospital's rule)：若 $f(x),g(x)$ 在 $x=a$ 处可导，且 $\lim\limits_{x \to a} f(x) = 0, \lim\limits_{x \to a} g(x) = 0$。那么 $\lim\limits_{x \to a} \dfrac{f(x)}{g(x)} = \lim\limits_{x \to a} \dfrac{f'(x)}{g'(x)}$.

因此 $\lim\limits_{x \to x_i} \dfrac{G(i)}{x-x_i} = G'(x_i)$.

因此，对 $G'$ 进行快速插值即可求出各个系数 $c_i = \dfrac{y_i}{\prod\limits_{i\neq j} x_i-x_j}$。

然后我们考虑分治，考虑 $F(x_{l \sim r})$ 这些点值求出的答案。

$$
\begin{aligned}
F_{l\sim r} =& \sum_{i=l}^r c_i \prod_{j=l, j\ne i}^r x-x_j \\\\
=& \left(\sum_{i=l}^{mid} c_i \prod_{j=l, j\ne i}^{mid} x-x_j\right) \left(\prod_{k=mid+1}^r x-x_k\right) + \left(\sum_{i=mid+1}^r c_i \prod_{j=mid+1, j\ne i}^r x-x_j\right) \left(\prod_{k=l}^{mid} x-x_k\right) \\\\
=& F_{l \sim mid} \left(\prod_{k=mid+1}^r x-x_k\right) + F_{mid+1 \sim r} \left(\prod_{k=l}^{mid} x-x_k\right)
\end{aligned}
$$

后面的乘积式是可以 $O(n\log ^2 n)$ 预处理的。

因此，时间复杂度为 $T(n) = 2T\left(\dfrac{n}{2}\right) + O(n\log n) = O(n\log^2 n)$

## 生成函数

好文章：[好文章 1](https://www.luogu.com.cn/blog/command-block/ntt-yu-duo-xiang-shi-quan-jia-tong) / [好文章 2](https://rqy.moe/Math/gf_correct/) / [好文章 3](https://www.luogu.com.cn/blog/command-block/sheng-cheng-han-shuo-za-tan) / [好文章 4](https://www.luogu.com.cn/blog/zyxxs/x-yi-x-jiang-tan-sheng-cheng-han-shuo-zai-ru-men) / [好文章 5](https://www.cnblogs.com/feiko/p/polylog.html) / [好文章 6](https://www.cnblogs.com/-Wallace-/p/count-by-egf.html)

好文章：

- [牛顿迭代1](https://blog.csdn.net/ccnt_2012/article/details/81837154) / [牛顿迭代2](http://picks.logdown.com/posts/209226-newtons-method-of-polynomial)
- [泰勒展开1](https://www.zhihu.com/question/25627482) / [泰勒展开2](https://www.shuxuele.com/algebra/taylor-series.html)
- [微积分](https://www.shuxuele.com/calculus/index.html)
- [生成函数](https://www.cnblogs.com/Appleblue17/p/14337965.html)
- 二项式反演：[1](https://blog.csdn.net/sizeof_you/article/details/86365003) / [2](https://www.cnblogs.com/birchtree/p/12811308.html) / [3](https://blog.csdn.net/zhouyuheng2003/article/details/85055709?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1.no_search_link&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1.no_search_link) / [4](https://blog.csdn.net/DOFYPXY/article/details/79116730)
- [第一类斯特林数 / 第二类斯特林数 / 贝尔数 小结](https://blog.csdn.net/a_forever_dream/article/details/106133933)
- [数列求和](https://zhuanlan.zhihu.com/p/50156796)

好题：[题单 1](https://www.luogu.com.cn/training/3295#information) / [题单 2](https://www.luogu.com.cn/training/1008)

我们把数列依次放在多项式的系数上，这时候这个多项式函数就称为「生成函数」。称这个多项式为「形式幂级数」。把这个多项式写成一个式子，称其为「封闭形式」。它们可以相互转化，并且可以直接放在一起计算。

- 换句话说，生成函数是一种构造。
- 生成函数得到的多项式并没有实际意义。
- 因为我们可以快速计算多项式全家桶，所以才出现了用生成函数加速的方法。

### 普通生成函数 $\mathbf{(OGF)}$

普通生成函数~~就是非常普通的生成函数~~，其形式为 $F(x)=\sum f_i·x^i$，其对应的序列为 $\langle f_0,f_1,f_2,\dots\rangle$。

- 加法：$F(x)\pm G(x)=\sum (f_i+g_i)x^i$，即序列 $\langle f_0+g_0,f_1+g_1,f_2+g_2,\dots\rangle$ 的生成函数是 $F+G$。其组合意义为 **集合并**。
- 乘法：$F(x)*G(x)=\sum\limits_{n} x^n\sum\limits_{i=0}^n f_i·g_{n-i}$，即两个序列的卷积 $\left\langle\sum_{i+j=n}f_i·g_j\right\rangle$ 的普通生成函数为 $F*G$。其组合意义为 **笛卡尔积**。

常用封闭形式：

$\begin{aligned}
(1) && \sum x^i &= \dfrac{1}{1-x} &\rightarrow& \langle 1,1,1,\dots \rangle \\\\
(2) && \sum a^ix^i &= \dfrac{1}{1-ax} &\rightarrow& \langle 1,a,a^2,\dots\rangle\\\\
(3) && \sum x^{ik} &= \dfrac{1}{1-x^k} &\rightarrow& \langle 1,\underbrace{0,0\dots,0}_{k-1},1,\underbrace{0,0\dots,0}_{k-1},1\dots \rangle\\\\
(4) && \sum \dfrac{x^i}{i} &= -\ln(1-x) &\rightarrow& \left\langle 1,\dfrac{1}{2},\dfrac{1}{3},\dfrac{1}{4},\dots \right\rangle\\\\
(5) && \sum \dfrac{x^i}{i!} &= e^x &\rightarrow &\left\langle1,\dfrac{1}{2!},\dfrac{1}{3!},\dfrac{1}{4!},\dots \right\rangle\\\\
(6) && \sum \binom{n}{i}x^i &= (x+1)^n &\rightarrow& \left\langle \binom{n}{0},\binom{n}{1},\binom{n}{2},\dots,\binom{n}{n} \right\rangle\\\\
(7) && \sum \binom{n+i-1}{n-1}x^i &= \left(\dfrac{1}{1-x}\right)^n &\rightarrow& \left\langle \binom{n-1}{n-1},\binom{n+1-1}{n-1},\binom{n+2-1}{n-1},\dots \right\rangle\\\\
\end{aligned}$

证明 / 理解：

1. 无穷等比数列求和。
2. 将 $ax$ 视作整体即可转化为 $(1)$。
3. 相当于把 $(1)$ 拉伸了 $k$ 倍。
4. 由 $\int\dfrac{1}{1-x} \mathrm dx = \ln (1-x)$，我们将 $(1)$ 中的多项式积分一下即可得到该式。
5. 由麦克劳林级数定义知。
6. 二项式展开。(注意这个是有限级数)
7. $(1)$ 式卷积 $n$ 次，那么此时 $f_i$ 就表示将 $n$ 个无标号小球分配到 $i$ 个有标号可空集合的方案数（隔板法）。

### 指数生成函数 $\mathbf{(EGF)}$

指数生成函数的形式为 $\hat F(x)=\sum f_i·\dfrac{x^i}{i!}$，其对应的序列也为 $\langle f_0,f_1,f_2,\dots\rangle$。当然它也可以被理解为「序列 $\left\langle\frac{f_0}{0!},\frac{f_1}{1!},\frac{f_2}{2!},\frac{f_3}{3!},\dots\right\rangle$ 的普通生成函数」。

- 加法：与普通生成函数相同。
- 乘法：

$$
\begin{aligned}
\hat F(x)*\hat G(x)&=\sum_{n}\sum_{i=0}^n f_i·\dfrac{x_i}{i!}·g_{n-i}·\dfrac{x^{n-i}}{(n-i)!}\\\\
&=\sum_{n}\dfrac{x^n}{n!}\sum_{i=0}^n \binom{n}{i}·f_i·g_{n-i}
\end{aligned}
$$

即两个序列的二项卷积 $\left\langle\sum_{i+j=n}\binom{n}{i}f_i·g_j\right\rangle$ 的指数生成函数为 $\hat F*\hat G$。

由此我们可以窥探到指数生成函数的组合意义，相当于把 $n$ 划分为两个集合再各自选择一种方案的方案数。

注意在实战中我们仍然要将系数除以阶乘当作普通生成函数用，以实现多项式运算。

常用封闭形式：

$\begin{aligned}
(1) && \sum \dfrac{x^i}{i!}&=e^x&\rightarrow&\langle1,1,1,\dots\rangle\\\\
(2) && \sum a^i·\dfrac{x^i}{i!}&=e^{a·x}&\rightarrow&\langle1,a,a^2,\dots\rangle\\\\
(3) && \sum (-1)^i·\dfrac{x^i}{i!}&=e^{-x}&\rightarrow&\langle1,-1,1,-1,\dots\rangle\\\\
(4) && &\dfrac{e^x+e^{-x}}{2}&\rightarrow&\langle1,0,1,0,\dots\rangle\\\\
(5) && &\dfrac{e^x-e^{-x}}{2}&\rightarrow&\langle0,1,0,1,\dots\rangle\\\\
\end{aligned}$

证明 / 理解：

1. 麦克劳林级数；
2. 将 $ax$ 视作整体；
3. 将 $(-x)$ 视作整体；
4. $((1)+(3))/2$；
5. $((1)-(3))/2$.


## $\textbf{exp}$ 的组合意义与 $\textbf{Euler}$ 变换

好文章：[好文章](https://blog.csdn.net/guizhiyu/article/details/108321359)

- 有标号计数：每个元素都带有编号，互相区分。
- 无标号计数：所有元素都 **无法区分**。其实也不是真的没法区分，如果这些元素带有其他的性质（如大小/种类等），只有它们的性质全部都相同才无法区分。

### 有标号小球 $\rightarrow$ 有标号集合

考虑 **指数生成函数** $F$ 的意义是：集合内部大小为 $i$ 有 $f_i$ 种不同的分配方案。

那么将若干个 **有标号小球** 分配到若干个 **有标号集合** 的方案数的 关于集合个数的指数生成函数 $G$ 为

$$G = \sum_{i=1}^{+\infty} F^i = \dfrac{F}{1-F}$$

其实就是枚举了一下有多少个集合，那么它们构成的 **有标号排列** 个数就是 $F$ 卷积 $i$ 次。

### 无标号小球 $\rightarrow$ 有标号集合

考虑 **普通生成函数** $F$ 的意义是：集合内部大小为 $i$ 有 $f_i$ 种不同的分配方案。

那么将若干个 **无标号小球** 分配到若干个 **有标号集合** 的方案数的 关于集合个数的普通生成函数 $G$ 为

$$G = \sum_{i=1}^\infty F^i = \dfrac{F}{1-F}$$

我们发现这里和「有标号小球 $\rightarrow$ 有标号集合」的形式是一样的，不过这里变成了普通生成函数。

- 普通生成函数：无标号计数；
- 指数生成函数：有标号计数。

### 有标号小球 $\rightarrow$ 无标号集合（$\exp$ 的组合意义）

考虑 **指数生成函数** $F$ 的意义是：集合内部大小为 $i$ 有 $f_i$ 种不同的分配方案。

那么将若干个 **有标号小球** 分配到若干个 **无标号集合** 的方案数的 关于集合个数的指数生成函数 $G$ 为

$$G = \sum_{i=1}^{+\infty}\dfrac{F^i}{i!} = \exp F_i$$

因为集合之间是无序的，所以需要除以 $i!$.

我们发现这就是多项式 $\exp$ 的定义。因此更直接地，有 $G=\exp F$，且 $F=\ln G$。注意也可以反过来考虑变成求 $\ln$.

### 无标号小球 $\rightarrow$ 无标号集合（$\mathbf {Euler}$ 变换）

考虑 **普通生成函数** $F$ 的意义是：集合内部大小为 $i$ 有 $f_i$ 种不同的分配方案。

我们设将若干个 **无标号小球** 分配到若干个 **无标号集合** 的方案数的 关于集合个数的普通生成函数为 $G$.

此时相同集合大小的相同方案是 **不可区分** 的，那么我们只能考虑对于每种相同方案决定使用多少个，即

$$\prod_i\prod_{j=1}^{f_i}\sum_{c=0}^{+\infty}x^{i·c}=\prod_{i}\dfrac{1}{(1-x^i)^{f_i}}$$

我们先上 $\ln$ 再 $\exp$ 可以干掉乘积式

$$\begin{aligned}
&\exp \sum_{i} -f_i \ln(1-x^i)&
=&\exp \sum_{i} f_i \sum_{j=1}^{+\infty} \dfrac{x^{ij}}{j}\\\\
=&\exp \sum_{j=1}^{+\infty} \dfrac{1}{j} \sum_if_i x^{ij}&
=&\exp \sum_{j=1}^{+\infty} \dfrac{F(x^j)}{j}\\\\
\end{aligned}$$

因此我们先求出 $\sum \dfrac{F(x^j)}{j}$，这个的时间复杂度是 $T(n)=\sum\limits_{i=1}^n \dfrac{n}{i}=O(n\log n)$ 的，我们再 $\exp$ 一下就可以在 $O(n\log n)$ 时间内计算。



## 组合数恒等式

[好文章1](https://blog.csdn.net/shulianghan/article/details/109180924) / [好文章2](https://oi-wiki.org/math/combinatorics/combination/#_13) / [好文章3](https://www.cnblogs.com/Parsnip/p/12518336.html)

- **吸收 / 提取恒等式**：

$$\binom n m = \dfrac{n}{m} \binom {n-1} {m-1}$$

- **列求和 / 上指标求和**：即枚举最后一个元素的位置。

$$\sum_{i=0}^m \binom{n+i} n = \binom{n+m+1}{n+1}$$

- **斜线求和**：下指标对称一下就变成列求和。

$$\sum_{i=0}^m \binom{n+i} i = \dbinom {n+m+1} m$$

- **三项式恒等式**：求集合的子集的子集个数，相当于求集合的子集的超集个数。

$$\binom n r \binom r k = \binom n k\dbinom {n-k} {r-k}$$

- **下指标卷积 / 范德蒙德卷积**：即枚举左半部分选了多少个元素。它拥有数学家的名字，是因为这个东西甚至是可以用生成函数刻画的。

$$\sum_{k=0}^n \dbinom n i \dbinom m {k-i} = \dbinom{n+m} k$$

还有另一种迷惑形式（~~有一次没看出来~~）：

$$\sum_{k} \binom n {a-k} \binom m {b+k} = \binom {n+m} {a+b}$$

- **下指标点积**：是范德蒙德卷积的特例。第二个组合数的下指标对称一下即可。

$$\sum_{i=0}^n \binom n i \binom m i = \binom {n+m} m$$

- **上指标卷积**：它等价于在中间插入一个分隔符，然后就变成 $(n+1)$ 个物品选择 $(a+b+1)$ 个物品的方案数和。**注意不要和下指标卷积混淆！** 上指标卷积的上下指标与下指标卷积相比均多加了个 $1$。

$$\sum_{i=0}^n \binom i a \binom {n-i} b = \binom {n+1}{a+b+1}$$

## 上升幂与下降幂

上升幂：$x^{\overline n} = \prod\limits_{i=0}^{n-1} (x+i)$

下降幂：$x^{\underline n} = \prod\limits_{i=0}^{n-1} (x-i)$

- **差分**

$$\begin{aligned}
\Delta x^{\overline n} &= x^{\overline n} - (x-1)^{\overline n} = (x+n-1)·x^{\overline{n-1}} - (x-1)·x^{\overline {n-1}} = nx^{\overline {n-1}} \\\\
\Delta x^{\underline n} &= x^{\underline n} - (x-1)^{\underline n} = x·(x-1)^{\underline{n-1}} - (x-n)·(x-1)^{\underline {n-1}} = nx^{\underline {n-1}} \\\\
\end{aligned}$$

- **前缀和**

类比差分可以得出前缀和：

$$\begin{aligned}
\sum_{x=1}^m x^{\overline n} &= \dfrac{x^{\overline {n+1}}}{n+1}\\\\
\sum_{x=1}^m x^{\underline n} &= \dfrac{x^{\underline {n+1}}}{n+1}\\\\
\end{aligned}$$

可以发现这与自然幂的 导数/积分 非常相似。

- **底数取反**

$$\begin{aligned}
x^{\overline n} &= (-1)^n (-x)^{\underline n}\\\\
x^{\underline n} &= (-1)^n (-x)^{\overline n}\\\\
\end{aligned}$$

## **下降幂多项式**

$$f(x)=\sum_{i=0}^n a_i x^{\underline i}$$

- **自然幂与下降幂的转化**（斯特林数）：

$\begin{aligned}
n^m&=\sum_{i=0}^m \begin{Bmatrix}m\\\\i\end{Bmatrix} n^{\underline i}\\\\
n^{\underline m}&=\sum_{i=0}^m(-1)^{m-i}\begin{bmatrix}m\\\\i\end{bmatrix}n^i\\\\
f(x)&=\sum_{i=0}^n a_i x^i=\sum_{i=0}^n a_i\sum_{j=0}^i \begin{Bmatrix}i\\\\j\end{Bmatrix}x^{\underline j}=\sum_{i=0}^n x^{\underline j}\sum_{j=i}^n \begin{Bmatrix}i\\\\j\end{Bmatrix}a_i\\\\
f(x)&=\sum_{i=0}^na_ix^{\underline i}=\sum_{i=0}^na_i\sum_{j=0}^i(-1)^{i-j}\begin{bmatrix}i\\\\j\end{bmatrix}x^j=\sum_{i=0}^ix^i\sum_{j=i}^n(-1)^{j-i}\begin{bmatrix}i\\\\j\end{bmatrix}a_i\\\\
\end{aligned}$

- **下降幂多项式乘法**

总体思路：系数表示 $\rightarrow$ 点值表示 $\rightarrow$ 系数表示

考虑求出 $F(0 \sim n),G(0 \sim n)$.

$$\begin{aligned}
F(x) &= \sum_{i=0} f_i x^{\underline i} \\\\
\dfrac{F(x)}{x!} &= \sum_{i=0} f_i ·\dfrac{1}{(x-i)!}
\end{aligned}
$$

因此，$F(0 \sim n)$ 组成的 $\mathrm EGF$ 为 $F$ 与 $e^x$ 的卷积。即


$$\begin{aligned}
F(x) &= F*e^x \\\\
F &= F(x) * e^{-x} \\\\
\end{aligned}
$$

因此，我们先将 $F$ 与 $e^x$ 卷积得到 $F$ 的点值表示，做完点值乘法后，然后再将 $F$ 的点值表示与 $e^{-x}$ 即可得到 $F$.

- **普通多项式转下降幂多项式**

先快速求值得到点值表示，然后与 $e^{-x}$ 卷积即可得到下降幂多项式。

- **下降幂多项式转普通多项式**

先与 $e^x$ 卷积得到点值表示，然后再快速插值得到普通多项式。

因为得到的点值表示是 $F(0\sim n)$，因此不需要用洛必达法则 + 快速求值得到系数了，可以直接预处理阶乘求得。

## 斯特林数

### 第一类斯特林数

- 第一类斯特林数（斯特林轮换数）：记为 $\begin{bmatrix}n\\\\m\end{bmatrix}$ 或 $S_1(n,m)$。

组合意义：将 $n$ 个有标号元素划分成 $m$ 个无标号 **轮换（即圆排列）** 的方案数。

递推式：$\begin{bmatrix}n\\\\m\end{bmatrix} = \begin{bmatrix}n-1\\\\m-1\end{bmatrix} + (n-1)·\begin{bmatrix}n-1\\\\m\end{bmatrix}$。

我们考虑第 $n$ 个元素，它要么新开一组，要么插到前面任意 $(n-1)$ 个元素之一所在位置的后面。

边界：$\begin{bmatrix}n\\\\0\end{bmatrix}=[n=0]$。

- **与排列 / 置换的关系**

$$\sum_{i=1}^n \begin{bmatrix}n\\\\i\end{bmatrix} = n!$$

一个排列对应一种置换，而置换可以分解成若干个置换环即圆排列。因此这是一一对应的。

- **上升幂与自然幂的转化**

$$x^{\overline n} = \sum_{i=0}^n \begin{bmatrix}n\\\\i\end{bmatrix} x^i$$

考虑归纳法：显然我们有 $x^{\overline 1}=x$.

若对于所有 $x^{\overline 1 \sim \overline {n-1}}$ 均成立，那么

$$\begin{aligned}
x^{\overline{n}} &= (x+n-1) x^{\overline {n-1}} \\\\
&= (x+n-1) \sum_{i=0}^{n-1} \begin{bmatrix}n-1\\\\i\end{bmatrix} x^i \\\\
&= \sum_{i=0}^{n-1} \begin{bmatrix}n-1\\\\i\end{bmatrix} x^{i+1} + (n-1) \sum_{i=0}^{n-1} \begin{bmatrix}n-1\\\\i\end{bmatrix} x^i \\\\
&= \sum_{i=1}^n \begin{bmatrix}n-1\\\\i-1\end{bmatrix} x^i + n \sum_{i=1}^n \begin{bmatrix}n\\\\i\end{bmatrix} x^i \\\\
&= \sum_{i=1}^n \left(\begin{bmatrix}n-1\\\\i-1\end{bmatrix} + (n-1) \begin{bmatrix}n-1\\\\i\end{bmatrix}\right) x^i \\\\
&= \sum_{i=1}^n \begin{bmatrix}n\\\\i\end{bmatrix} x^i\\\\
\end{aligned}$$

- **下降幂与自然幂的转化**

$$x^{\underline n} = \sum_{i=0}^n (-1)^{n-i} \begin{bmatrix}n\\\\i\end{bmatrix} x^i$$

证明考虑将下降幂转化为上升幂

$$\begin{aligned}
x^{\underline{n}} &= (-1)^n (-x)^{\overline n} \\\\
&= (-1)^n \sum_{i=0}^n \begin{bmatrix}n\\\\i\end{bmatrix} (-x)^i \\\\
&= \sum_{i=0}^n (-1)^{n-i} \begin{bmatrix}n\\\\i\end{bmatrix} x^i
\end{aligned}$$

- **第一类斯特林数·行**

设 $S_n$ 为第一类斯特林数的第 $n$ 行关于下指标的 **普通生成函数**。我们观察递推式，则有

$$\begin{aligned}
S_0 &= 1\\\\
S_n &= xS_{n-1} + (n-1)S_{n-1} = (x+n-1)S_{n-1} &&(n>0)\\\\
\end{aligned}$$

（这和上升幂的形式非常相似）

因此我们有

$$\begin{aligned}
S_n &= \prod_{i=0}^{n-1} (x+i) = x^{\overline n}
\end{aligned}$$

事实上， $S_n$ 的各项系数其实就是 $x^{\overline n}$ 按自然幂展开后的结果。

分治 FFT 可以做到 $O(n\log^2 n)$。

但是我们注意到 $x^{\overline {2n}} = x^{\overline n} · (x+n)^{\overline n}$。因此我们可以使用类似快速幂的方法倍增地求出 $x^{\overline n}$.

时间复杂度 $T(n) = T\left(\dfrac{n}{2}\right) + O(n\log n) = O(n\log n)$.

- **第一类斯特林数·列**

设 $S_m$ 为第一类斯特林数的第 $m$ 列关于上指标的 **指数生成函数**。

如果还是观察递推式，我们发现这样行不通。

我们考虑它的组合意义，其实就是要计算若干个有标号小球划分为 $m$ 个非空无标号集合的方案数，因为集合内要组合成圆排列，所以集合内分配方案关于集合大小的 **指数生成函数** 为 

$$G = \sum_{i=1} \dfrac{(i-1)!}{i!}·x^i = \sum_{i=1} \dfrac{1}{i}·x^i = -\ln (1-x)$$

那么

$$S_m = \dfrac{G^m}{m!} = \dfrac{(-\ln(1-x))^m}{m!}$$

直接多项式快速幂即可。注意因为 $[x^0] -\ln(1-x)=0$，因此我们要整体平移 $x^1$，最后再乘以 $x^m$。

### 第二类斯特林数

- 第二类斯特林数（斯特林子集数）：记为 $\begin{Bmatrix}n\\\\m\end{Bmatrix}$ 或 $S_2(n,m)$。

组合意义：将 $n$ 个有标号元素划分成 $k$ 个无标号 **集合** 的方案数。

递推式：$\begin{Bmatrix}n\\\\m\end{Bmatrix}=\begin{Bmatrix}n-1\\\\m-1\end{Bmatrix}+m·\begin{Bmatrix}n-1\\\\m\end{Bmatrix}$

我们考虑第 $n$ 个元素，它要么新开一组，要么插到前面 $m$ 组当中。

边界：$\begin{Bmatrix}n\\\\0\end{Bmatrix}=[n=0]$

- **$\textbf{Bell}$ 数**

集合划分数：将 $n$ 个有标号元素划分为若干个无标号集合的方案数。

由定义有

$$B_n = \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix}$$

它的指数生成函数可以用 $exp$ 的组合意义得到。集合内分配方案数的指数生成函数为 $\sum\limits_{i=1} \dfrac{x^i}{i!} = e^x -1$，因此 $B = \exp (e^x-1)$.

- **下降幂与自然幂的转化**

$$x^n = \sum\limits_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} x^{\underline i} = \sum\limits_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} \dbinom{x}{i} · i!$$

证明 1：考虑归纳法。显然有 $x^0 = x^{\underline 0}$，而

$$\begin{aligned}
x^n &= x ·x^{n-1} = x \sum_{i=0}^{n-1} \begin{Bmatrix}n-1\\\\i\end{Bmatrix} x^{\underline i} \\\\
&= \sum_{i=0}^{n-1} \begin{Bmatrix}n-1\\\\i\end{Bmatrix} (x^{\underline{i+1}} + i·x^{\underline i})\\\\
&= \sum_{i=1}^n \begin{Bmatrix}n-1\\\\i-1\end{Bmatrix} x^{\underline i} + \sum_{i=0}^{n-1} \begin{Bmatrix}n-1\\\\i\end{Bmatrix} i·x^{\underline i}\\\\
&= \sum_{i=1}^n \left(\begin{Bmatrix}n-1\\\\i-1\end{Bmatrix} + i\begin{Bmatrix}n-1\\\\i\end{Bmatrix}\right) x^{\underline i} \\\\
&= \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} x^{\underline i} \\\\
\end{aligned}$$

证明 2：我们考虑其组合意义。$x^n$ 表示 $n$ 个有标号小球划分为 $x$ 个有标号可空集合的方案数。也就是我们枚举有 $i$ 个集合非空，然后我们把 $n$ 个有标号元素划分为 $i$ 个有标号非空集合，这里方案数为 $\begin{Bmatrix}n\\\\i\end{Bmatrix} · i!$ 因此任何一种划分方式都能找到一一对应的非空划分方式。

- **推论 1：自然幂和**

推导 1：

$$\sum_{x=0}^m x^n = \sum_{x=0}^m \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} \binom{x}{i} i! = \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix}·i! \sum_{x=0}^m \binom{x}{i} = \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix}·\binom{m+1}{i+1}·i!$$

推导 2：

$$\sum_{x=0}^m x^n = \sum_{x=0}^m \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} x^{\underline i} = \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix} \sum_{x=0}^m x^{\underline i} = \sum_{i=0}^n \begin{Bmatrix}n\\\\i\end{Bmatrix}·\dfrac{x^{\underline {i+1}}}{i+1}$$

- **推论 2：斯特林数的另一种计算方法**

对原式进行二项式反演有

$$\begin{Bmatrix}n\\\\m\end{Bmatrix} = \dfrac{1}{m!} \sum_{i=0}^m (-1)^{m-i} \binom{m}{i} i^n$$

- **第二类斯特林数·行**

由上面的推论得到

$$\begin{aligned}
\begin{Bmatrix}n\\\\m\end{Bmatrix} &= \dfrac{1}{m!} \sum_{i=0}^m (-1)^{m-i} \binom{m}{i} i^n \\\\
&= \sum_{i=0} \dfrac{i^n}{i!}·\dfrac{(-1)^{m-i}}{(m-i)!}
\end{aligned}$$

直接卷积计算。

- **第二类斯特林数·列**

设 $S_m$ 为第二类斯特林数的第 $m$ 列关于上指标的 **普通生成函数**。

考虑其组合意义，其实还是有标号小球划分为 $m$ 个无标号集合问题。记集合内划分方案关于集合大小的 **指数生成函数** 为 $G$，那么

$$G = \sum_{i=1} \dfrac{1}{i!}·x^i = e^{x}-1$$

因此

$$\begin{aligned}
S_m &= \dfrac{G^m}{m!} = \dfrac{(e^x-1)^m}{m!} \\\\
&= \dfrac{1}{m!} \sum_{i=0}^m \dbinom{m}{i} (-1)^{m-i} e^{ix} \\\\
&= \dfrac{1}{m!} \sum_{i=0}^m \dbinom{m}{i} (-1)^{m-i} \sum_{j=0} \dfrac{i^j}{j!} · x^j \\\\
[x^j] S_m &= \dfrac{1}{m!} \sum_{i=0}^m (-1)^{m-i}\dbinom{m}{i} ·i^j
\end{aligned}$$

多项式快速幂即可。注意因为 $[x^0] e^x-1=0$，因此我们要整体平移 $x^1$，最后再乘以 $x^m$。

如果我们把生成函数拆开并提取系数，可以得出推论 2.

### 斯特林数相关恒等式

斯特林数卷积：

$$\begin{aligned}
\sum_{i=0}^n \begin{bmatrix}i\\\\x\end{bmatrix} \begin{bmatrix}n-i\\\\y\end{bmatrix} \binom{n}{i} &= \begin{bmatrix}n\\\\x+y\end{bmatrix} \binom{x+y}{x} \\\\
\sum_{i=0}^n \begin{Bmatrix}i\\\\x\end{Bmatrix} \begin{Bmatrix}n-i\\\\y\end{Bmatrix} \binom{n}{i} &= \begin{Bmatrix}n\\\\x+y\end{Bmatrix} \binom{x+y}{x} \\\\
\end{aligned}$$

这个和范德蒙德卷积很像。思考其组合意义：我们把所有元素分成两部分，一部分分成 $x$ 组，另一部分分成 $y$ 组。这等价于，先将所有元素分成 $x+y$ 组，然后从中抽取 $x$ 组（或 $y$ 组）。

## 伯努利数

人们为了计算自然数幂和费尽心思。以一种狭隘的角度来看，伯努利数可以说是通过自然数幂和找规律得到的。

定义(构造) 伯努利数(Bernoulli Number) $B_n$ 满足

$$\sum_{i=0}^m \binom{m+1}{i} B_i = [m=0]$$

根据该定义式可以得到 $B = \left\langle 1, -\dfrac{1}{2}, \dfrac{1}{6}, 0, -\dfrac{1}{30}, 0, \dfrac{1}{42}, \dots \right\rangle$.

接下来会介绍它与自然数幂和的关系。

- **伯努利数的生成函数**

对定义式两边加上 $B_{m+1}$ 得到

$$\begin{aligned}
\sum_{i=0}^{m+1} \binom{m+1}{i} B_i &= B_{m+1} + [m=0] \\\\
\sum_{i=0}^m \binom{m}{i} B_i &= B_m + [m=1] \\\\
\sum_{i=0}^m \dfrac{B_i}{i!} · \dfrac{1}{(m-j)!} &= \dfrac{B_m}{m!} + \dfrac{[m=1]}{m!}\\\\
\end{aligned}$$

使用指数生成函数刻画有

$$\begin{aligned}
B * e^x &= B + x \\\\
B &= \dfrac{x}{e^x-1}
\end{aligned}$$

多项式求逆即可计算。

- **自然数幂和关于指数的生成函数**

我们记指数生成函数 $S_n$ 的第 $k$ 项为 $\sum\limits_{i=0}^{n-1} i^k$，那么

$$
S_n = \sum_{k=0} \dfrac{x^k}{k!} \sum_{i=0}^{n-1} i^k 
= \sum_{i=0}^{n-1} \sum_{k=0} \dfrac{(ix)^k}{k!} 
= \sum_{i=0}^{n-1} e^{ix} 
= \dfrac{e^{nx} - 1}{e^x-1}
$$

提取系数后求逆后相乘即可。

- **自然数幂和关于项数的通项公式**

考虑用 $B$ 表示 $S_n$：

$$S_n = B * \dfrac{e^{nx} - 1}{x}$$

我们设 $G_n = \dfrac{e^{nx} - 1}{x}$，那么 $G_n[i] = \dfrac{n^{i+1}}{(i+1)!}$.

故

$$
\sum_{i=0}^{n-1} i^k = k!·S_n[k] 
= k! \sum_{i=0}^k B[k-i]·G_n[i]
= k!\sum_{i=0}^k \dfrac{B_{k-i}}{(i+1)!} n^{i+1} 
$$

## 分拆数

记 $F_n$ 为将正整数 $n$ 分为若干个无序正整数之和的方案数。

$F = \left\langle 1,1,1,2,2,3,4,5,6, \dots \right\rangle$

容易有

$$\begin{aligned}
F &= \prod_{i=1} \sum_{j=0} x^{ij} = \prod_{i=1} \dfrac{1}{1-x^i} \\\\
&= \exp \sum_{i=1} \ln \dfrac{1}{1-x^i} \\\\
&= \exp \sum_{i=1} \sum_{j=1} \dfrac{x^{ij}}{j}
\end{aligned}$$

时间复杂度 $O(n\log n)$.

- **五边形数定理**

不使用多项式技术，求出分拆数。

容易想到 $O(n^2)$ $\texttt{dp}$。设 $f_{n,s}$ 表示 $s$ 无序分拆成 $n$ 个正整数的方案数，有两种转移方式，一种是整体加 $1$，一种是在前面加一个 $1$（转移方式的 $\texttt{dp}$ 称为「旋转体积背包」），可以得到：

$$f_{n,s}=f_{n,s-n}+f_{n-1,s-1}$$

考虑分块。我们发现这种「旋转体积背包」的复杂度是 $O(\text{个数}\times\text{总和})$ 的，而一般的完全背包的复杂度是 $O(\text{种类}\times\text{总和})$ 的。这正好契合分块的思想。

- 对于 $\le\sqrt{N}$ 的数，由于种类不超过 $O(\sqrt n)$，因此我们做完全背包；
- 对于 $>\sqrt N$ 的数，由于数量不超过 $O(\sqrt n)$，我们对它们做旋转体积背包。最终将两种方案做个卷积即可。

时间复杂度 $O(n\sqrt n)$。

- **Ferrers 图**

我们构造一个图表示整数分拆。如 $12 = 5+4+2+1$ 可以表示为

```
*****
****
**
*
```

我们对它对角线翻转，可以得到 $12 = 4+3+2+2+1$

```
****
***
**
**
*
```

此时我们称这两种分拆方式为 **共轭分拆。** 

- $k$ 部分拆数：求 $f_{n,k} $对 $n$ 整数分拆成不超过 $k$ 个无序整数的方案数。

通过 Ferrers 图可知，这等于 对 $n$ 整数分拆成若干个 $\le m$ 的无序整数的方案数。

计算 $F = \prod\limits_{i=1}^m \sum\limits_{j=0} x^{ij}= \exp \sum\limits_{i=1}^m \sum\limits_{j=1} \dfrac{x^{ij}}{j}$ 即可。

- **整数分拆数量估计**：$f_n \approx O\left( e^{\sqrt {\frac{20}{3} n}} \right)$.

## 特征方程与特征根

- [好文章](https://zhuanlan.zhihu.com/p/104596563)

借助特征方程我们可以快速地求出一个齐次常系数线性递推数列的通项公式。不过这几乎就是纯数学内容了。

### 一阶线性递推数列

- 已知 $f_n=af_{n-1}+b$ 和 $f_0,f_1$，求 $f_n$ 的通项公式。

我们构造公比为 $a$ 的等比数列 $f_{n+1}-x=a(f_n-x)$，化简得到 $f_{n+1}=af_n+(1-a)x$，因此我们有 $(1-a)x=b$，即我们解出 $x=\dfrac{b}{1-a}$。

因此 $\langle f_n-x\rangle$ 是等比数列，我们将 $x$ 带回去解出公比和常数项即可。

### 二阶线性递推数列

- 已知 $f_n=af_{n-1}+bf_{n-2}$ 和 $f_0,f_1$，求 $f_n$ 的通项公式。

我们仍然构造 $f_n-pf_{n-1}=q(f_{n-1}-pf_{n-2})$，因此有 $f_n=(p+q)f_{n-1}-pqf_{n-2}$。

因此我们需要找到 $p,q$ 使得 $\left\{\begin{aligned}p+q&=a\\\\pq&=-b\end{aligned}\right.$，根据韦达定理，$p,q$ 就是 $x^2-ax-b=0$ 的两根。

我们解出来 $p,q$ 后，就有 $\langle f_n-pf_{n-1}\rangle$ 是公比为 $q$ 的等比数列。同时由于在这里 $p,q$ 是对称的，因此我们重复上面的步骤可以推出 $\langle f_n-qf_{n-1}\rangle$ 是公比为 $p$ 的等比数列。

于是我们有 $\left\{\begin{aligned}f_n-pf_{n-1}&=(f_1-pf_0)q^{n-1}&(1)\\\\f_{n}-qf_{n-1}&=(f_1-qf_0)p^{n-1}&(2)\end{aligned}\right.$

我们令 $(1)-(2)$ 得到 $f_{n}=\dfrac{f_1-qf_0}{p-q}p_n+\dfrac{f_1-pf_0}{q-p}q^n$。

$\triangle$ 我们称 $x^2-ax-b=0$ 是二阶齐次线性递推数列 $f_n=af_{n-1}+b_{n-2}$ 的特征方程。其两根 $p,q$ 为这个数列的特征根。

通过上面的通项公式我们可以发现 $f_n$ 为两个公比各为特征根的等比数列相加，因此不妨设 $f_n=\alpha p_n+\beta q_n$，代入 $\left\{\begin{aligned}\alpha+\beta&=f_0\\\\\alpha p+\beta q&=f_1\end{aligned}\right.$ 同样可以解出两个系数。

$\triangle$ 结论：对于一个二阶齐次常系数递推数列 $f_n=af_{n-1}+bf_{n-2}$，其通项公式为特征根为公比的两个等比数列相加。

### 高阶线性递推数列

记 $f_n=c_1f_{n-1}+c_2f_{n-2}+\dots+c_kf_{n-k}$，我们假设 $f_n$ 是公比为 $x$ 的等比数列，则有 $x^n=c_1x^{n-1}+c_2x^{n-2}+\dots+c_kx^{n-k}$，即 $x^k=c_1x^{k-1}+c_2x^{k-2}+\dots+c_k$。

这个方程有 $k$ 个根 $x_{1\sim k}$，那么这个 $k$ 个根各自作为公比就形成了 $k$ 个等比数列。由于这个递推式是线性的，所以我们将这 $k$ 个等比数列做线性加减也满足递推式。即

$$f_n=d_1x_1^n+d_2x_2^n+\dots+d_kx_k^n$$

那么是不是这个数列有无穷多种通项公式呢？显然不是的，因为我们还没有用上前 $k$ 个给定的值。我们解出 $\left\{\begin{aligned}d_1x_1^i+d_2x_2^i+\dots+d_kx_k^i=f_i\end{aligned}\right.$ 就能解出 $d_{1\sim k}$。

当然，从生成函数的角度我们有 $F=C*F+R$，其中 $R$ 是我们残存的一些余项，有 $R[i]=f_i-\sum\limits_{j=0}^{i-1} f_j \times c_{i-j}$，即 $R=C-F*C\pmod {x^k}$。它们可以快速算出。然后移一下项得到 $F=\dfrac{R}{1-C}$。多项式求逆即可。

## Prufer 序列

Prufer 序列建立了无根树和序列的一一对应。

对于一个 $n$ 个节点的树，它对应的 Prufer 长度为 $n-2$，值域为 $[1,n]$.

### 无根树 $\rightarrow$ Prufer 序列

我们令这个无根树的树根为 $n$，这样除了节点 $n$ 的每个节点就有了唯一的父亲。

- 选取树上编号最小的叶子节点，然后将其父亲的编号加入 Prufer 序列的末尾。
- 删除该叶子节点，继续进行下一轮操作，直至最后只剩下 $2$ 个节点为止。

用堆实现是 $O(n \log n)$ 的。接下来描述了用指针的方法实现 $O(n)$ 复杂度：

- 我们一开始令指针指向 $1$。
- 每一轮将指针向后移动直至找到叶子节点。此时指针指向的是编号最小的叶子节点。
- 将这个叶子节点的父亲加入 Prufer 序列的末尾。然后我们检查它的父亲在这个节点删除后是否为叶子节点并且编号比这个节点小，如果是则继续将这个父亲的父节点加入 Prufer 序列末尾，并继续往上检查。（注意这个时候指针并没有动，只是在临时地往上找而已）

### Prufer 序列 $\rightarrow$ 无根树

- 性质：**所有节点在 Prufer 序列中出现了 度数 $-1$ 次。**

根据这个性质我们可以通过数数的方式确定每个节点的度数，以及它们是不是叶子节点。

- 选取当前编号最小的叶子节点，然后将它的父亲设为当前 Prufer 序列的第 $1$ 元素；
- 删除该叶子节点，并将 Prufer 序列的第 $1$ 个元素删除，重复进行直至 Prufer 序列全部被删除。
- 此时未知父亲的只剩下两个节点，而 **其中一个节点必为节点 $n$**，我们将另一个节点的父亲设为 $n$ 即可。（或者人为地在 Prufer 序列后加上一个数 $n$）

我们仍然有使用指针的 $O(n)$ 做法：

- 一开始将指针设为 $1$。
- 每一轮将指针向后移动直至找到叶子节点。此时指针指向的是编号最小的叶子节点。
- 将这个叶子节点的父亲设为当前 Prufer 序列第 $1$ 个元素。然后我们检查这个节点的父亲是否成为新的叶子且编号比它小，若是则继续将这个父亲的父节点设为 Prufer 序列的下一个元素，并继续向上检查。

. $\textbf{Cayley 定理}$：$n$ 个有标号点的无根树个数为 $n^{n-2}$.

## 快速沃尔什变换 $\mathbf{(FMT/FWT)}$

位运算卷积：给定 $f(i),g(i) $ $ (0\le i < 2^n)$，求 $h(i)  = \sum\limits_{j \oplus k = i} f(j) \times g(k)$，其中 $\oplus$ 指某种位运算。

原理与 FFT 相似，都是先转化为一种特殊的「点值表示」，然后按位相乘，最后再转化为原来的序列。

假设我们得到的「点值表示」为 

$$fwt_f(i) = \sum_{j} c(i,j) \times f(j)$$

那么

$$\begin{aligned}
fwt_h(i) &= fwt_f(i) \times fwt_g(i) \\\\
&= \left( \sum_{j} c(i,j) \times f(j)\right) \left( \sum_{k} c(i,k) \times g(k) \right) \\\\
& = \sum_{j} \sum_{k} f(j) \times g(k) \times c(i,j) \times (i,k)
\end{aligned}$$

而

$$\begin{aligned}
fwt_h(i) &= \sum_{x} c(i,x) \times h(x) \\\\
&= \sum_{x} c(i,x) \sum_{j \oplus k = x} f(j) \times g(k) \\\\
&= \sum_{j} \sum_{k} f(j) \times g(k) \times c(i, j \oplus k)
\end{aligned}$$

故我们需要构造出的矩阵 $c(i,j)$ 需要满足 $c(i,j) \times c(i,k) = c(i,j \oplus k)$.

### OR 卷积：$h_i=\sum\limits_{j\ \mathrm{or}\ k=i}f_j \times g_k$

定义 $fwt_f(i) = \sum\limits_{j|i} f(j)$，可以证明 

$$fwt_f(i)·fwt_g(i) = \sum\limits_{j|i} \sum\limits_{k|i} f(j) \times g(k) = \sum\limits_{(j\ \mathrm{or}\ k)|i} f_(j) \times g(k) = fwt_h(i)$$

它对应的系数矩阵为 $c = \begin{bmatrix} 1 & 0 \\\\ 1 & 1\end{bmatrix}$.

转化：

- FWT：$f=Link(f_0,f_0+f_1)$

- IFWT：$f=Link(f_0,f_1-f_0)$

相当于求高维前缀和 / 差分。

### AND 卷积：$h_i=\sum\limits_{j\ \mathrm{and}\ k=i}f_jg_k$

定义 $fwt_f(i)=\sum\limits_{i|j} f(j)$，可以证明 

$$fwt_f(i)·fwt_g(i) = \sum\limits_{i|j} \sum\limits_{i|k} f(j) \times g(k) = \sum\limits_{i|(j\ \mathrm{and}\ k)} f(j) \times g(k) = fwt_h(i)$$

它对应的系数矩阵为 $c = \begin{bmatrix} 1 & 1 \\\\ 0 & 1\end{bmatrix}$.

转化：

- FWT：$f=Link(f_0+f_1,f_1)$

- IFWT：$f=Link(f_0-f_1,f_1)$

相当于求高维后缀和 / 差分。

### XOR 卷积：$h_i=\sum\limits_{j\ \mathrm{xor}\ k=i}f_jg_k$

定义 $x\bigotimes y=\texttt{popcount}(x\ \mathrm{and}\ y)\bmod 2$。

我们构造 $fwt_f(i)=\sum\limits_{i\ \mathrm{xor}\ j=0} f_(j)-\sum\limits_{i\ \mathrm{xor}\ j=1} f_(j)$。可以证明

$$
\begin{aligned}
fwt_f(i)·fwt_g(i) &= 
\left( \sum\limits_{i\ \mathrm{xor}\ j=0} f(j)- \sum\limits_{i\ \mathrm{xor}\ j=1} f(j) \right) \left( \sum\limits_{i\ \mathrm{xor}\ k=0} g(k) - \sum\limits_{i\ \mathrm{xor}\ k=1} g(k) \right) \\\\
&= \sum\limits_{i\ \mathrm{xor}\ (j\ \mathrm{xor}\ k)=0} f(j) \times g(k) - \sum\limits_{i\ \mathrm{xor}\ (j\ \mathrm{xor}\ k)=1} f(j) \times g(k) \\\\
&= fwt_h(i)
\end{aligned}
$$

它对应的系数矩阵为 $c = \begin{bmatrix} 1 & 1 \\\\ 1 & -1\end{bmatrix}$.


转化：

- FWT：$f=Link(f_0+f_1,f_0-f_1)$

- IFWT：$f=Link((f_0+f_1)/2,(f_0-f_1)/2)$

以上复杂度均为 $O(n\log n)$。

注意啦，FWT 是没有对模数有要求的，不要和 NTT 搞混淆了。

## 集合幂级数

- **集合占位幂级数**：定义二元幂级数 $f(x,y) = \sum\limits_S  f_S x^S y^{|S|}$，其中 $s$ 代表 **集合**，$i$ 代表集合大小。

### 子集卷积

- **子集卷积**：给定 $f_i,g_i(0\le i < 2^n)$，求 $h_i = \sum\limits_{j\subseteq i} f_j \times g_{i-j}$。

转化：

$$h_i = \sum\limits_{j\ \mathrm{or}\ k=i,|j|+|k|=|i|} f_j \times g_k$$

容易发现，子集卷积在第一维进行 $\texttt{OR}$ 卷积，在第二维进行加法卷积。这与形式集合占位幂级数的卷积形式是一样的。

我们可以将集合占位幂级数改写为 $f(x) = \sum\limits_{S} x^S \sum\limits_{i=0} f_{S,i} y^i$，那么此时每个 $x^S$ 的系数均可视作一个多项式（形式幂级数）。

因此，我们一开始先用 FWTor 变为点值表示。然后用朴素多项式乘法进行第二维上的卷积。最后再用一次 IFWTor 再变为系数表示。

注意，如果 $|S| \ne i$，我们需要 **钦定** $f_{S,i}=0$，因为这是不合法的。严谨地说，卷积前后我们要把不合法的位置全部设为 $0$。但是这里只做了一次子集卷积，对答案并没有影响，所以我们可以置之不理。

最后的答案为 $[x^{S}y^{|S|}] f(x,y)$.

时间复杂度 $O(n^2 2^n)$.

- **半在线子集卷积**：给定 $g_i(1\le i\le 2^n)$，求 $f_i = \sum\limits_{j\subseteq i} f_j \times g_{i-j}$。

因为朴素多项式乘法是可以半在线地计算的，因此我们可以 **交换维度** 进行卷积。

具体地来说，我们将占位幂级数改写为 $f(y) = \sum\limits_{i=0}  y^i \sum\limits_{S} f_{S,i} x^S$，此时我们可以视其为一个关于 $y$ 的形式幂级数，而每个 $y^i$ 的系数是一个占位幂级数。

因为半在线子集卷积也是从相对小的集合转移到相对大的集合上，所以此时的卷积就变成了分层转移。所以我们先按照集合大小（第二维）从小到大枚举，一步步地给每一维进行 FWTor，然后来一次多项式的暴力卷积，再做一遍 IFWTor 即可，然后将 $f_{S,i}$ 中 $|S| \ne i$ 设置为 $0$（因为这些位置是不合法的）。

以上复杂度均为 $O(n^2·2^n)$.

### 集合幂级数求逆 / 开方

将集合占位幂级数视作 $f(x) = \sum\limits_{S} x^S \sum\limits_{i=0} f_{S,i} y^i$。我们做完 FWTor 之后，给每一个多项式进行朴素多项式求逆，最后再进行一次 IFWTor 即可。

开方也和上面的类似。

### 集合幂级数 $\exp / \ln$

将集合占位幂级数视作 $f(x) = \sum\limits_{S} x^S \sum\limits_{i=0} f_{S,i} y^i$。我们做完 FWTor 之后，给每一个多项式进行朴素多项式指数函数 / 对数函数，最后再进行一次 IFWTor 即可。

以上的时间复杂度均为 $O(n^2·2^n)$.

它们都能用类似生成函数的角度来分析它们的组合意义。