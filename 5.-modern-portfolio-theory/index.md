# 

# 6. Modern Portfolio Theory

## 6.1 Framework

We can elaborate on our previous portfolio problem
$$
\max _{a} E u\left[Y_{0}\left(1+r_{f}\right)+a\left(\tilde{r}-r_{f}\right)\right]
$$
by considering $N>1$ risky assets with returns $\left(\tilde{r}_{1}, \tilde{r}_{2}, \ldots, \tilde{r}_{N}\right)$
$$
\begin{align*}
& \max _{a_{1}, a_2, \ldots, a_{N}} E u\left[Y_{0}\left(1+r_{f}\right)+\sum_{i=1}^{N} a_{i}\left(\tilde{r}_{i}-r_{f}\right)\right] \\
=& \max _{m_{1}, m_{2}, \ldots, w_{N}} E u\left[Y_{0}\left(1+r_{f}\right)+\sum_{i=1}^{N} w_{i} Y_{0}\left(\tilde{r}_{i}-r_{f}\right)\right] \\
=& \max _{m_{1}, w_{2}, \ldots, w_{N}} E u\left[Y_{0}\left(1+\tilde{r}_{P}\right)\right]=E u\left(\left(Y_{1}\right)\right)
\end{align*}
$$
where $w_{i}=a_{i} / Y_{0}$ is the share of initial wealth allocated to each asset. $\tilde{r}_{P}$ is the portfolio rate of return.

**Modern Portfolio Theory** examines the solution to this problem assuming that investors have **mean-variance utility**, that is, assuming that investors' preferences can be represented by a trade-off between the mean (expected value) and variance of the $N$ asset returns.

MPT was developed by **Harry Markowitz** (US, b.1927, Nobel Prize 1990 ) in the early 1950 s, the classic paper being his article "Portfolio Selection," *Journal of Finance* Vol.7 (March 1952 ): pp. $77-91$.

Assume that utility is provided by bundles of consumption goods, $u\left(c_{1}, c_{2}, \dots, c_{n}\right)$ where the indexing is cross dates and states

- States of nature are mutually exclusive
- For each date and state of nature $(\theta)$ there is a traditional budget constraint:

$$
p_{1 \theta} c_{1 \theta}+p_{2 \theta} c_{2 \theta}+\ldots+p_{m \theta} c_{m \theta} \leq Y_{\theta}
$$
- where the indexing runs across goods for a given state $\theta ;$ $(i=1,2, \ldots, m)$ correspond to the $m$ goods available in state of nature $\theta$; the $m$ quantities $c_{i \theta} ;$ and the $m$ prices $p_{i \theta} $ 
- $Y_{\theta}$ is the "end of period" wealth level available in that same state

### 6.1.1 Three steps

MPT summarizes an individual's decision problem as being undertaken sequentially, in three steps: 

1. **The Consumption-Savings Decision**: how to split period zero income/wealth $Y_{0}$ between current consumption now $C_{0}$ and saving $S_{0}$ for consumption in the future where $C_{0}+S_{0}=Y_{0}$
2. **The Portfolio Problem**: choose assets in which to invest one's savings so as to obtain a desired pattern of end-of-period wealth across the various states of nature; this means allocating $\left(Y_{0}-C_{0}\right)$ between a risk-free and $N$ risky assets
3. **The Consumption Choice**: Given the realized state of nature and the wealth level obtained, the choice of consumption bundles to maximize the utility function

$$
Y_{\theta}=\left(Y_{0}-C_{0}\right)\left[\left(1+r_{f}\right)+\Sigma_{i=1}^{N} w_{i}\left(r_{i \theta}-r_{f}\right)\right]
$$
### 6.1.2 backward induction

Starting from step 3:

