---
title: 电路基础 | Week 4 运算放大器
date: 2026-03-24
summary: 运算放大器、反向放大器、同向放大器、加法放大器、差分放大器、运算放大器的级联
---

# 5.2  运算放大器

**运算放大器**：一种用于执行加减乘除、微积分的有源电路器件。

通常采用 8 脚双列直插封装（DIP）。

![](attachments/Pasted%20image%2020260324081304.png)

![](attachments/Pasted%20image%2020260324084153.png)

# 5.3 理想运算放大器

理想运算放大器的特点：
- 开环增益无穷大：$A \approx \infty$
- 输入电阻无穷大：$R_i \approx \infty$
- 输出电阻为零：$R_o \approx 0$

理想运算放大器的重要性质：
- 输入电流都为零：$i_1 = i_2  = 0$
- 输入端电压差为零：$v_d = v_2 - v_1 = 0$

![](attachments/Pasted%20image%2020260327143343.png)

# 5.4 反向放大器

在这里对于节点 $1$ 有 $$\frac{- v_i}{R_1} + \frac{- v_o}{R_f} = 0 \quad \Rightarrow \quad v_o = - \frac{R_f}{R_1}v_i$$
反向放大器对于输入信号放大的同时对极性也进行了翻转。
![](attachments/Pasted%20image%2020260327143525.png)

# 5.5 同相放大器

对于 $v_1$ 处有 $$\frac{v_i}{R_1} + \frac{v_i-v_o}{R_f} = 0 \quad\Rightarrow\quad v_o = \left(1 + \frac{R_f}{R_1}\right)v_i$$

同相放大器为输入信号提供了正电压增益。

![](attachments/Pasted%20image%2020260327143909.png)

# 5.6 加法放大器

对于节点 $a$ 处有 $$\frac{-v_1}{R_1} + \frac{-v_2}{R_2} + \frac{-v_3}{R_3} + \frac{-v_0}{R_f} = 0 \quad\Rightarrow\quad v_0 = - \left( \frac{R_f}{R_1}v_1 + \frac{R_f}{R_2}v_2 + \frac{R_f}{R_3} v_3 \right)$$
加法放大器可以将多个输入合并，产生这些输入的加权和。
![](attachments/Pasted%20image%2020260327144610.png)

# 5.7 差分放大器

对于节点 $a,b$ 处有 $$\begin{cases} \displaystyle \frac{v-v_1}{R_1} + \frac{v-v_0}{R_2} = 0 \\\\ \displaystyle \frac{v-v_2}{R_3} + \frac{v}{R_4} = 0\end{cases}$$
解得 $$v_o = \frac{R_2(1 + R_1/R_2)}{R_1 (1 + R_3/R_4)} v_2 - \frac{R_2}{R_1} v_1$$

差分放大器对两个输入信号的差值进行放大并并抑制了共模信号。

![](attachments/Pasted%20image%2020260327145343.png)
# 5.8 运算放大器的级联电路

级联是指多个运算放大器按照首尾顺序相连，使得前一级的输出是下一级的输入，那么总增益是各个放大器的增益的乘积。

![](attachments/Pasted%20image%2020260327151800.png)


# Conclusion

![](attachments/Pasted%20image%2020260327151850.png)
![](attachments/Pasted%20image%2020260327151904.png)