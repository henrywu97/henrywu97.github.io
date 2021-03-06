# 

# 3. Nonparametric Regression Estimation

**Question**: How to estimate a regression function $ E\left(Y_{t} | X_{t}\right) $ using an observed bivariate sample $ \left\{Y_{t}, X_{t}\right\}_{t=1}^{T} $? Note that both $ Y_{t} $ and $ X_{t} $ are random variables here.

We first consider a few examples of regression functions.

**Example 1**: The auto-regression function
$$
r_{j}\left(X_{t-j}\right)=E\left(X_{t} | X_{t-j}\right)
$$

We can write

$$
X_{t}=r_{j}\left(X_{t-j}\right)+\varepsilon_{t}
$$

where $ E\left(\varepsilon_{t} | X_{t-j}\right)=0 $.

**Example 2**: The conditional variance
$$
\begin{aligned}
\sigma_{j}^{2}(x) &=\operatorname{var}\left(X_{t} | X_{t-j}\right) \\
&=E\left(X_{t}^{2} | X_{t-j}\right)-\left[E\left(X_{t} | X_{t-j}\right)\right]^{2}
\end{aligned}
$$

**Example 3**: The conditional distribution function

$$
\begin{aligned}
F_{t}(x) &=P\left(X_{t} \leq x | I_{t-1}\right) \\
&=E\left[1\left(X_{t} \leq x\right) | I_{t-1}\right]
\end{aligned}
$$

where $ I_{t-1} $ is an information set available at time $ t-1 . $ If we assume that $ \left\{X_{t}\right\} $ is an Markovian process. Then

$$
F_{t}(x)=E\left[1\left(X_{t} \leq x\right) | X_{t-1}\right]
$$

This is a **generalized regression function** of $ 1\left(X_{t} \leq x\right) $ on $ X_{t-1} $.

**Example 4**: The conditional characteristic function
$$
\varphi_{t}(u)=E\left[\exp \left(i u X_{t}\right) | I_{t-1}\right]
$$

If $ \left\{X_{t}\right\} $ is an Markovian process, then

$$
\varphi_{t}(u)=E\left[\exp \left(i u X_{t}\right) | X_{t-1}\right]
$$

This is a **generalized regression function** of $ \exp \left(i u X_{t}\right) $ on $ X_{t-1} $.

## 3.1 Kernel Regression Estimation

We first impose a **regularity condition** on the data generating process and the regression function.

**Assumption [DGP]**: (i) Suppose $ \left\{Y_{t}, X_{t}\right\}^{\prime} $ is an **IID** sequence such that the regression function $ r(x) \equiv E\left(Y_{t} | X_{t}=x\right) $ exists and is *twice continuously differentiable*; (ii) $ X_{t} $ is a continuous random variable with support $ [a, b] $ and probability density $ g(x) $ which is also *twice continuously differentiable* over $ [a, b] . $ Furthermore, $ g(x)>0 $ for all $ x \in[a, b] $.

We will relax the IID assumption to a serially dependent time series process at a later stage. Like in the case of density estimation, allowing mild serial dependence (e.g., $ \alpha $-mixing) in $ \left\{Y_{t}, X_{t}\right\}^{\prime} $ will not affect the asymptotic results derived under the IID assumption.

**Question**: How to estimate the regression function $ r(x) $?

We can always write

$$
Y_{t}=r\left(X_{t}\right)+\varepsilon_{t}
$$

where $ E\left(\varepsilon_{t} | X_{t}\right)=0 $ and $ \operatorname{var}\left(\varepsilon_{t} | X_{t}\right)=\sigma^{2}\left(X_{t}\right) $. Note that conditional heteroskedasticity may exist. We impose a continuity condition on $ \sigma^{2}(x) $.

**Assumption [Conditional Heteroskedasticity]**: $ \sigma^{2}(x) $ is continuous over the support $ [a, b] $ of $ X_{t} $.

###3.1.1 Nadaraya-Watson Estimator

For any given $ x $ in the support of $ X_{t}, $ define a kernel-based regression estimator

$$
\hat{r}(x)=\frac{\hat{m}(x)}{\hat{g}(x)}
$$

where the numerator

$$
\hat{m}(x)=\frac{1}{T} \sum_{t=1}^{T} Y_{t} K_{h}\left(x-X_{t}\right)
$$

is a weighted sample mean of $ \left\{Y_{t}\right\}, $ and, as before, the denominator

$$
\hat{g}(x)=T^{-1} \sum_{t=1}^{T} K_{h}\left(x-X_{t}\right)
$$

is the kernel estimator for density $ g(x) $ at point $ x . $ This kernel regression estimator was proposed by Nadaraya (1964) and Watson (1964) and so is also called the Nadaraya-Watson estimator.

Alternatively, we can express

$$
\hat{r}(x)=\sum_{t=1}^{T} \hat{W}_{t}(x) Y_{t}
$$

where the weighting function

$$
\hat{W}_{t}(x)=\frac{K_{h}\left(x-X_{t}\right)}{\sum_{t=1}^{T} K_{h}\left(x-X_{t}\right)}
$$

which sums to unity, that is,

$$
\sum_{t=1}^{T} \hat{W}_{t}=1
$$

Therefore, the Nadaraya-Watson estimator is a local weighted sample mean of $ \left\{Y_{t}\right\}_{t=1}^{n} $ where the weight $ \hat{W}_{t}(x) $ is zero outside the interval $ [x-h, x+h] $ when the kernel $ K(u) $ has bounded support on [-1,1].

We first provide a geometric interpretation for $ \hat{r}(x) . $ When the uniform kernel $ K(u)= $ $ \frac{1}{2} 1(|u| \leq 1) $ is used, the Nadaraya-Watson estimator becomes

$$
\hat{r}(x)=\frac{\sum_{t=1}^{T} Y_{t} 1\left(\left|X_{t}-x\right| \leq h\right)}{\sum_{t=1}^{T} 1\left(\left|X_{t}-x\right| \leq h\right)}
$$

This is a **local sample mean**, that is, the average of the observations $ \left\{Y_{t}\right\}_{t=1}^{T} $ for which the values of the corresponding explanatory variables $ \left\{X_{t}\right\} $ fall into the interval $ [x-h, x+h] $. Tukey (1961) calls this estimator the regressogram. **Intuitively**, suppose $ r(\cdot) $ is a smooth function, and we consider a small interval $ [x-h, x+h], $ which is centered at point $ x $ and has size $ 2 h, $ where $ h $ is small. Then $ r(\cdot) $ will be nearly a constant over this small interval and can be estimated by taking an average of the observations $ \left\{Y_{t}\right\} $ which correspond to those $ \left\{X_{t}\right\} $ whose values fall into the small interval.

More generally, we can assign different weights to observations of $ \left\{Y_{t}\right\}_{t=1}^{T} $ according to their distances to the location $ x $. This makes sense because the observations $ \left\{X_{t}\right\}_{t=1}^{T} $ closer to $ x $ will contain more information about $ r(x) $ at point $ x . $ The use of $ K(\cdot) $ is to assign different weights for observations $ \left\{Y_{t}, X_{t}\right\}_{t=1}^{T} $. Kernel regression is a special convolution filter used in engineering.

### 3.1.2 MSE and Optimal Bandwidth

**Question**: How to derive the asymptotic MSE of $ \hat{r}(x) $?

The Nadaraya-Watson estimator $ \hat{r}(x) $ is a ratio of two random variables. To simplify asymptotic analysis, for any given point $ x $, we consider the decomposition

$$
\begin{aligned}
\hat{r}(x)-r(x)=& \frac{\hat{m}(x)-r(x) \hat{g}(x)}{\hat{g}(x)} \\
=& \frac{\hat{m}(x)-r(x) \hat{g}(x)}{E[\hat{g}(x)]} \\
&+\frac{[\hat{m}(x)-r(x) \hat{g}(x)]}{E[\hat{g}(x)]} \cdot \frac{[E[\hat{g}(x)]-\hat{g}(x)]}{\hat{g}(x)} \\
=& \frac{\hat{m}(x)-r(x) \hat{g}(x)}{E[\hat{g}(x)]} \\
&+\text { higher order term. }
\end{aligned}
$$

Here the second term is of a higher order term because

$$
\hat{g}(x)-E[\hat{g}(x)] \stackrel{p}{\rightarrow} 0 \text { as } T \rightarrow \infty
$$

by **law of large number**. And by Taylor expansion

$$
E[\hat{g}(x)] \rightarrow g(x) \int_{-1}^{1} K(u) d u>0 \text { as } h \rightarrow 0
$$

It can be shown that the second term is of a higher order term that vanishes faster than the first term (how?). As a consequence, the convergence rate of $ \hat{r}(x) $ to $ r(x) $ is determined by the first term, which is the dominant term.

For the first term, using $ Y_{t}=r\left(X_{t}\right)+\varepsilon_{t}, $ we can write the numerator as follows:

$$
\begin{aligned}
\hat{m}(x)-r(x) \hat{g}(x)=& \frac{1}{T} \sum_{t=1}^{T}\left[Y_{t}-r(x)\right] K_{h}\left(x-X_{t}\right) \\
=& \frac{1}{T} \sum_{t=1}^{T} \varepsilon_{t} K_{h}\left(x-X_{t}\right) \\
&+\frac{1}{T} \sum_{t=1}^{T}\left[r\left(X_{t}\right)-r(x)\right] K_{h}\left(x-X_{t}\right) \\
=& \hat{V}(x)+\hat{B}(x), \quad \text { say }\\
=& \text{variance component + bias component}
\end{aligned}
$$

Here, the first term $ \hat{V}(x) $ is a variance effect, and the second term $ \hat{B}(x) $ is a bias effect.

We first consider the variance term. For simplicity, we first assume that $ \left\{Y_{t}, X_{t}\right\} $ is an IID sequence. Then for the variance component, we have

$$
\begin{aligned}
E\left[\hat{V}(x)^{2}\right] &=E\left[\frac{1}{T} \sum_{t=1}^{T} \varepsilon_{t} K_{h}\left(x-X_{t}\right)\right]^{2} \\
&=\frac{1}{T^{2}} E\left[\sum_{t=1}^{T} \varepsilon_{t} K_{h}\left(x-X_{t}\right)\right]^{2}\\
&=\frac{1}{T^{2}} \sum_{t=1}^{T} E\left[\varepsilon_{t}^{2} K_{h}^{2}\left(x-X_{t}\right)\right] \text { (by independence, and } E\left(\varepsilon_{t} | X_{t}\right)=0)\\
&=\frac{1}{T} E\left[\varepsilon_{t}^{2} K_{h}^{2}\left(x-X_{t}\right)\right] \\
&=\frac{1}{T} E\left[\sigma^{2}\left(X_{t}\right) K_{h}^{2}\left(x-X_{t}\right)\right]\left(\text { by } E\left(\varepsilon_{t}^{2} | X_{t}\right)=\sigma^{2}\left(X_{t}\right)\right) \\
&=\frac{1}{T} \int_{a}^{b}\left[\frac{1}{h} K\left(\frac{x-y}{h}\right)\right]^{2} \sigma^{2}(y) g(y) d y \\
&=\frac{1}{T h} \sigma^{2}(x) g(x) \int_{-1}^{1} K^{2}(u) d u[1+o(1)] \text{ (by Taylor expansion for g(y) and $ \sigma^2(y) $ simultaneously)}
\end{aligned}
$$

