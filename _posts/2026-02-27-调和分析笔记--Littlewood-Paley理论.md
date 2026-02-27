---
layout: post
title: "调和分析笔记--Littlewood-Paley理论"
date: 2026-02-27 10:00:00 +0800
tags: [调和分析, Littlewood-Paley, 傅里叶分析]
author: dxww
---

最近看调和分析看得头痛, 为了整理思路, 也为了方便别人, 我把看书(主要是张晓轶的Lecture Notes on the Basic Analysis Tools for Critical Dispersive PDEs)遇到的gap都填上, 写成这篇笔记. 这篇笔记过去长时间处于未完成/低质量状态, 这次决心把坑填好. 

首先我们需要紧支光滑函数来实现频率的局部化, 比方说如果$\phi\in C_c^\infty(U)$, 那么$(\phi \widehat f)^\vee$的频率(即它的Fourier变换)就被限制在了$U$内. 

取函数$\phi\in C^\infty_c(\mathbb{R}^d)$, 满足以下条件: 
(1)$0\le\phi\le1$, 
(2)在$B_1(0)$上$\phi\equiv1$, 且$\operatorname{supp}\phi\subset\{|x|\le2\}$, 
(3)$\phi$是径向函数, 且关于$|x|$递减. 

这样的$\phi$是存在的, 但是这里我们不讨论它的存在性(可以磨光$\chi_{B_{3/2}(0)}$得到, 磨光函数可见Evans偏微分方程第五章). **$\phi$取好后就固定, 并且在这篇文章里我们把字母$\phi$特别地留给这个函数, 而不做它用.**

定义$\psi(x)=\phi(x)-\phi(2x)$, 则首先容易检验$\psi$有如下性质: 
(1)$0\le\psi\le1$, 
(2)$\psi\in C_c^\infty(\mathbb{R}^d)$, 且$\operatorname{supp}\psi\subset\{1/2\le|x|\le2 \}$, 
(3)$\psi$是径向函数. 

同样的, **字母$\psi$特别地留给这个函数, 而不做它用.**

定义$\phi_j=\delta^{2^{-j}}\phi$, $\psi_j=\delta^{2^{-j}}\psi$. 这里$\delta$是伸缩算子, 定义为$\delta^\lambda f(x)\overset{def}{=}f(\lambda x)$. 那么: 
(1)$\operatorname{supp}\phi_j\subset\{|x|\le2^{j+1}\}$, 
(2)$\operatorname{supp}\psi_j\subset\{2^{j-1}\le|x|\le2^{j+1}\}$. 

我们将会看到, $\{\psi_j\}_{j\in\mathbb{Z}}$构成了$\mathbb{R}^d\setminus\{0\}$的局部有限的单位分解. 

>**引理1.** $\forall x\in \mathbb{R}^d\setminus\{0\}$, 有
$$\sum_{j=-\infty}^\infty\psi_j(x)=1$$
这个求和应该这样来理解: 对任何固定的$x\ne0$, 上面的求和中最多仅有三项非零, 所以实际上对每个$x\ne0$来说这都是一个有限和. 
**证明.** 由$\operatorname{supp}\psi_j\subset\{2^{j-1}\le|x|\le2^{j+1}\}$知对任何固定的$x\ne0$, 上面的求和中最多仅有三项非零. 
$$\sum_{j=-\infty}^\infty\psi_j(x)=\sum_{j=-\infty}^\infty\psi(2^{-j }x)=\sum_{j=-\infty}^\infty\left(\phi(2^{-j }x)-\phi(2^{-j +1}x)\right)$$
$$=\lim_{N\rightarrow+\infty}\sum_{j=-N}^N\left(\phi(2^{-j }x)-\phi(2^{-j +1}x)\right)$$
$$=\lim_{N\rightarrow+\infty}(\phi(2^{-N}x)-\phi(2^{N+1}x))=1$$
$\blacksquare$

