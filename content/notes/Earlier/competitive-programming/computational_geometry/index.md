---
title: OI 笔记合集 | 计算几何
date: 2022-04-07
summary: 向量、极坐标、距离、判断直线侧、判断相交、求交点、求周长/面积、二维凸包、旋转卡壳、半平面交、闵可夫斯基和、最小圆覆盖、平面最近点对
---


## 向量

- **平面向量基本定理**：如果两个向量 $\boldsymbol{e_1,e_2}$ 不共线，那么存在唯一实数对 $(a,b)$，使得与 $\boldsymbol{e_1,e_2}$ 共面的任意向量  $\boldsymbol{p}$ 满足 $\boldsymbol{p}=a\boldsymbol{e_1}+b\boldsymbol{e_2}$。此时 $\boldsymbol{e_1,e_2}$ 称为基底。

- **数量积**：也称为点积或内积。
	- 定义式：$\boldsymbol{a}·\boldsymbol{b}=|\boldsymbol{a}|·|\boldsymbol{b}|·\cos\langle \boldsymbol{a,b}\rangle$（注意结果是个标量）。
  	- 运算律：满足交换律，对数乘的结合律 和 对加法的分配律。
   - 判定两向量垂直：$\boldsymbol{a} \perp \boldsymbol{b} \Leftrightarrow \boldsymbol{a}·\boldsymbol{b} =0$.（$\cos\langle \boldsymbol{a,b}\rangle=0$）
   - 判定两向量共线：$\boldsymbol{a}//\boldsymbol{b}\Leftrightarrow \boldsymbol{a} = \lambda \boldsymbol{b} \Leftrightarrow \boldsymbol{a}·\boldsymbol{b}=|\boldsymbol{a}|·|\boldsymbol{b}|$.（$\cos\langle \boldsymbol{a,b}\rangle=1$）
   - 数量积坐标运算：$(a,b)·(c,d) = ab+cd$.
  	- 向量的模：$|(a,b)| = \sqrt{a^2+b^2}$.
   - 向量夹角：$\langle \boldsymbol{a},\boldsymbol{b} \rangle = \arccos\dfrac{\boldsymbol{a}·\boldsymbol{b}}{|\boldsymbol{a}|·|\boldsymbol{b}|}$.
   
- **向量积**：也称为叉积或外积。
	- 定义：两向量的向量积 $\boldsymbol{a}\times \boldsymbol{b}$ 仍为一个向量，其模长为 $|\boldsymbol{a}\times \boldsymbol{b}|=|\boldsymbol{a}|·|\boldsymbol{b}|·\sin\langle\boldsymbol{a},\boldsymbol{b}\rangle$，$\boldsymbol{a}\times \boldsymbol{b}$ 与 $\boldsymbol{a},\boldsymbol{b}$ 都垂直，它们满足右手定则。
   - 几何意义：$|\boldsymbol{a}\times\boldsymbol{b}|$ 为向量 $\boldsymbol{a},\boldsymbol{b}$ 围成的平行四边形的有向面积(也就是有正有负)。
   - 运算律：
		- 交换律：$\boldsymbol{a}\times\boldsymbol{b} = -\boldsymbol{b}\times\boldsymbol{a}$。因此计算叉积时 **要特别留意相乘的顺序**。
		- 对数乘的交换律：$(\lambda\boldsymbol{a})\times\boldsymbol{b} = \boldsymbol{a}\times(\lambda\boldsymbol{b})=\lambda(\boldsymbol{a}\times\boldsymbol{b})$.
		- 对加法的分配律：$(\boldsymbol{a}+\boldsymbol{b})\times\boldsymbol{c}=\boldsymbol{a}\times\boldsymbol{c}+\boldsymbol{b}\times\boldsymbol{c}$，$\boldsymbol{c}\times(\boldsymbol{a}+\boldsymbol{b})=\boldsymbol{c}\times\boldsymbol{a}+\boldsymbol{c}\times\boldsymbol{b}$.
   - 坐标表示：$|(a,b)\times(c,d)|=ad-bc$
   - 判定两向量共线：$\boldsymbol{a}//\boldsymbol{b}\Leftrightarrow |\boldsymbol{a} \times \boldsymbol{b}|=0$

