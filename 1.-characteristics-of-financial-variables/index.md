# 

# 1. Characteristics of financial variables
## 1.1 Prices and asset returns

Suppose that we observe financial time series data, e.g., daily stock close prices $ P_t $, for $ t=1,2,...,T $. 

We define daily simple return as

$$
R_t=\frac{P_t-P_{t-1}}{P_{t-1}},
$$

or

$$
R_t=\frac{\Delta P_t}{P_{t-1}},
$$

where $\Delta P_t=P_t-P_{t-1}$ is the increment of price from $t-1$ to $t$. 

Meanwhile, we define Log return as

$$
r_t=\log(P_t)-\log(P_{t-1})=\log\left(\frac{P_t}{P_{t-1}}\right).
$$

$r_t$ is also called continuously compounded return because

$$
\underset{m\rightarrow\infty}{\lim}\left(1+\frac{r}{m}\right)^m=e^r.
$$

Note that we could establish the relationship between $R_t$ and $r_t$ as

$$
r_t=\log\left(1+\frac{P_t-P_{t-1}}{P_{t-1}}\right)=\log(1+R_t)
$$

Question: What is the difference between $R_t$ and $r_t$? Are their values very close? Which one is always larger? (Hint: Taylor expansion of $\log(1+x)$ with $x$ close to 0.)

In reality, simple return is more realistic, while log return is more like a academic item. 

###  Multiperiod returns

We consider the stock price from period $t-k$ to $t$.\\

The simple return from $t-k$ to $t$ is

$$
\begin{aligned}
1+R_t(k)=&\frac{P_{t}}{P_{t-k}}=\frac{P_{t}}{P_{t-1}}\frac{P_{t-1}}{P_{t-2}}\cdots\frac{P_{t-k+1}}{P_{t-k}}\\
=&(1+R_{t})(1+R_{t-1})\cdots(1+R_{t-k+1})
\end{aligned}
$$

While the log return is

$$
\begin{aligned}
r_t(k)=&\log\left(\frac{P_{t}}{P_{t-k}}\right)=\log\left(\frac{P_{t}}{P_{t-1}}\frac{P_{t-1}}{P_{t-2}}\cdots\frac{P_{t-k+1}}{P_{t-k}}\right)\\
=&r_{t}+r_{t-1}+\cdots+r_{t-k+1}
\end{aligned}
$$

### Adjustment for Dividends

If a dividend $D_t$ is paid prior to time $t$, we define daily simple return as

$$
R_t=\frac{P_t+D_t-P_{t-1}}{P_{t-1}},
$$

and the log return is

$$
r_t=log(1+R_t)=log(P_t+D_t)-log(P_{t-1}),
$$

Similarly, one can define multiple-period returns with dividend adjustments.

## 1.2 Random Walk Model

### 1.2.1 Brownian motion

布朗运动(Brownian motion), 一种正态分布的独立增量连续随机过程($ B(t+2)-B(t+1) \perp B(t+1)-B(t) $)，可以证明布朗运动是马尔可夫过程、鞅过程和伊藤过程。布朗运动是在1827年英国植物学罗伯特·布朗(Robert Brown)利用一般的显微镜观察悬浮于水中由花粉所迸裂出之微粒时，发现微粒会呈现不规则状的运动，因而称它布朗运动。

Random walk: $ \varepsilon_t = log(P_t) - log(P_{t-1})$ is i.i.d, then logarithm of stock price is a random walk, which is a strong condition for financial analysis.

The $ \textcolor{blue}{\text{Random walk hypothesis}} $ states that the single-period log returns, $r_t$ are independent, then
$$
\begin{aligned}
1+R_t(k)=&\frac{P_{t}}{P_{t-k}}=\frac{P_{t}}{P_{t-1}}\frac{P_{t-1}}{P_{t-2}}\cdots\frac{P_{t-k+1}}{P_{t-k}}\\
=&(1+R_{t})(1+R_{t-1})\cdots(1+R_{t-k+1})\\
=&exp(r_t+r_{t-1}+\cdots+r_{t-k+1})
\end{aligned}
$$

and we have

$$
log(1+R_t(k))=r_t+r_{t-1}+\cdots+r_{t-k+1}.
$$

It is sometimes assumed further that the log returns $r_t$ are i.i.d., $N(\mu,\sigma^2)$.

### 1.2.2 Geometric Random Walks

