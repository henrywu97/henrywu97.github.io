# 

# 6. Capital Asset Pricing Model

## 6.1 MPT and the CAPM

The Capital Asset Pricing Model builds directly on Modern Portfolio Theory. It was developed in the mid-1960s by William Sharpe (US,
b.1934, Nobel Prize 1990), John Lintner (US, 1916-1983), and Jan Mossin (Norway, 1936-1987).

- William Sharpe, "Capital Asset Prices: A Theory of Market Equilibrium Under Conditions of Risk," Journal of Finance Vol.19 (September 1964): pp.425-442.

- John Lintner, "The Valuation of Risk Assets and the Selection of Risky Investments in Stock Portfolios and Capital Budgets," Review of Economics and Statistics Vol.47 (February 1965 ): pp. 13-37.

- Jan Mossin, "Equilibrium in a Capital Asset Market," Econometrica Vol.34 (October 1966): pp.768-783.

Assumptions of the Capital Asset Pricing Model

- Investors are risk-averse individuals who maximize the expected utility of their end-of-period wealth
- Investors are price-takers and have **homogeneous expectations** about asset returns that have a joint normal distribution
- There exists a risk-free asset such that investors may borrow or lend unlimited amounts at the risk-free rate.
- The quantities of assets are fixed. All assets are marketable and perfectly divisible.
- Asset markets are frictionless and information is costless and simultaneously available to all investors.
- There are no market imperfections such as taxes, regulations, or restrictions on short selling.

But whereas Modern Portfolio Theory is a theory describing the
demand for financial assets, the Capital Asset Pricing Model is a
theory describing equilibrium in financial markets.

By making an additional assumption, that supply equals demand in financial markets, the CAPM yields additional
implications about the pricing of financial assets and risky cash 
flows.

Like MPT, the CAPM assumes that investors have mean-variance utility and hence that either investors have quadratic Bernoulli utility functions or that the random returns on risky assets are normally distributed.

Thus, some of the same caveats that apply to MPT also apply to the CAPM. For example, one might hesitate before applying the CAPM to price options.

The traditional CAPM also assumes that there is a risk free asset as well as a potentially large collection of risky assets. Under these circumstances, as we've seen, all investors will hold some combination of the riskless asset and the tangency portfolio: the efficient portfolio of risky assets with the highest Sharpe ratio.

But the CAPM goes further than the MPT by imposing an
equilibrium condition. Because there is no demand for risky financial assets except to the extent that they comprise the tangency portfolio, and because, in equilibrium, the supply of financial assets must equal demand, **the market portfolio consisting of all existing financial assets must coincide with the tangency portfolio.**

In equilibrium, that is, "everyone" must "own the market."

## 6.2 CAPM

### 6.2.1 CML

In the CAPM, equilibrium in financial markets requires the demand for risky assets |the tangency portfolio| to coincide with the supply of financial assets|the market portfolio.
The CAPM's first implication is immediate: the market portfolio is efficient.

The line originating at $\left(0, r_{f}\right)$ and running through $\left(\sigma_{M}, E\left(r_{M}\right)\right)$ is called the capital market line (CML).

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427120637.png)

Endowed with point $A,$ we always have two choices available when there is a capital market: moving along the MVF or moving along CML by borrowing and lending. First move to B where MRS=MRT of the MVF, and $U_1$ increases to $U_2$; Then we can better off by moving to $M$ and borrowing to reach $C$, utility increases to $U_{3}$.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427121450.png)

In equilibrium, the MRS is the same for all individuals, regardless of their subjective attitude to risk.

Hence, it also follows that all individually optimal portfolios are
located along the CML and are formed as combinations of the risk free asset and the market portfolio.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427132749.png)

Recall that the trade-off between the standard deviation and expected return of any portfolio combining the riskless asset and the tangency portfolio is described by the linear relationship
$$
E\left(\tilde{r}_{\mathrm{P}}\right)=r_{f}+\left[\frac{E\left(\tilde{r}_{T}\right)-r_{f}}{\sigma_{T}}\right] \sigma_{P}
$$
since the CAPM implies that the tangency and market portfolios coincide, the formula for the Capital Market Line is likewise
$$
E\left(\tilde{r}_{P}\right)=r_{f}+\left[\frac{E\left(\tilde{r}_{M}\right)-r_{f}}{\sigma_{M}}\right] \sigma_{P}
$$
And since all individually optimal portfolios are located along the CML, it implies that the market portfolio's Sharpe ratio
$$
\frac{E{(\tilde{r_M})}-r_f}{\sigma_M}
$$
measures the equilibrium price of risk: the expected return that each investor gives up when he or she adjusts his or her total portfolio to reduce risk.

