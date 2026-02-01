---
title: OI 笔记合集 | 数论
date: 2021-12-21
summary: 逆元、拓展gcd、裴蜀定理、中国剩余定理、Lucas定理、BSGS算法、Cipolla算法、剩余系扩域、欧拉定理、狄利克雷卷积、杜教筛、Min_25筛、类欧几里得
---


## 逆元

- 求解 $ax\equiv1\pmod p$。

有解充要条件：$a\perp p$。（由裴蜀定理）

若 $p$ 是质数，我们使用费马小定理：$x\equiv a^{p-2}\pmod p$。

否则，我们使用 exgcd 求解 $ax+bp=1$ 。

$\textbf{离线线性求 } 1 \sim n \textbf{ 逆元}$

- **线性递推：** $i^{-1}=-\left\lfloor\dfrac{p}{i}\right\rfloor·(p\bmod i)^{-1}$。可以倒推回去证明。
- **配合阶乘：** 实战时我们经常还需要求 $fact(i)$ 以及 $fact(i)^{-1}$，我们直接先一遍 $fact(1\sim n)$，然后用 $O(\log p)$ 的时间求 $fact(n)^{-1}$。最后我们有：
	- $fact(i-1)^{-1}=fact(i)^{-1}·i$
   - $i^{-1}=fact(i)·fact(i-1)^{-1}$。
- **配合线性筛：** 通过欧拉筛我们可以求出每个合数的最小素因子 $d(i)$ 是什么。我们对 $[1,n]$ 里面的质数全部做一遍快速幂求逆元，然后对于其他合数可以递推求出 $i^{-1}=(i/d(i))^{-1}·d(i)^{-1}$。由于 $[1,n]$ 内的质数个数大约为 $\dfrac{n}{\ln n}$ 个，而快速幂时间复杂度为 $O(\log p)$，因此 $\log$ 可以视作抵消，复杂度为线性。



$\textbf{离线线性求 } a_1 \sim a_n \textbf{ 逆元}$

线性递推 / 配合线性筛都是基于 $1 \sim n$ 的性质的，这里无法直接沿用。我们考虑使用类似配合阶乘的做法。

1. 求出 $\prod\limits_{i=1}^n a_i$，此时我们可以在 $O(\log p)$ 的时间内求出 $\textrm{inv} = \left(\prod\limits_{i=1}^n a_i\right)^{-1}$.
2. 求出前缀积和后缀积 $\textrm{premul}(i) = \prod\limits_{j=1}^{i} a_i$，$\textrm{sufmul}(i) = \prod\limits_{j=i}^{n} a_i$.
3. 此时 $a_i^{-1} = \textrm{inv} \times \textrm{premul}(i-1) \times \textrm{sufmul}(i+1)$.

时间复杂度 $O(\log p + n)$.

## 拓展欧几里得，裴蜀定理

已知 $bx+(a\bmod b)y=c$，那么

$bx+\left(a-\left\lfloor\dfrac{a}{b}\right\rfloor b\right)y=c$，整理得到 $ay+b\left(x-\left\lfloor\dfrac{a}{b}\right\rfloor y\right)=c$.

有解条件：$gcd|c$。

中间变量通常是 $O(\text{值域}^2\sim \text{值域}^3)$ 大小。

通解：考虑一个加上 lcm，一个减去 lcm.

## 中国剩余定理

对于模线性方程组 $\begin{cases}x\equiv a_i\pmod {m_i}\end{cases}$

我们构造出通解：设 $N=\prod m_i$，

$x=\sum\limits_{i=1}^n a_i\times\dfrac{N}{m_i}\times\left[\left(\dfrac{N}{m_i}\right)^{-1}\right]_{m_i}\pmod {N}$。

证明：

- $i\neq j$ 时 $\dfrac{N}{m_j}$ 包含 $m_i$，消去了；
- $i= j$ 时后面两个东西乘起来 $\bmod m_i=1$ 。

