---
title: 数学分析 | Ch10+11 级数、不定积分、定积分、广义积分
date: 2025-02-25
summary: 不定积分、定积分、数项级数、无穷限广义积分、瑕积分
---

## 不定积分【重在计算】
### 定义
全体原函数
### 基本表
微商表反方向读
引出 $\displaystyle \int \sec^2 x \mathrm dx$，$\displaystyle \int \csc^2 x \mathrm dx$，$\displaystyle \int \frac{\mathrm dx}{\sqrt{1 - x^2}}$，$\displaystyle \int \frac{\mathrm dx}{1 + x^2}$
### 性质
- 线性性：加法、乘以常数
### 换元积分法（凑微分法）
$\int f(g(x)) g'(x) \mathrm dx = \int f(g(x)) \mathrm dx$
引出 $\int  \frac{\mathrm dx}{a^2+x^2}$，$\int \frac{\mathrm dx}{x^2-a^2}$，$\int \frac{\mathrm dx}{\sqrt{x^2 \pm a^2}}$，$\int \sec x \mathrm dx$

凑微分常见形式：
- $\displaystyle \int \frac{\mathrm dx}{x} = \frac{1}{2}\int \frac{d(x^2)}{x^2}$
- $\displaystyle \int x\mathrm dx = \int \frac{1}{2}\displaystyle d(x^2)$
- 

### 换元积分法（变量代换法）
令 $x = g(t)$，那么 $\int f(x) \mathrm dx = \int f(g(t))g'(t) \mathrm dt$，最后再回代 $t = g^{-1}(t)$
引出 **三角换元**
$\sqrt{a^2 - x^2}$ 则 $x = a \sin t$
$\sqrt{x^2+a^2}$ 则 $x = a\tan t$
$\sqrt {x^2 - a^2}$ 则 $x = a\sec t$

有时可以换成其他元：
- $\displaystyle \frac{\sqrt{x}}{1 + x ^ 2} \mathrm dx = \int \frac{t}{1 + t^4} d(t^2)$
### 分部积分法
$\int u \mathrm dv = uv - \int v \mathrm du$成 ，转换成剩下部分的求导
口诀：反对幂指三，靠左记作 $u$，靠右记作 $v$.
引出1：幂函数作 $u$ 时多次分部积分
引出2：$1$ 作为幂函数如 $\int \arcsin x \mathrm dx$
引出3：含三角函数循环原积分，解方程
引出4：用分部积分来求递推式
### 通用积分公式
有理函数积分：$\frac{A}{x - a}$，$\frac{A}{(x - a)^n}$，$\frac{Bx+C}{x^2+px+q}$，$\frac{Bx+C}{(x^2+px+q)^n}$
拆分时有待定系数法、取特殊值求极限法
三角有理函数积分：用万能公式变量代换换成关于 $\tan \frac{x}{2}$ 的有理函数
无理函数积分：变量代换化成有理函数，三角代换化成三角有理函数
## 定积分
### 定义
黎曼和的极限
### 性质
- 可积函数必有界（反证法，否则有区间可以搞到无穷大，极限不存在）
- 线性性：对加法、乘法满足（用相同的黎曼和）
- 可加性：两个首尾相连的区间的积分可以并在一起，一个区间的积分可以从中间断开（中间断开的两个小区间和进行放缩）
- 积分单调性（黎曼和），推出和 $0$ 比，和 $[m, M]$ 比，和绝对值比
### 一致连续、积分中值定理和微积分基本定理
对一个区间内所有点的连续变化可以统一标准度量。
- 闭区间连续函数一定一致连续【康托定理】（反证法，三等分法+区间套定理）
- 闭区间连续函数一定可积（每个区间的取值之差之和可以通过一致连续证得趋于0）
- 【积分第一中值定理】：两函数乘积积分等于一函数某点取值乘另一函数的积分（两积分相除，再用连续函数介值定理），引出积分等于区间内某点取值乘区间长度
- 连续函数的变上限积分一定连续（用连续的定义+积分中值定理来放缩）
- 连续函数的变上限积分一定可导，导数是该函数（用可导的定义+积分中值定理来放缩）
- 【微积分基本定理】连续函数的定积分等于原函数两端点取值差值（变上限积分之差）
- 【微积分基本定理】可积函数的定积分等于原函数两端点取值差值（黎曼和，每段的极限就是积分中值定理）
求定积分，则先求原函数，再算两端点取值之差。
### 定积分的计算
- 换元积分法，注意要改变积分上下限
- 分部积分法
有时可以不导出原函数而得到定积分的值

