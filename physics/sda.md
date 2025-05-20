---
layout: post
title: 统计物理
permalink: /physics/sda
usemathjax: true
---

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





# 第三章 蒙卡方法

# 第四章 统计检验
