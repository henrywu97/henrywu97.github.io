# 

# 3. GARCH Type Models

## 3.1 ARCH effect - volatility clustering

ARCH: autoregressive conditional heteroskedasticity.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210257.png)

ARCH effect - ACFs of r

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210348.png)

ARCH effect - ACFs of $ r^2 $

![image-20201120210421333](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20201120210421333.png)

ARCH effect - ACFs of $ | r | $

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210450.png)

ARCH models
Let $ P_{t} $ denote the price and $ r_{t}=\log \left(P_{t} / P_{t-1}\right) $ be the log-return at time $ t $.

Then

$$
r_{t}=\mu_{t}+e_{t}
$$

where $ \mu_{t}=E\left[r_{t} \mid F_{t-1}\right] $ denotes the conditional mean of the return, $ e_{t} $ is a diffusion term which may be modeled as

$$
e_{t}=\sigma_{t} \epsilon_{t}, \quad \epsilon_{t} \sim i . i . d .(0,1)
$$

where $ \sigma_{t}=\operatorname{Var}\left[r_{t} \mid F_{t-1}\right]>0 $ is determined by the information available
before time $ t, $ and $ \epsilon_{t} $ is assumed to be independent of $ \sigma_{t} $.
20
ARCH models
A simple specification for the volatility function $ \sigma_{t} $ is the autoregressive
conditional heteroskedastic (ARCH) model

$$
\sigma_{t}^{2}=a_{0}+a_{1} e_{t-1}^{2}+a_{2} e_{t-2}^{2}+\ldots+a_{p} e_{t-p}^{2}
$$

where $ a_{0}>0, a_{j} \geq 0(1 \leq j \leq p) $ are constants, and $ p $ is a positive integer.
This model allows for capturing the effect of volatility clustering.

ARCH(1) model
We consider the ARCH(1) model as a special example.

$$
\begin{aligned}
e_{t} &=\sigma_{t} \epsilon_{t} \\
\sigma_{t}^{2} &=a_{0}+a_{1} e_{t-1}^{2}
\end{aligned}
$$

where $ a_{0}>0, a_{1} \geq 0 . $ In particular, by the law of iterated expectation
(LIE), we have

$$
\begin{aligned}
E\left[e_{t}\right] &=0 \\
\operatorname{Var}\left[e_{t}\right] &=\frac{a_{0}}{1-a_{1}}
\end{aligned}
$$

where $ 0 \leq a_{1}<1 $
Suppose that $ \epsilon_{t} \sim i . i . d . N(0,1), $ then

$$
E\left(e_{t}^{4} \mid F_{t-1}\right)=3\left[E\left(e_{t}^{2} \mid F_{t-1}\right)\right]^{2}=3\left(a_{0}+a_{1} e_{t-1}^{2}\right)^{2}
$$

Therefore,

$$
E\left(e_{t}^{4}\right)=E\left[E\left(e_{t}^{4} \mid F_{t-1}\right)\right]=3 E\left(a_{0}+a_{1} e_{t-1}^{2}\right)^{2}=3 E\left(a_{0}^{2}+2 a_{0} a_{1} e_{t-1}^{2}+a_{1}^{2} e_{t-1}^{4}\right)
$$

Assume that $ m_{4}=E\left(e_{t}^{4}\right) $ is stationary, then

$$
m_{4}=\frac{3 a_{0}^{2}\left(1+a_{1}\right)}{\left(1-a_{1}\right)\left(1-3 a_{1}^{2}\right)}
$$

ARCH (1) model
To ensure that $ m_{4}>0, $ we have $ 0 \leq a_{1}^{2}<\frac{1}{3} . $ Then, the Kurtosis of $ e_{t} $ is

$$
\frac{E\left(e_{t}^{4}\right)}{\left[\operatorname{Var}\left(e_{t}\right)^{2}\right]^{2}}=3 \frac{a_{0}^{2}\left(1+a_{1}\right)}{\left(1-a_{1}\right)\left(1-3 a_{1}^{2}\right)} \times \frac{\left(1-a_{1}\right)^{2}}{a_{0}^{2}}=3 \frac{1-a_{1}^{2}}{1-3 a_{1}^{2}}>3
$$

This result implies that $ e_{t} $ has positive excess kurtosis, and it is more likely
to see outliers for $ e_{t} $.
ARCH (1) model
How to forecast volatility based on an estimated ARCH(1) model?
Suppose that we had estimated an ARCH(1) model

$$
\begin{aligned}
e_{t} &=\sigma_{t} \epsilon_{t} \\
\sigma_{t}^{2} &=a_{0}+a_{1} e_{t-1}^{2}
\end{aligned}
$$

using $ F_{T}, $ what are the one-step ahead forecast $ E\left[\sigma_{T+1}^{2} \mid F_{T}\right] $ and two-step
ahead forecast $ E\left[\sigma_{T+2}^{2} \mid F_{T}\right] $ given the information set $ F_{T} ? $

GARCH models
Bollerslev (1986) developed the $ \mathrm{GARCH}(\mathrm{p}, \mathrm{q}) $ model as