by change of variable, and the continuity of $ \sigma^{2}(\cdot) g(\cdot), $ where $ \sigma^{2}(x)=E\left(\varepsilon_{t}^{2} | X_{t}=x\right) $ is the conditional variance of $ \varepsilon_{t} $ or $ Y_{t} $ given $ X_{t}=x . $ Note that the variance $ E[\hat{V}(x)]^{2} $ is proportional to the inverse of $ T h $ because $ T h $ can be viewed as the effective sample size of the observations falling into the interval $ [x-h, x+h] $.

On the other hand, for the denominator, we have as $ h \rightarrow 0 $,

$$
\begin{aligned}
E[\hat{g}(x)] &=E\left[K_{h}\left(x-X_{t}\right)\right] \\
&=\int_{a}^{b} \frac{1}{h} K\left(\frac{x-y}{h}\right) g(y) d y \\
& \rightarrow g(x) \int_{-1}^{1} K(u) d u=g(x)
\end{aligned}
$$

if $ \int_{-1}^{1} K(u) d u=1 . $ It follows that

$$
E\left[\frac{\hat{V}(x)}{E[\hat{g}(x)}\right]^{2}=\frac{1}{T h} \frac{\sigma^{2}(x)}{g(x)} \int_{-1}^{1} K^{2}(u) d u[1+o(1)]
$$

Thus, the asymptotic variance of $ \hat{r}(x) $ is proportional to $ (T h)^{-1}, $ where $ T h $ is the approximate (effective) sample size of the observations in the interval $ [x-h, x+h] . $ The asymptotic variance of $ \hat{r}(x) $ is also proportional to $ \sigma^{2}(x) $ and to $ \int_{-1}^{1} K^{2}(u) d u . $ **Thus, the use of a downward weighting kernel $ K(\cdot) $ will reduce the variance of $ \hat{r}(x) $ as opposed to the use of the uniform kernel.** In other words, it improves the efficiency of the estimator when one discounts observations away from the point $ x $.

For the bias term $ \hat{B}(x) $, we first write

$$
\hat{B}(x)=E \hat{B}(x)+[\hat{B}(x)-E \hat{B}(x)]
$$

For any given interior point $ x \in[a+h, b-h], $ defining $ m(x)=r(x) g(x), $ we have

$$
\begin{aligned}
E \hat{B}(x)=& E\left[r\left(X_{t}\right) K_{h}\left(x-X_{t}\right)\right]-r(x) E\left[K_{h}\left(x-X_{t}\right)\right] \\
=& \int_{a}^{b} r(z) K_{h}(x-z) g(z) d z-r(x) \int_{a}^{b} K_{h}(x-z) g(z) d z \\
=& \int_{a}^{b} m(z) K_{h}(x-z) d z-r(x) \int_{a}^{b} g(z) K_{h}(x-z) d z \\
=& \int_{(a-x) / h}^{(b-x) / h} m(x+h u) K(u) d u \\
&-r(x) \int_{(a-x) / h}^{(b-x) / h} g(x+h u) K(u) d u \\
=& m(x) \int_{-1}^{1} K(u) d u \\
&+h m^{\prime}(x) \int_{-1}^{1} u K(u) d u \\
&+\frac{1}{2} h^{2} m^{\prime \prime}(x) \int_{-1}^{1} u^{2} K(u) d u[1+o(1)] \\
&-r(x) g(x) \int_{-1}^{1} K(u) d u \\
&-h r(x) g^{\prime}(x) \int_{-1}^{1} u K(u) u d u \\
&-\frac{1}{2} h^{2} r(x) g^{\prime \prime}(x) \int_{-1}^{1} u^{2} K(u) d u[1+o(1)] \\
=& \frac{1}{2} h^{2}\left[m^{\prime \prime}(x)-r(x) g^{\prime \prime}(x)\right] \int_{-1}^{1} u^{2} K(u) d u[1+o(1)] \\
=& \frac{1}{2} h^{2}\left[r^{\prime \prime}(x) g(x)+2 r^{\prime}(x) g^{\prime}(x)\right] C_{K}+o\left(h^{2}\right)
\end{aligned}
$$

where we have used the fact that

$$
\begin{aligned}
m^{\prime \prime}(x) &=[r(x) g(x)]^{\prime \prime} \\
&=\left[r^{\prime}(x) g(x)+r(x) g^{\prime}(x)\right]^{\prime} \\
&=r^{\prime \prime}(x) g(x)+2 r^{\prime}(x) g^{\prime}(x)+r(x) g^{\prime \prime}(x)
\end{aligned}
$$

It follows that the standardized bias

$$
\begin{aligned}
E\left[\frac{\hat{B}(x)}{E \hat{g}(x)}\right]=\frac{h^{2}}{2}\left[\frac{m^{\prime \prime}(x)}{g(x)}-\frac{r(x) g^{\prime \prime}(x)}{g(x)}\right] C_{K}+o\left(h^{2}\right)\\
=\frac{h^{2}}{2}\left[r^{\prime \prime}(x)+\frac{2 r^{\prime}(x) g^{\prime}(x)}{g(x)}\right] C_{K}+o\left(h^{2}\right)
\end{aligned}
$$

where we have made use of the fact that as $ h \rightarrow 0 $

$$
E[\hat{g}(x)] \rightarrow g(x) \int_{-1}^{1} K(u) d u=g(x)
$$

if $ \int_{-1}^{1} K(u) d u=1 . $ Intuitively, the bias of $ \hat{r}(x) $ consists of two components: one is $ \frac{1}{2} h^{2}\left[m^{\prime \prime}(x) / g(x)\right] C_{K}, $ which is contributed by the numerator $ \hat{m}(x) ; $ the other is $ -\frac{1}{2} h^{2}\left[r(x) g^{\prime \prime}(x) / g(x)\right] C_{K} $, which is contributed by the denominator $ \hat{g}(x), $ the estimator for density $ g(x) $.

**Question**: Do we have an asymptotically unbiased estimator if $ \int_{-1}^{1} K(u) d u \neq 1 $ (but other conditions on $ K(\cdot)  $ are the same (i.e., } $ \int_{-1}^{1} u K(u) d u=0, \int_{-1}^{1} K(u) u^{2} d u=C_{K} $)?

Yes, we still have

$$
E[\hat{B}(x)]=\frac{1}{2} h^{2}\left[m^{\prime \prime}(x)-r(x) g^{\prime \prime}(x)\right] \int_{-1}^{1} u^{2} K(u) d u[1+o(1)].
$$

**Intuitively**, both the numerator and denominator of the kernel regression estimator $ \hat{r}(x) $ will produce an integral $ \int_{-1}^{1} K(u) d u $ and their ratio is unity although the integral itself may not be equal to unity. This ensures that the asymptotic bias is still $ O\left(h^{2}\right) $ if $ K(u) $ is symmetric about $ 0 . $ The asymptotic bais will be $ O(h) $ if $ K(u) $ is not symmetric about 0.

Next, we consider the boundary bias problem for smoothed kernel regression.

**Question**: What happens to the bias $ E[\hat{B}(x)] $ if $ x \in[a, a+h) \cup(b-h, b], $ that is, if $ x $ is in the **boundary regions**? In particular, does $ E[\hat{B}(x)] \rightarrow 0 $ as $ h \rightarrow 0 $?

Yes, we still have

$$
\frac{E[\hat{B}(x)]}{E[\hat{g}(x)]}=O(h)=o(1)
$$

for $ x $ in the boundary regions (say, $ x=a+\tau h $ for $ \tau \in[0,1] $ ). This is different from the kernel density estimator $ \hat{g}(x) $. This follows because

$$
\begin{aligned}
E[\hat{B}(x)] &=[m(x)-r(x) g(x)] \int_{-\tau}^{1} K(u) d u+O(h) \\
&=O(h)
\end{aligned}
$$

and therefore

$$
\begin{aligned}
\frac{E[\hat{B}(x)]}{E[\hat{g}(x)]}&=\frac{[m(x)-r(x) g(x)] \int_{-\tau}^{1} K(u) d u}{g(x) \int_{-\tau}^{1} K(u) d u}+O(h)\\
&=O(h)
\end{aligned}
$$

However, the order $ O(h), $ which arises due to the fact that $ \int_{-\tau}^{1} u K(u) d u \neq 0, $ is slower than $ O\left(h^{2}\right), $ the rate of the bias in the interior region. The boundary correction techniques, such as the use of a jackknife kernel, are useful to further reduce the bias $ E[\hat{B}(x)] / E[\hat{g}(x)] $ for $ x $ in the boundary regions. They can reduce the bias up to order $ O\left(h^{2}\right), $ the same rate as in the interior regions, but still with different proportionality.

It remains to show that $ \hat{B}(x)-E[\hat{B}(x)] $ **is a higher order**. Again, for simplicity, we first assume that $ \left\{Y_{t}, X_{t}\right\} $ is IID. Put

$$
Z_{t} \equiv Z_{t}(x)=\left[r\left(X_{t}\right)-r(x)\right] K_{h}\left(x-X_{t}\right)
$$

Then

$$
\begin{aligned}
E[\hat{B}(x)-E \hat{B}(x)]^{2} &=E\left[\frac{1}{T} \sum_{t=1}^{T}\left(Z_{t}-E Z_{t}\right)\right]^{2} \\
&=\frac{1}{T^{2}} \sum_{t=1}^{T} E\left(Z_{t}-E Z_{t}\right)^{2} \text { by independence } \\
& \leq \frac{1}{T} E\left(Z_{t}^{2}\right) \\
&=\frac{1}{T} E\left\{\left[r\left(X_{t}\right)-r(x)\right]^{2} K_{h}^{2}\left(x-X_{t}\right)\right\} \\
& \leq \frac{C h}{T}[1+o(1)](\text { why? })
\end{aligned}
$$

is a higher order term.

It follows that

$$
\begin{aligned}
E[\hat{m}(x)-r(x) \hat{g}(x)]^{2}=& E[\hat{V}(x)+\hat{B}(x)]^{2} \\
=& E\left[\hat{V}^{2}(x)\right]+E\left[\hat{B}^{2}(x)\right] \\
=& E\left[\hat{V}^{2}(x)\right]+E\left[\hat{B}^{2}(x)\right]+E[\hat{B}(x)-E \hat{B}(x)]^{2} \\
=& \frac{1}{T h} D_{K} \sigma^{2}(x) g(x) \\
&+\frac{h^{4}}{4} C_{K}^{2}\left[m^{\prime \prime}(x)-r(x) g^{\prime \prime}(x)\right]^{2} \\
&+o\left((T h)^{-1}+h^{4}\right)
\end{aligned}
$$

Therefore, the asymptotic mean square error (MSE) of $ \hat{r}(x) $ is

$$
\begin{aligned}
E[\hat{r}(x)-r(x)]^{2}=& \frac{1}{T h} \frac{\sigma^{2}(x)}{g(x)} D_{K}+\frac{h^{4}}{4}\left[\frac{r^{\prime \prime}(x)+2 r^{\prime}(x) g^{\prime}(x)}{g(x)}\right]^{2} C_{K}^{2} \\
&+o\left((T h)^{-1}+h^{4}\right) \\
=& O\left(T^{-1} h^{-1}+h^{4}\right)
\end{aligned}
$$

The variance is proportional to $ (T h)^{-1} $ and the squared bias is proportional to $ h^{4} $. As a result, an increase in $ h $ will reduce the variance but increase the bias, and a decrese in $ h $ will increase the variance but reduce the bias. Optimal smoothing can be achieved by balancing the variance and the squared bias. The optimal choice of $ h $ is obtained by minimizing the MSE of $ \hat{r}(x): $

$$
h^{*}=c^{*} T^{-1 / 5}
$$

where the optimal proportionality

$$
\begin{aligned}
c^{*} &=\left[\frac{D_{K}}{C_{K}^{2}} \frac{\sigma^{2}(x) / g(x)}{\left[m^{\prime \prime}(x) / g(x)-r(x) g^{\prime \prime}(x) / g(x)\right]^{2}}\right]^{\frac{1}{3}} \\
&=\left[\frac{D_{K}}{C_{K}^{2}} \frac{\sigma^{2}(x) g(x)}{\left[r^{\prime \prime}(x)+2 r^{\prime}(x) g^{\prime}(x)\right]^{2}}\right]^{\frac{1}{3}}
\end{aligned}
$$

Thus, the optimal bandwidth $ h^{*} $ should be larger when the data is noisy (i.e., $ \sigma^{2}(x) $ is large) and should be small when the regression function $ r(x) $ is not smooth (large derivatives)

Like in density estimation, the optimal kernel for kernel regression estimation remains to be the Epanechnikov kernel

$$
K(u)=\frac{3}{4}\left(1-u^{2}\right) 1(|u|<1)
$$

In practice, it is found that the choice of $ h $ is more important than the choice of $ K(\cdot) $?

**Question**: How to estimate the derivatives of $ r(x), $ such as $ r^{\prime}(x) $ and $ r^{\prime \prime}(x) $ by the kernel method?

One approach is to use $ \hat{r}^{\prime}(x) $ and $ \hat{r}^{\prime \prime}(x), $ assuming that $ K(\cdot) $ is twice continuously differentiable. However, it may be noted that the optimal $ h^{*} $ that minimizes the asymptotic MSE of $ \hat{r}(\cdot) $ is not the same as the optimal bandwidth $ h $ that minimizes the asymptotic MSE of $ \hat{r}^{(d)}(\cdot) $, where $ d=1,2 $ respectively. A larger bandwidth is needed to estimate the derivatives of $ r(x) $.

In addition to the plug-in method, one can also use the **cross-validation method** to choose a data-driven bandwidth $ h . $ Let $ \hat{r}_{(t)}(x) $ be defined in the same way as $ \hat{r}(x) $ except the $ t $ -th observation $ \left(Y_{t}, X_{t}\right) $ is not used. This is called a "**leave-one-out**" estimator,
$$
\hat{r}_t(x)=\frac{\hat{m}_t (x)}{\hat{g}_t(x)}
$$

where the numerator
$$
\begin{aligned}
\hat{m}_t (x)&=\frac{1}{T} \sum_{s \neq t}^{T} Y_{t} K_{h}\left(x-X_{t}\right) \\
\hat{g}_t (x)&=\frac{1}{T} \sum_{s \neq t}^{T} K_{h}\left(x-X_{t}\right)
\end{aligned}
$$

Then the cross-validation procedure is to choose $ h $ to minimize the following sum of squared residuals, namely,
$$
\hat{h}^{*}=\min _{h} \sum_{t=1}^{T}\left[Y_{t}-\hat{r}_{(t)}\left(X_{t}\right)\right]^{2}
$$

The main reason why a leave-one-out estimator is used is that if one used a kernel regression estimator $ \hat{r}\left(X_{t}\right) $ using all observations including observation $ \left(Y_{t}, X_{t}^{\prime}\right)^{\prime} $ at time $ t $, then the optimal bandwidth which minimizes the sum of squared residuals will be obtained by setting $ h \rightarrow 0 $ and $ \hat{r}\left(X_{t}\right)=Y_{t} $. Furthermore, in the IID context, the leave-one-out estimator avoids a nonzero cross-product term which would otherwise "disturb" the mean squared error

$$
M S E[\hat{r}(\cdot)]=E\left[Y_{t}-\hat{r}\left(X_{t}\right)\right]^{2}
$$

In other words, the sum of squared residuals of the leave-one-out estimator $ \hat{r}_{(t)}\left(X_{t}\right) $ scaled by the same size $ T, $ will converge to $ \operatorname{MSE}[\hat{r}(\cdot)] $ plus a constant. As a result, it could be shown (how?) that $ \hat{h}^{*} $ will asymptotically minimize $ \operatorname{MSE}[\hat{r}(\cdot)]=E\left[Y_{t}-\hat{r}\left(X_{t}\right)\right]^{2} $ The cross-validation procedure is popular in nonparametric estimation, due to its optimality and robustness (when compared with the plug-in method).

## 3.2 Local Polynomial Estimation

To provide an motivation for local polynomial smoothing, we now provide an alternative interpretation for the Nadaraya-Watson estimator $ \hat{r}(x) $. First, we consider a sum of squared residuals (SSR) minimization problem

$$
\min _{r} \sum_{t=1}^{T}\left(Y_{t}-r\right)^{2}
$$

where $ r $ is a constant. The optimal solution is the sample mean

$$
\hat{r}=\bar{Y} \equiv \frac{1}{T} \sum_{t=1}^{T} Y_{t}
$$

Next, we consider a local weighted sum of squared residuals minimization problem

$$
\min _{r} \sum_{t=1}^{T}\left(Y_{t}-r\right)^{2} K_{h}\left(x-X_{t}\right)
$$

where $ r $ is, again, a real-valued constant. When $ K(u) $ has bounded support on [-1,1] this is the weighted sum of squared residuals to predict the observations $ \left\{Y_{t}\right\} $ for which the values of the corresponding explanatory variables $ \left\{X_{t}\right\} $ fall into the interval $ [x- $ $ h, x+h] $. The FOC is given by

$$
\sum_{t=1}^{T}\left(Y_{t}-\hat{r}\right) K_{h}\left(x-X_{t}\right)=0
$$

It follows that

$$
\begin{aligned}
\hat{r} & \equiv \hat{r}(x) \\
&=\frac{\sum_{t=1}^{T} Y_{t} K_{h}\left(x-X_{t}\right)}{\sum_{t=1}^{T} K_{h}\left(x-X_{t}\right)} \\
&=\frac{\hat{m}(x)}{\hat{g}(x)}
\end{aligned}
$$

This is a local constant estimator. In other words, **the Nadaraya-Watson estimator can be viewed as a locally weighted sample mean which minimizes a locally weighted sum of squared residuals**.

**Question**: Why only use a local constant estimator? Why not use a local linear function? More generally, why not use a local polynomial?

**Question**: What are the gains, if any, to use a local polynomial estimator?

### 3.2.1 Local Polynomial Estimator

We now consider a local polynomial estimator for the regression function $ r(x), $ where $ x $ is a given point in the support of $ X_{t} $. Suppose $ z $ is an arbitrary point in a small neighborhood of $ x, $ and $ r(z) $ is continuously differentiable with respect to $ z $ up to order $ p+1 $ in this neighborhood. Then by a $ (p+1) $-order Taylor series expansion, we have for all $ z $ in a small neighborhood of a fixed point $ x $,

$$
\begin{aligned}
r(z) &=\sum_{j=0}^{p} \frac{1}{j !} r^{(j)}(x)(z-x)^{j}+\frac{1}{(p+1) !} r^{(p+1)}(\bar{x})(z-x)^{p+1} \\
&=\sum_{j=0}^{p} \alpha_{j}(z-x)^{j}+\frac{1}{(p+1) !} r^{(p+1)}(\bar{x})(z-x)^{p+1}
\end{aligned}
$$

where $ \bar{x} $ lies in the segment between $ x $ and $ z, $ and the polynomial coefficient

$$
\begin{aligned}
\alpha_{j} & \equiv \alpha_{j}(x) \\
&=\frac{1}{j !} r^{(j)}(x), \quad j=0,1, \ldots, p
\end{aligned}
$$

depends on the point $ x . $ This relation suggests that one can use a local polynomial model to fit the function $ r(z) $ in the neighborhood of $ x $ as long as the observations in this neighborhood are "sufficiently rich."

Therefore, we consider the following local weighted sum of squared residuals minimization problem

$$
\min _{\alpha} \sum_{t=1}^{T}\left[Y_{t}-\sum_{j=0}^{p} \alpha_{j}\left(X_{t}-x\right)^{j}\right]^{2} K_{h}\left(x-X_{t}\right)=\sum_{t=1}^{T}\left(Y_{t}-\alpha^{\prime} Z_{t}\right)^{2} K_{h}\left(x-X_{t}\right)
$$

where $ \alpha=\left(\alpha_{0}, \alpha_{1}, \ldots, \alpha_{p}\right)^{\prime} $ and $ Z_{t}=Z_{t}(x)=\left[1,\left(X_{t}-x\right), \ldots,\left(X_{t}-x\right)^{p}\right]^{\prime} . $ Note that $ Z_{t}=Z_{t}(x) $ is a $ (p+1) $-dimensional local polynomial vector which depends on location $ x $. The resulting local weighted least squares estimator,

$$
\hat{r}(z)=\sum_{j=0}^{p} \hat{\alpha}_{j}(z-x)^{j} \text{ for all } z \text{ near } x
$$

is the so-called local polynomial estimator of $ r(z) $ for $ z $ near $ x, $ where $ \hat{\alpha} $ is the locally weighted least squares estimator, whose expression will be given below.

We now show that **the intercept estimator $ \hat{\alpha}_{0} $ is an estimator for $ r(x), $ and $ \nu ! \hat{\alpha}_{\nu} $ is an estimator for the derivative** $ r^{(\nu)}(x), $ where $ 1 \leq \nu \leq p $.

Since $ \hat{r}(z)=\sum_{j=0}^{p} \hat{\alpha}_{j}(z-x)^{j}, $ for all $ z $ near $ x $, the regression estimator at point $ x $ is then given by

$$
\hat{r}(x)=\sum_{j=0}^{p} \hat{\alpha}_{j}(x-x)^{j}=\hat{\alpha}_{0}
$$

Moreover, the derivative estimator of $ r^{(\nu)}(z) $ for $ z $ near the point $ x $ is given by

$$
\hat{r}^{(\nu)}(z)=\sum_{j=\nu}^{p} j(j-1) \cdots(j-\nu+1) ! \hat{\alpha}_{j}(z-x)^{j-\nu} \text { for } \nu \leq p
$$

Thus, we have the $ \nu $ -th order derivative estimator at point $ x $

$$
\hat{r}^{(\nu)}(x)=\nu ! \hat{\alpha}_{\nu}
$$

Interestingly, we can obtain $ \hat{r}(x) $ and $ \hat{r}^{(\nu)}(x) $ for $ 1 \leq \nu \leq p $ simultaneously. Local polynomial smoothing is rather convenient for estimating the $ r^{(\nu)}(x), \nu= $ $ 0,1, \ldots, p, $ simultaneously. **When $ p=0, $ we obtain a local constant estimator, i.e., the Nadaraya-Watson estimator. Obviously, a local polynomial estimator with $ p>0 $ always has a smaller sum of weighted squared residuals than the local constant estimator**, because for any local polynomial model, one can always simply set all slope coefficients equal to zero. This implies that the sum of weighted squared residuals will never be larger than that of the local constant estimator.

**To compute the local polynomial estimator, one has to choose $ p, $ the order of local polynomial, $ h, $ the bandwidth, and $ K(\cdot), $ the kernel function.** Often, a nonnegative kernel function $ K(\cdot) $ is used, which corresponds to a second order kernel function. The choices of $ (p, h) $ jointly determine the complexity of the local polynomial model. The choice of $ h $ is more important than the choice of $ p $ (why? Higher order doesn't improve convergence rate very much). It has been recommended that $ p=\nu+1 $ if the interest is in estimating $ r^{(\nu)}(x) $ for $ 0 \leq \nu \leq p $. When $ p=1 $, it is a **local linear smoother**. The choice of $ h $ can be based on data-driven methods such as the cross-validation or plug-in methods.

To obtain the closed form expression for the local weighted least squares estimator $ \hat{\alpha} $, a $ (p+1) \times 1 $ vector, we put

$$
\begin{aligned}
Z_{t} &=Z_{t}(x) \\
&=\left[1,\left(X_{t}-x\right),\left(X_{t}-x\right)^{2}, \ldots,\left(X_{t}-x\right)^{p}\right]^{\prime}
\end{aligned}
$$

a $ (p+1) \times 1 $ polynomial regressors vector, and a weighting function

$$
\begin{aligned}
W_{t} &=W_{t}(x) \\
&=K_{h}\left(x-X_{t}\right) \\
&=\frac{1}{h} K\left(\frac{x-X_{t}}{h}\right)
\end{aligned}
$$

Then the local sum of squared residuals can be written as

$$
\begin{aligned}
\sum_{t=1}^{T}\left[Y_{t}-\sum_{j=0}^{p} \alpha_{j}\left(X_{t}-x\right)^{j}\right]^{2} K_{h}\left(x-X_{t}\right)&=\sum_{t=1}^{T}\left(Y_{t}-\alpha^{\prime} Z_{t}\right)^{2} W_{t} \\
&=(Y-Z \alpha)^{\prime} W(Y-Z \alpha)
\end{aligned}
$$

where

$$
W=W(x)=\operatorname{diag}\left(W_{1}, \cdots, W_{T}\right)
$$

is a $ T \times T $ diagonal matrix, $ Z $ is a $ T \times(p+1) $ matrix, and $ Y $ is a $ T \times 1 $ vector. This is a local weighted least squares estimator when $ K(\cdot) $ has a bounded support [-1,1].

The FOC is

$$
\sum_{t=1}^{T} Z_{t} W_{t}\left(Y_{t}-Z_{t}^{\prime} \hat{\alpha}\right)=0
$$

or equivalently

$$
\sum_{t=1}^{T} Z_{t} W_{t} Y_{t}=\left(\sum_{t=1}^{T} Z_{t} W_{t} Z_{t}^{\prime}\right) \hat{\alpha}
$$

It follows that

$$
\begin{aligned}
\hat{\alpha} & \equiv \hat{\alpha}(x) \\
&=\left(\sum_{t=1}^{T} Z_{t} W_{t} Z_{t}^{\prime}\right)^{-1} \sum_{t=1}^{T} Z_{t} W_{t} Y_{t} \\
&=\left(Z^{\prime} W Z\right)^{-1} Z^{\prime} W Y
\end{aligned}
$$

**Question**: What are the advantages of using a local polynomial estimator?

### 3.2.2 Equivalent Kernel

To exploit the advantages of the local polynomial estimator for $ r(x), $ we now investigate its **asymptotic properties**.

Suppose our interest is in estimating $ r^{(\nu)}(x), $ where $ 0 \leq v \leq p $. Recalling the weighting function

$$
W_{t}=K_{h}\left(x-X_{t}\right)=\frac{1}{h} K\left(\frac{x-X_{t}}{h}\right)
$$

we define a $ j $-th order **locally weighted sample moment**

$$
\begin{aligned}
\hat{s}_{j} &=\hat{s}_{j}(x) \\
&=\sum_{t=1}^{T}\left(X_{t}-x\right)^{j} K_{h}\left(X_{t}-x\right) \\
&=\sum_{t=1}^{T}\left(X_{t}-x\right)^{j} W_{t}, \quad j=0,1, \ldots, p
\end{aligned}
$$

and let

$$
\begin{aligned}
\hat{S} &=\hat{S}(x) \\
&=Z^{\prime} W Z \\
&=\sum_{t=1}^{T} Z_{t} W_{t} Z_{t}^{\prime} \\
&=\left[\hat{s}_{(i-1)+(j-1)}\right]_{(i, j)}
\end{aligned}
$$

be a $ (p+1) \times(p+1) $ stochastic symmetric matrix, whose $ (i, j) $-th element is $ \hat{s}_{(i-1)+(j-1)}= \hat{s}_{i+j-2} $.

Then we have the local weighted least squares estimator

$$
\hat{\alpha}=\hat{S}^{-1} Z^{\prime} W Y
$$

Denote $ e_{\nu+1} $ for the $ (p+1) \times 1 $ unit vector with 1 at the $ (\nu+1) $-th position and 0 elsewhere. Then the $ \nu $ -th component of $ \hat{\alpha} $ is given by

$$
\begin{aligned}
\hat{\alpha}_{\nu} &=e_{\nu+1}^{\prime} \hat{\alpha} \\
&=e_{\nu+1}^{\prime} \hat{S}^{-1} Z^{\prime} W Y \\
&=e_{\nu+1}^{\prime} \hat{S}^{-1} \sum_{t=1}^{T} Z_{t} W_{t} Y_{t} \\
&=\sum_{t=1}^{T} e_{\nu+1}^{\prime} \hat{S}^{-1}\left(\begin{array}{c}
1 \\
\left(X_{t}-x\right) \\
\cdots \\
\left(X_{t}-x\right)^{p}
\end{array}\right) \frac{1}{h} K\left(\frac{X_{t}-x}{h}\right) Y_{t} \\
&=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) Y_{t}, \text { say }
\end{aligned}
$$

where the effective kernel $ \hat{W}_{\nu}(\cdot) $ is the multiplication of the kernel function $ K(\cdot) $ with a polynomial function, namely

$$
\begin{aligned}
\hat{W}_{\nu}(u) &=e_{\nu+1}^{\prime} \hat{S}^{-1}\left(\begin{array}{l}
1 \\
h u \\
\cdots & \\
(h u)^{p}
\end{array}\right) \frac{1}{h} K(u) \\
&=e_{\nu+1}^{\prime} \hat{S}^{-1} H P(u) \frac{1}{h} K(u)
\end{aligned}
$$

where

$$
H=\operatorname{diag}\left\{1, h, \ldots, h^{p}\right\}
$$

is a $ (p+1) \times(p+1) $ diagonal matrix, and

$$
P(u)=\left(1, u, \ldots, u^{p}\right)^{\prime}
$$

is a $ (p+1) \times 1 $ vector of a $ p $-th order polynomial in $ u $. Note that we will make change of variable $ u=\left(X_{t}-x\right) / h . $ Obviously, the local polynomial estimator differs from the Nadaraya-Watson estimator in using a different weighting function $ \hat{W}_{v}\left(\frac{X_{t}-x}{h}\right) $ for $ \left\{Y_{t}\right\}_{t=1}^{T} $.

**Question**: What properties does the effective kernel $ \hat{W}_{\nu}(u) $ have?

$ \hat{W}_{\nu}(u) $ is data driven, then it's also random.

**Lemma [Sample Orthogonality between $ \hat{W}_{\nu}(u) \text { and }\left(X_{t}-x\right)^{q} $]**: Let $ \hat{W}_{v}(u) $ be defined as above. Then
$$
\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right)\left(X_{t}-x\right)^{q}=\delta_{\nu, q} \text { for } 0 \leq \nu, q \leq p
$$