有了这些光滑截断函数, 我们可以来局部化一个函数的频率. 

定义三族Littlewood-Paley算子$\{P_k \}_{k\in\mathbb{Z}}$, $\{P_{\le k} \}_{k\in\mathbb{Z}}$和$\{P_{>k}\}_{k\in\mathbb{Z}}$, 它们是${\mathscr S}'$到${\mathscr S}'$的映射, 定义为
$$P_kf\overset{def}{=}(\psi_j\widehat f)^\vee=\check\psi_j\ast f$$
$$P_{\le k}f\overset{def}{=}(\phi_j\widehat f)^\vee=\check\phi_j\ast f$$
$$P_{>k}f\overset{def}{=}f-P_{\le k}f$$

由于Schwartz函数与缓增分布的卷积是一个不超过多项式增长的光滑函数(见Grafakos, GTM249), 所以我们知道$P_kf$和$P_{\le k}f$都是不超过多项式增长的光滑函数, 并且由Young不等式知当$f\in L^p$时, $P_kf$,$P_{\le k}f$都属于$L^p$. 

现在我们对任一缓增分布$f$定义Littlewood-Paley平方函数$Sf$. 
$$Sf(x)=\left(\sum_{k=-\infty}^{+\infty}|P_kf(x)|^2\right)^{1/2}$$
注意$Sf$是逐点定义的. 