$$
\begin{aligned}
r_{t} &=\mu+e_{t} \\
e_{t} &=\sigma_{t} \epsilon_{t}, \quad \epsilon_{t} \sim i . i . d .(0,1) \\
\sigma_{t}^{2} &=a_{0}+\underbrace{a_{1} e_{t-1}^{2}+\ldots+a_{p} e_{t-p}^{2}}_{\text {ARCH components }}+\underbrace{b_{1} \sigma_{t-1}^{2}+\ldots+b_{q} \sigma_{t-q}^{2}}_{\text {GARCH components }}
\end{aligned}
$$

where $ a_{0}>0, a_{i} \geq 0, b_{j} \geq 0, $ for $ 1 \leq i \leq p, 1 \leq j \leq q, $ and

$$
\sum_{i=1}^{p} a_{i}+\sum_{j=1}^{q} b_{j}<1
$$

GARCH models
It is easy to show that

$$
\begin{aligned}
E\left[e_{t}\right] &=0 \\
\operatorname{Var}\left[e_{t}\right] &=\frac{a_{0}}{1-a_{1}-\ldots-a_{p}-b_{1}-\ldots-b_{q}} \\
&=\frac{a_{0}}{1-\sum_{i=1}^{p} a_{i}-\sum_{j=1}^{q} b_{j}}
\end{aligned}
$$

which denote the long-run variance.

Residual diagnostics
How to verify that a particular GARCH(p,q) model has captured all the
ARCH effects?
We define $ \widehat{\epsilon}_{t}=\frac{\widehat{e}_{t}}{\hat{\sigma}_{t}} $ as the standardized residuals. If there is no ARCH effects in the standardized residuals, then GARCH(p,q) has captured all
the ARCH effects. Otherwise, we still have ARCH effects remained in $ \widehat{\epsilon}_{t} $
and we need to improve our current model.
GARCH-in-Mean
To account for risk premium, we propose a GARCH-in-Mean model

$$
\begin{aligned}
r_{t} &=\mu+g\left(\sigma_{t}\right)+e_{t} \\
e_{t} &=\sigma_{t} \epsilon_{t}, \quad \epsilon_{t} \sim i . i . d .(0,1) \\
\sigma_{t}^{2} &=a_{0}+\sum_{i=1}^{p} a_{i} e_{t-i}^{2}+\sum_{j=1}^{q} b_{j} \sigma_{t-j}^{2}
\end{aligned}
$$

where $ g(x) $ represents the form of compensational return for risks. In
particular, $ g(x)=\theta_{0}+\theta_{1} x $ (see Engle, Lilien, and Robins 1987 ) or
$ g(x)=\alpha_{0}+\alpha_{1} \sqrt{x} $

TGARCH model
Leverage effect: negative shocks are more likely to cause higher volatility
than positive shocks.
To account for the leverage effect, we propose a Threshold GARCH
(TGARCH) model

$$
\begin{array}{l}
r_{t}=\mu+e_{t} \\
e_{t}=\sigma_{t} \epsilon_{t}, \quad \epsilon_{t} \sim i . i . d .(0,1) \\
\sigma_{t}^{2}=a_{0}+\sum_{i=1}^{p} a_{i} e_{t-i}^{2}+\sum_{i=1}^{p} \gamma_{i} e_{t-i}^{2} 1\left(e_{t-i}<0\right)+\sum_{j=1}^{q} b_{j} \sigma_{t-j}^{2}
\end{array}
$$

where $ 1(.) $ is an indicator function, which can also be replaced by a
dummy variable.
3
Dummy variable in Financial Econometrics
Suppose we want to see whether there exists Monday effect in the stock
market. We define a dummy variable

$$
D_{t}=\left\{\begin{array}{ll}
1 & \text { Mondays; } \\
0 & \text { Other days. }
\end{array}\right.
$$

Then we run the regression

$$
r_{t}=\mu+\theta D_{t}+e_{t}
$$

and test

$$
\mathbb{H}_{0}: \theta=0
$$

vs $ \mathbb{H}_{1}: \theta \neq 0 $

IGARCH model
An Integrated GARCH model (IGARCH(p,q)) can be written as

$$
\begin{array}{l}
r_{t}=\mu+e_{t} \\
e_{t}=\sigma_{t} \epsilon_{t}, \quad \epsilon_{t} \sim i . i . d .(0,1) \\
\sigma_{t}^{2}=a_{0}+\sum_{i=1}^{p} a_{i} e_{t-i}^{2}+\sum_{j=1}^{q} b_{j} \sigma_{t-j}^{2}
\end{array}
$$

where $ \sum_{i=1}^{p} a_{i}+\sum_{j=1}^{q} b_{j}=1 $
Value at Risk (VaR)
Value at risk (VaR) is a measure of the risk of loss for investments. It
estimates how much a set of investments might lose (with a given
probability), given normal market conditions, in a set time period such as a
day.

$$
V a R=\mu-\sigma_{t} \Phi^{-1}(\alpha)
$$

For example, we invest $ \$ 10000 $ in an asset with monthly return $ \mu=0.01 $
and $ \sigma_{t}=0.05 . $ What is the $ 5 \% $ VaR for this investment?

Application - Shanghai Stock Exchange Composite Index

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120214135.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210556.png)