## 数项级数
### 定义
数列的部分和极限
求部分和技巧：裂项相消、等差或等比数列求和
几何级数在$|r|<1$ 时收敛，$|r|\ge 1$ 时发散
### 性质
- 线性性：乘某一常数、两收敛级数相加
- 修改有限项不改变级数收敛性（和原级数的差值是定值）
- 收敛级数的一般项趋于 $0$（级数的差分极限等于 $0$）
### 正项级数
- 正项级数收敛充要于部分和有上界（必要性：收敛则有上界，充分性：单调上升有上界则必收敛）
$p$ 级数在 $p>1$ 时收敛，$p \le 1$ 时发散（$p=1$按$2^k$分组求和，$p>1$放缩成$p=1$，$p<1$按$2^k$分组等比数列求和）
- 比较判别法：通过充分大项一般项的比较可以互推两级数敛散性
- 比较判别法相邻之比形式：相邻一般项之比的比较可以互推两级数敛散性
- 达朗贝尔判别法：相邻一般项之比和 $1$ 比较知敛散性（本质是和几何级数比较）
- 柯西判别法：$^n\sqrt{u_n}$和$1$ 的比较
- 拉阿比判别法：$\lim_{n \to \infty} n(\frac{u_n}{u_{n+1}}-1)$和$1$的比较（本质是和$p$级数比较），注意大小和敛散相反
- 柯西积分判别法：单降正项级数收敛充要于一般项定积分存在（每个长度为$1$的定积分可夹在两相邻级数之间）
### 一般项级数
- 莱布尼兹判别法：交错级数的绝对值单降趋于$0$，则交错级数收敛（上界为$u_1$，且$u_2n$单增）
- 柯西收敛原理：级数收敛充要于充分大的两级数之差可以无限小
- 绝对值级数收敛，则原级数收敛：绝对值不等式+柯西收敛原理
- 达朗贝尔判别法：相邻一般项绝对值之比和 $1$ 比较知敛散性（本质是和几何级数比较）
### 阿贝尔变换和乘积级数
级数是竖条之和 $\sum a_nb_n$，u可以转换成横条之和 $\sum (\Delta a_i) B_i + a_nb_n$
- 阿贝尔引理：$b_n$部分和有界，$a_n$单调趋于$0$，则乘积级数收敛（放缩$B_n\le M$，得到$M(|a_1|+2|a_n|)$）
- 狄利克雷判别法：$b_n$部分和有界，$a_n$单调趋于$0$，则乘积级数收敛（用柯西收敛原理放缩$a_n \le \epsilon , B_n\le K$且柯西收敛原理）
- 阿贝尔判别法：$b_n$级数收敛，$a_n$单调有界，则乘积级数收敛（用柯西收敛原理放缩$a_n \le K, \sum B_i \le \epsilon$）
## 无穷限广义积分
### 定义
变上限趋于无穷大的积分的极限。
> **方法：**
> 1. 先求变上限积分，再求极限，注意，如果有参数就要分类讨论！
>    【例：$\displaystyle \int_{0}^{+\infty} \frac{\mathrm dx}{x^p}, a > 0$】
> 2. 有时候，可以利用分部积分等方式，化为原来积分并解方程。
>    【例：$\displaystyle \int_{0}^{+\infty} e^{-ax} \sin bx \mathrm dx, a>0$】
### 敛散性判定
- $\triangle$ **柯西收敛原理**【经常用来判断积分敛散性】：无穷限积分存在充要于 $\forall \epsilon > 0, \exists A > 0, \forall A', A'' > A, \displaystyle \left|\int_{A'}^{A''} f(x) \mathrm dx\right| < \epsilon$（积分函数极限存在）
- **绝对值**无穷限积分存在，且任意有限区间 $[a, A]$ 可积，则原函数无穷限积分存在。或者说若绝对收敛，则条件收敛。（绝对值不等式+柯西收敛原理）
- **比较判别法**：充分大项 $\displaystyle \forall x / \lim_{x \to +\infty}$ 绝对值比较  $|f(x)| \le / \ge \varphi(x)$ （或求比 $\displaystyle \frac{|f(x)|}{\varphi(x)} \to l$）来互推敛散性。（柯西收敛原理）
- **比较幂函数判别法**：充分大绝对值与$\displaystyle \frac{C}{x^p}$求比来互推敛散性。
  $\displaystyle \int_{a}^{+\infty} \frac{C}{x^p} \mathrm dx$ 在 $p > 1$ 时收敛，在 $p \le 1$ 时发散。