where $ \delta_{v, q} $ is the Kronecker delta function, namely $ \delta_{\nu, q}=1 $ if $ \nu=q $ and $ \delta_{\nu, q}=0 $ otherwise.

The sample orthogonality between $ \hat{W}_{\nu}(u) $ and $ \left(X_{t}-x\right)^{q} $ is very useful in deriving the bias of the local polynomial estimator $ \hat{\alpha}_{\nu} $.

**Question**: What is the intuition behind this orthogonality?

**Proof**: Observing $ \left(X_{t}-x\right)^{q}=Z_{t}^{\prime} e_{q+1} $ and $ \hat{S}=Z^{\prime} W Z, $ we have

$$
\begin{aligned}
\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) Z_{t}^{\prime} e_{q+1} &=e_{\nu+1}^{\prime} \hat{S}^{-1}\left(\sum_{t=1}^{T} Z_{t} W_{t} Z_{t}^{\prime}\right) e_{q+1} \\
&=e_{\nu+1}^{\prime} I_{p+1} e_{q+1} \\
&=\delta_{\nu q}
\end{aligned}
$$

Now, let $ S $ be a non-stochastic $ (p+1) \times(p+1) $ matrix whose $ (i, j) $ th element $ S_{(i, j)} $ is $ s_{(i-1)+(j-1)}=s_{i+j-2}, $ where