ACFs and PACFs of $ r_t $.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210731.png)

Fitted model: $ r_{t}=0.000172+0.0594 r_{t-4}-0.0485 r_{t-6}+0.0536 r_{t-13} \mid+\widehat{e}_{t} $

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210757.png)

ACFs and PACFs of $ \hat{e}_{t} $ : the above model fully describes the serial
correlation in $ r_{t} $.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210833.png)

ARCH effect test forbe
t :

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210856.png)

ACFs and PACFs ofbe
2
t .

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120210945.png)

An estimated AR(13)-ARCH(1) model.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211042.png)

Fitted $ A R(13)-A R C H(1) $ model:
$$
\begin{aligned}
r_{t} &=0.00000572+0.0435 r_{t-4}-0.0406 r_{t-6}+0.0655 r_{t-13}+\widehat{e}_{t} \\
\widehat{e}_{t} &=\widehat{\sigma}_{t} \widehat{z}_{t} \\
\widehat{\sigma}_{t}^{2} &=0.000192+0.25 \hat{e}_{t-1}^{2}
\end{aligned}
$$

Time series plot of the standardized residuals $ \widehat{z}_{t}=\frac{\widehat{e}_{t}}{\sigma_{t}} . $ Are there any
ARCH effects left in $ z_{t} ? $

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211110.png)

ACFs and PACFs of bz
2
t .

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211144.png)

LM test for ARCH effects in bz
t .

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211202.png)

Improve the ARCH(1) model to GARCH(1,1).

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211220.png)

The fitted GARCH (1,1) model is
$ \begin{aligned} r_{t} &=r_{t}=0.000248+0.0233 r_{t-4}-0.0481 r_{t-6}+0.0224 r_{t-13}+\widehat{e}_{t}, \\ \widehat{e}_{t} &=\widehat{\sigma}_{t} \widehat{z}_{t} \\ \widehat{\sigma}_{t}^{2} &=0.000000130+0.0719 \widehat{e}_{t-1}^{2}+0.9257 \widehat{\sigma}_{t-1}^{2} \end{aligned} $

Standardized residuals of $ \widehat{z}_{t}=\frac{\widehat{e}_{t}}{\sigma_{t}} $ for the GARCH (1,1) model.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211239.png)

$ \mathrm{ACFs} $ and $ \mathrm{PACF}_{\mathrm{S}} $ for $ \hat{z}_{t}^{2} $

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211505.png)

LM test for ARCH effects in $ \widehat{z}_{t} $.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211530.png)

Estimated sequence of $ \widehat{\sigma}_{t}^{2} $.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211639.png)

Upper and lower bounds of $ \left[-\widehat{\sigma}_{t}, \widehat{\sigma}_{t}\right] . $

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211704.png)

Descriptive statistics of $ \hat{z}_{t} $. Does it follow a normal distribution?

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211754.png)

Quantile-Quantile (QQ) plot of $ \widehat{z}_{t} $ versus normal distribution.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211821.png)

Quantile-Quantile (QQ) plot of $ \widehat{z}_{t} $ versus t-distribution.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211849.png)

An estimated Threshold GARCH model to reveal the leverage eects.
Haiqiang

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120211926.png)

The fitted TGARCH model is

$$
\begin{aligned}
r_{t} &=0.00000160+0.0252 r_{t-4}-0.0472 r_{t-6}+0.0240 r_{t-13}+\widehat{e}_{t} \\
\widehat{e}_{t} &=\widehat{\sigma}_{t} \widehat{z}_{t} \\
\widehat{\sigma}_{t}^{2} &=0.00000137+0.0578 \widehat{e}_{t-1}^{2}+0.0238 \widehat{e}_{t-1}^{2} 1\left(\widehat{e}_{t-1}<0\right)+0.925 \widehat{\sigma}_{t-1}^{2}
\end{aligned}
$$

Application - Shanghai Stock Exchange Composite Index
An estimated GARCH-in-Mean model to detect risk premium.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201120212028.png)

The fitted GARCH-M model is

$$
\begin{array}{l}
r_{t}=0.00000934+0.0237 r_{t-4}-0.0478 r_{t-6}+0.0227 r_{t-13}+1.11 \widehat{\sigma}_{t}^{2}+\widehat{e}_{t} \\
\qquad \begin{array}{l}
(43) \\
(44)
\end{array}
\end{array}
$$

$ \widehat{\sigma}_{t}^{2}=0.000000130+0.0721 \widehat{e}_{t-1}^{2}+0.9258 \widehat{\sigma}_{t-1}^{2} $
Assignment 2: Literature Review
O Find a published paper in time series or financial econometrics or
quantitative investment (judge by yourself), read it and draft a two
pages (1500-2000 words) summary.
O Style: Words or Rmarkdown; Both English or Chinese are fine. Try to
summary instead of copy directly.
Due date: $ 7: 10 \mathrm{PM}, $ before class, Thursday of Week 6 (Oct.31th). Assignments will not be accepted after the due date.
O Grade: $ 15 \% $ of your final grade of this course.


