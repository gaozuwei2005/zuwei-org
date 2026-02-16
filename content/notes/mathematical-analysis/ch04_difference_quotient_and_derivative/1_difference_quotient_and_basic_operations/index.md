---
title: 数学分析 | 4.1 微商概念及其运算
date: 2024-12-02
summary: 微商的计算、基本初等函数的微商公式
---

## 微商的计算

> **定理 4.3（反函数的微商）**：若函数 $y = f(x)$，在 $x_0$ 附近连续且严格单调，且 $f'(x_0) \ne 0$，则其反函数 $x = \varphi(y)$ 在 $y_0 = f(x_0)$ 处可导，且
>
> $$\varphi'(y_0) = \frac{1}{f'(x_0)}$$
>
> **证明**：由于函数 $y = f(x)$，在 $x_0$ 附近连续且严格单调，因此反函数 $x = \varphi(y)$ 在 $y_0$ 处附近连续且严格单调。
> 
> 因此，在 $y_0$ 附近，若 $y - y_0 \ne 0$，那么 $x - x_0 = \varphi(y) - \varphi(y_0) \ne 0$，且 $y \rightarrow y_0$ 时 $x \rightarrow x_0$。
>
> 由复合函数求极限法则，可得
>
> $$\begin{aligned}
& \lim_{y \to y_0} \frac{\varphi(y) - \varphi(y_0)}{y - y_0} \\\\
=& \lim_{y \to y_0} \frac{\varphi(y) - \varphi(y_0)}{f(\varphi(y)) - f(\varphi(y_0))} \\\\
=& \lim_{x \to x_0} \frac{x - x_0}{f(x) - f(x_0)} \\\\
=& \frac{1}{f'(x_0)}
\end{aligned}$$

## 基本初等函数的微商公式（重点记忆）

1. 常数函数：$(c)' = 0$
2. 幂函数：$(x^n)' = nx^{n - 1}$，$\left(\dfrac{1}{x}\right)' = -\dfrac{1}{x^2}$, $(\sqrt{x})' = \dfrac{1}{2\sqrt x}$
3. 指数函数：$(a^x)' = a^x \ln a$，$(e^x)' = e^x$
4. 对数函数：$(\log_a x)' = \dfrac{1}{x \ln a}$，$(\ln x)' = \dfrac{1}{x}$
5. 三角函数：
   
   正弦 (sine) $\sin\theta = \dfrac{y}{r}$，余弦 (cosine) $\cos\theta = \dfrac{x}{r}$，
   
   正切 (tangent) $\tan\theta = \dfrac{y}{x}$ 和余切 (cotangent) $\cot\theta = \dfrac{x}{y}$，

   正割 (secant) $\sec\theta = \dfrac{r}{x}$ 和余割 (cosecant) $\csc\theta = \dfrac{r}{y}$

   **记忆方法**：
   
   - 正切和余切互为倒数：$\cot \theta = \dfrac{1}{\tan \theta}$ （正余切）

   - 正弦和余割互为倒数：$\csc \theta = \dfrac{1}{\sin \theta}$ （一个有 "co"，另一个就不能有 "co"）

   - 余弦和正割互为倒数：$\sec \theta = \dfrac{1}{\cos \theta}$ （一个有 "co"，另一个就不能有 "co"）
   
   $(\sin x)' = \cos x$
   
   $(\cos x)' = - \sin x$，

   **记忆方法**：正弦导数变余弦，余弦导数变负正弦
   
   $(\tan x)' = \left(\dfrac{\sin x}{\cos x}\right)' = \dfrac{\cos^2 x + \sin^2 x}{\cos^2 x} = \dfrac{1}{\cos^2 x} = \sec^2 x$

   $(\cot x)' = \left(\dfrac{1}{\tan x}\right)' = - \dfrac{1}{\tan^2 x·\cos^2 x} = - \dfrac{1}{\sin^2 x} = -\csc^2 x$

   **记忆方法**：切的导数是割的平方，且 "co" 同时出现或不出现。"co" 出现的时候要带负号。

   正切导数是正割平方，余切导数是负余割平方。

   $(\sec x)' = \left(\dfrac{1}{\cos x}\right)' = - \dfrac{- \sin x}{\cos^2 x} = \tan x \sec x$

   $(\csc x)' = \left(\dfrac{1}{\sin x}\right)' = - \dfrac{\cos x}{\sin^2 x} = - \cot x \csc x$

   **记忆方法**：割的导数变多一个切，且 "co" 同时出现或不出现。"co" 出现的时候要带负号。

   正割导数是正切正割，余割导数是负余切余割。


6. 反三角函数：

    $\begin{aligned}(\arcsin y)' = \dfrac{1}{(\sin x)'} =\dfrac{1}{\cos x} = \dfrac{1}{\sqrt{1 - \sin^2 x}} = \dfrac{1}{\sqrt{1 - y^2}}\ \left( -\dfrac{\pi}{2} < x < \dfrac{\pi}{2}, -1 < y < 1 \right)\end{aligned}$

    $\begin{aligned}(\arccos y)' = \dfrac{1}{(\cos x)'} = -\dfrac{1}{\sin x} = - \dfrac{1}{\sqrt{1 - \cos^2 x}} = - \dfrac{1}{\sqrt{1 - y^2}}, \ \left( 0 < x < \pi, -1 < y < 1 \right)\end{aligned}$

    **记忆方法**：反正余弦函数的导数都是 $\dfrac{1}{\sqrt{1 - y^2}}$ 的形式（联想 $|y| < 1$），反余弦函数会多一个符号。

    $\begin{aligned}(\arctan y)' = \dfrac{1}{(\tan x)'} = \cos^2 x = \dfrac{\cos^2 x}{\sin^2 x + \cos^2 x} = \dfrac{1}{1 + \tan^2 x} = \dfrac{1}{1 + y ^2},\ \left(-\dfrac{\pi}{2} < x < \dfrac{\pi}{2}, -\infty < y < \infty\right)\end{aligned}$

    $$\begin{aligned}(\operatorname{arccot} y)' &= \dfrac{1}{(\cot x)'} = -\sin^2 x = - \dfrac{\sin^2 x}{\sin^2 x + \cos^2 x} \\\\
    &= - \dfrac{1}{1 + \cot^2 x} = - \dfrac{1}{1 + y^2},\ \left( 0 < x < \pi, -\infty < y < \infty  \right)\end{aligned}$$

    **记忆方法**：反正余切函数的导数都是 $\dfrac{1}{1 + y^2}$ 的形式（联想 $y \in \mathbb R$），不过反余切函数会多一个符号。

    $$\begin{aligned}(\operatorname{arcsec} y)' &= \dfrac{1}{(\sec x)'} = \dfrac{\cos^2 x}{\sin x} = \dfrac{\cos^2 x}{\sqrt{1 - \cos^2 x}} \\\\
    &= \dfrac{1}{\sec^2 x\sqrt{1 - \dfrac{1}{\sec^2 x}}} = \dfrac{1}{|\sec x| \sqrt{\sec^2 x - 1}} = \dfrac{1}{|y|\sqrt{y^2 - 1}},\ \left( 0 < x < \dfrac{\pi}{2}\  或\  \dfrac{\pi}{2} < x < \pi, |y| > 1 \right)\end{aligned}$$

    $$\begin{aligned}(\operatorname{arccsc} y)' &= \dfrac{1}{(\csc x)'} = - \dfrac{\sin^2 x}{\cos x} = - \dfrac{\sin^2 x}{\sqrt{1 - \sin^2 x}} \\\\
    &= - \dfrac{1}{\csc^2 x\sqrt{1 - \dfrac{1}{\csc^2 x}}} = -\dfrac{1}{|\csc x| \sqrt{\csc^2 x - 1}} = -\dfrac{1}{|y|\sqrt{y^2 - 1}},\ \left( 0 < |x| < \dfrac{\pi}{2}, |y| > 1 \right)\end{aligned}$$

    **记忆方法**：反正余割函数的导数都是 $\dfrac{1}{|y|\sqrt{y^ 2  - 1}}$ 的形式（有点特别，联想 $|y| > 1$），不过反余切函数要多一个负号。