### 6.2.2 Covariance

Consider making an equally weighted portfolio of $n$ assets, i.e., with all $w_{j}=1 / n .$ Assume that among the rates of return, one has the maximum variance, $\sigma_{\max }^{2} .$ 

1. $\lim _{n \rightarrow \infty} \sigma_{p}^{2}=\bar{\sigma}_{i j}$

Observe that
$$
\sigma_{p}^{2}=\sum_{i=1}^{n} \sum_{j=1}^{n} W_{i} W_{j} \sigma_{i j}
$$
An equally weighted portfolio has
$$
\sigma_{p}^{2}=\frac{1}{n^{2}} \Sigma_{i=1}^{n} \Sigma_{j=1}^{n} \sigma_{i j}=\frac{1}{n^{2}} \Sigma_{i=1}^{n} \sigma_{i}^{2}+\frac{1}{n^{2}} \Sigma_{i=1}^{n} \Sigma_{j \neq i} \sigma_{i j}
$$
Observe that the first term satisfies
$$
\frac{1}{n^{2}} \Sigma_{i=1}^{n} \sigma_{i}^{2}<\frac{1}{n^{2}} * n * \sigma_{\max }^{2} \rightarrow 0 \Leftarrow n \rightarrow \infty
$$
The second term satisfies
$$
\frac{1}{n^{2}} \Sigma_{i=1}^{n} \Sigma_{j \neq i} \sigma_{i j}=\frac{n^{2}-n}{n^{2}} \bar{\sigma}_{i j} \rightarrow \bar{\sigma}_{i j} \Leftarrow n \rightarrow \infty
$$
the average covariance between rates of return.

Thus
$$
\lim _{n \rightarrow \infty} \sigma_{p}^{2}=\bar{\sigma}_{i j}
$$
2. $\lim _{n \rightarrow \infty} \frac{\partial \sigma_{p}^{2}}{\partial w_{i}}=2 \bar{\sigma}_{i j}$

With
$$
\sigma_{p}^{2}=\sum_{i=1}^{N} \sum_{j=1}^{N} w_{i} w_{j} \sigma_{i j}=\sum_{i=1}^{N} w_{i}^{2} \sigma_{i}^{2}+\sum_{i \neq j} w_{i} w_{j} \sigma_{i j}
$$
Take derivative,
$$
\frac{\partial \sigma_{p}^{2}}{\partial w_{i}}=2 w_{i} \sigma_{i}^{2}+2 \Sigma_{j>i} w_{j} \sigma_{i j}
$$
Evaluated where all $w_{i}=1 / n,$ this becomes
$$
2 \frac{\sigma_{i}^{2}}{n}+2 \frac{n-1}{n} \bar{\sigma}_{i j} \rightarrow 2 \bar{\sigma}_{i j} \Leftarrow n \rightarrow \infty
$$
the average covariance between rates of return, and
$$
\lim _{n \rightarrow \infty} \frac{\partial \sigma_{p}^{2}}{\partial w_{i}}=2 \bar{\sigma}_{i j}
$$
### 6.2.3 Deriving the CAPM

Consider an equilibrium, everyone holds combination of risk free asset and market portfolio. Next, let's consider an arbitrary asset - "asset $j^{\prime \prime}-$ with random return $\tilde{r}_{j},$ expected return $E\left(\tilde{r}_{j}\right),$ and standard deviation $\sigma_{j} .$ (Possible, even though $M$ already contains $j$.))

MPT would take $E\left(\tilde{r}_{j}\right)$ and $\sigma_{j}$ as "data" - that is, as given.

The CAPM again goes further and asks: if asset $j$ is to be demanded by investors with mean-variance utility, what restrictions must $E\left(\tilde{r}_{j}\right)$ and $\sigma_{j}$ satisfy?

To answer this question, consider an investor who takes the portion of his or her initial wealth that he or she allocates to risky assets and divides it further: using the fraction $w$ to purchase asset $j$ and the remaining fraction $1-w$ to buy the market portfolio.

Note that since the market portfolio already includes some of asset $j$ choosing $w>0$ really means that the investor "overweights" asset $j$ in his or her own portfolio. Conversely, choosing $w<0$ means that the investor "underweights" asset $j$ in his or her own portfolio.

Based on our previous analysis, we know that this investor's portfol of risky assets now has random return
$$
\tilde{r}_{P}=w \tilde{r}_{j}+(1-w) \tilde{r}_{M}
$$
expected return
$$
E\left(\tilde{r}_{P}\right)=w E\left(\tilde{r}_{j}\right)+(1-w) E\left(\tilde{r}_{M}\right)
$$
and variance
$$
\sigma_{P}^{2}=w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}
$$
where $\sigma_{j M}$ is the covariance between $\tilde{r}_{j}$ and $\tilde{r}_{M} .$ We can use these formulas to trace out how $\sigma_{P}$ and $E\left(\tilde{r}_{P}\right)$ vary as $w$ changes.