## 拓展中国剩余定理

合并两个方程 
$$
\begin{cases}
x\equiv a_1\pmod {m_1}\\\\
x\equiv a_2\pmod {m_2}
\end{cases}
$$

可以得到 $m_1k_1+m_2k_2=a_2-a_1$，由特解构造通解 $k_1=k'_1+c·(lcm/m_1),k_2=k'_2-c·(lcm/m_2)$。

那么 $x=m_1k_1+a_1=m_1(k'_1+c·(lcm/m_1))+a_1=lcm·c+(m_1k_1'+_1)$。

即 $x\equiv a_1k_1'+b_1\pmod{lcm}$。

常见应用：将模数拆成多个较小的数（一般为质数）相乘的形式，最后再用 (ex)crt 合并。这导致了一堆「XXX 加强版」/「拓展 XXX」。

## Lucas 定理

$\dbinom{n}{m}\bmod p=\dbinom{n/p}{m/p}·\dbinom{n\bmod p}{m\bmod p}$

递归求解。在 $n,m$ 的值域超过了 $p$ 并且 $p$ 是质数时用。

## 拓展 Lucas 定理

拆模数 $P=\prod {p_i}^{k_i}$，其中 $p_i$ 是质数。最后再使用 EXCRT 把它们给合并。

求 $\dfrac{n!}{m!(n-m)!}\pmod {{p_i}^{k_i}}$，然而我们无法求逆元。因为可能里面有些乘数是 $p_i$ 的倍数，不满足裴蜀定理。

考虑提取 $p_i$。求 $n!$ 能拆成多少个 $p_i$：$c(n)=\sum_k n/p_i^k$。于是把分离 $p_i$ 后的结果乘上 $p^{c(n)-c(m)-c(n-m)}$ 即可。

接下来求 $n!$ 分离后的结果 $r(n)$。那么可以递归求解 $$r(n)=[r(p^k-1)]^{n/p^k}\times r(n\bmod p^k)\times r(n/p)$$

前面两个可以通过预处理 $1\sim p^k$ 的阶乘分离后的结果得到。

最后一个 $r(n/p)$ 的意义是：把 $p,2p,3p,\dots $ 拎出来整体除以 $p$，然后又是一个子问题。

简明叙述：拆模数用 excrt 合并，三个阶乘分别提取模数然后递归求解，最后就能求逆元了。

## 离散对数：BSGS 算法

求解离散对数 $a^x\equiv b\pmod p$，保证 $a\perp p$。

我们把 $x\le\sqrt p$ 的 $a^x$ 全部扔进 hashmap 里面，然后对于每个 $a^{k\sqrt p}$，我们查找 $\dfrac{b}{a^{k\sqrt p}}$ 在 hashmap 里面是否有值即可。如果查找成功，答案为 $k\sqrt p+x$。

## 二次剩余：Cipolla 算法

求解二次剩余：$x^2\equiv n\pmod p$，保证 $p$ 是奇质数。

解的数量：最多两个，并且它们互为相反数。（证明：$x_1^2-x_2^2\equiv(x_1+x_2)(x_1-x_2)\equiv0$，则 $x_1+x_2\equiv0\pmod p$）

有解充要条件：$n^{\frac{p-1}{2}}\equiv1\pmod p$；无解充要条件：$n^{\frac{p-1}{2}}\equiv-1\pmod p$.

Cipolla 算法：找到一个 $a$ 使得 $a$ 不是二次剩余。令 $i=\sqrt{a^2-n}$（请类比复数）。那么 $(a+i)^{\frac{p+1}{2}}$ 为一个解，另一个解也自然得出。

## 剩余系扩域

- 剩余系：某一个特定的正整数 $p$，所有整数模 $p$ 所得的余数域 。