Step 3 is a standard microeconomic problem and its solution can be summarized by a Bernoulli utility function $u\left(Y_{\theta}\right)$ representing the (maximum) level of utility that results from optimizing in step 3 given that the wealth available in state $\theta$ is $Y_{\theta}:$
$$
\begin{align*}
u\left(Y_{\theta}\right) \equiv \operatorname{def} \max _{\left(c_{1} \theta, \ldots, c_{m \theta}\right)} &u\left(c_{1 \theta}, \ldots, c_{m \theta}\right)\\
s.t.\quad &p_{1 \theta} c_{1 \theta}+p_{2 \theta} c_{2 \theta}+\ldots+p_{m \theta} c_{m \theta} \leq Y_{\theta}
\end{align*}
$$
Step 2: Maximizing $E u\left(Y_{\theta}\right)$ across all states of nature becomes the objective of step
$$
\max _{\left(w_{1}, w_{2}, \ldots, w_{N}\right)} E u(\tilde{Y})=\Sigma_{\theta} \pi_{\theta} u\left(Y_{\theta}\right)
$$
The end-of-period wealth can be written as
$$
\begin{aligned}
\tilde{Y} &=\left(Y_{0}-C_{0}\right)\left(1+\tilde{r}_{P}\right) \\
\tilde{r}_{P} &=r_{f}+\Sigma_{i=1}^{N} w_{i}\left(\tilde{r}_{i}-r_{f}\right)
\end{aligned}
$$
Clearly an appropriate redefinition of the utility function leads to
$$
\max E u(\tilde{Y})=\max E u\left[\left(Y_{0}-C_{0}\right)\left(1+\tilde{r}_{P}\right)\right]=\operatorname{def} \max E \hat{u}(\tilde{r_{P}})
$$
The level of investable wealth, $\left(Y_{0}-C_{0}\right)$, becomes a parameter of the "U-hat" representation.

Finally, given the characteristics (e.g., expected return, standard deviation) of the optimally chosen portfolio, the optimal consumption and savings levels can be selected in step 1.

From now on we work with utility functions defined on $\tilde{r}_{P}$. **This utility index can be further constrained to be a function of the mean and variance of the probability distribution of $r_{P}$**

This simplification can be accepted either as a working approximation or it may result from two further (alternative) hypotheses made within the expected utility framework. 

## 6.2 Justifying Mean-Variance Utility

The mean-variance utility hypothesis seemed natural at the time the MPT first appeared, and it retains some intuitive appeal today. But viewed in the context of more recent developments in financial economics, particularly the development of vN-M expected utility theory, it now looks a bit peculiar.

The main justication for using a mean-variance approximation is its tractability

- Probability distributions are cumbersome to manipulate and difficult to estimate empirically
- Summarizing them by their first two moments is appealing

A first question for us, therefore, is: Under what conditions will investors have preferences over the means and variances of asset returns?

### 6.2.1 approximate case

In the approximate case, using a **simple Taylor series approximation**, one can also see that the mean and variance of an agent's wealth distribution are critical to the determination of his expected utility for any distribution.

If we start, as we did previously, by assuming an investor has preferences over terminal wealth $\tilde{Y}$, potentially random because of randomness in the asset returns, described by a vN-M expected utility function $E[u(\tilde{Y})]$ we can write
$$
\tilde{Y}=E(\tilde{Y})+[\tilde{Y}-E(\tilde{Y})]
$$
and interpret the portfolio problem as a trade-off between the expected payoff
$$
E(\tilde{Y})
$$
and the size of the "bet"
$$
[\tilde{Y}-E(\tilde{Y})]
$$

With this interpretation in mind, consider a second-order Taylor approximation of the Bernoulli utility function $u$ once the outcome $[\tilde{Y}-E(\tilde{Y})]$ of the bet is known:
$$
u(\tilde{Y}) \approx u[E(\tilde{Y})]+u^{\prime}[E(\tilde{Y})][\tilde{Y}-E(\tilde{Y})]+\frac{1}{2} u^{\prime \prime}[E(\tilde{Y})][\tilde{Y}-E(\tilde{Y})]^{2}
$$

Now go back to the beginning of the period, before the outcome of the bet is known, and take expectations to obtain
$$
E[u(\tilde{Y})] \approx u[E(\tilde{Y})]+\frac{1}{2} u^{\prime \prime}[E(\tilde{Y})] \sigma^{2}(\tilde{Y})
$$

The right-hand side of this expression is in the desired form: if u is increasing, it rewards higher mean returns and if u is concave, it penalizes higher variance in returns.

So one possible justification for mean-variance utility is to assume that the size of the portfolio bet $\tilde{Y}??? E(\tilde{Y})$ is small enough to make this Taylor approximation a good one. 

But it isn't safe to assume that portfolio bets are small.

### 6.2.2 Exact case

#### Case 1: Quadratic Utility Function

A second possibility is to assume that **the Bernoulli utility function is quadratic**, with
$$
u(Y)=a+b Y+c Y^{2}
$$
with $b>0$ and $c<0,$ Then
$$
\begin{aligned}
u^{\prime}(Y) &=b+2 c Y \\
u^{\prime \prime}(Y) &=2 c
\end{aligned}
$$
so that $u^{\prime \prime \prime}(Y)=0$ and all higher-order derivatives are zero as well. **In this case, the second-order Taylor approximation holds exactly.**