> **方法：** 先看这个被积函数的「阶」也就是增长级别，然后用合适的幂函数来比较。
> $e^{x}$ 看作指数$\to +\infty$的幂函数，$\ln x$ 看作指数 $\to 1^+$ 的幂函数，
> $\ln^{-1} x$ 看作指数$\to 1^-$ 的幂函数，$e^{-x}$ 看作指数 $\to -\infty$ 的幂函数。
> $\sin x, \cos x, \arctan x$ 看作常数。
> 相当于求极限，有时需要用洛必达法则来判断增长速度。
> 【例：$\displaystyle \int_{0}^{+\infty} x^a e^{-x}, a \ge 0$】【例：$\displaystyle \int_{0}^{+\infty} \frac{\mathrm dx}{x^a \ln x}$】
> 
> **方法**：如果出现复合函数的求阶，那么需要用泰勒公式展开来估计。
> 【例：$\displaystyle \int_1^{+\infty} \left[ \ln\left( 1 + \frac{1}{x} \right) - \frac{1}{1 + x}\right] \mathrm dx$，对 $\ln$ 展开一项】
> 【例：$\displaystyle \int_1^{+\infty} \ln\left( \cos\frac{1}{x} + \sin \frac{1}{x} \right)\mathrm dx$，对 $\cos, \sin$ 展开一项，再对 $\ln$ 展开一项】
- **积分第二中值定理（形式一）：** 若 $f(x)$ 在 $[a, b]$ 可积，$g(x)$ 在 $[a, b]$ 上单调，那么存在 $\xi \in [a, b]$ ，使得
  $$\int_a^b f(x)g(x) \mathrm dx = g(a) \int_a^\xi f(x) \mathrm dx + g(b) \int_\xi^b f(x) \mathrm dx$$
   （以 $g(x)-g(a)$ 代 $g(x)$）
- **积分第二中值定理（形式二）：** 若 $f(x)$ 在 $[a, b]$ 可积，$g(x)$ 在 $[a, b]$ 单调上升且恒 $\ge 0$，那么存在 $\xi \in [a, b]$ ，使得
  $$\int_a^b f(x)g(x) \mathrm dx = g(b) \int_\xi^b f(x) \mathrm dx$$
  $g(x)$ 在 $[a, b]$ 单调下降且恒 $\ge 0$，那么存在 $\xi \in [a, b]$ ，使得
  $$\int_a^b f(x)g(x) \mathrm dx = g(a) \int_a^\xi f(x) \mathrm dx$$
 （用单调函数可积+$F(x)$连续函数介值定理，转换成对乘积积分的估计，然后将乘积积分黎曼和进行阿贝尔变换，然后对和式中的所有 $F(x_i)$ 放缩）
