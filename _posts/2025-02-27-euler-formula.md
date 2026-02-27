---
layout: post
title: "欧拉公式的证明"
date: 2025-02-27 14:30:00 +0800
tags: [复分析, 欧拉公式]
author: dxww
---

欧拉公式是复分析中最优美的结果之一：

$$
e^{i\theta} = \cos\theta + i\sin\theta
$$

当 $\theta = \pi$ 时，我们得到著名的欧拉恒等式：

$$
e^{i\pi} + 1 = 0
$$

## 泰勒级数证明

### 指数函数的泰勒展开

$$
e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

### 正弦和余弦的泰勒展开

$$
\sin x = \sum_{n=0}^{\infty} (-1)^n \frac{x^{2n+1}}{(2n+1)!} = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots
$$

$$
\cos x = \sum_{n=0}^{\infty} (-1)^n \frac{x^{2n}}{(2n)!} = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots
$$

### 代入 $x = i\theta$

将 $x = i\theta$ 代入指数函数的泰勒展开：

$$
e^{i\theta} = 1 + i\theta + \frac{(i\theta)^2}{2!} + \frac{(i\theta)^3}{3!} + \frac{(i\theta)^4}{4!} + \cdots
$$

利用 $i^2 = -1$，$i^3 = -i$，$i^4 = 1$ 等关系：

$$
e^{i\theta} = 1 + i\theta - \frac{\theta^2}{2!} - i\frac{\theta^3}{3!} + \frac{\theta^4}{4!} + \cdots
$$

将实部和虚部分开：

$$
e^{i\theta} = \left(1 - \frac{\theta^2}{2!} + \frac{\theta^4}{4!} - \cdots\right) + i\left(\theta - \frac{\theta^3}{3!} + \frac{\theta^5}{5!} - \cdots\right)
$$

这正是：

$$
e^{i\theta} = \cos\theta + i\sin\theta
$$

证毕！∎

## 几何解释

从几何角度看，$e^{i\theta}$ 表示复平面上单位圆上角度为 $\theta$ 的点。

$$
z = e^{i\theta} = \cos\theta + i\sin\theta
$$

其中：
- 实部 $\text{Re}(z) = \cos\theta$
- 虚部 $\text{Im}(z) = \sin\theta$  
- 模 $|z| = \sqrt{\cos^2\theta + \sin^2\theta} = 1$