Note, however, that for a quadratic utility function
$$
R_{A}(Y)=-\frac{u^{\prime \prime}(Y)}{u^{\prime}(Y)}=-\frac{2 c}{b+2 c Y}
$$
which is increasing in $Y$.
Hence, quadratic utility has the undesirable implication that the amount of wealth allocated to risky investments declines when wealth increases.

#### Case 2: Normality Assumption

???Theorem???If $\tilde{Y}$ is normally distributed, there exists a function $v$ such that
$$
E u(\tilde{Y})=v\left(\mu_{Y}, \sigma_{Y}\right)
$$
Moreover, if $\tilde{Y}$ is normally distributed and

- $u$ is increasing, then $v$ is increasing in $\mu_{Y}$
- $u$ is concave, then $v$ is decreasing in $\sigma_{Y}$
- $u$ is concave, then indifference curves defined over $\mu_{Y}$ and $\sigma_{Y}$ are convex

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200417115416.png)

Problems with the normality assumption:

- limited liability instruments such as stocks can pay at worst a negative return of $-100 \%$ (complete loss of the investment)

- Returns on assets like options are highly non-normal.
- While the normal is perfectly symmetric about its mean, **high-frequency** returns are frequently skewed to the right and index returns appear skewed to the left
$$
S(\tilde{r_{i t}})=E\left[\frac{\left(r_{i t}-\mu_{i}\right)^{3}}{\sigma_{i}^{3}}\right]
$$

- Sample high-frequency return distributions for many assets exhibit excess kurtosis or "fat tails"
$$
K(\tilde{r_{i}})=E\left[\frac{\left(r_{i t}-\mu_{i}\right)^{4}}{\sigma_{i}^{4}}\right]
$$

## 6.3 $\max E \hat{u}(\tilde{r}_{P})$

In a mean-variance (M-V) framework, an investor's wants to maximize a function $u\left(\mu_{r}, \sigma_{P}\right)$. He likes expected return $\left(\mu_{r}\right)$ and dislikes standard deviation $\left(\sigma_{P}\right)$ 

Recall that portfolio $A$ is said to exhibit mean-variance dominance over portfolio B if either
$$
\begin{align*}
\mu_{A}>\mu_{B} \text { and } \sigma_{A} \leq \sigma_{B}\\
{\mu_{A} \geq \mu_{B}} \text { and } \sigma_{A} < \sigma_{B}
\end{align*}
$$
We can then define the **efficient frontier** as the set of all portfolios that are not mean-variance dominated by any other portfolio. By denition, no ("rational") mean-variance investor would choose to hold a portfolio not located on the efficient frontier.

The shape of the efficient frontier is of primary interest; let us examine the efficient frontier in the two-asset case for a variety of possible asset return correlations.

### 6.3.1 Two Risky Assets

Consider forming a portfolio from two risky assets:
$$
\begin{align*}
\tilde{r}_{1}, \tilde{r}_{2}&=\text{random returns}\\
\mu_{1}, \mu_{2}&=\text{expected returns}\\
\sigma_{1}, \sigma_{2}&=\text{standard deviations}
\end{align*}
$$
Assume $\mu_{1}<\mu_{2}$ and $\sigma_{1}<\sigma_{2}$ to create a trade-off between expected return and risk.