为了证明Littlewood-Paley定理, 我们需要一族Rademacher函数$\{r_m(t)\}_{m\ge0}$. 我们定义$r_0(t)$是一个$\mathbb{R}$上周期为1的周期函数, 满足
$$r_0(t)=\left\{
                        \begin{array}{ll}
                          &1, \ \ \ \ \ (0\le t<1/2) \\
                          &-1,\ \ (1/2\le t<1)
                        \end{array}
                      \right.$$
再定义$r_m(t)=r_0(2^mt)$. 易见$r_m$的周期为$2^{-m}$, 它在$[0,2^{-m})$上前一半是1, 后一半是-1. 

>**引理2.** 设$0\le m_1<\cdots < m_k$是一些互不相等的整数, 则
$$\int_0^1r_{m_1}(t)\cdots r_{m_k}(t)dt=0$$
**证明.**  把$[0,1]$分成$2^{m_k}$个区间讨论即可, 在每个区间上积分都是零, 加起来自然也是0. 
$\blacksquare$

这个引理有一个很简单但是等下会用到的推论. 

>**推论3.** 如果$\int_0^1r_{m_1}(t)\cdots r_{m_k}(t)dt\ne0$, 那么$k$是偶数, 并且$m_1,\ldots,m_k$可以分为$k/2$组, 每组里的两个数相等. 并且此时$r_{m_1}(t)\cdots r_{m_k}(t)\equiv1$. 

对一个$l^2$中的元素$a=\{a_m\}_{m\ge0}$, 我们定义函数$F(t)=\sum_{m=0}^\infty a_mr_m(t)$, 这是逐点定义的. 由于$l^2\subset l^1$, 我们知道对每个$t$, 这个级数都是绝对收敛的. 

>**引理4.**  设$1<p<\infty$, 则
$$\|F\|_{L^p[0,1]}\sim_p\|F\|_{L^2[0,1]}=\|a\|_{l^2}$$
**证明.** 当$1 < p\le2$时由Hölder不等式有$\|F\|_{L^p[0,1]}\le\|F\|_{L^2[0,1]}$. 同理, $2\le p<\infty$时$\|F\|_{L^2[0,1]}\le\|F\|_{L^p[0,1]}$. 
我们暂时先来计算$\|F\|_{L^2[0,1]}$. 
$$\|F\|_2^2=\int_0^1\left(\sum_{m=0}^\infty a_mr_m(t)\right)^{2}dt$$
$$\overset{\text{控制收敛定理}}{=}\sum_{m,m'=0}^\infty\int_0^1a_mr_m(t)a_{m'}r_{m'}(t)dt$$
由推论3知只有那些$m=m'$的项不为零, 故
$$\|F\|_2^2=\sum_{m=0}^\infty a_m^2$$
现在我们对$k\ge1$计算$\|F\|_{2k}$. 
$$\|F\|_{2k}^{2k}=\int_0^1\left(\sum_{m=0}^\infty a_mr_m(t)\right)^{2k}dt$$
$$=\sum_{m_1,\cdots,m_{2k}=0}^\infty\int_0^1a_{m_1}r_{m_1}(t)\cdots a_{m_{2k}}r_{m_{2k}}(t)dt$$
利用推论3, 乘法计数原理以及不全相异全排列, 得到上式
$$\le\frac{(2k)!}{(2!)^k}\sum_{m_1,\cdots,m_{k}=0}^\infty a_{m_1}^2\cdots a_{m_k}^2=C_k\|a\|_{l^2}^{2k}=C_k\|F\|_2^{2k}$$
这告诉我们$\|F\|_{2k}\le C_k\|F\|_2$. 对任何$p>2$, 存在一个$k$使得$p<2k$, 譬如说可以取$k=\left[ p/2\right]+1$. 由插值定理, $\|F\|_p\le\|F\|_2^\theta\|F\|_{2k}^{1-\theta}=C_k^{1-\theta}\|F\|_2\lesssim_p\|F\|_2$. 最后当$ 1 < p<2 $时, 由插值定理, $\|F\|_2\le\|F\|_p^\theta\|F\|_4^{1-\theta}\lesssim\|F\|_p^\theta\|F\|_2^{1-\theta}$, 故$\|F\|_2^\theta\lesssim\|F\|_p^\theta\Rightarrow\|F\|_2\lesssim\|F\|_p$. 
$\blacksquare$

除了Rademacher函数, 我们还需要一个Mikhlin-Hörmander乘子定理. 

>**定理5(Mikhlin-Hörmander乘子定理).** 设$1<p<\infty$, 再设$k>d/2+1$是一个整数. 如果$m\in C^k(\mathbb{R}^d\setminus\{0\})$满足一些有界性条件, 具体来说, 如果存在$B>0$使得
$$\|m\|_{\infty}\le B$$
$$|\partial^\alpha m(\xi)|\le B|\xi|^{-|\alpha|}\ \ \ \forall \alpha\ \text{s.t.}|\alpha|\le k$$
那么$m$是一个$L^p(\mathbb{R}^d)$乘子, 即由$m$定义的算子
$$Tf=(m\widehat{f})^\vee$$
是$L^p$有界的, 并且
$$\|T\|_{L^p\rightarrow L^p}\lesssim_{d,p} B$$


下面是我们遇到的主要结果. 

>**定理6(Littlewood-Paley定理).** 当$1<p<\infty$时, 对任何$f\in L^p$, 有$Sf\in L^p$, 并且$\|Sf\|_p\approx_{d,p,\psi}\|f\|_p$. 
**证明.** 我们首先证明$\|Sf\|_p\lesssim_{d,p,\psi }\|f\|_p$. 
利用引理4, 我们有
$$Sf(x)=\left(\sum_{m=-\infty}^\infty|P_mf(x)|^2\right)^{1/2}$$
$$\overset{Minkowski}{\le}\left(\sum_{m=0}^\infty|P_mf(x)|^2\right)^{1/2}+\left(\sum_{m=0}^\infty|P_{-m}f(x)|^2\right)^{1/2}$$
$$\overset{\text{引理4}}{\lesssim_p}\left\|\sum_{m=0}^\infty P_mf(x)r_m(t)\right\|_{L_t^p([0,1])}+\left\|\sum_{m=0}^\infty P_{-m}f(x)r_m(t)\right\|_{L_t^p([0,1])}$$
在这个不等式两边取$p$次幂, 利用初等不等式$(a+b)^p\le 2^p(a^p+b^p)$, 然后对$x$积分再开$p$次方, 再利用$(a+b)^{1/p}\le2^{1/p}(a^{1/p}+b^{1/p})$就得到
$$\|Sf(x)\|_{L_x^p(\mathbb{R}^d)}\lesssim_p\left\|\sum_{m=0}^\infty P_mf(x)r_m(t)\right\|_{L_{t,x}^p([0,1]\times\mathbb{R}^d)}+\left\|\sum_{m=0}^\infty P_{-m}f(x)r_m(t)\right\|_{L_{t,x}^p([0,1]\times\mathbb{R}^d)}$$
$$\overset{\text{Hölder}}{\le}\left\|\sum_{m=0}^\infty P_mf(x)r_m(t)\right\|_{L_t^\infty(0,1;L_x^p(\mathbb{R}^d))}+\left\|\sum_{m=0}^\infty P_{-m}f(x)r_m(t)\right\|_{L_t^\infty(0,1;L_x^p(\mathbb{R}^d))}$$
为了控制这两项, 我们定义两个算子$T_t,T_t'$: 
$$T_tf(x)=\sum_{m=0}^\infty P_mf(x)r_m(t)$$
$$T_t'f(x)=\sum_{m=0}^\infty P_{-m}f(x)r_m(t)$$
我们只要能够说明$\|T_t\|_{L^p\rightarrow L^p},\|T_t'\|_{L^p\rightarrow L^p}\le C$, 并且这里$C$不依赖于$t$, 就立即得到$\|Sf\|_p\le2C\|f\|_p$. 
考察$T_t,T_t'$所对应的乘子: 
$$m_t(\xi)=\sum_{m=0}^\infty\psi(2^{-m}\xi)r_m(t)$$
$$m_t'(\xi)=\sum_{m=0}^\infty\psi(2^m\xi)r_m(t)$$
然后检查这两个乘子确实满足Mikhlin-Hörmander乘子定理的条件即可, 我们现在就来做这件事.
首先由于$\{\psi_j\}_{j\in\mathbb{Z}}$是$\mathbb{R}^d\setminus\{0\}$局部有限的单位分解, 所以$m_t,m_t'\in C^\infty(\mathbb{R}^d\setminus\{0\})$, 并且
$$\|m_t\|_\infty,\|m_t'\|_\infty\le3$$
然后我们估计导数, 固定$\xi\ne0$, 设$2^{m_0}\le|\xi|<2^{m_0+1}$, 有 
$$|\partial^\alpha m_t(\xi)|=\left|\sum_{m=0}^\infty2^{-m|\alpha|}(\partial^\alpha\psi)(2^{-m}\xi)r_m(t)\right|$$
$$=\left|\sum_{m=m_0-1}^{m_0+1}2^{-m|\alpha|}(\partial^\alpha\psi)(2^{-m}\xi)r_m(t)\right|$$
$$\le(2^{-(m_0-1)|\alpha|}+2^{-m_0|\alpha|}+2^{-(m_0+1)|\alpha|})\|\partial\psi\|_\infty\lesssim_\psi|\xi|^{-|\alpha|}$$
这就验证好了, $m_t'$的验证也是完全类似的, 所以我们利用Mikhlin-Hörmander乘子定理得到$\|Sf\|_p\lesssim_{d,p,\psi}\|f\|_p$. 
定理的另一半我们使用对偶方法来证明. 我们现在假设$f\in\mathscr{S}$, 一般的$L^p$函数可以用标准的稠密性论证达到. 
$$\|f\|_p=\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}f(x)\overline{g(x)}dx$$
$$\overset{\text{Parseval}}{=}\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}\widehat f(\xi)\overline{\widehat g(\xi)}d\xi$$
$$=\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}\sum_{k\in\mathbb{Z}}\psi_k(\xi)\widehat f(\xi)\overline{\widehat g(\xi)}d\xi$$
注意到在$\operatorname{supp}\psi_k$上$\psi_{k-1}+\psi_k+\psi_{k+1}=1$, 故上式
$$=\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}\sum_{k\in\mathbb{Z}}\psi_k\widehat f\overline{(\psi_{k-1}+\psi_k+\psi_{k+1})\widehat g}d\xi$$
$$\overset{\text{记}\widetilde P_k=P_{k-1}+P_k+P_{k+1}}{=}\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}\sum_{k\in\mathbb{Z}}P_kf\tilde P_kgdx$$
$$\le\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\int_{\mathbb{R}^d}\left(\sum_{k\in\mathbb{Z}}|P_kf|^2\right)^{1/2}\left(\sum_{k\in\mathbb{Z}}|\tilde P_kg|^2\right)^{1/2}dx$$
$$\le\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\|Sf\|_p\|Sg\|_{p'}$$
$$\lesssim_{d,p,\psi}\sup_{g\in\mathscr{S},\|g\|_{p'}=1}\|Sf\|_p\|g\|_{p'}=\|Sf\|_p$$
这就完成了证明. $\blacksquare$

在定理的证明中可以看到, 我们还额外定义了一个$\tilde P_k$, 它对应的乘子是$\psi_{k-1}+\psi_k+\psi_{k+1}$. 之后我们还会经常这样做, 也就是**用其他的函数$\widetilde\psi$代替$\psi$作为乘子, 得到其他的频率局部化算子$\widetilde P_kf=((\delta^{2^{-k}}\widetilde\psi)\widehat f)^\vee$.** 为了搞清楚这样的替换会带来什么影响, 比如是否影响到Littlewood-Paley定理的成立, 我们现在来理一理证明过程中到底依赖了$\psi$的什么性质. 

在证明$\|Sf\|_p\lesssim\|f\|_p$的过程中, 我们对$\psi$仅有的要求是要使得$m_t,m_t'$满足Mikhlin-Hörmander乘子定理的条件. **而这只需要$\psi\in C_c^\infty(\mathbb{R}^d)$并且存在$a<b$使得$\operatorname{supp}\psi\subset\{a\le|x|\le b\}$就可以.**

在证明$\|f\|_p\lesssim\|Sf\|_p$的过程中, 我们用到了定理的前一半, 并且还要求在$\operatorname{supp}\psi_k$上$\psi_{k-1}+\psi_k+\psi_{k+1}=1$, **这里实际上是要求$\{\psi_k\}$是局部有限的单位分解, 或者存在$\lambda>0$使得$\{\lambda\psi_k\}$是局部有限的单位分解.**

我们把这个讨论整理成注记. 

>**注记7.** (1)如果$\widetilde\psi\in C_c^\infty(\mathbb{R}^d)$并且存在$a<b$使得$\operatorname{supp}\widetilde\psi\subset\{a\le|x|\le b\}$, 那么相应的Littlewood-Paley平方函数$\widetilde Sf$满足$\|\widetilde Sf\|_p\lesssim\|f\|_p$. 
(2)额外地, 如果存在$\lambda>0$使得$\{\lambda\psi_k\}$是局部有限的单位分解, 那么$\|f\|_p\lesssim\|\widetilde Sf\|_p$. 

我们常常会取的其他频率局部化算子以及它们对应的乘子有
- $\widetilde P_k=\sum_{l=-k_0}^{k_1}P_{k+l}$, 对应的乘子是$\widetilde\psi=\sum_{l=-k_0}^{k_1}\psi_l$. 这满足注记7的第一条, 也满足第二条. 
- $\widetilde P_k=2^{-ks}|\nabla|^sP_k$, 对应的乘子是$\widetilde\psi=|\xi|^s\psi$. 这个算子满足注记7的第一条, 但不满足第二条. 