- **向量的旋转**：设 $\boldsymbol{a}=(x,y)$，我们记 $l=|\boldsymbol{a}|$，$\alpha$ 为 $\boldsymbol{a}$ 的倾角，那么有 $x=l\cos\alpha,y=l\sin\alpha$。此时我们旋转角度 $\theta$ 得到 

$$\begin{aligned}
\boldsymbol{b}&=(l\cos(\alpha+\theta),l\sin(\alpha+\theta))\\\\
&=(l·(\cos\alpha\cos\theta-\sin\alpha\sin\theta),l·(\cos\alpha\sin\theta+\sin\alpha\cos\theta))\\\\
&=(x\cos\theta-y\sin\theta,x\sin\theta+y\cos\theta)
\end{aligned}
$$

（其实就是转换成极坐标再转换回来）

建议将向量封装为一个 $\text{Vector}$ 类来运算。

## 极坐标与极坐标系

极坐标系和平面直角坐标系是两种不同的位置表示方法。

极坐标系的几大要素：

- **极点**：即这个坐标系的原点 $O$；
- **极轴**：自极点引出一条射线作为始边；
- **单位长度**：在数学问题中通常为 $1$；
- **单位角度**：通常选取弧度制；
- **正方向**：通常选取逆时针方向。

坐标表示：设 $P$ 为平面上一点，那么 $PO$ 的长度即为 **极径**，记为 $\rho$；以极轴为始边，$PO$ 为终边的角 $\angle xOP$ 为 **极角**，记为 $\theta$，那么有序数对 $(\rho,\theta)$ 即为 $P$ 的 **极坐标**。

由终边相同的角的定义可知，$(\rho,\theta+2k\pi)(k\in \mathbb{Z})$ 其实表示的是一样的点，特别地，极点的极坐标为 $(0,\theta)(\theta\in \mathbb R)$。综上，平面内的点的极坐标表示有无数多种。因此我们通常令 $0\le \theta < 2\pi$.

直角坐标 $(x,y)$ 与极坐标 $(\rho,\theta)$ 的转化：

- 直角坐标 $\rightarrow$ 极坐标：$\rho=\sqrt{x^2+y^2},\theta=\arctan \dfrac{y}{x}(x\ne 0)$. 注意特判 $x=0$ 的情况。
- 极坐标 $\rightarrow$ 直角坐标：$x=\rho \cos\theta, y=\rho \sin\theta$.

建议使用 $\texttt{math.h}$ 库中的 $\texttt{atan2(y,x)}$ 函数计算辐角，它可以特判 $x=0$ 的情况。注意该函数返回的值域为 $(-\pi,\pi]$.

## 平面几何若干

### 三种距离

- **欧几里得距离**：两点连线得到的线段的长度。也常被称为 **直线距离**。两点 $A,B$ 的欧几里得距离为 $\sqrt{\sum\limits_{i=1}^n (x_{A,i} - x_{B,i})^2}$.
- **曼哈顿距离**：一点只通过 **与坐标轴平行的直线** 到达另一点的最短路程。两点 $A,B$ 的欧几里得距离为 $\sum\limits_{i=1}^n |x_{A,i} - x_{B,i}|$.
- **切比雪夫距离**：两点在任意坐标维度上的 **最大差值**。两点 $A,B$ 的切比雪夫距离为 $\max\limits_{i=1}^n |x_{A,i} - x_{B,i}|$.

二维平面上与一点距离为定值的性质：

- 与一个点的欧几里得距离为 $D$ 的点形成一个圆，其圆心为该点，半径为 $D$。
- 与一个点的曼哈顿距离为 $D$ 的点形成一个旋转 $45^\circ$ 的正方形，其对角线交点为该点，对角线长度为 $2D$.
- 与一个点的切比雪夫为 $D$ 的点形成一个与坐标轴平行的正方形，其对角线交点为该点，边长长度为 $2D$.
- 三维及以上的几何形状便是高维球体、正 $2^{n-1}$ 面体和正放的高维正方体。


**曼哈顿距离与切比雪夫距离的转化**：

- 曼哈顿 $\rightarrow$ 切比雪夫；$(x,y)\rightarrow(x+y,x-y)$.
- 切比雪夫 $\rightarrow$ 曼哈顿；$(x,y)\rightarrow\left(\frac{x-y}{2},\frac{x+y}{2}\right)$.