If $w$ is the fraction of initial wealth allocated to asset 1 and $1-w$ is the fraction of initial wealth allocated to asset $2,$ the random return $\tilde{r}_{P}$ on the portfolio is
$$
\tilde{r}_{P}=w \tilde{r}_{1}+(1-w) \tilde{r}_{2}
$$
and the expected return $\mu_{p}$ on the portfolio is
$$
\begin{aligned}
\mu_{P} &=E\left[w \tilde{r}_{1}+(1-w) \tilde{r}_{2}\right] \\
&=w E\left(\tilde{r}_{1}\right)+(1-w) E\left(\tilde{r}_{2}\right) \\
&=w \mu_{1}+(1-w) \mu_{2}
\end{aligned}
$$
The variance of the random portfolio return
$$
\begin{aligned}
\sigma_{P}^{2} &=E\left[\left(\tilde{r_{P}}-\mu_{P}\right)^{2}\right] \\
&=E\left(\left[w \tilde{r}_{1}+(1-w) \tilde{r}_{2}-w \mu_{1}-(1-w) \mu_{2}\right]^{2}\right) \\
&=E\left(\left[w\left(\tilde{r}_{1}-\mu_{1}\right)+(1-w)\left(\tilde{r}_{2}-\mu_{2}\right)\right]^{2}\right) \\
&=E[w^{2}\left(\tilde{r}_{1}-\mu_{1}\right)^{2}+(1-w)^{2}\left(\tilde{r}_{2}-\mu_{2}\right)^{2}\\
&\quad+2 w(1-w)\left(\tilde{r}_{1}-\mu_{1}\right)\left(\tilde{r}_{2}-\mu_{2}\right)] \\
&=w^{2} E\left[\left(\tilde{r}_{1}-\mu_{1}\right)^{2}\right]+(1-w)^{2} E\left[\left(\tilde{r}_{2}-\mu_{2}\right)^{2}\right] \\
&\quad+2 w(1-w) E\left[\left(\tilde{r}_{1}-\mu_{1}\right)\left(\tilde{r}_{2}-\mu_{2}\right)\right] \\
&=w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{12}\\
&=w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{1} \sigma_{2} \rho_{12}
\end{aligned}
$$
where
$$
\begin{aligned}
\sigma_{12}= \text{the covariance between } \tilde{r}_{1} \text{ and } \tilde{r}_{2} \\
\rho_{12}= \text{the correlation between } \tilde{r}_{1} \text{ and } \tilde{r}_{2}
\end{aligned}
$$

**The source of the gains from diversification**: the expected portfolio return is a weighted average of the expected returns on the individual asset returns, but the standard deviation of the portfolio return is not a weighted average of the standard deviations of the returns on the individual assets and can be reduced by choosing a mix of assets.

**Minimum Variance Portfolio(MVP)**
$$
\sigma_{P}^{2}=w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{1} \sigma_{2} \rho_{12}
$$
We can minimize the portfolio variance by setting the first derivative equal to zero:
$$
\frac{d \sigma_{P}^{2}}{d w}=2 w \sigma_{1}^{2}-2 \sigma_{2}^{2}+2 w \sigma_{2}^{2}+2 \sigma_{12}-4 w \sigma_{12}=0
$$
and solve for $w^{*}$
$$
w^{*}=\frac{\sigma_{2}^{2}-\sigma_{12}}{\sigma_{1}^{2}+\sigma_{2}^{2}-2 \sigma_{12}}
$$

#### Case 1: $\rho_{12}=1$

To see more specifically how this works, start with the case where $\rho_{12}=1$ so that the individual asset returns are perfectly correlated. This is the one case in which there are **no gains from diversification**. With $\rho_{12}=1$
$$
\begin{aligned}
\mu_{P} &=w \mu_{1}+(1-w) \mu_{2} \\
\sigma_{P} &=\left[w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{1} \sigma_{2} \rho_{12}\right]^{1 / 2} \\
&=\left[w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{1} \sigma_{2}\right]^{1 / 2} \\
&=\left(\left[w \sigma_{1}+(1-w) \sigma_{2}\right]^{2}\right)^{1 / 2} \\
&=w \sigma_{1}+(1-w) \sigma_{2}
\end{aligned}
$$
In this special case, the standard deviation of the return on the portfolio is a weighted average of the standard deviations of the returns on the individual assets.

![](https://upload-images.jianshu.io/upload_images/20447423-df4b8d20b1369389.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

To show that $P_{1} P_{2}$ is a straight line: no matter what percentage of wealth $w$ we choose to invest in $X$ the trade-off between expected value and standard deviation is constant.
$$
\begin{aligned}
\text { Slope } &=\frac{d \mu_{P}}{d \sigma_{P}} \\
&=\frac{d \mu_{P} / d w}{d \sigma_{P} / d w} \\
&=\frac{\mu_{2}-\mu_{1}}{\sigma_{2}-\sigma_{1}}
\end{aligned}
$$

#### Case 2: $\rho_{12}=-1$

Next, let's consider the opposite extreme, in which $\rho_{12}=-1$ so that the individual asset returns are perfectly, but negatively, correlated:
$$
\begin{aligned}
\sigma_{P} &=\left[w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}+2 w(1-w) \sigma_{1} \sigma_{2} \rho_{12}\right]^{1 / 2} \\
&=\left[w^{2} \sigma_{1}^{2}+(1-w)^{2} \sigma_{2}^{2}-2 w(1-w) \sigma_{1} \sigma_{2}\right]^{1 / 2} \\
&=\left(\left[w \sigma_{1}-(1-w) \sigma_{2}\right]^{2}\right)^{1 / 2} \\
&=\pm\left[w \sigma_{1}-(1-w) \sigma_{2}\right]
\end{aligned}
$$
In this special case, the setting
$$
\begin{align*}
w^{*}&=\frac{\sigma_{2}^{2}-\sigma_{12}}{\sigma_{1}^{2}+\sigma_{2}^{2}-2 \sigma_{12}}\\
&=\frac{\sigma_{2}}{\sigma_{1}+\sigma_{2}}
\end{align*}
$$
creates a "synthetic" risk free portfolio(at $w^{*}, \sigma_{P}=0$ )!
When $\rho_{12}=-1,$ so that individual asset returns are perfectly, but negatively correlated, risk can be eliminated via diversification.

