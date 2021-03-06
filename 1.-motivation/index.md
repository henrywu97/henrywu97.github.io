# 

# 1. Motivation

## 1.1 Nonparametric Estimation

Suppose $ \left\{X_{t}\right\} $ is a strictly stationary process with marginal probability density function $ g(x) $ and pairwise joint probability density function $ f_{j}(x, y) $ of $ \left(X_{t}, X_{t-j}\right) $, and a random sample $ \left\{X_{t}\right\}_{t=1}^{T} $ of size $ T $ is observed. Then,

- How to estimate the <u>marginal pdf</u> $ g(x) $ of $ \left\{X_{t}\right\} ? $
- How to estimate the <u>pairwise joint pdf</u> $ f_{j}(x, y) $ of $ \left(X_{t}, X_{t-j}\right) ? $
- How to estimate the <u>autoregression function</u> $ r_{j}(x)=E\left(X_{t} | X_{t-j}=x\right) ? $
- How to estimate the <u>spectral density (自回归函数的傅里叶变换)</u> $ h(\omega) $ of $ \left\{X_{t}\right\} ? $
- How to estimate the <u>generalized spectral density</u> $ f(\omega, u, v) $ of $ \left\{X_{t}\right\} ? $
- How to estimate the <u>bispectral density</u> $ b\left(\omega_{1}, \omega_{2}\right) ? $
- How to estimate a <u>nonlinear autoregressive conditional heteroskedastic model</u> $ X_{t}=\mu\left(X_{t-1}, \ldots, X_{t-p}\right)+\sigma\left(X_{t-1}, \ldots, X_{t-q}\right) \varepsilon_{t}, \quad\left\{\varepsilon_{t}\right\} \sim i . i . d .(0,1) $ where $ \mu(\cdot) $ and $ \sigma(\cdot) $ are unknown functions of the past information. Under certain regularity conditions, $ \mu(\cdot) $ is the <u>conditional mean</u> of $ X_{t} $ given $ I_{t-1}=\left\{X_{t-1}, X_{t-2}, \ldots\right\} $ and $ \sigma^{2}(\cdot) $ is the <u>conditional variance</u> of $ X_{t} $ given $ I_{t-1} $
- How to estimate a <u>semi-nonparametric functional coefficient autoregressive process</u> $ X_{t}=\sum_{j=1}^{p} \alpha_{j}\left(X_{t-d}\right) X_{t-j}+\epsilon_{t}, \quad E\left(\varepsilon_{t} | I_{t-1}\right)=0 $ where $ \alpha_{j}(\cdot) $ is unknown, and $ d>0 $ is a time lag parameter?
- How to estimate a nonparametric <u>additive autoregressive process</u>

$$
X_{t}=\sum_{j=1}^{p} \mu_{j}\left(X_{t-j}\right)+\varepsilon_{t}, \quad E\left(\varepsilon_{t} | I_{t-1}\right)=0 \text { a.s. }
$$

where the $ \mu_{j}(\cdot) $ functions are unknown?

- How to estimate a locally linear <u>time-varying regression</u> model

$$
Y_{t}=X_{t}^{\prime} \beta(t / T)+\varepsilon_{t}
$$

where $ \beta(\cdot) $ is an unknown smooth deterministic function of time?

- How to use these estimators in economic and financial applications?

**Nonparametric estimation** is often called **nonparametric smoothing**, since a key parameter called <u>smoothing parameter</u> is used to control the degree of the estimated curve. Nonparametric smoothing first arose from spectral density estimation in time series analysis. In a discussion of the seminal paper by Bartlett (1946), Henry Daniels suggested that <u>a possible improvement on spectral density estimation could be made by smoothing the periodogram</u> (see Chapter 3 ), which is the squared discrete Fourier transform of the random sample $ \left\{X_{t}\right\}_{t=1}^{T} $. The theory and techniques were then systematically developed by Bartlett (1948,1950). Thus, smoothing techniques were already
prominently featured in time series analysis more than 70 years ago.

In the earlier stage of nonlinear time series analysis (see Tong (1990)), the focus was on various nonlinear parametric forms, such as threshold autoregressive models, smooth transition autoregressive models, and Regime-switch Markov chain autoregressive models (see Chapter 8 for details). Recent interest has been mainly in nonparametric curve estimation, which does not require the knowledge of the functional form beyond certain
smoothness conditions on the underlying function of interest.

**Question**: Why is nonparametric smoothing popular in statistics and econometrics?

There are several **reasons for the popularity of nonparametric analysis**. In particular, three main reasons are:

- Demands for nonlinear approaches;
- Availability of large data sets;
- Advance in computer technology.