$$
s_{j}=\int_{-1}^{1} u^{j} K(u) d u, \quad j=0,1, \ldots, p
$$

Then

$$
S=\int_{-1}^{1} P(u) K(u) P(u)^{\prime} d u
$$

Next, we define a non-stochastic **equivalent kernel function** by

$$
\tilde{K}_{\nu}(u)=e_{\nu+1}^{\prime} S^{-1} P(u) K(u)
$$

This scalar-valued equivalent kernel $ \tilde{K}(\cdot) $ has the following properties.

**Lemma [Equivalent Kernel]**: Suppose $ \left\{Y_{t}, X_{t}\right\} $ is a stationary $ \alpha $-mixing process with $ \alpha(j) \leq C j^{-\beta} $ for $ \beta>\frac{5}{2}, $ the marginal probability density $ g(x) $ of $ \left\{X_{t}\right\} $ is bounded on an interval $ [a, b] $ and has a continuous derivative at point $ x \in[a, b], $ and the kernel function $ K(\cdot) $ satisfies a Lipschitz condition. Then

(1) for any given point $ x $ in the interior region $ [a+h, b-h] $,

$$
\hat{W}_{\nu}(u)=\frac{1}{T h^{\nu+1} g(x)} \tilde{K}_{\nu}(u)\left[1+O_{P}\left(a_{T}\right)\right]
$$