相当于把坐标轴旋转了 $45^\circ$.

至于更高维（三维及以上）就没有这样精巧的转化了，比如三维的情况下，曼哈顿距离为定值的点形成了一个由两个正四棱锥底面相拼而成的八面体（考虑 $z$ 坐标从下往上移动得到的截面易得），而切比雪夫形成的是一个正方体。这显然不是旋转坐标系就能转化的。

我们考虑这种转化的实质，其实就是 $|x_i-y_i| = \max(x_i-y_i,-(x_i-y_i))$，即枚举这个值添不添负号。而当有多个坐标的时候，我们暴力枚举所有的情况，即

$$\begin{aligned}
\sum_{i=1}^n |x_i-y_i| & = \sum_{i=1}^n \max \\\{x_i-y_i, y_i-x_i\\\} \\\\
& = \max_{S=0}^{2^n-1} \left(\sum_{i \in S} x_i-y_i + \sum_{i \notin S} y_i-x_i\right)
\end{aligned}$$

我们需要将 $x_i$ 和 $y_i$ 分开，于是我们令

$$f(S,x) = \sum_{i\in S} x_i + \sum_{i\notin S} -x_i$$

则

$$\sum_{i=1}^n |x_i-y_i| = \max_{S=0}^{2^n-1} f(S,x) - f(S,y)$$

这个时候已经和曼哈顿距离很像了，只不过少了个绝对值。因此，我们可以将互为补集的一对去掉一个。因此 $n$ 维的曼哈顿距离可以转化为 $2^{n-1}$ 维的切比雪夫距离。例如三维的情况：

$$\begin{aligned}
x_1 &= a + b + c \\\\
x_2 &= a + b - c \\\\
x_3 &= a - b + c \\\\
x_4 &= a - b - c \\\\
\end{aligned}$$

这样就能实现(单方)的转化。至于切比雪夫距离转回曼哈顿距离，就需要解方程了，注意因为 $n \ge 3$ 的时候这里有多于 $3$ 个方程，所以可能会出现无解的情况。

### 如何记录线段 / 圆

- 线段：记录起点向量 $\boldsymbol{st}$ 和方向向量 $\boldsymbol{dir}$.（若直线则只需记录方向向量）
- 圆：记录圆心 $\boldsymbol{O}$ 和半径 $r$.

### 判断一个点在一条直线的哪一侧

已知向量 $\overrightarrow{AB}$ 和点 $C$，判断点 $C$ 位于有向直线 $AB$ 的哪一侧。

计算二维叉积

$$\overrightarrow{AB} \times \overrightarrow{AC}=(x_B-x_A)(y_C-y_A)-(y_B-y_A)(x_C-x_A)$$

- 若结果 $>0$，则 $C$ 位于 $AB$ 的左侧（逆时针方向）。
- 若结果 $=0$，则 $A,B,C$ 三点共线。
- 若结果 $<0$，则 $C$ 位于 $AB$ 的右侧（顺时针方向）。

### 判断两线段是否相交

记要判断的两条线段为 $AB,CD$。我们分两步判断：

- **快速排斥实验**：令 $AB,CD$ 分别以其为对角线作矩形，若这两个矩形有交集，则「通过」快速排斥实验；
- **跨立实验**：我们判断 $A,B$ 是否分别在 $CD$ 的两侧，$C,D$ 是否分别在 $AD$ 的两侧，如果均满足则「通过」跨立实验。

如果均通过两个实验，可以证明两线段相交。

### 求两直线交点