我们已经可以计算剩余系下的加减乘法和逆元，至于开方却必须要满足 $x^{\frac{p-1}{2}}\equiv 1\pmod p$，如果 $x^{\frac{p-1}{2}}\equiv-1\pmod p$ 就无法开方了。例如，$\sqrt5$ 在 $\mod 998244353$ 意义下不存在。

我们可以类比实数域的扩域，我们随便找一个无法开方的数（例如 $5$），令 $i\equiv\sqrt 5\pmod p$，则此时我们就将剩余系拓展成一个二维的平面，用 $a+bi$ 或 $a+b\sqrt 5$ 表示一个数。然后就可以愉快地进行运算了。

注意乘法的时候要将 $i^2$ 替换成你选择的那个数，例如 

$$(1+\sqrt 5)(2-\sqrt 5)\equiv2-\sqrt 5+2\sqrt 5-5\equiv-3+\sqrt 5\pmod {998244353}$$

## 欧拉定理

- 欧拉函数 $\varphi(n)$：$[1,n]$ 内与 $n$ 互质的个数。
$\varphi(n)=\sum_{i=1}^n [i\perp n]$
- 特别的，如果 $n$ 是质数，则 $\varphi(n)=n-1$
- 求单点值：$\varphi(n)=n·\prod\limits_{p\in P,i|n} \dfrac{p-1}{p}$
- 求 $1\sim n$ 的值：积性函数，可以线性筛；

欧拉定理：若 $a\perp p$，则 $a^{\varphi(p)}\equiv1\pmod p$.

$\Rightarrow$ 若 $p$ 是质数，那么可以得出 $a^{p-1}\equiv 1\pmod p$（费马小定理）

拓展欧拉定理：

$$a^n\equiv
\begin{cases}
a^{n\bmod \varphi(p)},&a\perp p\\\\
a^n,&a\not\perp p,n<\varphi(p)\\\\
a^{n\bmod \varphi(p)+\varphi(p)},&a\not\perp p,n\ge \varphi(p)
\end{cases}\pmod p$$

应用：降幂，直接预处理 $0\sim \phi (p)$ 的幂即可。

## 狄利克雷卷积和常用数论函数