Indeed, as Granger (1999) points out, the speed in computing technology increases much faster than the speed at which data grows.

## 1.2 Basic Ideas of Nonparametric Smoothing

To obtain basic ideas about nonparametric smoothing methods, we now consider two examples, one is the estimation of a regression function, and the other is the estimation of a probability density function.

**Example 1 [Regression Function]**: Consider the first order autoregression function
$$
r_{1}(x)=E\left(X_{t} | X_{t-1}=x\right)
$$

We can write

$$
X_{t}=r_{1}\left(X_{t-1}\right)+\varepsilon_{t}
$$

where $ E\left(\epsilon_{t} | X_{t-1}\right)=0 $ by construction. We assume $ E\left(X_{t}^{2}\right)<\infty $

Suppose a sequence of bases $ \left\{\psi_{j}(x)\right\} $ constitutes a <u>complete orthonormal basis</u> for the space of square-integrable functions. Then we can always decompose the function
$$
r_{1}(x)=\sum_{j=0}^{\infty} \alpha_{j} \psi_{j}(x)
$$

where the Fourier coefficient

$$
\alpha_{j}=\int_{-\infty}^{\infty} r_{1}(x) \psi_{j}(x) d x
$$

which is the projection of $ r_{1}(x) $ on the base $ \psi_{j}(x) $.

Suppose there is a quadratic function $ r_{1}(x)=x^{2} $ for $ x \in[-\pi, \pi] . $ Then
$$
\begin{aligned}
r_{1}(x) &=\frac{\pi^{2}}{3}-4\left(\cos (x)-\frac{\cos (2 x)}{2^{2}}+\frac{\cos (3 x)}{3^{2}}-\cdots\right) \\
&=\frac{\pi^{2}}{3}-4 \sum_{j=1}^{\infty}(-1)^{j-1} \frac{\cos (j x)}{j^{2}}
\end{aligned}
$$

For another example, suppose the regression function is a step function, namely

