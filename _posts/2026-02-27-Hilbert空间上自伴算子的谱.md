---
layout: post
title: "Hilbert空间上自伴算子的谱"
date: 2026-02-27
tags: [Hilbert空间, 自伴算子, 谱]
author: dxww
---

今天和室友讨论了一个题目, 证明Hilbert空间上自伴算子的谱都是实的, 感觉有些地方需要记录一下, 以免忘了. 这篇笔记将会充满跳步, 只是为了自己能看懂. 

以下我们假设$H$是复Hilbert空间, $T\in B(H)$是自伴的. 

**命题1.** 则$\forall\lambda\in\mathbb{C}$, $\forall x\in H$, 我们有
$$\|(\lambda I-T)x\|\ge|\mathrm{Im}\lambda|\|x\|$$
**证明.** 首先$\langle(\lambda I-T)x,x\rangle-\langle x,(\lambda I-T)x\rangle=2i\mathrm{Im}\lambda\cdot\|x\|^2$, 两边取模有$2|\mathrm{Im\lambda}|\|x\|^2\le2\|x\|\|(\lambda I-T)x\|$, 即证. $\rule{3mm}{3mm}$

**命题2.** 设$\mathrm{Im}\lambda\ne0$, 则$\mathrm{im}(\lambda I-T)$是闭的. 
**证明.** 由命题1可以证明(自己取Cauchy列搞一搞). $\rule{3mm}{3mm}$

我们再注意到一些事实(这应当成已封装好的东西记在脑子里, 视为熟知的事实), 即对任何$A\in B(H)$, 成立着$(\mathrm{im}A)^\perp=\ker A^*$. 当$A$是闭值域算子时, 由于Hilbert空间有正交分解定理(见另一篇笔记《Riesz表示定理与Lax-Milgram定理》), 再加上闭值域定理, 我们知道$H=\ker A\oplus\mathrm{im}A^*=\ker A^*\oplus\mathrm{im}A$. 由此可见, 一个算子的值域是不是闭的有一定的重要性. 

**命题3.** $\sigma(T)\subset\mathbb{R}$. 
**证明.** 任取$\lambda\in\sigma(T)$, 如果$\lambda\in\sigma_p(T)$, 即$\lambda I-T$不是单的, 那显然. 所以我们只需考虑$\lambda\in\sigma(T)\setminus\sigma_p(T)$, 即$\lambda I-T$是单的, 此时它必然不是满的. 由之前的讨论我们知道$\ker(\lambda I-T)^*=\ker(\overline\lambda I-T)\ne\{0\}$, 故$\overline\lambda\in\sigma_p(T)$, 故$\overline\lambda$是实的. $\rule{3mm}{3mm}$