---
layout: post
title: 统计物理
permalink: /physics/sda
usemathjax: true
---

# 第一章 随机变量

### 累积分布函数

观测值小于等于x的概率

---

$$
\begin{align}
	F(x) &= \sum_{xi \le x} P(x_i) & \text{离散}
	\\
	F(x) &= \int_{-\infin}^x f(x\prime)dx\prime & \text{连续}
\end{align}
$$

---



### 分位数

使$F(x) = \alpha$的x，或者说$x = F^{-1}(\alpha)$



### 联合概率密度分布函数

---

$$
\iiint f(x, y) dx dy = 1
$$

---

$$
f_x(x) = \int f(x, y) dy = \int g(x | y)f_y(y) dy
$$

---

上面这个函数称为边缘概率密度函数，显然这个函数在有两个变量的情况下只考虑一个变量



# 第二章 常用分布

## 2.1 二项/多项分布

要么成功，要么失败

N次试验中成功n次概率、期待值、方差

---

$$
\begin{align}
	f(n; N, p) &= \mathrm{C}^n_{N} p^n (1-p)^{N-n}
	\\
	E[n] &= Np
	\\
	V[n] &= Np(1 - p)
\end{align}
$$

---

多项分布，每一次实验的结果不止两个，每一个结果对应一个p，显然

---

$$
\sum_i p_i = 1
$$

---

若有N次实验，每一次试验产生一个结果，试验完成后，第一个可能结果有n1次出现，第二个有n2个，显然

---

$$
\begin{align}
	\sum_i n_i &= N
	\\
	f(n_1, ..., n_m; N; p_1, ..., p_m) &= \frac{N!}{n_1!n_2!...n_m!}p_1^{n_1}...p_m^{n_m} 
\end{align}
$$

---

如果这样思考：第i个事件发生了即为成功，没有发生（发生了其他的事件）则为失败，这不就是个二项分布吗，所以第i个事件的期望和方差同上面的二项分布



## 2.2 泊松分布

在二项分布的极限情况，即N很大p很小，Np为一个有限值，二项分布近似为泊松分布

---

$$
\begin{align}
	f(n;\nu) &= \frac{\nu^n}{n!} e^{-\nu}
	\\
	E[n] &= \nu
	\\
	V[n] &= \nu
\end{align}
$$

---

**若$\nu$很大，则泊松分布可以近似为高斯分布**



## 2.3 均匀分布

---

$$
\begin{align}
	f(x; \alpha, \beta) &= \begin{cases} \frac{1}{\beta - \alpha} & \alpha \le x \le \beta 
	\\ 0 & otherwise
	\end{cases}
	
	\\
	E[x] &= \frac{1}{2} (\alpha + \beta)
    \\
    V[x] &= \frac{1}{12} (\beta - \alpha)^2
\end{align}
$$

---



## 2.4 指数分布

---

$$
\begin{align}
	f(x; \alpha, \beta) &= \frac{1}{\xi}e^{-x / \xi}
	\\
	E[x] &= \xi
	\\
	V[x] &= \xi^2
\end{align}
$$

---



## 2.5 高斯分布

---

$$
\begin{align}
	f(x; \mu, \sigma^2) &= \frac{1}{\sqrt{2 \pi \sigma^2}}\exp(-\frac{(x - \mu)^2}{2 \sigma^2})
	\\
	E[x] &= \mu
	\\
	V[x] &= \sigma^2
\end{align}
$$

---

一个小定理:

---

$$
y \sim N(\mu, \sigma^2)
\Rightarrow
x = \frac{y - \mu}{\sigma} \sim N(0, 1)
$$

---

### 中心极限定理

如果n个**独立连续**随机变量，$\mu_i, \sigma^2_i$，**没有说他们是什么分布**，他们的和满足$\mu = \sum_i \mu_i, \sigma^2 = \sum_i \sigma^2_i$的高斯分布。



## 2.6 卡方分布

函数形式不想写

---

$$
\begin{align}
	E[z] &= n
	\\
	V[z] &= 2n
\end{align}
$$

---

上面的n是自由度，若$x_i \sim N(0, 1)$，则$\sum_ix_i^2$满足自由度为N的卡方分布。所以拟合的卡方每自由度最好是1



# 第三章 蒙卡方法

## 3.2 变量变换法





# 第四章 统计检验