$$
r_{1}(x)=\left\{\begin{array}{cl}
-1 & \text { if }-\pi<x<0 \\
0 & \text { if } x=0 \\
1 & \text { if } 0<x<\pi
\end{array}\right.
$$

Then we can still expand it as an infinite sum of periodic series,

$$
\begin{aligned}
r_{1}(x) &=\frac{4}{\pi}\left[\sin (x)+\frac{\sin (3 x)}{3}+\frac{\sin (5 x)}{5}+\cdots\right] \\
&=\frac{4}{\pi} \sum_{j=0}^{\infty} \frac{\sin [(2 j+1) x]}{(2 j+1)}
\end{aligned}
$$

In general, we do not assume that the function form of $ r_{1}(x) $ is known, except that we still maintain the assumption that $ r_{1}(x) $ is a square-integrable function. Because $ r_{1}(x) $ is square-integrable, we have

$$
\begin{aligned}
\int_{-\infty}^{\infty} r_{1}^{2}(x) d x &=\sum_{j=0}^{\infty} \sum_{k=0}^{\infty} \alpha_{j} \alpha_{k} \int_{-\infty}^{\infty} \psi_{j}(x) \psi_{k}(x) d x \\
&=\sum_{j=0}^{\infty} \sum_{k=0}^{\infty} \alpha_{j} \alpha_{k} \delta_{j, k} \text { by orthonormality } \\
&=\sum_{j=0}^{\infty} \alpha_{j}^{2}<\infty
\end{aligned}
$$

where $ \delta_{j, k} $ is the <u>Kronecker delta function</u>: $ \delta_{j, k}=1 $ if $ j=k $ and 0 otherwise.

The squares summability implies $ \alpha_{j} \rightarrow 0 $ as $ j \rightarrow \infty, $ that is, $ \alpha_{j} $ becomes less important as the order $ j \rightarrow \infty . $ This suggests that a truncated sum
$$
r_{1 p}(x)=\sum_{j=0}^{p} \alpha_{j} \psi_{j}(x)
$$

<u>can be used to approximate $ r_{1}(x) $ arbitrarily well if $ p $ is sufficiently large</u>. The approximation error, or the bias,
$$
\begin{aligned}
b_{p}(x) & \equiv r_{1}(x)-r_{1 p}(x) \\
&=\sum_{j=p+1}^{\infty} \alpha_{j} \psi_{j}(x) \\
& \rightarrow 0
\end{aligned}
$$

However, the coefficient $ \alpha_{j} $ is unknown. To obtain a feasible estimator for $ r_{1}(x), $ we consider the following sequence of truncated regression models

$$
X_{t}=\sum_{j=0}^{p} \beta_{j} \psi_{j}\left(X_{t-1}\right)+\varepsilon_{p t}
$$

where $ p \equiv p(T) \rightarrow \infty $ is the number of series terms that depends on the sample size $ T $. We need $ p / T \rightarrow 0 $ as $ T \rightarrow \infty, $ i.e., the number of $ p $ is much smaller than the sample size $ T . $ Note that the regression error $ \varepsilon_{p t} $ is not the same as the true innovation $ \varepsilon_{t} $ for each given $ p $. Instead, it contains the true innovation $ \varepsilon_{t} $ and the bias $ b_{p}\left(X_{t-1}\right) $.

The ordinary least squares estimator

$$
\begin{aligned}
\hat{\beta} &=\left(\Psi^{\prime} \Psi\right)^{-1} \Psi^{\prime} X \\
&=\left(\sum_{t=2}^{T} \psi_{t} \psi_{t}^{\prime}\right)^{-1} \sum_{t=2}^{T} \psi_{t} X_{t}
\end{aligned}
$$

where

$$
\Psi=\left(\psi_{1}^{\prime}, \ldots, \psi_{T}^{\prime}\right)^{\prime}
$$

is a $ T \times p $ matrix, and

$$
\psi_{t}=\left[\psi_{0}\left(X_{t-1}\right), \psi_{1}\left(X_{t-1}\right), \ldots, \psi_{p}\left(X_{t-1}\right)\right]^{\prime}
$$

is a $ p \times 1 $ vector. The series-based regression estimator is

$$
\hat{r}_{1 p}(x)=\sum_{j=0}^{p} \hat{\beta}_{j} \psi_{j}(x)
$$

To ensure that $ \hat{r}_{1 p}(x) $ is asymptotically unbiased, we must let $ p=p(T) \rightarrow \infty $ as $ T \rightarrow \infty $ (e.g., $ p=\sqrt{T} $ ). However, if $ p $ is too large, the number of estimated parameters will be too large, and as a consequence, the sampling variation of $ \beta $ will be large (i.e., the estimator $ \hat{\beta} $ is imprecise.) We must <u>choose an appropriate $ p=P(T) $ so as to balance the bias and the sampling variation</u>. The truncation order $ p $ is called a **smoothing parameter** because it controls the smoothness of the estimated function $ \hat{r}_{1 p}(x) . $ In general, for any given sample, a large $ p $ will give a smooth estimated curve whereas a small $ p $ will give a wiggly estimated curve. If $ p $ is too large such that the variance of $ \hat{r}_{1 p}(x) $ is larger than its squared bias, we call that there exists **oversmoothing**. In contrast, if $ p $ is too sall such that the variance of $ \hat{r}_{1 p}(x) $ is smaller than its squared bias, then we call that there exists **undersmoothing**. <u>Optimal smoothing is achieved when the variance of $ \hat{r}_{1 p}(x) $ balances its squared bias</u>. The series estimator $ \hat{r}_{1 p}(x) $ is called a **global smoothing method**, because once $ p $ is given, the estimated function $ \hat{r}_{1 p}(x) $ is determined over the entire domain of $ X_{t} $.

<u>Under suitable regularity conditions, $ \hat{r}_{1 p}(x) $ will consistently estimate the unknown function $ r_{1}(x) $ as the sample size $ T $ increases</u>. This is called **nonparametric estimation** because no parametric functional form is imposed on $ r_{1}(x) $.

The base functions $ \left\{\psi_{j}(\cdot)\right\} $ can be the <u>Fourier series</u> (i.e., the sin and cosine functions $ ), $ and $ B $ -spline functions if $ X_{t} $ has a bounded support. See (e.g.) Andrews (1991, Econometrica and Hong and White (1995, Econometrica) for applications.

**Example 2 [Probability Density Function]**: Suppose the PDF $ g(x) $ of $ X_{t} $ is a smooth function with unbounded support. We can expand
$$
g(x)=\phi(x) \sum_{j=0}^{\infty} \beta_{j} H_{j}(x)
$$

where the function

$$
\phi(x)=\frac{1}{\sqrt{2 \pi}} \exp \left(-\frac{1}{2} x^{2}\right)
$$

is the $ N(0,1) $ density function, and $ \left\{H_{j}(x)\right\} $ is the sequence of Hermite polynomials, defined as
$$
(-1)^{j} \frac{d^{j}}{d x^{j}} \Phi(x)=-H_{j-1}(x) \phi(x) \text { for } j>0
$$

where $ \Phi(\cdot) $ is the $ N(0,1) $ CDF. For example,

$$
\begin{array}{l}
H_{0}(x)=1 \\
H_{1}(x)=x \\
H_{2}(x)=\left(x^{2}-1\right) \\
H_{3}(x)=x\left(x^{2}-3\right) \\
H_{4}(x)=x^{4}-6 x^{2}+3
\end{array}
$$

See, for example, Magnus, Oberhettinger and Soni (1966, Section 5.6) and Abramowitz and Stegun (1972, Ch.22).

Here, the **Fourier coefficient**
$$
\beta_{j}=\int_{-\infty}^{\infty} g(x) H_{j}(x) \phi(x) d x
$$

Again, $ \beta_{j} \rightarrow 0 $ as $ j \rightarrow \infty $ given $ \sum_{j=0}^{\infty} \beta_{j}^{2}<\infty $

The $ N(0,1) $ PDF $ \phi(x) $ is the leading term to approximate the unknown density $ g(x) $ and the Hermite polynomial series will capture departures from normality (e.g., skewness and heavy tails).

To estimate $ g(x), $ we can consider the sequence of truncated probability densities

$$
g_{p}(x)=C_{p}^{-1} \phi(x) \sum_{j=0}^{p} \beta_{j} H_{j}(x)
$$

where the constant

$$
C_{p}=\sum_{j=0}^{p} \beta_{j} \int H_{j}(x) \phi(x) d x
$$

is a normalization factor to ensure that $ g_{p}(x) $ is a PDF for each $ p $. The unknown parameters $ \left\{\beta_{j}\right\} $ can be estimated from the sample $ \left\{X_{t}\right\}_{t=1}^{T} $ via the maximum likelihood estimation (MLE) method. For example, suppose $ \left\{X_{t}\right\} $ is an IID sample. Then

$$
\hat{\beta}=\arg \max _{\beta} \sum_{t=1}^{T} \ln \hat{g}_{p}\left(X_{t}\right)
$$

To ensure that

$$
\hat{g}_{p}(x)=\hat{C}_{p}^{-1} \phi(x) \sum_{j=0}^{p} \hat{\beta}_{j} H_{j}(x)
$$

is asymptotically unbiased, we must let $ p=p(T) \rightarrow \infty $ as $ T \rightarrow \infty . $ However, $ p $ must grow more slowly than the sample size $ T $ grows to infinity so that the sampling variation of $ \hat{\beta} $ will not be too large.

For the use of Hermite Polynomial series expansions, see (e.g.) Gallant and Tauchen (1996, Econometric Theory), Ait-Sahalia (2002, Econometrica), and Cui, Hong and Li (2020).

## 1.3 Advantages & Disadvantages of nonparametric smoothing

**Question**: What are the **advantages of nonparametric smoothing methods**?

They require <u>few assumptions or restrictions on the data generating process</u>. In particular, they do not assume a specific functional form for the function of interest (of course certain smoothness condition such as differentiability is required). They can <u>deliver a consistent estimator for the unknown function, no matter whether it is linear or nonlinear</u>. Thus, nonparametric methods can effectively <u>reduce potential systematic biases due to model misspecification</u>, which is more likely to be encountered for parametric modeling.

**Question**: What are the **disadvantages** of nonparametric methods?

- Nonparametric methods <u>require a large data set for reasonable estimation</u>. Furthermore, there exists a notorious problem of "curse of dimensionality", when the function of interest contains multiple explanatory variables. This will be explained below.
- There exists another notorious "boundary effect" problem for nonparametric estimation near the boundary regions of the support. This occurs due to asymmetric coverage of data in the boundary regions.
- <u>Coefficients are usually difficult to interpret from an economic point of view</u>.
- There exists a danger of <u>potential overfitting</u>, in the sense that nonparametric method, due to its flexibility, tends to capture non-essential features in a data which will not appear in out-of-sample scenarios.

The above two motivating examples are the so-called **orthogonal series expansion methods**. There are other nonparametric methods, such as <u>splines smoothing, kernel smoothing, $ k $ -near neighbor, and local polynomial smoothing</u>. As mentioned earlier,
series expansion methods are examples of so-called **global smoothing**, because the coefficients are estimated using all observations, and they are then used to evaluate the values of the underlying function over all points in the support of $ X_{t} . $ A nonparametric series model is an increasing sequence of parametric models, as the sample size $ T $ grows. In this sense, it is also called a sieve estimator. 

In contrast, kernel and local polynomial methods are examples of the so-called **local smoothing methods**, because estimation only requires the observations in a neighborhood of the point of interest. Below <u>we will mainly focus on kernel and local polynomial smoothing methods,</u> due to their simplicity and intuitive nature.