where

$$
a_{T}=[\ln (T) / T h]^{1 / 2}+h
$$

(2) Moreover, the equivalent kernel $ \tilde{K}_{\nu}(\cdot) $ satisfies the following orthogonality condition

$$
\int_{-1}^{1} u^{q} \tilde{K}_{\nu}(u) d u=\delta_{\nu, q}, \text { for } 0 \leq \nu, q \leq p
$$

This lemma implies that

$$
\begin{aligned}
\hat{\alpha}_{\nu} &=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) Y_{t} \\
&=\frac{1}{T h^{\nu+1} g(x)} \sum_{t=1}^{T} \tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) Y_{t}\left[1+O_{P}\left(a_{T}\right)\right]
\end{aligned}
$$

In other words, **the local polynomial estimator $ \hat{\alpha}_{v} $ works like a kernel regression estimator with a known probability density $ g(x) $ so that there is no need to estimate $ g(x) $.** This explains why the local polynomial estimator adapts to various design densities, including the boundary region or the region where $ g^{\prime}(x) $ is large in absolute value. Therefore, the bias due to estimation of unknown density $ g(x) $ does not enter the MSE criterion of the local polynomial estimator. This is the main advantage of the local polynomial estimator over the Nadaraya-Watson estimator. In particular, it fits well even where $ g^{\prime}(x) $ is large in absolute value. In the regions where $ g^{\prime}(x) $ is large in absolute value, the standard Nadaraya-Watson kernel estimator cannot fit well, due to asymmetric data coverage which yields a large bias. Note that a large value of $ g^{\prime}(x) $ in absolute value implies that the observations $ \left\{X_{t}\right\} $ will not be covered symmetrically in a small neighborhood centered at $ x $.

**Proof**: We first consider the $ (p+1) \times(p+1) $ denominator matrix $ \hat{S}=\left[\hat{s}_{(i-1)+(j-1)}\right]_{(i, j)} $ which is stochastic. Observe that for $ j=0,1, \ldots, p $,
$$
\frac{1}{T h^{j}} \hat{s}_{j}=\frac{1}{T} \sum_{t=1}^{T}\left(\frac{X_{t}-x}{h}\right)^{j} K_{h}\left(x-X_{t}\right)
$$

is like a kernel density estimator with the generalized kernel function $ u^{j} K(u) $. Therefore, by law of large number and Taylor expansion we have

$$
\frac{1}{T h^{j}} \hat{s}_{j}=g(x) s_{j}+O_{P}\left(a_{T}\right), \quad j=0,1, \ldots, p
$$

where the $ O_{P}(h) $ component in

$$
a_{T}=\left[(1 / T h)^{1 / 2} \ln T+h\right]
$$

is contributed by law of large number and the bias term in a first order Taylor series expansion of the integral

$$
\begin{aligned}
& E\left[\left(\frac{X_{t}-x}{h}\right)^{j} K_{h}\left(x-X_{t}\right)\right] \\
=& \int_{a}^{b}\left(\frac{y-x}{h}\right)^{j} \frac{1}{h} K\left(\frac{x-y}{h}\right) g(y) d y \\
=&\int_{\frac{a-x}{h}}^{\frac{b-x}{h}} u^{j} K(u) g(x+h u) d u \\
=&g(x)\int_{-1}^{1} u^{j} K(u) d u + O_p(h)\\
=&g(x)s_j + O_p(h)
\end{aligned}
$$

Recall $ H=\operatorname{diag}\left\{1, h, \ldots, h^{p}\right\} $ and the $ (i, j) $-th element $ \hat{S}_{(i, j)}=\hat{s}_{(i-1)+(j-1)} . $ It follows that

$$
\frac{1}{T} H^{-1} \hat{S} H^{-1}=g(x) S\left[1+O_{P}\left(a_{T}\right)\right]
$$

or equivalently

$$
\hat{S}=T g(x) H S H\left[1+O_{P}\left(a_{T}\right)\right]
$$

Substituting this expression into the definition of the effective kernel $ \hat{W}_{\nu}(u), $ we obtain

$$
\begin{aligned}
\hat{W}_{\nu}(u) &=e_{\nu+1}^{\prime} \hat{S}^{-1} H P(u) \frac{1}{h} K(u) \\
&=e_{\nu+1}^{\prime}\{T g(x) H S H\}^{-1} H P(u) \frac{1}{h} K(u)\left[1+O_{P}\left(a_{T}\right)\right] \\
&=\frac{1}{T h^{\nu+1} g(x)}\left[e_{\nu+1}^{\prime} S^{-1} P(u) K(u)\right]\left[1+O_{P}\left(a_{T}\right)\right] \\
&=\frac{1}{T h^{\nu+1} g(x)} \tilde{K}_{\nu}(u)\left[1+O_{P}\left(a_{T}\right)\right]
\end{aligned}
$$

where we have used the fact that $ e_{\nu+1}^{\prime} H=h^{\nu} e_{\nu+1}^{\prime} $.

The properties for the equivalent kernel $ \tilde{K}_{\nu}(u) $ can be shown in the same way as the proof of the first part of the lemma for $ \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) . $ Observing $ u^{q}=P(u)^{\prime} e_{q+1}, $ we have

$$
\begin{aligned}
\int_{-1}^{1} u^{q} \tilde{K}_{\nu}(u) d u &=\int_{-1}^{1} \tilde{K}_{\nu}(u) u^{q} d u \\
&=e_{\nu+1}^{\prime}\left[S^{-1} \int_{-1}^{1} P(u) K(u) P(u)^{\prime} d u\right] e_{q+1} \\
&=e_{\nu+1}^{\prime} S^{-1} S e_{q+1} \\
&=e_{\nu+1}^{\prime} I_{p+1} e_{q+1} \\
&=\delta_{\nu, q}
\end{aligned}
$$

This completes the proof of the second part of the lemma for $ \tilde{K}_{\nu}(u) $.

We note that a similar lemma holds for an equivalent boundary kernel function when $ x $ is not an interior point in $ [a+h, b-h] $. The difference is that the range of the integral has to be changed from [-1,1] to $ [-\tau, 1] $ or $ [-1, \tau] $, depending on whether $ x $ is in the left boundary region or the right boundary region.

In other words, **the location-dependent weight function $ \hat{W}_{v}\left[\left(X_{t}-x\right) / h\right] $ has an equivalent kernel which automatically adapts to the boundary region**. See more discussions below.

### 3.2.3 Asymptotic Properties of Local Polynomial Estimator

**Question**: What is the MSE of $ \hat{\alpha} $?

Noting $ Y_{t}=r\left(X_{t}\right)+\varepsilon_{t}, $ we first write the $ v $-th component of $ \hat{\alpha} $

$$
\begin{aligned}
\hat{\alpha}_{\nu}-\alpha_{\nu} &=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) Y_{t}-\alpha_{\nu} \\
&=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) \varepsilon_{t}+\left[\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) r\left(X_{t}\right)-\alpha_{\nu}\right] \\
&=\hat{V}+\hat{B}, \text { say. }
\end{aligned}
$$

For the first term $ \hat{V}, $ using the formula

$$
\hat{S}=T g(x) H S H\left[1+O_{P}\left(a_{T}\right)\right]
$$

which has been proven earlier, we can write

$$
\begin{aligned}
\hat{V} &=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) \varepsilon_{t} \\
&=e_{\nu+1}^{\prime} \hat{S}^{-1} Z^{\prime} W \varepsilon \\
&=\frac{1}{T h^{\nu} g(x)} e_{\nu+1}^{\prime} S^{-1} H^{-1} Z^{\prime} W \varepsilon\left[1+O_{P}\left(a_{T}\right)\right]
\end{aligned}
$$

where we used the fact that $ e_{\nu+1}^{\prime} H^{-1}=h^{-\nu} e_{\nu+1}^{\prime} . $ Furthermore, assuming that $ \left\{Y_{t}, X_{t}\right\} $ is IID, we have

$$
\begin{aligned}
& E\left(Z^{\prime} W \varepsilon \varepsilon^{\prime} W Z\right) \\
=& E\left[\sum_{t=1}^{T} \varepsilon_{t} Z_{t} K_{h}\left(X_{t}-x\right)\right]\left[\sum_{s=1}^{T} \varepsilon_{s} Z_{s}^{\prime} K_{h}\left(X_{s}-x\right)\right] \\
=& \sum_{t=1}^{T} E\left[\varepsilon_{t}^{2} Z_{t} K_{h}^{2}\left(X_{t}-x\right) Z_{t}^{\prime}\right]\left(\text { by } E\left(\varepsilon_{t} | X_{t}\right)=0\right) \\
=& T E\left[\varepsilon_{t}^{2} Z_{t} K_{h}^{2}\left(X_{t}-x\right) Z_{t}^{\prime}\right](\text { by independence }) \\
=& \frac{T}{h} \sigma^{2}(x) g(x) H S^{*} H[1+o(1)]
\end{aligned}
$$

by change of variable and continuity of $ \sigma^{2}(\cdot), $ where $ S^{* *} $ is a $ (p+1) \times(p+1) $ matrix with $ (i, j) $-th element

$$
\begin{aligned}
S_{(i, j)}^{*} &=s_{(i-1)+(j-1)}^{*} \\
&=\int_{-1}^{1} u^{(i-1)+(j-1)} K^{2}(u) d u
\end{aligned}
$$

Note that $ S^{*} \neq S $ because the integral here is weighted by $ K^{2}(u) $ rather than $ K(u) $.

It follows that the asymptotic variance of $ \hat{\alpha}_{\nu} $