![](https://upload-images.jianshu.io/upload_images/20447423-2b5e448c75ad1276.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

To show that $P_{2} P_{m v p}$ and $P_{m v p} P_{1}$ are linear: the slope is invariant to changes in percentage of an investor's portfolio invested in $X$
$$
\begin{aligned}
\text {Slope } P_{m v p} P_{1} &=\frac{d \mu_{P}}{d \sigma_{P}}=\frac{d \mu_{P} / d w}{d \sigma_{P} / d w} \\
&=\frac{\mu_{1}-\mu_{2}}{\sigma_{1}+\sigma_{2}}<0 \\
\text { Slope } P_{2} P_{m v p} &=\frac{d \mu_{P}}{d \sigma_{P}}=\frac{d \mu_{P} / d w}{d \sigma_{P} / d w} \\
&=\frac{\mu_{1}-\mu_{2}}{-\left(\sigma_{1}+\sigma_{2}\right)}>0
\end{aligned}
$$

#### Case 3: $???1 < \rho_{12} < 1$

In all intermediate cases, there will still be gains from diversification. These gains will become stronger as $\rho_{12}$ declines from 1 to -1.

In general, the MVF is convex, because it is bounded by the triangle ABC.

![](https://upload-images.jianshu.io/upload_images/20447423-68c858308865c7cd.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

As $\rho_{12}$ decreases from $\color{#F05}{0.5}  \color{#000}{\text{ to }0}, \color{#50A}{-0.5}, \color{#085}{-0.75}$, the gains from diversification strengthen.

![](https://upload-images.jianshu.io/upload_images/20447423-779612f41a3e8e19.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

### 6.3.2 Three Risky Assets

With three assets, for example, an investor can choose
$$
\begin{align*}
w_{1}&= \text{share of initial wealth allocated to asset 1}\\
w_{2}&= \text{share of initial wealth allocated to asset 2}\\
1-w_{1}-w_{2}&= \text{share of initial wealth allocated to asset 3}
\end{align*}
$$


Given the choices of $w_{1}$ and $w_{2}$
$$
\begin{aligned}
\tilde{r}_{P} &=w_{1} \tilde{r}_{1}+w_{2} \tilde{r}_{2}+\left(1-w_{1}-w_{2}\right) \tilde{r}_{3} \\
\mu p &=w_{1} \mu_{1}+w_{2} \mu_{2}+\left(1-w_{1}-w_{2}\right) \mu_{3} \\
\sigma_{p}^{2} &=w_{1}^{2} \sigma_{1}^{2}+w_{2}^{2} \sigma_{2}^{2}+\left(1-w_{1}-w_{2}\right)^{2} \sigma_{3}^{2} \\
&\quad +2 w_{1} w_{2} \sigma_{1} \sigma_{2} \rho_{12}+2 w_{1}\left(1-w_{1}-w_{2}\right) \sigma_{1} \sigma_{3} \rho_{13} \\
&\quad +2 w_{2}\left(1-w_{1}-w_{2}\right) \sigma_{2} \sigma_{3} \rho_{23}
\end{aligned}
$$

First , Find MVF

????????????2 ?????????????????????????????????????????????????????????????????????

In the case with two risky assets, the choice of w simultaneously determines $\mu_p$and $\sigma_p$.

Our problem is to solve

$$
\begin{align*}
\min _{w_{1}, w_{2}}\quad &\sigma_{P}^{2}\\
s.t.\quad  &\mu_{P}=\bar{\mu}
\end{align*}
$$
for a given value of $\bar{\mu}$.
But since we are more used to solving constrained maximization problems, consider the reformulated, but equivalent, problem:
$$
\begin{align*}
\max _{w_{1}, w_{2}}\quad &-\sigma_{P}^{2}\\
s.t.\quad  &\mu_{P}=\bar{\mu}
\end{align*}
$$
Set up the Lagrangian, using the expressions for $\mu_{P}$ and $\sigma_{P}$ derived previously:
$$
\begin{aligned}
L &=-{\Large[}w_{1}^{2} \sigma_{1}^{2}+w_{2}^{2} \sigma_{2}^{2}+\left(1-w_{1}-w_{2}\right)^{2} \sigma_{3}^{2}\\
&\quad+2 w_{1} w_{2} \sigma_{1} \sigma_{2} \rho_{12}+2 w_{1}\left(1-w_{1}-w_{2}\right) \sigma_{1} \sigma_{3} \rho_{13} \\
&\quad+2 w_{2}\left(1-w_{1}-w_{2}\right) \sigma_{2} \sigma_{3} \rho_{23}{\Large]} \\
&\quad+\lambda\left[w_{1} \mu_{1}+w_{2} \mu_{2}+\left(1-w_{1}-w_{2}\right) \mu_{3}-\bar{\mu}\right]
\end{aligned}
$$

F.O.C. for $w_{1}$
$$
\begin{aligned}
0 &=-2 w_{1}^{*} \sigma_{1}^{2}+2\left(1-w_{1}^{*}-w_{2}^{*}\right) \sigma_{3}^{2} \\
&-2 w_{2}^{*} \sigma_{1} \sigma_{2} \rho_{12}-2\left(1-w_{1}^{*}-w_{2}^{*}\right) \sigma_{1} \sigma_{3} \rho_{13} \\
&+2 w_{1}^{*} \sigma_{1} \sigma_{3} \rho_{13}+2 w_{2}^{*} \sigma_{2} \sigma_{3} \rho_{23} \\
&+\lambda^{*} \mu_{1}-\lambda^{*} \mu_{3}
\end{aligned}
$$
F.O.C. for $w_{2}$
$$
0=-2 w_{2}^{*} \sigma_{2}^{2}+2\left(1-w_{1}^{*}-w_{2}^{*}\right) \sigma_{3}^{2}
$$
$$
\begin{array}{l}
-\quad 2 w_{1}^{*} \sigma_{1} \sigma_{2} \rho_{12}+2 w_{1}^{*} \sigma_{1} \sigma_{3} \rho_{13} \\
-\quad 2\left(1-w_{1}^{*}-w_{2}^{*}\right) \sigma_{2} \sigma_{3} \rho_{23}+2 w_{2}^{*} \sigma_{2} \sigma_{3} \rho_{23} \\
+\quad \lambda^{*} \mu_{2}-\lambda^{*} \mu_{3}
\end{array}
$$
B.C.
$$
w_{1}^{*} \mu_{1}+w_{2}^{*} \mu_{2}+\left(1-w_{1}^{*}-w_{2}^{*}\right) \mu_{3}=\bar{\mu}
$$
The two first-order conditions and the constraint form a system of three equations in the three unknowns: $w_{1}^{*}, w_{2}^{*}$ and $\lambda^{*}$.

Moreover, the equations are linear in the unknowns $w_{1}^{*}, w_{2}^{*}$ and $\lambda^{*}$ Given specific values for $\mu_{1}, \mu_{2}, \mu_{3}, \sigma_{1}, \sigma_{2}, \sigma_{3}, \rho_{12}, \rho_{13}, \rho_{23},$ and $\bar{\mu}$ they can be solved quite easily.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080732.png)

### 6.3.3 N Risky Assets

Organize the portfolio shares and expected returns into a vectors:
$$
w=\left[\begin{array}{c}
w_{1} \\
w_{2} \\
\vdots \\
w_{N}
\end{array}\right] \quad \text { and } \quad \mu=\left[\begin{array}{c}
\mu_{1} \\
\mu_{2} \\
\vdots \\
\mu_{N}
\end{array}\right]
$$
where
$$
w_{1}+w_{2}+\ldots+w_{N}=1
$$
Meanwhile, the variances and covariances can be organized into a matrix - a collection of rows and columns:
$$
\Sigma=\left[\begin{array}{lccc}
\sigma_{1}^{2} & \sigma_{1} \sigma_{2} \rho_{12} & \dots & \sigma_{1} \sigma_{N} \rho_{1 N} \\
\sigma_{1} \sigma_{2} \rho_{12} & \sigma_{2}^{2} & \dots & \sigma_{2} \sigma_{N} \rho_{2 N} \\
& \cdot & \dots & \cdot \\
\sigma_{1} \sigma_{N} \rho_{1 N} & \sigma_{2} \sigma_{N} \rho_{2 N} & \dots & \sigma_{N}^{2}
\end{array}\right]
$$
Using the rules from linear algebra for multiplying vectors and matrices, the expected return on any portfolio with shares in the vector $w$ is
$$
\mu^{\prime} w
$$

and the variance of the random return on the portfolio is
$$
w^{\prime} \Sigma w
$$

Hence, the problem of minimizing the variance for a given mean can be written compactly as
$$
\max _{w}-w^{\prime} \Sigma w \quad \text { s.t. } \quad \mu^{\prime} w=\bar{\mu} \quad \text { and } \quad I^{\prime} w=1
$$
where $I$ is a vector of $N$ ones.

Problems of this form are called quadratic programming problems and can be solved very quickly on a computer even when the number of assets $N$ is large. We can also add more constraints, such as $w_{i} \geq 0,$ ruling out short sales.

The minimum variance frontier traces out the minimized variance or standard deviation for each required mean return.

Adding assets shifts the minimum variance frontier to the left, as opportunities for diversication are enhanced(???????????????????????????????????????????????????). 

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080633.png)

But portfolio A exhibits mean-variance dominance over portfolio B, since it offers a higher expected return with the same standard deviation.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080549.jpg)

Define the **efficient frontier** as the set of all portfolios that are not mean-variance dominated by any other portfolio. The efficient frontier extends only along the top arm of the minimum variance frontier.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080508.jpg)