It is easy to show

$$
\frac{P_{t}}{P_{t-k}}=1+R_t(k)=exp(r_t+r_{t-1}+\cdots+r_{t-k+1})
$$

Taking $ k=t $, we have

$$
P_t=P_0exp(r_t+r_{t-1}+\cdots+r_{1})
$$

We call such a process **whose logarithm is a random walk** (in this case $ P_t$ ) a $ \textcolor{blue}{\text{geometric random walk}} $ or an $ \textcolor{red}{\text{exponential random walk}} $. If add the assumption that $r_t$ are i.i.d., normal distribution, the process is a $ \textcolor{blue}{\text{lognormal geometric random walk}} $.

Simulating a stock price process

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed@master/Figs/20201103203309.jpg)

### 1.2.3 Descriptive statistics

For stationary time series $X_t$, we define its descriptive statistics as

- Mean $\mu=E[X]$;
- Variance $\sigma^2=E[(X-E[X])^2]$;
- Skewness $sk=\frac{E[(X-E[X])^3]}{\sigma^3}$;
- Kurtosis $K=\frac{E[(X-E[X])^4]}{\sigma^4}$.

For normal distributions, $sk=0$ and $K=3$. 

Taking Normal distribution as a benchmark, we define $K-3$ as the excess kurtosis.

With $ T $ realizations of $ X_t $, $ t=1,2,...,T $, we could compute

- Sample mean $\widehat\mu=T^{-1}\sum_{t=1}^TX_t$;
- Sample variance $\widehat\sigma^2=(T-1)^{-1}\sum_{t=1}^T(X_t-\widehat\mu)^2$;
- Sample skewness $\widehat{sk}=T^{-1}\sum_{t=1}^T(X_t-\widehat\mu)^3/\widehat\sigma^3$;
- Sample kurtosis $\widehat K=T^{-1}\sum_{t=1}^T(X_t-\widehat\mu)^4/\widehat\sigma^4$.

If $X$ follows normal distribution, then $\widehat{sk}\approx0$ and $\widehat K\approx 3$.

**Why do we care about these moments?**

- Sample mean: telling us the **return performance,** cared most by investors, studied most in the literature as well
- Sample variance: the typical **measurement for volatility** (standard error); see Sharpe ratio; and covariance matrix could be applied for portfolio construction.
- Sample skewness: the measurement for **crash risk**
- Sample kurtosis: the measurement for **heavy tail**, needed for Central Limit Theorem

## 1.3 Testing for Normality

### 1.3.1 Jarque-Bera test

As $T\rightarrow\infty$, we have

$$
\sqrt T\widehat{sk}\overset{D}{\longrightarrow} N(0, 6),
$$

and

$$
\sqrt T(\widehat K-3)\overset{D}{\longrightarrow} N(0, 24).
$$

Jarque-Bera test statistic

$$
\qquad J=T\left(\frac{\widehat{sk^2}}{6}+\frac{(\widehat K-3)^2}{24}\right).
$$

In the Jaque-Bera test, we specify

$$
\begin{aligned}
\mathbb H_0:&\, X \mbox{ follows normal distribution}\\
\mathbb H_1:&\, X \mbox{ does NOT follow normal distribution.}
\end{aligned}
$$

Under the null hypothesis, $\widehat{sk}$ converge to a normal random variable with mean zero, and the same for $\widehat K-3$. Therefore, $ J\sim \chi^2_{(2)}. $

Under the alternative hypothesis, we would get a large value of $J$. 

Decision rule: we reject the null hypothesis when $J$ is larger than the critical value, for example, $ \chi^2_{(2)}(0.95) $ under $5\%$ significance level.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201103205122.png)

### A real example: Shanghai Composite Index}

We consider the daily close prices of the Shanghai Stock Exchange (SSE) Composite Index from 1 Jan 2000 to 31 Dec 2016.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201105185618.png)



![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201105185749.png)

Phenomena: the probability of large shock is higher than normal distribution

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201105185950.png)

![image-20201105190033160](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20201105190033160.png)

Simple return and Log return are very close when they are small.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed@master/Figs/20201105190243.png)

Table: Descriptive statistics of Daily Simple and Log returns