$$
\begin{aligned}
\operatorname{avar}(\hat{V}) &=\frac{1}{T h^{\nu} g(x)} e_{\nu+1}^{\prime} S^{-1} H^{-1} E\left(Z^{\prime} W \varepsilon \varepsilon^{\prime} W Z\right) H^{-1} S^{-1} \frac{1}{T h^{\nu} g(x)} \\
&=\frac{1}{T h^{2 \nu+1}} \frac{\sigma^{2}(x)}{g(x)} e_{\nu+1}^{\prime} S^{-1} S^{*} S^{-1} e_{\nu+1}[1+o(1)] \\
&=\frac{1}{T h^{2 \nu+1}} \frac{\sigma^{2}(x)}{g(x)} \int_{-1}^{1} \tilde{K}^{2}_{\nu}(u) d u[1+o(1)] \\
&=O\left(T^{-1} h^{-2 \nu-1}\right)
\end{aligned}
$$

where, as before, $ \tilde{K}_{\nu}(u)=e_{\nu+1}^{\prime} S^{-1} P(u) K(u) $ is the equivalent kernel, and

$$
\begin{aligned}
\int_{-1}^{1} \tilde{K}_{\nu}^{2}(u) d u &=\int_{-1}^{1}\left[e_{\nu+1}^{\prime} S^{-1} P(u) K(u)\right]\left[K(u) P(u)^{\prime} S^{-1} e_{\nu+1}\right] d u \\
&=e_{\nu+1}^{\prime} S^{-1}\left[\int_{-1}^{1} P(u) K^{2}(u) P(u)^{\prime} d u\right] S^{-1} e_{\nu+1} \\
&=e_{\nu+1}^{\prime} S^{-1} S^{*} S^{-1} e_{\nu+1}
\end{aligned}
$$

Note that this result is obtained under the IID assumption for $ \left\{Y_{t}, X_{t}\right\}_{t=1}^{T} . $ It still holds under a suitable mixing condition, using an analogous reasoning to that for the kernel density estimator $ \hat{g}(x) $.

**Question**: How to compute the order of magnitude of the bias $ \hat{B} $?

Taking a Tailor series expansion around a small neighborhood of $ x, $ up to order $ p+1 $ namely,

$$
\begin{aligned}
r\left(X_{t}\right) &=\sum_{j=0}^{p} \frac{1}{j !} r^{(j)}(x)\left(X_{t}-x\right)^{j}+\frac{1}{(p+1) !} r^{(p+1)}\left(\bar{x}_{t}\right)\left(X_{t}-x\right)^{p+1} \\
&=\sum_{j=0}^{p} \frac{1}{j !} r^{(j)}(x)\left(X_{t}-x\right)^{j}+R\left(x, X_{t}\right)
\end{aligned}
$$

where $ \bar{x}_{t} $ lies in the segment between $ x $ and $ X_{t} $, we have

$$
\begin{aligned}
\hat{B}=& \sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) r\left(X_{t}\right)-\alpha_{\nu} \\
=& \sum_{j=0}^{p} \frac{1}{j !} r^{(j)}(x) \sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right)\left(X_{t}-x\right)^{j} \\
&-\frac{1}{\nu !} r^{(\nu)}(x) \\
&+\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right)
\end{aligned}
$$

where $ \alpha_{\nu}=\frac{1}{\nu !} r^{(\nu)}(x), $ and the reminder

$$
R\left(x, X_{t}\right)=\frac{1}{(p+1) !} r^{(p+1)}\left(\bar{x}_{t}\right)\left(X_{t}-x\right)^{p+1}
$$

where $ \bar{x}_{t}=\lambda X_{t}+(1-\lambda) x $ for some $ \lambda $ in $ [0,1] . $ Then using the expression $ r\left(X_{t}\right)= $ $ \sum_{j=1}^{p} \alpha_{j}\left(X_{t}-x\right)^{j}+R\left(x, X_{t}\right) $ and the asymptotic equivalence between $ \hat{W}_{\nu}(\cdot) $ and $ \tilde{K}_{\nu}(\cdot) $, by **orthogonality** we have

$$
\begin{aligned}
\hat{B} &=\sum_{t=1}^{T} \hat{W}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right) \\
&=\frac{1}{T h^{\nu+1} g(x)} \sum_{t=1}^{T} \tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right)\left[1+O_{P}\left(a_{T}\right)\right] \\
&=\tilde{B}\left[1+O_{P}\left(a_{T}\right)\right], \text { say }
\end{aligned}
$$

by Chebyshev's inequality. We now consider $ \tilde{B} $. It can be shown that

$$
\begin{aligned}
\tilde{B}-E \tilde{B} &=\frac{1}{T h^{\nu+1} g(x)} \sum_{t=1}^{T}\left\{\tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right)-E\left[\tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right)\right]\right\} \\
&=O_{P}\left(\ln (T)(T h)^{-1 / 2} h^{-\nu} h^{p+1}\right)
\end{aligned}
$$

which is a higher order term. (Question: how to show this under the IID assumption and more generally under a suitable mixing condition on $ \left\{Y_{t}, X_{t}\right\} ? $ ). Thus, the bias is determined by

$$
\begin{aligned}
E \tilde{B}=& \frac{1}{T h^{\nu+1} g(x)} E \sum_{t=1}^{T} \tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) R\left(x, X_{t}\right) \\
=& \frac{1}{T h^{\nu+1} g(x)} E \sum_{t=1}^{T} \tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) \frac{r^{(p+1)}(x)}{(p+1) !}\left(X_{t}-x\right)^{p+1} \\
&+\frac{1}{T h^{\nu+1} g(x)} E \sum_{t=1}^{T} \tilde{K}_{\nu}\left(\frac{X_{t}-x}{h}\right) \frac{\left[r^{(p+1)}\left(\bar{x}_{t}\right)-r^{(p+1)}(x)\right]}{(p+1) !}\left(X_{t}-x\right)^{p+1} \\
=& \frac{h^{p+1}}{h^{\nu} g(x)} \frac{r^{(p+1)}(x)}{(p+1) !} \int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) g(x+h u) d u+O\left(h^{p+2-\nu}\right) \\
=& \frac{h^{p+1}}{h^{\nu}} \frac{1}{(p+1) !} r^{(p+1)}(x) \int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) d u+O\left(h^{p+2-\nu}\right) \\
=& \frac{1}{h^{\nu}} \frac{h^{p+1} r^{(p+1)}(x)}{(p+1) !} e_{\nu+1}^{\prime} S^{-1} C+O\left(h^{p+2-\nu}\right)
\end{aligned}
$$

where $ C=\int_{-1}^{1} u^{p+1} P(u) K(u) d u $ is a $ (p+1) \times 1 $ vector with the $ i $ -th element $ \int_{-1}^{1} u^{(p+1)-(i-1)} K(u) d u $ and we have made use of the fact that $ \tilde{K}_{\nu}(u)=e_{\nu+1}^{\prime} S^{-1} P(u) K(u) $.

**Question**: Why do we have $ \int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) d u=e_{\nu+1}^{\prime} S^{-1} C $?

Recalling $ \tilde{K}_{\nu}(u)=e_{\nu+1}^{\prime} S^{-1} P(u) K(u) $, we have

$$
\begin{aligned}
\int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) d u &=e_{\nu+1}^{\prime} S^{-1} \int_{-1}^{1} u^{p+1} P(u) K(u) d u \\
&=e_{\nu+1}^{\prime} S^{-1} C
\end{aligned}
$$

It follows that the asymptotic MSE of $ \hat{\alpha}_{\nu} $

$$
\begin{aligned}
\operatorname{MSE}\left(\hat{\alpha}_{\nu}, \alpha_{\nu}\right)=& \frac{1}{T h^{2 \nu+1}} \frac{\sigma^{2}(x)}{g(x)} e_{\nu+1}^{\prime} S^{-1} S^{*} S^{-1} e_{\nu+1} \\
&+\left[\frac{h^{p+1-\nu} r^{(p+1)}(x)}{(p+1) !}\right]^{2} e_{\nu+1}^{\prime} S^{-1} C C^{\prime} S^{-1} e_{\nu+1} \\
=& \frac{1}{T h^{2 \nu+1}} \frac{\sigma^{2}(x)}{g(x)} \int_{-1}^{1} \tilde{K}_{\nu}^{2}(u) d u \\
&+h^{2(p+1-\nu)}\left[\frac{r^{(p+1)}(x)}{(p+1) !}\right]^{2}\left[\int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) d u\right]^{2} \\
=& O\left(T^{-1} h^{-2 \nu-1}+h^{2(p+1-\nu)}\right) \\
=& O\left(T^{-1} h^{-1}+h^{4}\right) \text { if } p=1, \nu=0
\end{aligned}
$$

Therefore, the local WLS estimator $ \hat{\alpha}_{v} $ can consistently estimate the Taylor series expansion coefficient $ \alpha_{\nu} $

$$
\nu ! \hat{\alpha}_{\nu} \rightarrow^{p} \nu ! \alpha_{\nu}=r^{(\nu)}(x) \text { as } T \rightarrow \infty
$$

By minimizing the asymptotic MSE, the optimal convergence rate of $ \hat{\alpha}_{v} $ can be achieved by choosing the bandwidth

$$
h^{*} \propto T^{-\frac{1}{2 p+3}}
$$

Interestingly, the optimal bandwidth $ h^{*} $ does not depend on the order of the derivative $ \nu $. We are using the same $ h $ in estimating all $ \left\{\alpha_{\nu}\right\}_{\nu=0}^{p} $-Of course, the proportionality still depends on $ \nu $.

The intuitive idea of local polynomial smoothing in econometrics can be dated back to Nerlove $ (1966), $ where he uses a piecewise linear regression to estimate a nonlinear cost function for the electricity industry. White $ (1980, $ International Economic Review) also has a closely related discussion. He shows that *the OLS estimators that are based on the whole sample are not estimating the derivative coefficients* in a Taylor series expansion model, unless the regression function $ E\left(Y_{t} | X_{t}\right) $ is a linear function of $ X_{t} $. White (1980) discusses the case of OLS estimation over the entire support of $ X_{t} $. Apparently, *the OLS estimator can consistently estimate the regression function and its derivaties when a small neighborhood is considered*. This is exactly the idea behind local polynomial smoothing.

Next, we use the central limit theory to derive the asymptotic distribution of $ \hat{\alpha}_{v} $ 

**Theorem [Asymptotic Normality]**: If $ h=O\left(T^{-1 /(2 p+3)}\right) $ and $ r^{(p+1)}(x) $ is continuous, then as $ T \rightarrow \infty $

$$
\sqrt{T h}\left[H(\hat{\alpha}-\alpha)-\frac{h^{p+1} r^{(p+1)}(x)}{(p+1) !} S^{-1} C\right] \rightarrow^{d} N\left(0, \frac{\sigma^{2}(x)}{g(x)} S^{-1} S^{*} S^{-1}\right)
$$