### 6.3.4 N risky asset and 1 risk-free asset

So far, however, our analysis has assumed that there are only risky assets. An additional, quite striking, result emerges when we add a risk free asset to the mix.

This implication was first noted by **James Tobin** (US, 1918-2002, Nobel Prize 1981) in his paper ???Liquidity Preference as Behavior Towards Risk," Review of Economic Studies Vol.25 (February 1958): pp.65-86.

Risk free asset: money market mutual fund (MMMF), T-bill,  deposit rate. It is usually assumed that the rate of return on the risk-free asset is equal to the borrowing and lending rate in the economy.

Consider, therefore, the larger portfolio formed when an investor allocates the fraction $w$ of his or her initial wealth to a  to a portfolio of risky assets and the remaining fraction $1-w$ to a risk free asset with return $r_{f}$ If the risky part of this portfolio has random return $\tilde{r},$ expected return $\mu_{r}=E(\tilde{r})$ and variance $\sigma_{r}^{2}=E\left[\left(\tilde{r}-\mu_{r}\right)^{2}\right]$ then the larger portfolio has random return $\tilde{r}_{P}=w \tilde{r}+(1-w) r_{f}$ with expected return
$$
\mu_{P}=E\left[w \tilde{r}+(1-w) r_{f}\right]=w \mu_{r}+(1-w) r_{f}
$$
and variance
$$
\begin{aligned}
\sigma_{P}^{2} &=E\left[\left(\tilde{r}_{p}-\mu_{P}\right)^{2}\right] \\
&=E\left[w \tilde{r}+(1-w) r_{f}-w \mu_{r}-(1-w) r_{f}\right]^{2} \\
&=E\left[w\left(\tilde{r}-\mu_{r}\right)\right]^{2}=w^{2} \sigma_{r}^{2}
\end{aligned}
$$
The expression for the portfolio's variance
$$
\sigma_{P}^{2}=w^{2} \sigma_{r}^{2}
$$
implies
$$
\sigma_{P}=w \sigma_{r}
$$
Hence
$$
w=\frac{\sigma_{P}}{\sigma_{r}}
$$