The red curve traces out how $\sigma_{P}$ and $E\left(\tilde{r}_{P}\right)$ vary as $w$ changes, that is, as asset $j$ gets underweighted or overweighted relative to the market portfolio. 

The red curve passes through $M,$ since when $w=0$ the new portfolio coincides with the market portfolio. For all other values of $w$, however, the red curve must lie below the CML.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427184910.png)

Otherwise, a portfolio along the CML would be dominated in mean-variance by the new portfolio. Financial markets would no longer be in equilibrium, since some investors would no longer be willing to hold the market portfolio.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427185055.png)

Together, these observations imply that the red curve must be
tangent to the CML at point M.

Key point: Tangent means equal in slope.

We already know that the slope of the Capital Market Line is
$$
\frac{E\left(\tilde{r}_{M}\right)-r_{f}}{\sigma_{M}}
$$
But what is the slope of the red curve?

Let $f\left(\sigma_{P}\right)$ be the function defined by $E\left(\tilde{r}_{P}\right)=f\left(\sigma_{P}\right)$ and therefore describing the red curve.

Next, define the functions $g(w)$ and $h(w)$ by
$$
\begin{aligned}
g(w) &=E\left(\tilde{r}_{P}\right)=w E\left(\tilde{r}_{j}\right)+(1-w) E\left(r_{M}\right) \\
h(w) &=\sigma_{P}=\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}
\end{aligned}
$$
Substitute into
$$
E\left(\tilde{r}_{P}\right)=f\left(\sigma_{P}\right)
$$
then
$$
g(w)=f(h(w))
$$
and use the chain rule to compute
$$
g^{\prime}(w)=f^{\prime}(h(w)) h^{\prime}(w)=f^{\prime}\left(\sigma_{P}\right) h^{\prime}(w)
$$
and get
$$
f^{\prime}\left(\sigma_{P}\right)=\frac{g^{\prime}(w)}{h^{\prime}(w)}
$$
and compute $g^{\prime}(w)$ and $h^{\prime}(w)$ from the formulas we know
$$
g(w)=w E\left(\tilde{r}_{j}\right)+(1-w) E\left(r_{M}^{\prime}\right)
$$
implies
$$
g^{\prime}(w)=E\left(\tilde{r}_{j}\right)-E\left(\tilde{r}_{M}\right)
$$
$$
h(w)=\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}
$$

implies 
$$
\begin{aligned}
h^{\prime}(w)&=\frac{1}{2}\left(\frac{2 w \sigma_{j}^{2}-2(1-w) \sigma_{M}^{2}+2(1-2 w) \sigma_{j M}}{\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}}\right)\\
&=\frac{w \sigma_{j}^{2}-(1-w) \sigma_{M}^{2}+(1-2 w) \sigma_{j M}}{\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}}

\end{aligned}
$$
Thus
$$
\begin{aligned}
f^{\prime}\left(\sigma_{P}\right) &=\frac{g^{\prime}(w)}{h^{\prime}(w)} \\
&=\left[E\left(\tilde{r}_{j}\right)-E\left(\tilde{r}_{M}\right)\right]\\
&* \frac{\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}}{w \sigma_{j}^{2}-(1-w) \sigma_{M}^{2}+(1-2 w) \sigma_{j M}}
\end{aligned}
$$
The red curve is tangent to the CML at M. Hence $f^{\prime}\left(\sigma_{P}\right)$ equals the slope of the CML when $w=0$