where $ \alpha=\left[r(x), r^{(1)}(x), \ldots, r^{(p)}(x) / p !\right]^{\prime} $. Therefore

$$
\begin{array}{c}
\sqrt{T h^{2 \nu+1}}\left[\hat{r}^{(\nu)}(x)-r^{(\nu)}(x)-\frac{h^{p+1-\nu} r^{(p+1)}(x)}{(p+1) !} \int_{-1}^{1} u^{p+1} \tilde{K}_{\nu}(u) d u\right] \\
\rightarrow^{d} N\left(0, \frac{(\nu !)^{2} \sigma^{2}(x)}{g(x)} \int_{-1}^{1} \tilde{K}_{\nu}^{2}(u) d u\right)
\end{array}
$$

### 3.2.4 Boundary Behavior of Local Polynomial Estimator

**Question**: The above asymptotic results, namely MSE and asymptotic normality, hold for $ x $ in the interior region, i.e., $ x \in[a+h, b-h] $. What happens if $ x $ is in the boundary region?

For simplicity, we assume $ [a, b]=[0,1] $ and consider a left boundary point $ x=\tau h $ for $ \tau \in[0,1] . $ Then following reasoning analogous to what we have done for an interior point, we can obtain

$$
\begin{aligned}
\operatorname{MSE}\left[\hat{\alpha}_{\nu}(\tau h)\right]=& E\left[\hat{\alpha}_{\nu}(\tau h)-\alpha_{\nu}(0)\right]^{2} \\
=& \frac{1}{T h^{2 \nu+1}} \frac{\sigma^{2}(0)}{g(0)} e_{\nu+1}^{\prime} S_{\tau}^{-1} S_{\tau}^{*} S_{\tau}^{-1} e_{\nu+1} \\
&+\left[\frac{h^{p+1-\nu} r^{(p+1)}(0)}{(p+1) !}\right]^{2} e_{\nu+1}^{\prime} S_{\tau}^{-1} C_{\tau} C_{\tau}^{\prime} S_{\tau}^{-1} e_{\nu+1}
\end{aligned}
$$

where $ S_{\tau}, S_{\tau}^{*} $ and $ C_{\tau} $ are defined in the same way as $ S, S^{*} $ and $ C, $ with the lower bounds of all integrals involved being changed from -1 to $ -\tau . $ For example, $ S_{\tau} $ is a $ (p+1) \times(p+1) $ matrix, with its $ (i, j) $-th element equal to

$$
s_{(i-1)+(j-1), \tau}=\int_{-\tau}^{1} u^{(i-1)+(j-1)} K(u) d u
$$

Then optimal bandwidth

$$
h^*_\tau=C^*_\tau T^{-\frac{1}{2p+3}}
$$

Interestingly, the bias of $ \hat{\alpha}_{\nu}(x) $ is of the same order of magnitude no matter whether $ x $ is in the interior region or in the boundary region of $ [a, b]=[0,1]  $. Of course, the proportionality does depend on the location of $ x, $ namely $ \tau $ if $ x $ is in the boundary region.

Thus, the local polynomial estimator automatically adapts to the boundary region and **does not suffer from the boundary bias problem** as the standard kernel method.

**Question**: What is the intuition behind this? Why does the local polynomial regression estimator behave differently from the Nadaraya-Watson regression estimator? The latter has a bias equal to $ O(h) $ in the boundary region.

We consider the local linear estimator (i.e., $ p=1 $ ) as an example. The key here is the joint use of the local intercept and local slope. **The latter provides flexibility to adapt to asymmetric data coverage such as those in the boundary regions**. As a result, the bias of the local linear estimator in the boundary region is much smaller than without using a slope parameter.

An alternative interpretation is that the local polynomial estimator is equivalent to a kernel estimator but with a known density $ g(x) $, even when $ x $ is in the boundary region. Thus, **the boundary bias due to density estimation does not arise for the local polynomial estimator**.

We can also obtain an analogous asymptotic normality for $ \hat{\alpha}_{\nu}(\tau h) $ in the boundary region.

**Theorem [Asymptotic Normality]**: Suppose $ h=O\left(T^{-1 /(2 p+3)}\right) $ and $ r^{(p+1)}(x) $ is continuous. Then as $ T \rightarrow \infty $,

$$
\sqrt{T h}\left[H[\hat{\alpha}(\tau h)-\alpha(0)]-\frac{h^{p+1} r^{(p+1)}(0)}{(p+1) !} S_{\tau}^{-1} C_{\tau}\right] \rightarrow^{d} N\left(0, \frac{\sigma^{2}(0)}{g(0)} S_{\tau}^{-1} S_{\tau}^{*} S_{\tau}^{-1}\right)
$$

where

$$
\alpha(0)=\left[r(0), r^{(1)}(0), \ldots, r^{(p)}(0) / p !\right]^{\prime}
$$

Therefore, as $ T \rightarrow \infty $,

$$
\begin{array}{l}
\quad \sqrt{T h^{2 \nu+1}}\left[\hat{r}^{(\nu)}(\tau h)-r^{(\nu)}(0)-\frac{h^{p+1-\nu} r^{(p+1)}(0)}{(p+1) !} \int_{-\tau}^{1} u^{p+1} \tilde{K}_{\nu, \tau}(u) d u\right] \\
\rightarrow^{d} N\left(0, \frac{(\nu !)^{2} \sigma^{2}(0)}{g(0)} \int_{-\tau}^{1} \tilde{K}_{\nu, \tau}^{2}(u) d u\right)
\end{array}
$$

where the equivalent boundary kernel

$$
\tilde{K}_{\nu, \tau}(u)=e_{\nu+1}^{\prime} S_{\tau}^{-1} P(u) K(u)
$$

**Proof**: The proof is similar to the derivation of the asymptotic MSE for the local polynomial estimator in the interior region.

**Question**: *Why is the local polynomial estimator useful in economic applications?*

First of all, it avoids the well-known boundary problem in smoothed kernel regression estimation. Second, it has a smaller bias term for the regression estimator in the areas where the marginal density $ g(x) $ of $ X_{t} $ is a steep slope (i.e., when $ g^{\prime}(x) $ is large in absolute value), and consequently is more efficient than the Nadaraya-Watson estimator. A steep slope of $ g(x) $ means that the observations will be asymmetrically distributed around $ x $.

Smoothed nonparametric regression estimators have been widely used in econometrics and economics. For example,

- Ait-Sahalia and Lo (1998, Journal of Finance) use a multivariate kernel-based regression estimator to estimate the option pricing function

$$
\begin{aligned}
G_{t} &=G\left(X_{t}, P_{t}, \tau_{t}, r_{t, m}\right) \\
&=\exp \left[-r_{t, m}(m-t)\right] \int_{-\infty}^{\infty} Y\left(p_{t}, X_{t}\right) f_{t}^{*}\left(P_{m} ; T\right) d p_{t}
\end{aligned}
$$

where $ X_{t} $ is the strike price at time $ t, P_{t} $ is the price of the underlying asset at time $ t, m $ is the length of maturity of the option, and $ r_{t, m} $ is the riskfree rate at time $ t $ with maturity $ m $.

They then use

$$
\frac{\partial^{2} \hat{G}_{t}}{\partial^{2} X_{t}}=\exp \left[-r_{t, t}(T-t)\right] \hat{f}^{*}\left(P_{t}\right)
$$

to obtain the risk-neutral probability density estimator $ \hat{f}^{*}\left(P_{t}\right), $ which contains rich information about investor preferences and dynamics of data generating process.

- Ait-Sahalia (1996), Stanton (1997), and Chapman and Pearson (1999) use the Nadaraya-Watson estimator $ \hat{r}\left(X_{t-1}\right) $ to estimate $ E\left(X_{t} | X_{t-1}\right), $ where $ X_{t} $ is the spot interest rate, and examine whether the the drift function $ \mu\left(X_{t}\right) $ in the diffusion model

$$
d X_{t}=\mu\left(X_{t}\right) d t+\sigma\left(X_{t}\right) d W_{t}
$$

is linear or nonlinear.

There are many potential topics in time series econometrics that can apply smoothed nonparametric regression estimators. Below are some examples.

**Example 1 [Time-Varying CAPM]**: Consider a Capital Asset Pricing Model (CAPM) with time-varying parameters:

$$
X_{i t}=\alpha_{i}\left(I_{t-1}\right)+\beta_{i}\left(I_{t-1}\right)^{\prime} \lambda_{t}+\varepsilon_{i t}, \quad i=1, \ldots, n, t=1, \ldots, T
$$

where

$$
E\left(\epsilon_{i t} | I_{t-1}\right)=0
$$

This is related to the debate about constant betas versus non-constant betas. From the Euler equation,

$$
\alpha_{i t}=\alpha_{i}\left(I_{t-1}\right), \quad \beta_{i t}=\beta_{i}\left(I_{t-1}\right)
$$

are possibly time-varying coefficients. Suppose $ \alpha_{i t}=\alpha_{i}\left(Z_{t}\right) $ and $ \beta_{i t}=\beta_{i}\left(Z_{t}\right) $, where $ Z_{t} $ is some state variable or vector in $ I_{t-1} $ but the functional forms $ \alpha_{i}(\cdot) $ and $ \beta_{i}(\cdot) $ are unknown. Then one can estimate $ \alpha_{i}(\cdot) $ and $ \beta_{i}(\cdot) $ by solving the local sum of squared residuals minimization problem

$$
\min _{\left\{\alpha_{i}(\cdot), \beta_{i}(\cdot)\right\}} \sum_{i=1}^{n} \sum_{t=1}^{T}\left[X_{i t}-\alpha_{i}\left(Z_{t}\right)-\beta_{i}\left(Z_{t}\right)^{\prime} \lambda_{t}\right]^{2} K_{h}\left(z-Z_{t}\right)
$$

for example, in local linear polynomial 

$$
\begin{aligned} 
\alpha_{i}\left(Z_{t}\right)&=\alpha_{i 0}+\alpha_{i 1}\left(Z_{t}-z\right)+ \text{higher order trem} \\
\beta_{i}\left(Z_{t}\right)&=\beta_{i 0}+\beta_{i 1}\left(Z_{t}-z\right)+ \text{higher order trem}
\end{aligned}
$$

and we have

$$
\begin{aligned}
\hat{\alpha}_{i}(z)=\hat{\alpha}_{i 0} \\
\hat{\beta}_{i}(z)=\hat{\beta}_{i 0}
\end{aligned}
$$

**Question**: What is the economic rationale that $ \alpha_{i t} $ and $ \beta_{i t} $ are time-varying?

Kevin Wang (2002, Journal of Finance), Ang and Kristense (2012, Journal of Financial Economics), and Li and Yang (2012, Journal of Empirical Finance) all consider time-varying betas by assuming that the time-varying betas are unknown functions of economic variables or time.