Hence, with $\sigma_{r}$ given, a larger share of wealth $w$ allocated to risky assets is associated with a higher standard deviation $\sigma_{P}$ for the larger portfolio.

Then, we have
$$
\begin{aligned}
\mu_{P} &=\frac{\sigma_{P}}{\sigma_{r}} \mu_{r}+\left(1-\frac{\sigma_{P}}{\sigma_{r}}\right) r_{f} \\
&=r_{f}+\left(\frac{\mu_{r}-r_{f}}{\sigma_{r}}\right) \sigma_{P}
\end{aligned}
$$
It shows that for portfolios of risky and riskless assets:
o The relationship between $\sigma_{P}$ and $\mu_{P}$ is linear.
o The slope of the linear relationship is given by the **Sharpe ratio**, defined here as the "expected excess return" offered by the risky components of the portfolio divided by the standard deviation of the return on that risky component:
$$
\frac{\mu_{r}-r_{f}}{\sigma_{r}}
$$
Note that the tangency portfolio T can be identified as the portfolio along the efficient frontier of risky assets that has the highest Sharpe ratio.

All investors with mean-variance utility will prefer some combination of the risk free asset and risky portfolio T to any other portfolio.

???Theorem???With N risky assets and a risk-free one, the efficient frontier is a straight line.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200413183147.png)