When $w=0$ 
$$
\begin{aligned}
f^{\prime}\left(\sigma_{P}\right)&=\left[E\left(\tilde{r}_{j}\right)-E\left(r_{M}^{2}\right)\right] * \frac{\left[w^{2} \sigma_{j}^{2}+(1-w)^{2} \sigma_{M}^{2}+2 w(1-w) \sigma_{j M}\right]^{1 / 2}}{w \sigma_{j}^{2}-(1-w) \sigma_{M}^{2}+(1-2 w) \sigma_{j M}} \\
&=\frac{\left[E\left(\tilde{r}_{j}\right)-E\left(r_{M}\right)\right] \sigma_{M}}{\sigma_{j M}-\sigma_{M}^{2}}
\end{aligned}
$$
Meanwhile, we know that the slope of the CML is
$$
\frac{E(r \tilde{m})-r_{f}}{\sigma_{M}}
$$
The tangency of the red curve with the CML at M therefore requires
$$
\frac{\left[E\left(\tilde{r}_{j}\right)-E\left(\tilde{r}_{M}\right)\right] \sigma_{M}}{\sigma_{j M}-\sigma_{M}^{2}}=\frac{E(r \tilde{m})-r_{f}}{\sigma_{M}}
$$
Finally, we have
$$
E\left(\tilde{r}_{j}\right)=r_{f}+\frac{\sigma_{j M}}{\sigma_{M}^{2}}\left[E\left(r_{M}^{\prime}\right)-r_{f}\right]
$$
Let
$$
\beta_{j}=\frac{\sigma_{j M}}{\sigma_{M}^{2}}
$$
so that this key equation of the CAPM can be written as
$$
E\left(\tilde{r}_{j}\right)=r_{f}+\beta_{j}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
where $\beta_{j},$ the "beta" for asset $j,$ depends on the covariance between the returns on asset $j$ and the market portfolio.

This equation summarizes a very strong restriction. It implies that if we rank individual stocks or portfolios of stocks according to their betas, their expected returns should all lie along a single security market line with slope $E\left(r_{M}\right)-r_{f}$

According to the CAPM, all assets and portfolios of assets lie along a single **security market line**. Those with higher betas have higher expected returns.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200427190857.png)

Any portfolio of m securities locate on the SML. Show for $m=2$: 
$$
\begin{aligned}
\mu_{p} &=w \mu_{i}+(1-w) \mu_{j} \\
&\left.=w\left[r_{f}+\beta_{i}\left(\mu_{M}-r_{f}\right)\right]+(1-w)\left[r_{f}+\beta_{j}\left(\mu_{M}-r_{f}\right)\right]\right) \\
&=r_{f}+\left[w \beta_{i}+(1-w) \beta_{j}\right]\left(\mu_{M}-r_{f}\right) \\
&=r_{f}+\left[w \frac{\operatorname{cov}\left(\tilde{r}_{i}, r_{M}^{2}\right)}{\sigma_{M}^{2}}+(1-w) \frac{\operatorname{cov}\left(\tilde{r}_{j}, r_{M}^{2}\right)}{\sigma_{M}^{2}}\right]\left(\mu_{M}-r_{f}\right) \\
&=r_{f}+\frac{\operatorname{cov}\left(w \tilde{r}_{i}+(1-w) \tilde{r}_{j}, r_{M}^{2}\right)}{\sigma_{M}^{2}}\left(\mu_{M}-r_{f}\right) \\
&=r_{f}+\frac{\operatorname{cov}\left(\tilde{r}_{p}, r_{M}^{2}\right)}{\sigma_{M}^{2}}\left(\mu_{M}-r_{f}\right) \\
&=r_{f}+\beta_{p}\left(\mu_{M}-r_{f}\right)
\end{aligned}
$$
$\beta_{p}$ is a value-weighted average of $\beta_{i}$ and $\beta_{j}$, which means that $\beta$ is additive.

### 6.2.4 CML V.S. SML

Capital Market Line

- Efficient set given 1 risk free and $n$ risky assets.
- Relevant for choice between alternative portfolios.
- Drawn in $\left(\sigma_{p}, \mu_{p}\right)$ diagram.
- ray starting at $\left(0, r_{f}\right)$ in that diagram. 

Security market line

- Location of all traded assets in equilibrium.
- Also location of any portfolio of these assets.
- Not relevant for choice between assets which are already traded, so that equilibrium prices are observable.
- But relevant if equilibrium price at $t=0$ is unknown.
- Drawn in $\left(\beta_{j}, \mu_{j}\right)$ diagram.
- A line through $\left(0, r_{f}\right)$ in that diagram

With
$$
\begin{aligned}
&\sigma_{i M}=\rho_{iM} \cdot \sigma_{i} \sigma_{M}\\
&\beta_{i}=\frac{\sigma_{i M}}{\sigma_{M}^{2}}=\frac{\rho_{iM} \cdot \sigma_{i} \sigma_{x}}{\sigma_{m}^{2}}=\frac{\rho_{iM} \cdot \sigma_{i}}{\sigma_{M}}
\end{aligned}
$$

Rewrite CML & SML
$$
\begin{aligned}
&S M L: \quad E\left(\tilde{r}_{i}\right)=r_{f}+\frac{E\left(\tilde{r}_{M}\right)-r_{f}}{\sigma_{M}} \rho_{i M} \cdot \sigma_{i}\\
&C M L: \quad E\left(\tilde{r}_{i}\right)=r_{f}+\frac{E\left(\tilde{r_M}\right)-r_{f}}{\sigma_{M}}\sigma_i
\end{aligned}
$$