- **狄利克雷判别法**：若 $f(x)$ 变上限积分有界，$g(x)$ 单调趋于 $0$，则二者无穷限乘积积分 $\displaystyle \int_a^{+\infty} f(x) g(x) \mathrm dx$ 收敛。
  （柯西收敛原理+积分第二中值定理，放缩 $\displaystyle \left |\int f(x) \right | \le M, |g(x)| \le \epsilon$）
- **阿贝尔判别法**：若 $f(x)$ 变上限积分收敛，$g(x)$ 单调有界，那么二者无穷限乘积积分 $\displaystyle \int_a^{+\infty} f(x) g(x) \mathrm dx$ 收敛。
  （柯西收敛原理+积分第二中值定理，放缩 $\displaystyle \left|\int f(x) \right| \le \epsilon, |g(x)| \le M$）
> **方法**：
> 常见有界变上限积分：$\displaystyle \int_1^{+\infty} \cos x, \int_1^{+\infty} \sin x$
> 对于 $|\cos x|$，经常放缩为 $\displaystyle |\cos x| \ge \cos^2 x = \frac{1 + \cos 2x}{2}$
## 瑕积分
### 定义
变上/下限趋于暇点的积分的极限
> **方法**：
> 1. 先计算变上/下限积分，再求它的极限判断敛散性
> 【例：$\displaystyle \int_a^b \frac{\mathrm dx}{(x - a)^p}$，$\displaystyle \int_{-1}^1 \frac{\mathrm dx}{\sqrt{1 - x^2}}$】
> 2. 若有两个暇点，可以利用可加性原理 $\displaystyle \int_a^b f(x) \mathrm dx = \int_a^c f(x) \mathrm dx + \int_c^b f(x) \mathrm dx$
### 积分法
换元法、分部积分法
### 性质
- 线性性、可加性
- **柯西收敛原理**：瑕积分存在充要于上下限趋于暇点的定积分极限为 $0$：任给 $\epsilon > 0$，存在 $\eta > 0$，$\displaystyle \forall 0 < \eta', \eta'' < \eta, \left|\int_{a + \eta'}^{b + \eta''}(x) \mathrm dx\right| < \epsilon$（积分函数极限存在）
- 绝对值瑕积分存在，则原函数瑕积分存在（绝对值不等式+柯西收敛原理）
### 敛散性判定
**和无穷限积分关系**：可以换元 $\displaystyle y = \frac{1}{x - a}, x = \frac{1}{y} + a, \mathrm dx = -\frac{\mathrm dy}{y^2}$，那么可以转换成无穷限积分，因此二者敛散性判定是类似的。
$$\int_a^b f(x) \mathrm dx = \int_{\frac{1}{b - a}}^{+\infty} \frac{f\left( a + \frac{1}{y} \right)}{y^2} \mathrm dy$$
- 比较判别法：充分接近瑕点的函数绝对值比较（或求比）来互推敛散性，**需要两个函数都是正的或者取绝对值**。
- **比较幂函数判别法**：充分接近瑕点绝对值与$\displaystyle \frac{1}{(x - a)^p} (p?1)$求比或者直接比较，来互推敛散性。
  对于 $\displaystyle \int_a^b \frac{c}{(x - a)^p}$，当 $p < 1$ 收敛，当 $p \ge 1$ 发散。
> 方法：$\ln x$ 发散得比任何负幂函数都要慢
>$\ln x, e^x, \sin x, \cos x$
- 狄利克雷判别法：若 $f(x)$ 变上/下限 $\to a$ 积分有界，$g(x) (x \to a)$ 单调趋于 $0$，则二者无穷限乘积积分收敛（柯西收敛原理+积分第二中值定理，放缩 $|\int f(x)| \le M, |g(x)| \le \epsilon$）
- 阿贝尔判别法：若 $f(x)$ 变上/下限 $\to a$ 积分收敛，$g(x) (x \to a)$ 单调有界，那么二者无穷限乘积积分收敛（柯西收敛原理+积分第二中值定理，放缩 $|\int f(x)| \le \epsilon, |g(x)| \le M$）