**Example 2 [Time-varying Risk Aversion and Equity Risk Premium Puzzle]** Suppose a representative economic agent is solving the lifetime utility maximization problem

$$
\max _{\left\{C_{t}\right\}} E\left[\sum_{j=0}^{\infty} \beta^{j} U\left(C_{t+j}\right) | I_{t}\right]
$$

subject to the inter-temporal budget constraint

$$
C_{t}=P_{t}\left(A_{t+1}-A_{t}\right) \leq Y_{t}+D_{t} A_{t}
$$

where $ C_{t} $ is the consumption, $ A_{t} $ is a financial asset, $ Y_{t} $ is the labor income, $ D_{t} $ is the dividends on the asset, and $ P_{t} $ is the price of asset. 

The Euler equation for this maximization problem is

$$
E\left[\beta\left(\frac{U^{\prime}\left(C_{t+1}\right)}{U^{\prime}\left(C_{t}\right)}\right)\left(\frac{P_{t+1}+D_{t+1}}{P_{t}}\right)-1 | I_{t}\right]=0
$$

where $ \left(P_{t+1}+D_{t+1}\right) / P_{t} $ is the gross return on the asset in percentage, $ \beta U^{\prime}\left(C_{t+1}\right) / U^{\prime}\left(C_{t}\right) $ is the inter-temporal marginal rate of substitution, also called the stochastic discount factor. The latter is the time-discounted risk attitude of the representative economic agent.

Suppose the utility function $ U(\cdot) $ of the representative economic agent is

$$
U\left(C_{t}\right)=\frac{C_{t}^{1-\gamma}-1}{1-\gamma}, \text { for } \gamma>0
$$

This is the so-called Constant Relative Risk Aversion (CRRA) utility function. The parameter $ \gamma $ is a measure of the degree of risk aversion. The larger $ \gamma, $ the more risk averse the economic agent.

With the CRRA utility function, the Euler equation becomes

$$
E\left[\beta\left(\frac{C_{t+1}}{C_{t}}\right)^{-\gamma}\left(\frac{P_{t+1}+D_{t+1}}{P_{t}}\right)-1 | I_{t}\right]=0
$$

The unknown parameters $ \beta $ and $ \gamma $ can be estimated using the generalized method of moments. The empirical estimate for $ \gamma $ is too small to justify the observed relatively large difference between stock returns and bond returns. This difficulty is called an "equity risk premium puzzle."

The equity risk premium puzzle exists because the excess of stock returns over re- turns on investments in bonds is larger than could be explained by standard models of "rational asset" prices. This was first proposed by Mehra and Prescott (1985, "The Equity Premium Puzzle," Journal of Monetary Economics 15). Since then, various efforts have been made to explain this puzzle.

Among many other things, a possible solution is to assume both structural parameters $ \beta $ and $ \gamma $ are **time-varying**, namely $ \beta_{t}=\beta\left(I_{t-1}\right) $ and $ \gamma_{t}=\gamma\left(I_{t-1}\right), $ where $ I_{t-1} $ is the information set available at time $ t-1 . $ More specifically, we can assume that $ \beta_{t}=\beta\left(X_{t}\right) $ and $ \gamma_{t}=\gamma\left(X_{t}\right) $ for some unknown smooth functions $ \beta(\cdot) $ and $ \gamma(\cdot), $ where $ X_{t} \in I_{t-1} $ is a state vector that is expected to affect both $ \beta_{t} $ and $ \gamma_{t} $. These time-varying functions can reveal useful information about how the risk attitude of the economic agent changes with the state variables $ X_{t} $.

**Question**: How to estimate $ \beta(\cdot) $ and $ \gamma(\cdot) $?

Recall that the Euler equation is a conditional moment specification, which can be equivalently converted into a generalized regression model:

$$
\beta\left(X_{t}\right)\left(\frac{C_{t+1}}{C_{t}}\right)^{-\gamma\left(X_{t}\right)}\left(\frac{P_{t+1}+D_{t+1}}{P_{t}}\right)=1+\varepsilon_{t+1}
$$

where $ \varepsilon_{t+1} $ is a stochastic pricing error satisfying the MDS property

$$
E\left(\epsilon_{t+1} | I_{t}\right)=0
$$

As a result, we can estimate the unknown functions $ \beta(\cdot) $ and $ \gamma(\cdot) $ using minimizing the following local sum of squared generalized residuals:

$$
\min _{\beta(\cdot), \gamma(\cdot)} \sum_{t=1}^{T}\left[\beta\left(X_{t}\right)\left(\frac{C_{t+1}}{C_{t}}\right)^{-\gamma\left(X_{t}\right)}\left(\frac{P_{t+1}+D_{t+1}}{P_{t}}\right)-1\right]^{2} K_{h}\left(\frac{x-X_{t}}{h}\right)
$$

where $ \beta(x) $ and $ \gamma(x) $ will be estimated by some low-order local polynomial estimators, such as local linear estimators.

More generally, one can incorporate the Euler equations into a time-varying GMM framework

$$
E\left\{Z_{t}\left[\beta\left(X_{t}\right)\left(\frac{C_{t+1}}{C_{t}}\right)^{-\gamma\left(X_{t}\right)}\left(\frac{P_{t+1}+D_{t+1}}{P_{t}}\right)-1\right]\right\}=0
$$

where $ Z_{t} $ is a set of instrumental variables (transform from conditional condition to unconditional condition). By approximating $ \beta(x) $ and $ \gamma(x) $ using a local polynomial respectively, we can obtain local polynomial GMM estimators for $ \beta(x) $ and $ \gamma(x) $ by **minimizing a local quadratic form of the sample moment**.

For example, in local linear polynomial

$$
\begin{aligned} 
\gamma\left(X_{t}\right)&=\gamma_{0}+\gamma_{ 1}\left(X_{t}-x\right)+ \text{higher order trem} \\
\beta\left(X_{t}\right)&=\beta_{ 0}+\beta_{1}\left(X_{t}-x\right)+ \text{higher order trem}
\end{aligned}
$$

and we have

$$
\begin{aligned}
\hat{\gamma}(z)=\hat{\gamma}_{0} \\
\hat{\beta}(z)=\hat{\beta}_{0}
\end{aligned}
$$

**Example 3 [Functional-Coefficient Autoregressive Model]**: Suppose $ \left\{X_{t}\right\} $ is a strictly stationary time series process and follows a **generalized AR(p) process**:

$$
E\left(X_{t} | I_{t-1}\right)=\sum_{j=1}^{p} \alpha_{j}\left(X_{t-d}\right) X_{t-j}
$$

where the autoregressive coefficient $ \alpha_{j}\left(X_{t-d}\right) $ is a function of $ X_{t-d} $, and the functional form $ \alpha_{j}(\cdot) $ is unknown. The lag order $ d $ is called a delay parameter.

**Example 4 [Volatility Smile and Derivatives Pricing]**: To derive the price of a European call option, Black and Scholes (1973) impose the following assumptions: 

- (A1): $ d \ln S_{t}=\mu d t+\sigma d W_{t} $, where $ W_{t} $ is the Brownian motion, and $ S_{t} $ is the underlying stock price;
- (A2): Frictionless and complete market (no transaction costs; short sales allowed);
- (A3): Constant riskfree interest rate $ r $
- (A4): European call option, whose payoff function is given by

$$
\phi\left(S_{t}\right)=\max \left(S_{t}-K, 0\right)
$$

where $ K $ is the strike price.

Based on a no-arbitrage argument, the following European call option price can be derived:

$$
\pi_{t}=S_{0} \Phi(d)-K e^{-r t} \Phi(d-\sigma \sqrt{t})
$$

where $ t=m-\tau_{t}, m $ is the maturity period, and

$$
d=\frac{\ln \left(S_{0} / K e^{-r t}\right)}{\sigma \sqrt{t}}+\frac{1}{2} \sigma \sqrt{\tau}
$$

From the Black-Scholes formula, we can inversely derive the volatility

$$
\sigma_{t}^{2}=\sigma^{2}\left(K_{t}, S_{t}, r_{t}, \tau_{t}, \pi_{t}\right)
$$

This is called the **implied volatility.** If the pricing formula is correct, then the implied volatility $ \sigma_{t}^{2} $ is a constant function of strike price $ K_{t} . $ This is because $ \sigma_{t}^{2} $ depends only on the data generating process and should not depend on the strike price in any manner. 

In contrast, if the pricing is incorrect (e.g., the log-normality assumption cannot capture heavy tails of the asset price distribution), then $ \sigma_{t}^{2} $ is generally a convex function of strike price $ K_{t} . $ This is called a **volatility smile**.

**Question**: Is the concept of volatility smile well-defined when the distribution of the underlying asset is non-Gaussian (i.e., not log-normal)?

### 3.2.5 Curse of Dimensionality and Dimension Reduction

Like in multivariate probability density estimation, we will also encounter the curse of dimensionality for regression estimation, when the dimension $ d $ of the regressors vector $ X_{t} $ is high. Again, **some simplifying assumptions can be made to reduce the curse of dimensionality**. Some restrictions on the unknown functions of interest may come from economic theory. For example, a demand function must satisfy the property of a homogeneous function of degree zero. Below are a few examples often used in econometrics and time series econometrics:

**Example [single Index Model]**:
$$
Y_{t}=m\left(X_{t}^{\prime} \beta^{0}\right)+\varepsilon_{t}
$$

where $ E\left(\varepsilon_{t} | X_{t}\right)=0, $ the linear combination $ X_{t}^{\prime} \beta^{0} $ is a scalar variable, and the functional form $ m(\cdot) $ is unknown. Often, the interest is inference of unknown parameter $ \beta^{0} $. See Stoker (1986) for more discussion.

**Example [Partially Linear Regression Model]**:
$$
Y_{t}=X_{t}^{\prime} \beta^{0}+m\left(Z_{t}\right)+\varepsilon_{t}
$$

where $ E\left(\varepsilon_{t} | X_{t}, Z_{t}\right)=0, $ and $ m(\cdot) $ is an unknown function of $ Z_{t} $ only. Here, the interest is inference of the marginal effect of the economic variables $ X_{t} $. However, one has to consistently estimate the unknown function $ m\left(Z_{t}\right) $ in order to obtain consistent estimation of parameter $ \beta^{0} $.

**Example [Functional Coefficient Model]**:

$$
Y_{t}=X_{t}^{\prime} \beta\left(Z_{t}\right)+\varepsilon_{t}
$$

where $ E\left(\varepsilon_{t} | X_{t}, Z_{t}\right)=0, $ and the parameter vector $ \beta(\cdot) $ is an unknown function of $ Z_{t} $ only.

**Example [Additive Nonlinear Autoregressive Model]**:

$$
X_{t}=\sum_{j=1}^{p} \alpha_{j}\left(X_{t-j}\right)+\varepsilon_{t}
$$

where the $ \alpha_{j}(\cdot) $ functions are unknown.