Thus an asset lies on both CML & SML i.f.f. $\rho_{iM}=1$. While any asset lies a SML. Therefore, a asset lies on CML i.f.f. it's market portfolio or the combination of market portfolio & risk-free asset.

### 6.2.5 Interpretation

$$
E\left(\tilde{r}_{j}\right)=r_{f}+\frac{\sigma_{j M}}{\sigma_{M}^{2}}\left[E\left(r_{M}^{\prime}\right)-r_{f}\right]
$$

The expected rate of return on any asset depends on only one characteristic of that asset, namely its rate of return's covariance with the rate of return on the market portfolio.

The expected rate of return is equal to the risk free interest rate plus a term which depends on a measure of risk. (Higher risk means higher expected rate of return.) The relevant measure of risk is the asset's beta. This is multiplied with the expected excess rate of return on the market portfolio.

Risk measure depends on covariance because the covariance
determines how much that asset will contribute to the risk of the agent's portfolio. This is true for any agent, since all hold the same risky portfolio.

There are two complementary ways of interpreting this result.
Both bring us back to the theme of diversification emphasized by MPT. Both take us a step further, by emphasizing as well the idea of aggregate risk, which cannot be "diversified away," and idiosyncratic
risk, which can be diversified away.

#### Aggregate risk & idiosyncratic risk

The first approach uses the CAPM equation in its original form
$$
E\left(\tilde{r}_{j}\right)=r_{f}+\frac{\sigma_{j M}}{\sigma_{M}^{2}}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
together with the definition of correlation, which implies
$$
\rho_{j M}=\frac{\sigma_{j M}}{\sigma_{j} \sigma_{M}}
$$
Then the CAPM relationship
$$
E\left(\tilde{r}_{j}\right)=r_{f}+\left[\frac{E\left(\tilde{r}_{M}\right)-r_{f}}{\sigma_{M}}\right] \rho_{j M} \sigma_{j}
$$
The term inside brackets is the equilibrium price of risk. And since the correlation lies between -1 and 1 , the term $\rho_{j M} \sigma_{j}$ satisfying
$$
\rho_{j M} \sigma_{j} \leq \sigma_{j}
$$
represents the "portion" of the total risk $\sigma_{j}$ in asset $j$ that is correlated with the market return.

![](https://upload-images.jianshu.io/upload_images/20447423-7cad6eb2d4dbb08a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

The **idiosyncratic risk** in asset j , that is, the portion that is uncorrelated with the market return, can be diversified away by holding the market portfolio.

Since this risk can be freely shed through diversification, it is not "priced."

Hence, according to the CAPM, risk in asset j is priced only to the extent that it takes the form of aggregate risk that, because it is correlated with the market portfolio, cannot be diversified away.

Thus, according to the CAPM:

- Only assets with random returns that are positively correlated with the market return earn expected returns above the risk free rate. They must, in order to induce investors to take on more aggregate risk.

- Assets with returns that are uncorrelated with the market return have expected returns equal to the risk free rate, since their risk can be completely diversified away.

- Assets with negative betas??????that is, with random returns that are negatively correlated with the market return?????? have expected returns below the risk free rate! For these assets, $E(\tilde{r_j}) -  r_f < 0$ is like an "insurance premium" that investors will pay in order to insulate themselves from aggregate risk.

#### Statistical interpretation

The second approach to interpreting the CAPM uses
$$
E\left(\tilde{r}_{j}\right)=r_{f}+\beta_{j}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
together with the definition of
$$
\beta_{j}=\frac{\sigma_{j M}}{\sigma_{M}^{2}}
$$
Consider a statistical regression of the random return $\tilde{r}_{j}$ on asset $j$ on a constant and the market return $\tilde{r}_{M}$
$$
\tilde{r}_{j}=\alpha+\beta_{j} \tilde{r_n}+\varepsilon_{j}
$$
This regression breaks the variance of $\tilde{r}_{j}$ down into two "orthogonal" (uncorrelated) components:

- The component $\beta_{j} r_{M}$ that is systematically related to variation in the market return.

- The component $\varepsilon_{j}$ that is not. 

The slope coefficient in a linear regression is
$$
\beta_{j}=\frac{\sigma_{j M}}{\sigma_{M}^{2}}
$$
the same "beta" as in the CAPM!

But this is not an accident: to the contrary, it restates the conclusion that, according to the CAPM, risk in an individual asset is only to the extent that it is correlated with the market return.
$$
\begin{aligned}
\tilde{r}_{j} &=\alpha+\beta_{j} \tilde{r}_{M}+\varepsilon_{j} \\
E\left(\tilde{r}_{j}\right) &=r_{f}+\beta_{j}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
\end{aligned}
$$
the CAPM equation implies $E\left(\varepsilon_{j}\right)=0$ and
$$
\begin{aligned}
\operatorname{cov}\left(\varepsilon_{j}, \tilde{r_{M}}\right) &=\operatorname{cov}\left(\tilde{r}_{j}-\alpha-\beta_{j} r \tilde{M}, r_{M}^{2}\right) \\
&=\operatorname{cov}\left(\tilde{r}_{j}, r_{M}\right)-\beta_{j} \operatorname{var}\left(\tilde{r}_{M}\right) \\
&=\sigma_{j M}-\beta_{j} \sigma_{M}^{2}=0
\end{aligned}
$$
This allows us to split $\sigma_{j}^{2}$ in two parts:
$$
\operatorname{var}\left(\tilde{r}_{j}\right) \equiv \sigma_{j}^{2}=\beta_{j}^{2} \sigma_{M}^{2}+\sigma_{\varepsilon_{j}}^{2}=\beta_{j} \sigma_{j M}+\sigma_{\varepsilon_{j}}^{2}
$$
First term is the aggregate risk. This is reflected in the market valuation. Second term is the unsystematic risk or idiosyncratic risk. As we have seen, it is not reflected in market valuation. The sum of the two called total risk or variance risk. This is relevant for portfolios(MPT), evaluated for being the total wealth of someone, but not for individual securities, to be combined with other securities in portfolios.

##### Asset evaluation

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200429113612.png)