![](https://cdn.luogu.com.cn/upload/image_hosting/txz1dew3.png)

我们要计算 $AB,CD$ 的交点 $F$ 的具体坐标。此时我们作平行四边形 $ADCE$，平行四边形 $ABIE$，$F$ 为 $AB,CD$ 交点。并作 $AE$ 分别过 $B,F$ 的高 $BH,FG$.

那么有 $S_{\text{平行四边形}ABIE}=-|\overrightarrow{AB}\times\overrightarrow{CD}|,S_{\text{平行四边形}ADCE}=-|\overrightarrow{AD}\times\overrightarrow{CD}|$.

由于这两个平行四边形同底，所以面积比等于对应高比 $\dfrac{FG}{BH}=\dfrac{S_{\text{平行四边形}ADCE}}{S_{\text{平行四边形}ABIE}}=\dfrac{|\overrightarrow{AD}\times\overrightarrow{CD}|}{|\overrightarrow{AB}\times\overrightarrow{CD}|}$。我们记其为 $k$.

可以发现 $\triangle AFG\backsim \triangle ABH$，因而有 $\dfrac{AF}{AB} = \dfrac{FG}{BH}=k$.

因此 $\overrightarrow{AF} = \overrightarrow{AB}·k$.

那么 $F = A + \overrightarrow{AF} = A + \overrightarrow{AB}·k$.

### 求多边形周长和面积

我们将顶点 $P_{1\sim n}$ 按照逆时针排序。

- 周长：就是相邻两点的距离之和

$$C=\sum_{i=1}^n|P_iP_{i\bmod n+1}|$$

- 面积：选定一个点 $P_1$，往其他顶点各发射一条射线，就剖分成了 $(n-2)$ 个三角形。然后依次使用向量积计算这些三角形的面积即可。

$$S=\dfrac{1}{2}\sum_{i=2}^{n-1}|\overrightarrow{P_1P_i}\times\overrightarrow{P_iP_{i+1}}|$$

## 判断一个点是否在凸包内

总体思路：我们将凸包剖分成 $(n-2)$ 个三角形，然后我们快速找到这个点只可能在哪个三角形里面，然后判断一下这个点是否在该三角形内。

我们选定一个顶点 $P_1$，然后将凸包平移至该顶点与原点重合。同时我们也将要询问的点 $Q$ 对应地平移。

然后将剩下 $(n-1)$ 个点 $P_{2\sim n}$ 按照逆时针顺序排列，显然它们的辐角是单调递增的。那么我们就可以根据 $Q$ 的辐角通过二分查找找到它对应的三角形 $\triangle P_1P_iP_{i+1}$。接下来我们直接判断 $Q$ 是否在 $P_iP_{i+1}$ 的内侧即可。

例外地，如果 $Q$ 的辐角小于 $P_2$ 的辐角或者大于 $P_n$ 的辐角，那么我们直接返回 $\texttt{false}$ 即可。

特别提醒，如果使用 $\texttt{atan2(y,x)}$ 计算一个点的辐角，因为这个函数的值域是 $(-\pi,\pi]$，所以如果我们任意地选择一个点作为起始点，那么辐角就可能会出现「断层」的情况。有两种解决办法：

1. 处理辐角：计算完辐角后，从左到右扫描一遍，如果出现断层就令该后缀整体加 $2\pi$.
2. 合理选择起始点：这提示我们应该选择「最靠左上方」的顶点，于是我们先逆时针地计算每一条边的方向向量，找到辐角最小的方向向量的起始点，那么如果我们选择这个起始点，那么辐角就会限制在 $\left[-\pi,\dfrac{\pi}{2}\right]$，不会出现断层。

设凸包大小为 $n$，有 $q$ 次询问，时间复杂度为 $O(n+q\log n)$.

## 二维凸包

- 二维凸包：在平面上能包含所有点的面积&周长均最小的凸多边形。

### Andrew 算法

我们将所有的点按照横坐标为第一关键字，纵坐标为第二关键字对 $P_{1\sim n}$ 进行升序排序。显然，排序后第一个点和最后一个点均会构成上凸壳&下凸壳。

我们先第一步从左往右扫描，求出下凸壳，第二步再从从右往左扫描求出上凸壳。那么上凸壳 + 下凸壳 = 凸包。

下面只讨论求下凸壳的情况，上凸壳的求法是类似的。

现在要假如要加入 $P_i$。设当前栈的栈顶两个元素自上而下分别为 $S_1,S_2$，我们计算 $|\overrightarrow{S_2S_1}\times\overrightarrow{S_1P_i}|$，如果值不为正，那么我们弹出栈顶。重复这样的操作直到叉积为正位置。最后我们把 $P_i$ 加入栈顶。

### Graham 扫描法

我们将所有的点按照极坐标双关键字升序排序，显然第一个元素和最后一个元素必然是凸包内的点。我们从左往右依次加入 $P_i$，然后选取栈顶 $S_1$，若 $|\overrightarrow{OS_1}\times\overrightarrow{S_1P_i}|$，值为负则弹出栈顶值为正为止。

这种算法只需进行一次从左往右的扫描。但是求极角会有点麻烦。还有一个重大缺陷是，我们依次得到的凸包上的点不是顺/逆时针排列的（而是按照极角 - 极径排列），这导致我们只得到了一系列散点，而无法知道凸包到底长什么样子，无法对这个凸包进行进一步的操作。

实战推荐使用 Andrew 算法。

以上两种方法时间复杂度均为 $O(n\log n)$。

## 旋转卡壳

旋转卡壳可以求任意两点距离的最大值。也就是凸包直径。

我们在建出凸包之后，考虑凸包上的每一条边 $P_iP_{i+1}$，我们找到与这一条边距离最远的点 $D$，那么我们检查 $P_iD$ 与 $P_{i+1}D$ 的最大值即可。

由于当边顺时针移动，最远点 $D$ 也在顺时针移动，因此可以直接从上一次的最远点开始遍历。

## 半平面交

- 左半平面：对于一个非零向量 $\boldsymbol a$，以 $\boldsymbol a$ 的起点为原点，将 $\boldsymbol a$ 视为一条有向直线，其左半平面定义为所有满足  $\boldsymbol a \times \boldsymbol x > 0$ 的向量 $\boldsymbol x$ 所在的集合。
- 右半平面：类似地，$\boldsymbol a$ 的右半平面定义为所有满足 $\boldsymbol a \times \boldsymbol x < 0$ 的向量 $\boldsymbol x$ 所在的集合。
- 半平面交：给定若干向量及其对应的左（或右）半平面，求这些半平面的交集。若交集非空，则该交集为一个凸集（在二维情形下为一个凸多边形或无界凸区域）。

如何记录不在起点不在源点的向量：直接记录起始点(也是个向量) $\boldsymbol{st}$ 和方向向量 $\boldsymbol{dir}$ 即可。

- $(\boldsymbol{st},\boldsymbol{dir})$ 的左半平面 $=$ $(\boldsymbol{st},-\boldsymbol{dir})$ 的右半平面。

我们将所有的向量按照方向向量的极角进行排序。

我们要先考虑极角相等的向量，此时它们的半平面是包含与被包含的关系，显然我们只考虑被包含的最小的半平面，这是容易检查的。

然后将它们依次加入。我们用一个 **双端队列** 来维护当前的凸包。同时，如果当前凸包的向量超过两个 ，它们就会出现交点。为了方便，我们同时记录相邻两个向量的交点。

当我们要加入一个向量的时候，我们先检查队尾的交点是否在该向量对应的半平面里面，如果不在，那么就说明这个交点已经失去作用，我们弹出队尾。

因为可能快要结束的时候，队尾的向量会对队首的交点产生影响，所以我们应再用同样的方法检查队首元素。

最后，我们检查队首是否会让队尾的交点失效。因为队尾没有受到队首的限制，我们需要检查一遍才能保证正确性。

如何判断交为空，我们在最后检查相邻的两个向量的方向向量的极角之差是否 $\ge \pi$。因为凸包的各个内角都小于 $180^\circ$，如果超过了就说明凸包不存在。

时间复杂度为 $O(n\log n)$.

## 闵科夫斯基和

- 闵科夫斯基和 (Mincowski Addition)：对于两个凸包 $A,B$，它们的闵科夫斯基和为一个集合 $S=\\\{p+q \mid p\in A,q\in B\\\}$，其中加法 $p+q$ 定义为向量加法。

![](https://cdn.luogu.com.cn/upload/image_hosting/jl317by2.png)

可以发现，闵科夫斯基和的边均由原凸包的边平移得到。

于是我们将两个凸包的边的方向向量拎出来按照辐角升序做一个归并排序即可。

注意可能会有两条边共线（辐角相等）的情况。大多数情况下，如果不影响题目，我们可以不用理会它。要把它消除也很简单，合并时判断一下，如果相邻两边共线，就把两边对应的方向向量加起来合并为一个即可。

剩下的问题是，起点是什么？

事实上，我们直接在各个凸包中任选一个起点，然后闵科夫斯基和凸包的起点就是它们的和。

时间复杂度为 $O(n)$.

## 最小圆覆盖（随机增量法）

- 最小圆覆盖：给定 $n$ 个点，求半径最小的圆使得所有的点均在圆内。

考虑维护前 $i$ 个点的最小圆覆盖 $C$。我们执行这样的步骤：

- 遍历 $i\in [1,n]$，判断 $P_i$ 是否在圆 $C$ 内。
	- 如果 $P_i$ 在圆 $C$ 内，那么跳过；
   - 如果 $P_i$ 不在圆 $C$ 内，那么 $P_i$ **必然在前 $i$ 个点的最小圆覆盖上**。我们设置 $C=(P_i,0)$，并执行：
		- 遍历 $j\in [1,i)$，判断 $P_i$ 是否在圆 $C$ 内。
			- 如果 $P_j$ 在圆 $C$ 内，那么跳过；
			- 如果 $P_j$ 不在圆 $C$ 内，我们令 $C$ 为以 $P_iP_j$ 为直径的圆，并执行：
				- 遍历 $k\in [1,j)$，仍然判断 $P_k$ 是否在 $C$ 内。如果不在，我们令我们令 $C$ 为过 $P_i,P_j,P_k$ 三点的圆。

如何计算三点共圆：假设这三点为 $A,B,C$，我们按照尺规作图的方法，一步步计算。

- 作 $AB,BC$ 的中点 $M_1,M_2$：令 $M_1=\dfrac{A+B}{2},M_2=\dfrac{B+C}{2}$。
- 过 $M_1,M_2$ 分别作 $AB,BC$ 的垂线 $H_1,H_2$，显然起点向量分别为 $M_1,M_2$，方向向量为 $\overrightarrow{AB},\overrightarrow{BC}$ 旋转 $90^\circ$，即 $(x,y)\rightarrow(-y,x)$.
- 求 $H_1,H_2$ 的交点 $O$：求直线交点参见前文。

时间复杂度：我们发现这 $n$ 个点中只有 $3$ 个点会对答案产生贡献，那么每个点为时间复杂度贡献的概率为 $\dfrac{3}{n}$。

- 第一层循环的期望复杂度 $T_1(n)=T_1(n-1)+\dfrac{3}{n}T_2(n)$.
- 第二层循环的期望复杂度 $T_2(n)=T_2(n-1)+\dfrac{3}{n}T_3(n)$.
- 第三层循环的期望复杂度 $T_3(n)=O(n)$.

容易计算出 $T_1(n)=T_2(n)=T_3(n)=O(n)$.。

建议求最小圆覆盖前将点集 $\texttt{random\_shuffle}$ 一下。

- 随机增量法的形式为 $T(n)=T(n-1)+P(n)·g(n)$，即每个元素 $i$ 有 $P(i)$ 的概率贡献 $g(i)$ 的复杂度，我们常常通过随机的方法避免最坏情况。

## 平面最近点对

### 分治做法

我们先将所有的点按照 **横坐标为第一关键字，纵坐标为第二关键字** 进行升序排序。

考虑分治，我们以 $p_{mid}$ 为界，计算 $p_{1\sim mid}$ 和 $p_{mid+1\sim r}$ 的最近点对的距离，然后取它们的最小值，我们记为 $\rm minDis$.

然后，我们以 $x_{mid}$ 为界将平面分成两部分，显然 $p_{1\sim mid}$ 在左半平面，$p_{mid+1\sim r}$ 在右半平面。那么我们现在需要计算的就是一点在左半平面，另一点在右半平面的距离最小值。

那么显然这些点均与直线 $x=x_{mid}$ 的距离 $< \rm minDis$，否则距离就不可能比 $\rm minDis$ 还要更小。因此，我们将所有与横坐标 $x_{mid}$ 之差的绝对值 $< \rm minDis$ 放进一个集合里，记其为 $B$.

对于集合内的所有点，我们将它们按照 **纵坐标为第一关键字，横坐标为第二关键字** 进行升序排序。对于所有 $p_i \in B$，我们再取 $B$ 集合内所有纵坐标与 $y_i$ 的差 $< \rm minDis$ 的 $p_i$。换句话说，我们要构建出一个新的点集 $C(i)$，将所有 $p_j \in B$ 满足 $y_i-y_j<\rm minDis$ 放进这个集合里面。然后，我们遍历 $C(i)$ 内所有的点，检查它们与 $p_i$ 的距离最小值并更新答案。

可以证明， $C(i)$ 的大小不超过 $7$。

- 可以发现，$C(i)$ 内的点它们都在 $(x_{mid},y_i)$ 分别往左下和右下作一个边长为 $\rm minDis$ 的正方形内。这两个正方形刚好一个在左半平面，一个在右半平面。因此这两个正方形内的点的两点最小距离 $\ge \rm minDis$，那么一个正方形最多可以容纳多少个点呢？

- 我们将每个正方形横竖对半划分成 $4$ 个边长为 $\dfrac{1}{2} \rm minDis$ 的小正方形。显然每个正方形内的最远距离为对角线长度 $\dfrac{\sqrt 2}{2} \rm minDis<\rm minDis$，因此每个小正方形最多只会有 $1$ 个点。

- 因此最坏情况下，每个小正方形均有 $1$ 个点，除去 $p_i$ 后只剩下 $7$ 个点，也就是说 $C(i)$ 的大小不超过 $7$。

在实现的时候，其实我们不需要每次都对点集再排一遍序，我们一开始先按照横坐标第一关键字排序，在分治的时候，我们顺带进行纵坐标第一关键字的归并排序即可，这样就可以做到时间复杂度 $T(n)=2T\left(\dfrac{n}{2}\right)+O(n)=O(n\log n)$.

### 非分治做法

其实这是由分治做法演变而来的。

我们还是一开始将所有点按照横坐标第一关键字，纵坐标第二关键字排序。

现在我们已经得到了前 $(i-1)$ 个点的最近点对距离 $\rm minDis$，现在我们还是把与 $p_i$ 的横坐标距离 $< \rm minDis$，纵坐标距离 $< \rm minDis$ 拎出来放到集合里，然后再检查 $p_i$ 与集合内所有点的距离最小值。仍然可以用类似方法证明集合大小是线性的。

如何把满足条件的点拎出来？我们用 $\texttt{set}$ 将维护纵坐标第一关键字升序排序。

- 每次将 $p_i$ 放入 $\texttt{set}$ 内。
- 因为我们要找到与 $y_i$ 之差的绝对值 $<\rm minDis$ 的点，所以我们倒序遍历容器中的每一个 $p_j$，直至 $y_i-y_j\ge \rm minDis$ 即可。
- 注意，如果遍历到有 $x_i-x_j\ge \rm minDis$，我们直接把它们弹出，因为它们一定不会被后面的点所贡献。

时间复杂度为 $O(n\log n)$.

### 随机增量法

我们现在已经把 $(i-1)$ 个点的最近点对距离 $\rm minDis$ 算出来了，现在要计算 $p_i$ 与前 $(i-1)$ 个点的最近点对距离。

我们将所有的点按照 $\rm minDis$ 为边长的正方形网格图划分为若干个部分。对于 $p_i$，我们就将 $p_i$ 与它所在的网格相邻的 $9$ 个网格内的点均检查一遍最小值。

如果最小值发生了变化，我们就重构一遍网格。

因为每个点对最近点对的贡献概率 $P(i)=\dfrac{2}{i}$，而重构一次的复杂度为 $O(i)$，因此总时间复杂度为 $T(n) = T(n-1)+\dfrac{2}{n}·O(n) = O(n)$.

建议一开始前随机打乱点集。


> References: [好文章1](https://zuytong.blog.luogu.org/ji-suan-ji-he) / [好文章2](https://www.luogu.com.cn/blog/six-z/computation-geometry) / [好文章3](https://www.luogu.com.cn/blog/klii/ji-suan-ji-he-ru-men) / [好文章4](https://www.luogu.com.cn/blog/command-block/ji-suan-ji-he-suan-fa-hui-zong) / [好文章 5](https://www.cnblogs.com/xzyxzy/p/10033130.html) / [OI wiki 1](https://oi-wiki.org/math/vector/) / [OI wiki 2](https://oi-wiki.org/geometry/)