|                        | Simple Return | Log Return |
| ---------------------- | ------------- | ---------- |
| Mean                   | 0.000326      | 0.000192   |
| Standard Deviation     | 0.016328      | 0.016362   |
| Skewness               | -0.184995     | -0.341840  |
| Kurtosis               | 7.467776      | 7.488846   |
| Jarque-Bera Statistic  | 3445.118      | 3534.125   |
| P-value of the JB test | 0.0000        | 0.0000     |

- Negative skewness, higher crash risk for log return
- Huge kurtosis, heavy tail
- Refuse JB test's null hypothesis, not normal distributed

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201105192907.png)

- Positive or negative correlation may depends on some pattern like trade volunm.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20201105190920.png)

### Quantile-Quantile (QQ) plot

A simpler way to examine Normality:

- We compare the quantiles of the log return data with the normal distribution that has the same mean and variance.
- If log return follows normal distribution, then they should have the same quantiles (on the 45 degree line).

Compare the distribution of LR with Normal distribution. Heavier tail.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed@master/Figs/20201105191655.png)

How about $ t $-distribution? Thinner tail.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed@master/Figs/20201105191719.png)

Measuring serial autocorrelation

We define $k$-th order **autocovariance** as

$$
\gamma(k)=Cov(r_t, r_{t+k})=E[r_tr_{t+k}]-E[r_t]E[r_{t+k}],
$$

and $k$-th order serial **autocorrelation** as

$$
\rho(k)=\frac{\gamma(k)}{\gamma(0)}.
$$

We estimate $\gamma(k)$ by

$$
\widehat\gamma(k)=T^{-1}\sum_{t=1}^{T-k}(r_t-\bar r)(r_{t+k}-\bar r),
$$

where $\bar r=T^{-1}\sum_{t=1}^nr_t$. Therefore, $\widehat\rho(k)=\widehat\gamma(k)/\widehat\gamma(0)$.

Suppose that

$$
X_t=\mu +X_{t-1}+\epsilon_t, 
$$
where $X_t=P_t$ or $X_t=p_t$. Historically, $\mu$(drift) was often assumed to be zero

- RW1: $\epsilon_t \sim IID;\, E \epsilon_t=0 $
- RW2: $\epsilon_t $ is independent over time; $ E \epsilon_t=0 $
- RW3: For all $k$, $cov(\epsilon_t, \epsilon_{t-k} )=0$

Then, provided $E\epsilon_t^2 \leq C < \infty, RW1\Rightarrow RW2 \Rightarrow RW3 $

【Martingale】A **martingale** is a time-series process $X_t$ obeying

$$
E[X_{t+1} | X_t, X_{t-1}, \dots ]=X_t
$$

or equivalently, call $\epsilon_{t+1}=X_{t+1}-X_t$ a martingale difference sequence

$$
E[\epsilon_t | X_{t-1}, X_{t-2}, \dots ]=0
$$

This corresponds with the notion of a fair game: If you toss a coin against opponent and bet successively at fair odds with initial capital $X_0$, current capital $X_t$ is martingale. This is the case that $\mu=0$; More generally, by **transforming conditional mean to unconditional**, we might assume that

【RW2.5 (Fama)】: $ \epsilon_{t+1}=X_{t+1}-X_t-\mu $, is a martingale difference (MDS).

Martingale property implies that

$$
cov(\epsilon_t, g(X_{t-1}, X_{t-2}, \dots) )=0
$$

for any (measurable) function $g.$

In particular

$$
g(X_{t-1}, X_{t-2}, \dots)=X_{t-k}-X_{t-k-1}-\mu =\epsilon_{t-k}
$$
so stronger condition than RW3.

## 1.4 Efficient Markets Hypothesis

Fama (1970, JoF): A market in which prices always 'fully reflect' available information is called 'efficient' $\Rightarrow$ EMH

- If prices are predictable $\Rightarrow$ opportunities for superior returns (free lunch) $\Rightarrow$ will be competed away immediately by a lot of hungry traders $\Rightarrow$ unpredictable random walk
    - If a security believed to be underpriced, buying pressure $\Rightarrow$ jump up to a level where no longer thought a bargain
    - If a security believed to be overpriced, (short-)selling pressure $\Rightarrow$ jump down to a level where no longer thought too expensive

- As a result, market forces respond to news quickly and make prices the best available estimates of fundamental values, i.e. values justified by likely future cash flows and preferences of investors/consumers

We **distinguish among three forms of market efficiency depending on the information set** with respect to which efficiency is defined