The Security Market Line indicates the required rate of return in equilibrium 

- if the actual return lies above SML: underpriced, so buy it
- if the actual return lies below SML: overpriced, so sell it
- excess return(alpha)=actual return-required return

## 6.3 Application of CAPM

### 6.3.1 Valuing Risky Cash Flows

Let $\tilde{C}_{t+1}$ denote a random payoff to be received at time $t+1$ ("one period from now" and let $P_{t}^{C}$ denote its price at time $t$ ("today.")

If $\tilde{C}_{t+1}$ was known in advance, that is, if the payoff were riskless, we could find its value by discounting it at the risk free rate:
$$
P_{t}^{C}=\frac{\tilde{C}_{t+1}}{1+r_{f}}
$$
But when $\tilde{C}_{t+1}$ is truly random, we need to find its expected value $E\left(\tilde{C}_{t+1}\right)$ and then "penalize" it for its riskiness either by discounting at a higher rate
$$
P_{t}^{C}=\frac{E\left(\tilde{C}_{t+1}\right)}{1+r_{f}+\psi}
$$
or by reducing its value more directly
$$
P_{t}^{C}=\frac{E\left(\tilde{C}_{t+1}\right)-\Psi}{1+r_{f}}
$$
The CAPM can help us identify the appropriate risk premium $\psi$ or $\Psi$.

#### risk premium $\psi$ 

Our previous analysis suggests that, broadly speaking, the risk premium implied by the CAPM will somehow depend on the extent to which the random payoff $\tilde{C}_{t+1}$ is correlated with the return on the market portfolio.

To apply the CAPM to this valuation problem, we can start by observing that with price $P_{t}^{C}$ today and random payoff $\tilde{C}_{t+1}$ one period from now, the return on this asset or investment project is defined by
$$
1+\tilde{r}_{C}=\frac{\tilde{C}_{t+1}}{P_{t}^{C}}
$$
or
$$
\tilde{r}_{C}=\frac{\tilde{C}_{t+1}-P_{t}^{C}}{P_{t}^{C}}
$$
where the notation $\tilde{r}_{C}$ emphasizes that this return, like the future cash flow itself, is risky.

Now the CAPM implies that the expected return $E\left(\tilde{r}_{C}\right)$ must satisfy
$$
E\left(\tilde{r}_{\mathrm{C}}\right)=r_{f}+\beta_{C}\left[E\left(r_{M}^{\prime}\right)-r_{f}\right]
$$
where the project's beta depends on the covariance of its return with the market return:
$$
\beta_{C}=\frac{\sigma_{C M}}{\sigma_{M}^{2}}
$$
This is what takes skill: with an existing asset, one can use data on the past correlation between its return and the market return to estimate beta. With a totally new project that is just being planned, a combination of experience, creativity, and hard work is often needed to choose the right value for $\beta_{C}$.

But once a value for $\beta_{C}$ is determined, we can use
$$
E\left(\tilde{r}_{C}\right)=r_{f}+\beta_{C}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
together with the definition of the return itself
$$
\tilde{r}_{C}=\frac{\tilde{C}_{t+1}}{P_{t}^{C}}-1
$$
to write
$$
E\left(\frac{\tilde{C}_{t+1}}{P_{t}^{C}}-1\right)=r_{f}+\beta_{C}\left[E\left(r_{M}\right)-r_{f}\right]
$$
which implies
$$
\begin{aligned}
\left(\frac{1}{P_{t}^{C}}\right) E\left(\tilde{C}_{t+1}\right) &=1+r_{f}+\beta_{C}\left[E\left(r_{M}\right)-r_{f}\right] \\
P_{t}^{C} &=\frac{E\left(\tilde{C}_{t+1}\right)}{1+r_{f}+\beta_{C}\left[E\left(r_{M}\right)-r_{f}\right]}
\end{aligned}
$$
Right-hand side is "expected present value", with Risk-adjusted discount rate(RADR). Risk-adjustment again depends on $\left(E\left(\tilde{r}_{M}\right)-r_{f}\right) / \sigma_{M}^{2}$ and covariance.
$$
E\left(\tilde{r}_{C}\right)=r_{f}+\beta_{C}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
the CAPM implies a risk premium of
$$
\psi=\beta_{C}\left[E\left(\tilde{r_{M}}\right)-r_{f}\right]
$$
depends critically on the covariance between the return on the risky project and the return on the market portfolio.

#### risk premium $\Psi$

Alternatively,
$$
\left(\frac{1}{P_{t}^{C}}\right) E\left(\tilde{C}_{t+1}\right)=1+r_{f}+\beta_{C}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right]
$$
can be rewritten as
$$
P_{t}^{C}=\frac{E\left(\tilde{C}_{t+1}\right)-P_{t}^{C} \beta_{C}\left[E\left(\tilde{r_{M}}\right)-r_{f}\right]}{1+r_{f}}
$$
indicating that the CAPM also implies
$$
\Psi=P_{t}^{C} \beta_{C}\left[E\left(\tilde{r_{M}}\right)-r_{f}\right]
$$
which, again as expected, depends critically on the covariance between the return on the risky project and the return on the market portfolio.
$$
P_{t}^{C}=\frac{E\left(\tilde{C}_{t+1}\right)-P_{t}^{C} \beta_{C}\left[E\left(\tilde{r_{M}}\right)-r_{f}\right]}{1+r_{f}}
$$
Note that
$$
E\left(\tilde{C}_{t+1}\right)-P_{t}^{C} \beta_{C}\left[E\left(\tilde{r_{M}}\right)-r_{f}\right]
$$
is called the certainty equivalent (in the CAPM sense) of $\tilde{C}_{t+1}$. Price today is present value of expression, just as if that would be received with certainty one period into the future. Not what is called certainty equivalent in expected utility theory.
$$
\begin{aligned}
\left(\frac{1}{P_{t}^{C}}\right) E\left(\tilde{C}_{t+1}\right) &=1+r_{f}+\beta_{C}\left[E\left(\tilde{r}_{M}\right)-r_{f}\right] \\
&=1+r_{f}+\frac{\operatorname{Cov}\left(\frac{\tilde{C}_{t+1}}{P_{t}}-1, \tilde{r}_{M}\right)}{\sigma_{M}^{2}}\left[E\left(r_{M}^{2}\right)-r_{f}\right] \\
&=1+r_{f}+\frac{E\left(r_{M}\right)-r_{f}}{\sigma_{M}^{2}}\left[\operatorname{Cov}\left(\frac{\tilde{C}_{t+1}}{P_{t}^{C}}, r_{M}^{-}\right)-\operatorname{Cov}\left(1, r_{M}\right)\right] \\
&=1+r_{f}+\lambda \operatorname{Cov}\left(\frac{\tilde{C}_{t+1}}{P_{t}^{C}}, r_{M}^{-}\right) \\
&=1+r_{f}+\lambda \frac{\operatorname{Cov}\left(\tilde{C}_{t+1}, \tilde{r}_{M}\right)}{P_{t}^{C}}
\end{aligned}
$$
where $\lambda=\left(\mu_{M}-r_{f}\right) / \sigma_{M}^{2}$

