# 

##常用分布
|                |                 |                                                              |                     |                        |                                           |
| -------------- | --------------- | ------------------------------------------------------------ | ------------------- | ---------------------- | ----------------------------------------- |
|                |                 | PDF/PMF                                                      | 期望                | 方差                   | MGF                                       |
| 均匀分布       | $X \sim U[a,b]$ |                                                              | $E(X)=(a+b)/2$      | $var(X)=(b-a)^2/12$    |                                           |
| 伯努利分布     |                 | $\begin{aligned}	f_X(x)&=	\begin{cases}	p, &x=1\\	1-p, &x=0\\	\end{cases}\\	&=p^{x}(1-p)^{1-x}, x=0,1\end{aligned}$ | $E(X)=p$            | $var(X)=p(1-p)$        | $M_X(t)=pe^t+1-p,t \in(-\infty,\infty)$   |
| 正态分布       |                 | $f_{X}(x)=\frac{1}{\sqrt{2 \pi \sigma^{2}}} e^{-(x-\mu)^{2} / 2 \sigma^{2}},-\infty<x<\infty$ | $E(X)=\mu$          | $var(X)=\sigma^2$      | $M_X(t)=e^{\mu t+ \frac{\sigma^2}{2}t^2}$ |
| 柯西分布       |                 | $f_{X}(x)=\frac{1}{\pi \sigma} \left[1+\left(\frac{x-\mu}{\sigma}\right)^{2}\right]^{-1}, x \in \mathbb{R}$ | 不存在              | 不存在                 | 不存在/一阶及以矩上均不存在               |
| $\chi^2_{\nu}$ |                 |                                                              | $E(\chi^2_\nu)=\nu$ | $var(\chi^2_\nu)=2\nu$ | $M_X(t)=(1-2t)^{-\frac{\nu }{2}}$         |
| $t_\nu$        |                 | $\frac{N(0,1)}{\sqrt{\chi^2_\nu/\nu}}$                       | 0                   | $\nu/(\nu-2)$          | 不存在                                    |
| $F_{p,q}$      |                 | $\frac{U/p}{V/q}$                                            |                     |                        |                                           |





## 抽样分布

| 统计量                                                       | 抽样分布        |
| ------------------------------------------------------------ | --------------- |
| $\frac{\bar{X}_n-\mu}{\sigma/\sqrt{n}}$                      | $N(0.1)$        |
| $\frac{\sum_{i=1}^{n}(X_i-\mu)^2}{\sigma^2}$                 | $\chi^2_{n} $   |
| $\frac{(n-1)S^2_n}{\sigma^2}=\frac{\sum^n_{i=1}(X_i-\bar{X}_n)}{\sigma^2}$ | $\chi^2_{n-1} $ |
| $\frac{\bar{X}_{n}-\mu}{S_{n} / \sqrt{n}} =\frac{\frac{X_{n}-\mu}{\sigma / \sqrt{n}}}{\sqrt{\frac{(n-1) S^{2}_n}{\sigma^{2}} /(n-1)}}\sim \frac{N(0,1)}{\sqrt{\chi_{n-1}^{2} /(n-1)}}$ | $t_{n-1}$       |
| $\frac{\frac{(n-1) S_{X}^{2} / \sigma_{X}^{2}}{n-1}}{\frac{(m-1) S_{Y}^{2} \sigma_{Y}^{2}}{m-1}} \sim \frac{\chi_{n-1}^{2} /(n-1)}{\chi_{m-1}^{2} /(m-1)}$ | $F_{n-1,m-1}$   |




