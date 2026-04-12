---
title: 代数结构 | Week 2 整数、高斯整数
date: 2026-03-13
summary: 整数及其剩余类、高斯整数及其剩余类
---

# 整数及其剩余类

关于整数、带余除法、模加与模乘运算，在中学已经非常透彻地学习过，此处不再赘述。

**贝祖定理**：$\forall a, b \in  \mathbb Z$，则 $\exists s, t \in Z$ 使得 $as + bt = (a, b)$
- 推论：$(a, b) = 1\Leftrightarrow \exists s, t,\  as + bt = 1$
- 推论：$ax \equiv 1 \pmod m \  \Leftrightarrow (a, m) =1$
- $\displaystyle by + \left( a - b\left\lfloor\frac{a}{b}\right\rfloor\right)x = 1 \  \Leftrightarrow \  ax + b \left(y - \left\lfloor\frac{a}{b}\right\rfloor x\right) = 1$

# 高斯整数及其剩余类

**高斯整数**：形如 $a + b\mathrm i$ 的复数，其中 $a, b \in \mathbb Z$，记作
$$\mathbb Z[i] = \\\{a +b \mathrm i \mid a , b \in \mathbb Z\\\}$$

**共轭高斯整数**：$a + b\mathrm i$ 和 $a - b\mathrm i$ 互为共轭高斯整数，通常用 $\alpha,\  \overline{\alpha}$ 来互称

**高斯整数的模 / 范数**：$\mathcal N(\alpha) = \alpha \overline{\alpha} = a^2 + b^2$

高斯整数对于加、减、乘法封闭，但对除法不封闭（因为可能使实部与虚部变为有理数）。

**高斯整除**：对于 $\alpha ,\beta \in \mathbb Z[\mathrm i]$，若 $\exists \gamma \in \mathbb Z[\mathrm i],\  \alpha = \beta \gamma$，则 $\beta \mid \alpha$，否则 $\beta \not \mid \alpha$.

**高斯整除的性质**：
- $\alpha \beta = 0 \ \Leftrightarrow \  \alpha = 0 \text{ or } \beta = 0$
- 逆元：只有 $\pm 1$ 和 $\pm \mathrm i$ 存在在 $\mathbb Z[\mathrm i]$ 下的乘法逆元
	- $0$ 是任意高斯整数的倍数，$\pm 1,\  \pm \mathrm i$ 是任意高斯整数的因子（称平凡因子）
	- 若 $\alpha = u \beta,\  u \in \\\{\pm 1, \pm \mathrm i\\\}$，则 $\alpha$ 与 $\beta$ *相伴*，一者是另一者的 *伴元*，记作 $\alpha \sim \beta$
	- 因子仅有平凡因子的高斯整数成为 *素元*，非平凡因子称为 *真因子*
- 自反性：$\alpha \mid \alpha$
- 传递性：$\alpha \mid \beta,\  \beta \mid \gamma \Rightarrow \alpha \mid \gamma$
- 广义反对称性：$\alpha \mid \beta,\  \beta \mid \alpha \Leftrightarrow \alpha \sim \beta$
- 线性性：$\gamma \mid \alpha,\  \gamma \mid \beta \Rightarrow \forall \theta,\phi \in \mathbb Z,\  \gamma \mid (\alpha \theta + \beta \phi)$
- $\forall \gamma \ne 0\  \alpha \mid \beta \Leftrightarrow \alpha \gamma \mid \beta \gamma$
- 整除与范数：若 $\alpha \mid \beta$ 则 $\mathcal N(\alpha) \mid \mathcal N(\beta)$.

**带余数除法**：对于高斯整数 $\alpha,\  \beta\ (\beta \ne 0)$，则 $\exists \gamma,\theta$，其中 $0 \le \mathcal N(\theta) < \mathcal N(\beta)$ 使得 $\alpha = \gamma \beta + \theta$