Multiply $P_{t}^{C}$ on both sides
$$
E\left(\tilde{C}_{t+1}\right)=P_{t}^{C}\left(1+r_{f}\right)+\lambda \operatorname{Cov}\left(\tilde{C}_{t+1}, \tilde{r}_{M}\right)
$$
and thus
$$
P_{t}^{C}=\frac{E\left(\tilde{C}_{t+1}\right)-\lambda \operatorname{Cov}\left(\tilde{C}_{t+1}, \tilde{r}_{M}\right)}{1+r_{f}}
$$

#### Valuation of firms

$$
P_{0}^{c}=\frac{E\left(\tilde{C}_{1}\right)-\lambda \operatorname{Cov}\left(\tilde{C}_{1}, \tilde{r}_{M}\right)}{1+r_{f}} \equiv V\left(\tilde{C}_{1}\right)
$$
defines valuation function $V\left(\text { ), given some } r_{f}, r_{M}\right.$

- $\tilde{C}_{1}$ is value of share at $t=1,$ including dividends.
- Consider firm is financed $100 \%$ by equity (no debt). Firm's net cash flow at $t=1$ goes to shareholders, thus plug in the net cash flow instead of $\tilde{C}_{1}$, Then formula gives value of all shares in firm.

What if $\tilde{C}_{1}=a \tilde{C}_{i 1}+b \tilde{C}_{j 1}$? $(a>0, b>0)$ 