[好文章1](https://www.cnblogs.com/tttkf/p/15952812.html) / [好文章2](https://www.luogu.com.cn/blog/command-block/mu-bi-wu-si-fan-yan-ji-ji-ying-yong)

**狄利克雷(Dirichlet)卷积**：$(f*g)(n)=\sum\limits_{d|n}f(d)	·g(n/d)$。

### 性质

- 若 $f(n),g(n)$ 是积性函数，则 $(f*g)(n)$ 也是极性函数。
- 满足 1.交换律；2.结合律； 3.对函数加法的结合律
- 单位元：$\epsilon(n)=[n=1]$，我们有 $(f*\epsilon)(n)=\sum\limits_{d|n}[d=1]·f(n/d)=f(n)$。
- 逆元：若对于一个函数 $f(n)$ 存在 $f*g=\epsilon$，则我们称 $f,g$ 互为逆元。

### 常见数论函数

- 单位函数：$\epsilon(n)=[n=1]$；
- $\omega(n)$：$n$ 的互不相同的素因子个数。
- 幂函数：$id_k(n)=n^k$，当 $k=1$ 时为恒等函数 $id(n)=n$，$k=0$ 是为常数函数 $1(n)=1$；
- $d(n)/\sigma_0(n)=\sum_{d|n} 1=1*1$：$n$ 的约数个数。
- $\sigma_1(n)=\sum_{d|n}d=id*1$，约数和。
- $\sigma_k(n)=\sum_{d|n}d^k=id_k*1$：$n$ 的约数 $k$ 次幂之和。
- 欧拉函数：$\varphi(n)=\sum_{i=1}^n [i\perp n]$，即 $[1,n]$ 内与 $n$ 互质的个数。
- 莫比乌斯函数：
$$\mu(n)=
\begin{cases}
(-1)^{\omega(n)},&& \text{if n is a square-free positive integer}\\\\
0,&&\rm otherwise
\end{cases}$$

以上除了 $\omega(n)$ 均为积性函数。

以上函数都可以借助线性筛在 $O(n)$ 时间复杂度内推出 $1\sim n$ 的值。

~~某网传知名图片~~

![](https://cdn.luogu.com.cn/upload/image_hosting/j4ds5pcn.png)

由于互不相同质因子个数 / 约数个数 / 约数和相对值域来说小得多，因此这衍生出了一大堆 ~~CF/AT 上的妙妙结论题~~。

### 常用结论

#### 狄利克雷卷积形式

- 欧拉函数反演：$\varphi*1=id$，即 $n=\sum\limits_{d|n}\varphi(d)$
- 莫比乌斯反演：$\mu*1=\epsilon$，即 $[n=1]=\sum\limits_{d|n}\mu(d)$
- $\mu*id=\varphi$
- 若 $f(n)=\sum\limits_{d|n}g(d)$，则 $g(n)=\sum\limits_{d|n}\mu(d)·f(n/d)$
	- 证明：$f=g*1\Leftrightarrow f*\mu=g*1*\mu\Leftrightarrow g=f*\mu$
   - 理解：本质是一种容斥，对 $n$ 的约数按照互不相同质数的多少进行容斥。
   
#### 乘积形式 / 前缀和形式
- $\mu(xy)=\mu(x)·\mu(y)·[x\perp y]$；
- $d(xy)=\sum\limits_{i|x}\sum\limits_{j|y}[i\perp j]=\sum\mu(d)\left\lfloor\dfrac{x}{d}\right\rfloor\left\lfloor\dfrac{y}{d}\right\rfloor$
- 拓展 $$\begin{aligned}d(xyz)&=\sum\limits_{i|x}\sum\limits_{j|y}\sum\limits_{k|z}[i\perp j][i\perp k][j\perp k]\\\\&=\sum_a\sum_b\sum_c\mu(a)\mu(b)\mu(c)
\left\lfloor\dfrac{x}{lcm(a,b)}\right\rfloor
\left\lfloor\dfrac{y}{lcm(a,c)}\right\rfloor
\left\lfloor\dfrac{z}{lcm(b,c)}\right\rfloor\end{aligned}$$
- $\varphi(xy)=\dfrac{\varphi(x)\varphi(y)\gcd(x,y)}{\varphi(\gcd(x,y))}$
- $\sum\limits_{i=1}^n d(n)=\sum\limits_{i=1}^n\left\lfloor\dfrac{n}{i}\right\rfloor$，即考虑每个数对答案的贡献。

## Dirichlet 前缀和

> 给定 $g_{1\sim n}$，求 $f_i = \sum\limits_{j|i} g_j$.

我们将每个质数当作一维，每个数在每个质数维的坐标为其质因数分解之后，这个质数对应的指数。

这样我们就把这问题转化为高维前缀和问题了。

狄利克雷前缀和相当于求 $g = f * id$。
    
一开始令所有 $f_i \leftarrow g_i$；
   
每一轮我们选取一个质数 $p$，然后令所有 $f_{i \times p} \leftarrow f_{i \times p} + f_i$，注意这里是从前往后枚举 $i$，这样才能连续贡献。

> 给定 $g_{1\sim n}$，求 $f_i = \sum\limits_{i|j} g_j$.

高维前缀和 $\rightarrow$ 高维后缀和。

即贡献方式改为 $f_{i} \leftarrow f_i + f_{i \times p}$，从后往前枚举。
   
> 给定 $g_{1\sim n}$，求 $f_i = \sum\limits_{j|i} g_j·\mu(i/j)$.

相当于高维差分。

我们将贡献方式改为 $f_{i \times p} \leftarrow f_{i \times p} - f_i$。因为如果当 $x$ 有质数平方项则 $\mu(x)=0$，所以我们不可以连续贡献，因此我们应当从后往前枚举。

> 给定 $g_{1\sim n}$，求 $f_i = \sum\limits_{j|i} g_j·h(i/j)$，其中 $h$ 是 **完全积性函数**。

也就是说我们可以将 $h(i/j)$ 分解成若干个 $h(p_i)$ 相乘。

因此我们将贡献的系数直接改为 $h(p)$，即 $f_{i \times p} \leftarrow f_{i \times p} + f_i·h(p)$，从前往后枚举。
   
以上时间复杂度的计算形式均为 $T(n)=\sum\limits_{p_i} \dfrac{n}{p_i}=O(n\log\log n)$.

> 给定 $g_{1\sim n}$，求 $f_i = \sum\limits_{j|i} g_j·h(i/j)$，其中 $h$ 是 **积性函数**。

我们可以将 $h(i/j)$ 分解成若干个互质的 $h(p_i^k)$ 相乘。

每一轮我们整体处理 $\times h(p_i^k)$ 的转移。我们从后往前枚举，每次将 $f(i)$ 贡献给 $f(i \times p), f(i \times p^2), f(i \times p^3)\dots$ 直至超过 $n$。

对于每一轮的时间复杂度为 $\sum\limits_{i=1} \dfrac{n}{p^i} = \dfrac{n}{p-1} = O\left(\dfrac{n}{p}\right)$.

因此总时间复杂度仍为 $T(n) = \sum\limits_{p=1} O\left(\dfrac{n}{p_i}\right) = O(n\log\log n)$.
   


## 杜教筛

杜教筛利用了狄利克雷卷积，可以在 **非线性时间** 内求积性函数 **前缀和**。它利用了狄利克雷卷积的性质。

我们设现在有三个数论函数 $f,g,h$ 满足 $f * g = h$，那么有

$$\begin{aligned}
\sum_{n=1}^N h(n) &= \sum_{n=1}^N \sum_{i|n} f(i)·g\left(\dfrac{n}{i}\right) \\\\
&= \sum_{i=1}^N f(i) \sum_{i|n}^N g\left(\dfrac{n}{i}\right) \\\\
&= \sum_{i=1}^N f(i) \sum_{n=1}^{\left\lfloor\frac{N}{i}\right\rfloor} g(n) \\\\
\end{aligned}$$

我们用前缀和标记简化一下和式的表达

$$\begin{aligned}
S_h(N) &= \sum_{i=1}^N f(i)·S_g\left(\left\lfloor\dfrac{N}{i}\right\rfloor\right) \\\\
f(1)·S_g(N) &= S_h(n) - \sum_{i=2}^N f(i)·S_g\left(\left\lfloor\dfrac{N}{i}\right\rfloor\right)
\end{aligned}$$

这样我们就得到了求 $S_g(N)$ 的递归式，显然我们可以使用整除分块达到转移 $O(\sqrt N)$ 的复杂度，但是我们最多会涉及多少个状态呢？容易发现，我们一直在对 $N$ 整除以一个 $\ge 2$ 的数，由 $\left\lfloor\frac{\left\lfloor\frac{N}{a}\right\rfloor}{b}\right\rfloor=\left\lfloor\frac{N}{ab}\right\rfloor$ 可知，我们涉及的状态都是初始的 $N$ 整除某个数的结果，因此时间复杂度这些数的转移复杂度之和。

我们只取最大的前 $\sqrt N$ 个数计算（显然这样是同阶的），为 $T(n) = \sum\limits_{i=1}^{\sqrt n} O\left(\sqrt \frac{N}{i}\right) = O(n^{\frac{3}{4}})$.

在实际过程中我们可以先预处理 $S_g(1 \sim M)$ 的值，那么此时的时间复杂度为 $T(n) = M + \sum\limits_{i=1}^{\sqrt \frac{N}{M}} O\left(\sqrt \frac{N}{i}\right) = O(M + NM^{-\frac{1}{2}})$。 我们令 $M = NM^{-\frac{1}{2}}$ 解得 $M = N^{\frac{2}{3}}$，那么最优复杂度为 $O(N^{\frac{2}{3}})$.

因此，我们只需要快速知道 $S_f(n),S_h(n)$ 在 $N$ 整除后得到的所有数的单点值，就可以在 $O(N^{\frac{2}{3}})$ 下求出单点前缀和 $S_g(N)$.

- $\mu * I = \epsilon \Rightarrow S_{\mu}(N) = 1 - \sum\limits_{i=2}^N S_{\mu}\left(\left\lfloor\frac{N}{i}\right\rfloor\right)$
- $\varphi * I = id \Rightarrow S_{\varphi}(N) = \frac{n(n+1)}{2} - \sum\limits_{i=2}^N S_{\varphi}\left(\left\lfloor\frac{N}{i}\right\rfloor\right)$

## Min_25 筛

Min_25 筛可以在非线性时间内求一个 **积性函数** 的前缀和，但这个函数需要满足：

- $f(p)$ 是(或者能转化为求) **低阶多项式**。
- 对质数的幂单点求值 $f(p^c)$ 能 **快速算出**。

为了方便，我们将 $1$ 撇开，最后再将答案加上 $f(1)$ 即可。我们将 $[2,n]$ 按照质数和合数分开计算，

$$\sum_{p_i\in \mathbb P \land 2\le p_i\le n} f(p_i) + \sum_{p_i\in \mathbb P \land p_i\le \sqrt n \land p_i^k \le n} f(p_i^k) \left( \sum_{2\le i\le \lfloor\frac{n}{p_i^k}\rfloor \land \texttt{minp}(i) > p_i } f(i) + [k > 1]\right)$$

其实就是对于合数枚举了一下它的最小质因子 $\texttt{minp}(i)=p$，然后我们再枚举了这个最小质因子对应的幂次，然后将这一类数全部剔除掉这个最小质因子，就变成了一个子问题。我们不妨设 $S(n,x)$ 为 $[2,n]$ 中经过 $x$ 轮埃氏筛后剩下的数（即所有质数和最小质因数 $> p_x$ 的合数）所有函数单点值之和，那么类似于上面的式子有

$$S(n,x) = \sum_{p_i \in \mathbb P \land p_x<p_i\le n} f(p) + \sum_{p_i\in \mathbb P \land p_x < p_i \le \sqrt n \land p_i^k \le n} f(p_i^k) \left( S\left(\left\lfloor\dfrac{n}{p_i^k}\right\rfloor,i\right) + [k > 1]\right)$$

答案即为 $S(n,0)$.

右边的和式可以递归求解，现在就剩下左边的 **区间质数单点值之和** 了。

为了快速计算这个东西，我们拆成两个前缀之差 $sumf(n) - sumf(p_x)$，因为当 $p_x > \sqrt n$ 时 $S(n,x) = S(n,x-1)$（已经把所有质数筛完了），因此 $sumf(p_x)$ 可以在 $O(\sqrt n)$ 时间内预处理。而又因为递归过程中仍然是像杜教筛那样将 $n$ 不断整除，因此我们只需要计算 $n$ 整除后的所有结果 $sumf\left(\left\lfloor\frac{n}{i}\right\rfloor\right)$ 即可。

因为 $f(x)$ 是个多项式，所以我们拆成若干个项的幂 $f_k(x) = x^k$，然后把它们线性加减即得答案。

设 $g(n,x)$ 表示 $[2,n]$ 经过 $(x-1)$ 轮埃氏筛之后剩下的数的 $k$ 次幂之和，那么剩下的要么是质数，要么是最小质因子 $\ge p_x$ 的合数。因此

$$g(n,x) = g(n,x-1) - p_x^k\left(g\left(\left\lfloor\frac{n}{p_x}\right\rfloor, x-1\right) - \sum_{i=1}^{x-1} p_i^k\right)$$

减去一段质数前缀是因为如果这些数与 $p_x$ 相乘，最小质因子就不会是 $p_x$ 了。这个前缀和可以预处理。

因为 $f_k(x) = x^k$ 是个 **完全积性函数**，所以我们无需再枚举 $p_x$ 的幂强令它们互质了。

这里计算质数单点值之和的转移是 $O(1)$ 的，而对于状态数为 $T(n) = \sum\limits_{i=1}^{\sqrt n} O\left(\dfrac{\sqrt {\frac{n}{i}}}{\log \frac{n}{i}}\right) = O\left(\frac{n^{\frac{3}{4}}}{\log n}\right)$.

而计算 $S(n,x)$ 的复杂度也被证明为 $O\left(\frac{n^{\frac{3}{4}}}{\log n}\right)$ 或 $O\left(n^{1-\epsilon}\right)$。不过常数似乎比杜教筛还小，可以跑 $n = 10^{10}$ .注意在计算 $S(n,x)$ 的时候，递归 **不需要记忆化**！否则会慢很多。（这部分好玄学）

## 类欧几里得算法

Warning：类欧几里得算法和欧几里得算法没有什么关系。只是其时间复杂度证明与欧几里得算法类似而已。

我们需要求一类类似线段下整点个数的和式

$$\begin{aligned}
f(a,b,c,n) &= \sum_{i=0}^n 
	\left\lfloor \dfrac{ai+b}{c} \right\rfloor \\\\
g(a,b,c,n) &= \sum_{i=0}^n
	\left\lfloor \dfrac{ai+b}{c} \right\rfloor^2 \\\\
h(a,b,c,n) &= \sum_{i=0}^n
	i\left\lfloor \dfrac{ai+b}{c} \right\rfloor \\\\
\end{aligned}$$

接下来的内容我也没啥特别好的理解。就跟着模板走吧。

幂和记号：$s_1(n) = \sum\limits_{i=0}^n i = \dfrac{n(n+1)}{2}$，$s_2(n) = \sum\limits_{i=0}^n i^2 = \dfrac{n(n+1)(2n+1)}{6}$

- **边界：$\textbf{a=0}$**

$$\begin{aligned}
f(0,b,c,n) &=
\lfloor b/c \rfloor(n+1) \\\\
g(0,b,c,n) &= 
\lfloor b/c \rfloor^2 (n+1) \\\\
h(0,b,c,n) &=
\lfloor b/c \rfloor s_1(n)\\\\
\end{aligned}$$

- **取模：$\textbf{a} \ge \textbf{c}$ 或 $\textbf{b} \ge \textbf{c}$**

我们想要将 $a,b$ 缩小到 $[0,c)$ 的范围内。所以要取模。

因此有这个整除式的转化

$$\begin{aligned}
\left\lfloor \dfrac{ai+b}{c} \right\rfloor
=& \left\lfloor
\dfrac{\left(\lfloor a/c \rfloor·c + a \bmod c\right)·i +\left(\lfloor b/c \rfloor·c + b \bmod c\right)}{c} \right\rfloor \\\\
=& \lfloor a/c \rfloor·i + 
\lfloor b/c \rfloor + 
\left\lfloor 
\dfrac{\left(a \bmod c\right)·i + \left(b \bmod c\right)}{c} 
\right\rfloor \\
\end{aligned}$$

我们记 $f'/g'/h' = f/g/h(a \bmod c, b \bmod c,c,n)$，把上式代入，并暴力拆开则有

$$\begin{aligned}
f(a,b,c,n) &=
\lfloor a/c \rfloor s_1(n) + 
\lfloor b/c \rfloor (n+1) + 
f'\\\\
g(a,b,c,n) &=
\lfloor a/c \rfloor^2 s_2(i) + 
\lfloor b/c \rfloor^2 (n+1) + 
g' +
2 \lfloor a/c \rfloor h' + 
2 \lfloor b/c \rfloor f' + 
2 \lfloor a/c \rfloor \lfloor b/c \rfloor s_1(n)
\\\\
h(a,b,c,n) &= 
\lfloor a/c \rfloor s_2(i) + 
\lfloor b/c \rfloor s_1(i) + 
h'
\end{aligned}$$

- **交换：$\textbf{otherwise}$**

考虑拆分贡献

$$\begin{aligned}
f(a,b,c,n)
&= \sum_{i=0}^n 
	\left\lfloor \dfrac{ai+b}{c} \right\rfloor \\\\
&= \sum_{i=0}^n \sum_{j=1}^{m}
	\left[
   		j \le \left\lfloor \dfrac{ai+b}{c} \right\rfloor
   \right] \\\\
&= \sum_{i=0}^n \sum_{j=0}^{m-1}
	\left[
   		j+1 \le \left\lfloor \dfrac{ai+b}{c} \right\rfloor
   \right]
\end{aligned}$$

其中 $m = \lfloor (an+b)/c\rfloor$.

考虑处理那个判断式

$$\begin{aligned}
j+1 &\le \left\lfloor \dfrac{ai+b}{c} \right\rfloor \\\\
cj+c &\le ai+b \\\\
i &\ge \dfrac{cj+c-b}{a} \\\\
i &> \left\lfloor \dfrac{cj+c-b-1}{a} \right\rfloor
\end{aligned}$$

考虑交换和式再代回去

$$\begin{aligned}
f(a,b,c,n)
&= \sum_{j=0}^{m-1}
	n - \left\lfloor \dfrac{cj+c-b-1}{a} \right\rfloor \\\\
&= nm - f(c,c-b-1,a,m-1)
\end{aligned}$$

我们令 $T = \left\lfloor \dfrac{cj+c-b-1}{a} \right\rfloor$, $f'/g'/h' = f/g/h(c,c-b-1,a,m-1)$.

这里平方不太好处理，故考虑 $n^2 = 2\sum\limits_{i=0}^n i - n$，则

$$\begin{aligned}
  \begin{aligned}
    g(a,b,c,n)
    &= \sum_{i=0}^n 
        \left\lfloor \dfrac{ai+b}{c} \right\rfloor^2  \\\\
    &= 2\left(
          \sum_{i=0}^n \sum_{j=1}^{m}
            j
           \left[
                j \le \left\lfloor \dfrac{ai+b}{c} \right\rfloor
           \right]
       \right) - 
       f(a,b,c,n) \\\\
    &= 2\left(
          \sum_{j=0}^{m-1}
            (j+1) \left( n-T \right)
       \right) - 
       f(a,b,c,n) \\\\
    &= (2ns_1(m) - 2f' - 2h') - (nm - f') \\\\
    &= nm(m+1) - f' - 2h' \\\\
  \end{aligned}
   \begin{aligned}
      h(a,b,c,n)
      &= \sum_{i=0}^n 
          i \left\lfloor \dfrac{ai+b}{c} \right\rfloor  \\\\
      &= \sum_{i=0}^n
            i \sum_{j=1}^{m}
              \left[
                j \le \left\lfloor \dfrac{ai+b}{c} \right\rfloor
             \right] \\\\
      &= \sum_{j=0}^{m-1}
              \sum_{i=0}^n
              i [i>t] \\\\
      &= \sum_{j=0}^{m-1}
              \dfrac{1}{2} (t+1+n)(n-t) \\\\
      &= \dfrac{1}{2}
          \left(
              nm(n+1) - f' - g'
         \right)
  \end{aligned}
\end{aligned}
$$

- **时间复杂度**

我们发现，$(c,c-b-1,a,m-1)$ 与 $(a,b,c,n)$ 相比就是 $a,c$ 交换了一下，因此下一次又能再取模，交换 $\dots$

因此时间复杂度与欧几里得算法相同，均为 $O(\log w)$，其中 $w$ 为值域。