- **Weak form** - **historical prices** fully reflected in current price: Can't profit from strategies based on past prices
- **Semi strong form** - **all public information** (past prices, annual reports, quality of management, earnings forecasts, macroeconomic news, etc.) fully reflected in current prices: Can't outsmart others since they read newspapers too
- **Strong form** - **all private and public information** fully reflected in current prices: Can't profit from knowledge of tomorrow's news (bonds downgraded by rating agencies, new drug failed to be approved, book-cooking by Enron, last-quarter earnings, M\&A deals, etc.)

Econometric Issue

- **Joint Hypothesis Problem.** Any test of weak form EMH must assume an equilibrium asset pricing model that defines 'normal' security returns against which investor returns are measured. If we reject the hypothesis that investors can't achieve superior risk-adjusted returns, we don't know if markets are inefficient or if the underlying model is misspecified. 
- we should allow 

$$
r_t=\mu_t+\epsilon_t,
$$

mostly assuming $\mu_t=\mu$ is constant or small, where $\epsilon_t$ is a martingale difference sequence with respect to some information set $\mathcal{F}_{t-1},$ i.e., $E(\epsilon | \mathcal{F}_{t-1} )=0$ and $\mu_t$ is the risk premium that is given from some asset pricing model.

### Testing of EMH under RW1

The population autocovariance and autocorrelation functions of a stationary series $Y_t$

$$
\gamma_s=cov(Y_t, Y_{t-s})=E[(Y_t-EY_t)(Y_{t-s}-EY_{t-s})] \\

\rho_s=\frac{\gamma_s}{\gamma_0}
$$
for $s=0, \pm 1, \pm 2, \dots$ Take $Y_t=r_t$ or $R_t$ can estimate these  by the sample equivalents

$$
\hat{\gamma_s}=\frac{1}{T} \mathop{\sum}\limits_{t=s+1}^T (Y_t-\bar{Y})(Y_{t-s}-\bar{Y}) \\

\hat{\rho_s}=\frac{\hat{\gamma_s}}{\hat{\gamma_0}}. 
$$
The efficient markets hypothesis says that $\gamma_s, \rho_s=0$ for all $s \neq 0$

#### 检验单个ACF

Assume further that $Y_t \text{is i.i.d.}$ It can be shown that for any $k,$
$$
\sqrt{T} \hat{\rho_k} \Rightarrow N(0,1) 
$$

under the null hypothesis of no correlation.

Therefore, you can **test the null hypothesis by comparing $\hat{\rho_k}$ with the so-called 'Bartlett intervals'**
$$
[-z_{\alpha/2}/\sqrt{T}, z_{\alpha/2}/\sqrt{T}],
$$

where $z_\alpha$ are normal critical values. Values of $\hat{\rho_k}$ lying outside this interval are inconsistent with the null hypothesis. Literally, **this is testing the hypothesis that $\rho_k=0$ versus $\rho_k \neq 0$ for a given $ k $.**

Under the alternative hypothesis

$$
\sqrt{T} \hat{\rho_k} \mathop{\rightarrow}\limits^{P} \infty 
$$
for at least one $k.$

#### 检验联合ACF / Ljung-Box白噪声检验

In fact, under this assumption we have

$$
\sqrt{T} (\hat{\rho_1}, \dots, \hat{\rho_P})^T \Rightarrow N(0,I_P). 
$$
The **Box-Pierce** $Q$ statistic
$$
Q=T\mathop{\sum}\limits_{j=1}^P \hat{\rho}_j^2
$$
can be used to **test the joint hypothesis** that $\rho_1=0, \dots, \rho_P=0$ versus the general alternative. We have

$$
Q\Rightarrow \chi_P^2 
$$
Under the null hypothesis, so reject when $Q>\chi_P^2(\alpha)$ for an $\alpha$-level test.

**Box-Ljung** version is known to have better finite sample performance, which can be used test white noise,  
$$
Q=T(T+2)\mathop{\sum}^{p}_{j=1} \frac{\hat{\rho}_j^2}{T-j}
$$
实际上，由于p的选择会影响Q的表现，所以经常选用多个p值模拟。研究表明$ p \approx \ln(T) $会有较好的功效。在分析季节性时间序列时，由于时间隔为周期的倍数的自相关系数更加重要，所以这个一般性的规则需要加以修正。