Linearity of $E()$ and $\operatorname{cov}()$ implies $P_{0}^{C}=a P_{0}^{i}+b P_{0}^{i}$
$$
\begin{aligned}
P_{0}^{C} &=\frac{E\left(\tilde{C}_{1}\right)-\lambda \operatorname{Cov}\left(\tilde{C}_{1}, r_{M}\right)}{1+r_{f}} \\
&=\frac{E\left(a \tilde{C}_{i 1}+b \tilde{C}_{j 1}\right)-\lambda \operatorname{cov}\left(\tilde{C}_{1}, r_{M}\right)}{1+r_{f}} \\
&=\frac{E\left(a \tilde{C}_{i 1}+b \tilde{C}_{j 1}\right)-\lambda \operatorname{cov}\left(a \tilde{C}_{i 1}+b \tilde{C}_{j 1}, r_{M}\right)}{1+r_{f}} \\
&=\frac{\partial E\left(\tilde{C}_{i 1}\right)+b E\left(\tilde{C}_{j 1}\right)-\lambda\left[\operatorname{acov}\left(\tilde{C}_{i 1}, r_{M}\right)+b \operatorname{cov}\left(\tilde{C}_{j 1}, \tilde{r}_{M}\right)\right]}{1+r_{f}} \\
&=a P_{0}^{i}+b P_{0}^{j}
\end{aligned}
$$
where $\lambda=\left(\mu_{M}-r_{f}\right) / \sigma_{M}^{2}$ Diversification is no justification for mergers; Diversification can be done by shareholders.

## 6.4 Pros and Cons of CAPM

### 6.4.1 empirical shortcomings

An enormous literature is devoted to empirically testing the CAPM's implications.

Although results are mixed, studies have shown that when individual portfolios are ranked according to their betas, expected returns tend to line up as suggested by the theory.

A famous article that presents results along these lines is by Eugene Fama (Nobel Prize 2013) and James MacBeth, "Risk, Return, and Equilibrium," Journal of Political Economy Vol.81 (May-June 1973),pp.607-636.

Early work on the MPT, the CAPM, and econometric tests of the efficient markets hypothesis and the CAPM is discussed extensively in Eugene Fama's 1976 textbook, Foundations of Finance.

More recent evidence against the CAPM's implications is presented by Eugene Fama and Kenneth French, "Common Risk Factors in the Returns on Stocks and Bonds," Journal of Financial Economics Vol.33 (February 1993): pp.3-56.

This paper shows that equity shares in small firms and in firms with high book (accounting) to market value have expected returns that differ strongly from what is predicted by the CAPM alone.

Quite a bit of recent research has been directed towards understanding the source of these "anomalies".

### 6.4.2 Pros

Despite some **empirical shortcomings**, however, the CAPM quite usefully deepens our understanding of the gains from diversification.

Related, the CAPM alerts us to the important distinction between idiosyncratic risk, which can be diversified away, and aggregate risk, which cannot.

Like MPT, the CAPM must rely on one of the **two strong assumptions**??????either quadratic utility or normally-distributed returns|that justify mean-variance utility.

And while the CAPM is an equilibrium theory of asset pricing, it stops short of linking asset returns to underlying economic fundamentals.

### 6.4.3 APT & ADT

These last two points motivate our interest in other asset pricing theories, which are less restrictive in their assumptions and/or draw closer connections between asset prices and the economy as a whole.

Arbitrage Pricing Theory, to which we will turn our attention next, yields many of the same implications as the CAPM, but
requires less restrictive assumptions about preferences and the distribution of asset returns.

The equilibrium version of Arrow-Debreu theory draws links between asset prices and the economy that are only implicit in the CAPM.