### 6.3.5 Optimal Portfolio Choice

The optimal portfolio is naturally dened as that portfolio maximizing the investor's (mean-variance) utility; That portfolio for which he is able to reach the highest indifference curve in MV space;

#### Indifference Curve in MV Space

Recall that either of two sets of assumptions will imply that indifference curves in this $ \mu-\sigma $ diagram slope upward and are convex:

- Investors have vN-M expected utility with quadratic Bernoulli utility functions
- Asset returns are normally distributed and investors have vN-M expected utility with increasing and concave Bernoulli utility functions

??? 

Such curves will be increasing and convex from the origin; They are increasing because additional risk needs to be compensated by higher means; They are convex if and only if the investor is characterized by increasing absolute risk aversion (IARA), which is the case under MV preferences, as we have claimed.

#### Criterion

Each indifference curve maps out all combinations of risk and return that provide us with the same utility. The slope of indifference curve indicates the **marginal rate of substitution(MRS)** between our preference for risk and return, which is subjective.

The effcient frontier shows the tradeoff between risk and return, the slope of which indicates the marginal rate of transformation(MRT) offered by MVF. 

An important feature of the optimal portfolio that we choose to maximize our utility is that **the subjective MRS is exactly equal to the objectively determined MRT** between risk and return.

#### Without Risk-free Asset

Investor B is less risk averse than investor A. Different investors face the same assessment of the return and risk offered by risky assets, they may hold different portfolios. But all optimal
portfolios are along the efficient frontier.

Thus, the mean-variance utility hypothesis built into Modern Portfolio Theory implies that all investors choose optimal portfolios along the efficient frontier.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200425210954.png)

#### With Risk-free Asset

With $ MRS_A = \frac{\Delta \mu}{\Delta \sigma}> MRS_B $, investor B is less risk averse than investor A. But both choose same combination of the "tangency portfolio" T and the risk free asset.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200413193313.png)

??? Theorem???Any risk averse investor, independently of her risk aversion, will diversify between a risky (tangency portfolio) fund and the riskless asset.

???two-fund theorem/ separation theorem???all investors will invest in the same two funds, the risk-free asset on the one hand, and the risky portfolio (T) identified by the tangency point.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080430.png)

Equity mutual fund managers can all focus on building the unique portfolio that lies along the efficient frontier of risky assets and has the highest Sharpe ratio.

Each individual investor can then tailor his or her own portfolio by choosing the combination of the riskless assets and the risky mutual fund that best suits his or her own aversion to risk.

## 6.4 Pros and Cons of MPT

### 6.4.1 Cons

First, basic assumptions may not hold: either utility must be quadratic or asset returns must be normal to support mean-variance utility hypothesis.

Second, the estimation or "calibration" of the model's parameters.

With $N$ risky assets, the vector $\mu$ of expected returns contains $N$ elements and the matrix $\Sigma$ of variances and covariances contains $N(N+1) / 2$ unique elements. When $N=100,$ for example, there are $100+(100 \times 101) / 2=5150$ parameters to estimate!

And to use data from the past to estimate these parameters, one has to assume that past averages and correlations are a reliable guide to the future.

### 6.4.2 Pros

On the other hand, the MPT teaches us a very important lesson about how individual assets with imperfectly, and especially negatively, correlated returns can be combined into a diversified portfolio to reduce risk.

And the MPT's separation theorem suggests that a retirement savings plan that allows participants to choose between a money market mutual fund and a well-diversified equity fund is fully optimal under certain circumstances and perhaps close enough to optimal more generally.

Finally, our first equilibrium model of asset pricing, the Capital Asset Pricing Model, builds directly on the foundations provided by Modern Portfolio Theory. 

## 6.5 Practice

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080143.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080330.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427080348.png)
