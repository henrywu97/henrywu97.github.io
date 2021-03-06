# 

# 2. Kernel Density Method

## 2.1 Univariate Density Estimation

### 2.1.0 Parametric Approach

Suppose $ \left\{X_{t}\right\} $ is a <u>strictly stationary time series process</u> with unknown marginal PDF $ g(x) $.

**Question**: How to <u>estimate the marginal</u> PDF $ g(x) $ of the time series process $ \left\{X_{t}\right\} ? $

We first **consider a parametric approach**. Assume that $ g(x) $ is an $ N\left(\mu, \sigma^{2}\right) $ PDF with unknown $ \mu $ and $ \sigma^{2} $ ? Then we know the functional form of $ g(x) $ up to two unknown parameters $ \theta=\left(\mu, \sigma^{2}\right)^{\prime} $

$$
g(x, \theta)=\frac{1}{\sqrt{2 \pi \sigma^{2}}} \exp \left[-\frac{1}{2 \sigma^{2}}(x-\mu)^{2}\right], \quad-\infty<x<\infty
$$

To estimate $ g(x, \theta), $ it suffices to estimate two unknown parameters $ \mu $ and $ \sigma^{2} $. Based on the random sample $ \left\{X_{t}\right\}_{t=1}^{T}, $ we can obtain the <u>maximum likelihood estimators (MLE)</u>,

$$
\begin{aligned}
\hat{\mu} &=\frac{1}{T} \sum_{t=1}^{T} X_{t} \\
\hat{\sigma}^{2} &=\frac{1}{T} \sum_{t=1}^{T}\left(X_{t}-\hat{\mu}\right)^{2}
\end{aligned}
$$

The approach taken here is called a **parametric approach**, that is, assuming that the unknown PDF is a known functional form up to some unknown parameters. It can be shown that the parameter estimator $ \theta $ converges to the unknown parameter value $ \theta_{0} $ at a root-$ T $ **convergence rate** in the sense that $ \sqrt{T}\left(\hat{\theta}-\theta_{0}\right)=O_{P}(1), $ or $ \hat{\theta}-\theta_{0}=O_{P}\left(T^{-1 / 2}\right) $ where $ \hat{\theta}=\left(\hat{\mu}, \hat{\sigma}^{2}\right)^{\prime}, \theta_{0}=\left(\mu_{0}, \sigma_{0}^{2}\right)^{\prime}, $ and $ O_{P}(1) $ denotes boundedness in probability. The root-$ T $ convergence rate is called the parametric convergence rate for $ \hat{\theta} $ and $ g(x, \hat{\theta}) $. As
we will see below, nonparametric density estimators will have a slower convergence rate.

**Question**: What is the definition of $ O_{P}\left(\delta_{T}\right) ? $

Let $ \left\{\delta_{T}, T \geq 1\right\} $ be a sequence of positive numbers. A random variable $ Y_{T} $ is said to be at most of order $ \delta_{T} $ in probability, written $ Y_{T}=O_{P}\left(\delta_{T}\right), $ if the sequence $ \left\{Y_{T} / \delta_{T}, T \geq 1\right\} $ is tight, that is, if

$$
\lim _{\lambda \rightarrow \infty} \lim _{T \rightarrow \infty} \sup P\left(\left|Y_{T} / \delta_{T}\right|>\lambda\right)=0
$$

Tightness is usually indicated by writing $ Y_{T} / \delta_{T}=O_{P}(1) $

**Question**: What is the <u>advantage of the parametric approach</u>?

By the mean-value theorem, we obtain

$$
\begin{aligned}
g(x, \hat{\theta})-g(x) &=g\left(x, \theta_{0}\right)-g(x)+\frac{\partial}{\partial \theta} g(x, \bar{\theta})\left(\hat{\theta}-\theta_{0}\right) \\
&=0+\frac{1}{\sqrt{T}} \frac{\partial}{\partial \theta} g(x, \bar{\theta}) \sqrt{T}\left(\hat{\theta}-\theta_{0}\right) \\
&=0+O_{P}\left(T^{-1 / 2}\right) \\
&=O_{P}\left(T^{-1 / 2}\right)
\end{aligned}
$$

Intuitively, the first term, $ g\left(x, \theta_{0}\right)-g(x), $ is the bias of the density estimator $ g(x, \hat{\theta}) $ which is zero if the assumption of correct model specification holds. The second term, $ \frac{\partial}{\partial \theta} g(x, \bar{\theta})\left(\hat{\theta}-\theta_{0}\right), $ is due to the sampling error of the estimator $ \hat{\theta}, $ which is unavoidable no matter whether the density estimator $ g(x, \theta) $ is correctly specified. This term converges to zero in probability at the parametric root-$ T $ rate.

**Question**: <u>What happens if the correct model specification assumption fails</u>? That is, what happens if $ g(x, \theta) \neq g(x) $ for all $ \theta $?

When the density model $ g(x, \theta) $ is not correctly specified for the unknown PDF $ g(x) $, the estimator $ g(x, \hat{\theta}) $ will not be consistent for $ g(x) $ because the bias $ g\left(x, \theta^{*}\right)-g(x) $ never vanishes no matter how large the sample size $ T $ is, where $ \theta^{*}=p \lim \hat{\theta} $.

We now introduce a nonparametric estimation method for $ g(x) $ which will not assume any restrictive functional form for $ g(x) $. Instead, it lets data speak for the correct functional form for $ g(x) $.

### 2.1.1 Kernel Density Estimator

**Kernel smoothing** is a kind of local smoothing. The purpose of **nonparametric probability density estimation** is to construct an estimate of a PDF without imposing restrictive functional form assumptions. Typically the only condition imposed on the unknown PDF is that it has **at least first two order bounded derivatives**. 

In this circumstance, we may <u>use only local information about the value of the PDF at any given point in the support</u>. That is, the value of the PDF of a point $ x $ must be calculated from data values that lie in a neighborhood of $ x, $ and to ensure consistency the neighborhood must shrink to zero as the sample size $ T $ increases. In the case of kernel density estimation, the radius of the effective neighborhood is roughly equal to the so-called "bandwidth" of a kernel density estimator, which is essentially a smoothing parameter. Under the assumption that the PDF is univariate with at least first two order bounded derivatives, and using a nonnegative kernel function, the size of bandwidth that optimizes the performance of the estimator in term of the mean squared error (MSE) criterion is proportional to the rate $ T^{-1 / 5}  $. The number of "parameters" needed to model the unknown PDF within a given interval is approximately equal to the number of bandwidths that can be fitted into that interval, and so is roughly of size $ T^{1 / 5} $. Thus, nonparametric density estimation involves the adaptive fitting of approximately $ T^{1 / 5} $ parameters, with this number growing with the sample size $ T $.

Suppose we are interested in estimating the value of the PDF $ g(x) $ at a given point $ x $ in the support of $ X_{t}  $. There are **two basic instruments in kernel estimation**: the kernel function $ K(\cdot) $ and the bandwidth $ h . $ Intuitively, <u>the former gives weighting to the observations in an interval containing the point</u> $ x $, and <u>the latter controls the size of the interval containing observations</u>.

We first introduce an important instrument for local smoothing. This is called a kernel function.

**Definition [Second Order Kernel $ K(\cdot) $]**: A second order or positive kernel function $ K(\cdot) $ is a **pre-specified symmetric PDF** such that

1. non-negative (PDF)
2. $ \int_{-\infty}^{\infty} K(u) d u=1 $
3. $ \int_{-\infty}^{\infty} K(u) u d u=0 $
4. $ \int_{-\infty}^{\infty} u^{2} K(u) d u=C_{K}<\infty $
5. $ \int_{-\infty}^{\infty} K^{2}(u) d u=D_{K}<\infty $

Intuitively, the kernel function $ K(\cdot) $ is a **weighting function** that will "discount" the observations whose values are more away from the point $ x $ of interest.

The kernel functions satisfying the above condition are called a **second order or positive kernel**. It should be emphasized that the kernel $ K(\cdot) $ has nothing to do with the unknown PDF $ g(x) $ of $ \left\{X_{t}\right\} ; $ <u>it is just a weighting function for observations when constructing a kernel density estimator</u>. More generally, we can define a $ q $-th order kernel $ K(\cdot), $ where $ q \geq 2 $.

**Definition [$q$th Order Kernel]**: $ K(\cdot) $ satisfies the conditions that

1. $ \int_{-\infty}^{\infty} K(u) d u=1 $
2. $ \int_{-\infty}^{\infty} u^{j} K(u) d u=0 $ for $ 1 \leq j \leq q-1 $
3. $ \int_{-\infty}^{\infty} u^{q} K(u) d u<\infty $
4. $ \int_{-\infty}^{\infty} K^{2}(u) d u<\infty $

For a higher order kernel (i.e., $ q>2 $ ), $ K(\cdot) $ <u>will take some negative values at some points</u>.

**Question**: Why is a higher order kernel useful? Can you give an example of a third order kernel? And an example of a fourth order kernel?

**Higher order kernels can reduce the bias of a kernel estimator to a higher order**. An example of higher order kernels is given in Robinson (1991).

We now consider **some examples of second order kernels**:

- Uniform kernel

$$
K(u)=\frac{1}{2} 1(|u| \leq 1)
$$

- Gaussian kernel

$$
K(u)=\frac{1}{\sqrt{2 \pi}} \exp \left(-\frac{1}{2} u^{2}\right) ; \quad-\infty<u<\infty
$$

- Epanechnikov Kernel

$$
K(u)=\frac{3}{4}\left(1-u^{2}\right) 1(|u| \leq 1)
$$

- Quartic kernel

$$
K(u)=\frac{15}{16}\left(1-u^{2}\right)^{2} 1(|u| \leq 1)
$$

Among these kernels, the Gaussian kernel has **unbounded support**, while all other kernels have bounded supports of $ [-1,1] . $ Also, the uniform kernel assigns an equal weighting within its support; in contrast, all other kernels have a **downward weighting** scheme.

**Question**: How does the kernel method work?

Let $ x $ be a fixed point in the support of $ X_{t} $. Given a pre-chosen second kernel $ K(u) $, we define a kernel density estimator for $ g(x) $ based on the random sample $ \left\{X_{t}\right\}_{t=1}^{T} $:

$$
\begin{aligned}
\hat{g}(x) &=T^{-1} \sum_{t=1}^{T} K_{h}\left(x-X_{t}\right) \\
&=\frac{1}{T} \sum_{t=1}^{T} \frac{1}{h} K\left(\frac{x-X_{t}}{h}\right) \\
&=\frac{1}{h} \int_{-\infty}^{\infty} K\left(\frac{x-y}{h}\right) d \hat{F}(y)
\end{aligned}
$$

where

$$
K_{h}(u)=\frac{1}{h} K\left(\frac{u}{h}\right)
$$

$ h=h(T)>0 $ is called a **bandwidth** or a window size, and $ \hat{F}(y)=T^{-1} \sum_{t=1}^{T} 1\left(X_{t} \leq y\right) $ is the marginal empirical distribution function of the random sample $ \left\{X_{t}\right\}_{t=1}^{T} $. This is exactly the same as the estimator introduced in Chapter 3, and it was first proposed by Rosenblatt (1956) and Parzen (1962) and so is also called the Rosenblatt-Parzen kernel density estimator.

We see immediately that the well-known histogram is a special case of the kernel density estimator $ \hat{g}(x) $ with the choice of a uniform kernel. 

**Example 1 [Histogram]**: If $ K(u)=\frac{1}{2} 1(|u| \leq 1), $ then
$$
\hat{g}(x)=\frac{1}{2 h T} \sum_{t=1}^{T} 1\left(\left|x-X_{t}\right| \leq h\right)
$$

Intuitively, with the choice of a uniform kernel, the kernel density estimator $ \hat{g}(x) $ is the relative sample frequency of the observations on the interval $ [x-h, x+h] $ which centers at point $ x $ and has **a size of $ 2 h $.** Here, $ 2 h T $ is approximately the sample size of the small interval $ [x-h, x+h], $ when the size $ 2 h $ is small enough. Alternatively, $ T^{-1} \sum_{t=1}^{T} 1\left(\left|x-X_{t}\right| \leq h\right) $ is the relative sample frequency for the observations falling into the small interval $ [x-h, x+h], $ which, by the law of large numbers, is approximately equal to the probability

$$
\begin{aligned}
E\left[1\left(\left|x-X_{t}\right| \leq h\right)\right] &=P\left(x-h \leq X_{t} \leq x+h\right) \\
&=\int_{x-h}^{x+h} g(y) d y \\
& \approx 2 h g(x)
\end{aligned}
$$

if $ h $ is small enough and $ g(x) $ is continuous around the point $ x $. Thus, the histogram is a reasonable estimator for $ g(x), $ and indeed it is a consistent estimator $ g(x) $ if $ h $ vanishes to zero but at a slower rate than sample size $ T $ goes to infinity.

?????????????????????????????????????????????????????????

**Question**: Under what conditions will the density estimator $ \hat{g}(x) $ be consistent for the known density function $ g(x) $?

We impose an assumption on the data generating process and the unknown PDF $ g(x) $.

**Assumption 3.1 [Smoothness of PDF]**: (i) $ \left\{X_{t}\right\} $ is a strictly stationary process with marginal PDF $ g(x) $; (ii) $ g(x) $ has a bounded support on $ [a, b], $ and is continuously twice differentiable on $ [a, b], $ with $ g^{\prime \prime}(\cdot) $ being Lipschitz-continuous in the sense that $ \left|g^{\prime \prime}\left(x_{1}\right)-g^{\prime \prime}\left(x_{2}\right)\right| \leq C\left|x_{1}-x_{2}\right| $ for all $ x_{1}, x_{2} \in[a, b], $ where $ a, b $ and $ C $ are finite constants.

**Question**: How to define the derivatives at the boundary points?

By convention, the derivatives of $ g(\cdot) $ at boundary points $ a $ and $ b $ are

$$
\begin{aligned}
g^{\prime}(a)=\lim _{x \rightarrow 0^{+}} \frac{g(a+x)-g(a)}{x} \\
g^{\prime}(b)=\lim _{x \rightarrow 0^{-}} \frac{g(b+x)-g(b)}{x}
\end{aligned}
$$

Similarly for the second derivatives $ g^{\prime \prime}(a) $ and $ g^{\prime \prime}(b) $ at the boundary points of the support $ [a, b] $.

For convenience, we further impose an additional condition on kernel $ K(\cdot), $ which will actually be maintained throughout this chapter.

**Assumption 3.2 [Second Order Kernel with Bounded Support]**: $ K(u) $ is a positive kernel function with a bounded support on [-1,1].

**This bounded support assumption is not necessary**, but it simplifies the asymptotic analysis and interpretation.

### 2.1.2 Asymptotic Bias and Boundary Effect

Our purpose is to show that $ \hat{g}(x) $ is a consistent estimator for $ g(x) $ for a given point $ x $ in the support. Now we decompose

$$
\hat{g}(x)-g(x)=[E \hat{g}(x)-g(x)]+[\hat{g}(x)-E \hat{g}(x)]
$$

It follows that the mean squared error of the kernel density estimator $ \hat{g}(x) $ is given by

$$
\begin{aligned}
\operatorname{MSE}(\hat{g}(x)) &=[E \hat{g}(x)-g(x)]^{2}+E[\hat{g}(x)-E \hat{g}(x)]^{2} \\
&=\operatorname{Bias}^{2}[\hat{g}(x)]+\operatorname{var}[\hat{g}(x)]
\end{aligned}
$$

The first term is the squared bias of the estimator $ \hat{g}(x), $ which is nonstochastic, and the second term is the variance of $ \hat{g}(x) $ at the point $ x $. We shall show that under suitable regularity conditions, both the bias and the variance of $ \hat{g}(x) $ vanish to zero as the sample size $ T $ goes to infinity.

We **first consider the bias**. For any given point $ x $ in the interior region $ [a+h, b-h] $ of the support $ [a, b] $ of $ X_{t}, $ we have

$$
\begin{aligned}
E[\hat{g}(x)]-g(x) =&\frac{1}{T} \sum_{t=1}^{T} E K_{h}\left(x-X_{t}\right)-g(x) \\
=&E\left[K_{h}\left(x-X_{t}\right)\right]-g(x)\text { (by identical distribution)} \\
=&\int_{a}^{b} \frac{1}{h} K\left(\frac{x-y}{h}\right) g(y) d y-g(x)\\
=&\int_{(a-x) / h}^{(b-x) / h} K(u) g(x+h u) d u-g(x) \text{ (by change of variable  $ \frac{y-x}{h}=u $)}\\
=& \int_{-1}^{1} K(u) g(x+h u) d u-g(x) \\
=& g(x) \int_{-1}^{1} K(u) d u-g(x) \\
&+h g^{\prime}(x) \int_{-1}^{1} u K(u) d u \\
&+\frac{1}{2} h^{2} \int_{-1}^{1} u^{2} K(u) g^{\prime \prime}(x+\lambda h u) d u \text{  (by Taylor expansion)}\\
=& \frac{1}{2} h^{2} C_{K} g^{\prime \prime}(x)+\frac{1}{2} h^{2} \int_{-1}^{1}\left[g^{\prime \prime}(x+\lambda h u)-g^{\prime \prime}(x)\right] u^{2} K(u) d u \\
=& \frac{1}{2} h^{2} C_{K} g^{\prime \prime}(x)+o\left(h^{2}\right)
\end{aligned}
$$

where the second term

$$
\int_{-1}^{1}\left[g^{\prime \prime}(x+\lambda h u)-g^{\prime \prime}(x)\right] u^{2} K(u) d u \rightarrow 0
$$

as $ h \rightarrow 0 $ by Lebesgue's dominated convergence theorem, and the boundedness and continuity of $ g^{\prime \prime}(\cdot) $ and $ \int_{-1}^{1} u^{2} K(u) d u<\infty $.

Therefore, for the point $ x $ in the interior region $ [a+h, b-h], $ the bias of $ \hat{g}(x) $ is proportional to $ h^{2} . $ Thus, we must let $ h \rightarrow 0 $ as $ T \rightarrow \infty $ in order to have the bias vanish to zero as $ T \rightarrow \infty $.

The above result for the bias is obtained under the **identical distribution assumption** on $ \left\{X_{t}\right\} . $ It is irrelevant to whether $ \left\{X_{t}\right\} $ is IID or serially dependent. In other words, **it is robust to serial dependence** in $ \left\{X_{t}\right\} $.

**Question**: What happens to the bias of $ \hat{g}(x) $ if $ x $ is outside the interior region $ [a+h, b-h] $?

We say that $ x $ is outside the interior region $ [a+h, b-h] $ if $ x $ in $ [a, a+h] $ or $ [b-h, b] $ These two regions are called **boundary regions** of the support. Their sizes are equal to $ h $ and so vanish to zero as the sample size $ T $ increases.

Suppose $ x=a+\lambda h \in[a, a+h) $, where $ \lambda \in[0,1) $. We shall call $ x $ is a point in the left boundary region of the support $ [a, b] $. Then

$$
\begin{aligned}
E[\hat{g}(x)]-g(x) &=E\left[K_{h}\left(x-X_{t}\right)\right]-g(x) \\
&=\frac{1}{h} \int_{a}^{b} K\left(\frac{x-y}{h}\right) g(y) d y-g(x) \\
&=\int_{(a-x) / h}^{(b-x) / h} K(u) g(x+h u) d u-g(x) \\
&=\int_{-\lambda}^{1} K(u) g(x+h u) d u-g(x) \\
&=g(x) \int_{-\lambda}^{1} K(u) d u-g(x) \\
&+h \int_{-\lambda}^{1} u K(u) g^{\prime}(x+\tau h u) d u \\
&=g(x)\left[\int_{-\lambda}^{1} K(u) d x-1\right]+O(h) \\
&=O(1)
\end{aligned}
$$

if $ g(x) $ is bounded away from zero, that is, if $ g(x) \geq \epsilon>0 $ for all $ x \in[a, b] $ for any small but fixed constant $ \epsilon $. Note that the $ O(1) $ term arises since $ \int_{-\lambda}^{1} K(u) d x=1 $ for any $ \lambda<1 $.

Thus, if $ x \in[a, a+h) $ or $ (b-h, b], $ the bias $ E[\hat{g}(x)]-g(x) $ may never vanish to zero even if $ h \rightarrow 0 . $ This is due to the fact that there is no symmetric coverage of observations in the boundary region $ [a, a+h) $ or $ (b-h, b] $. This phenomenon is called the **boundary effect or boundary problem** of kernel estimation.

There have been several **solutions** proposed in the smoothed nonparametric literature. These include the following methods.

- **Trimming Observations**: 

    Do not use the estimate $ \hat{g}(x) $ when $ x $ is in the boundary regions. That is, only estimate and use the densities for points in the interior region $ [a+h, b-h] $.

    This approach has a drawback. Namely, valuable information may be lost because $ \hat{g}(x) $ in the boundary regions contain the information on the tail distribution of $ \left\{X_{t}\right\}, $ which is particularly important to financial economists (e.g., extreme down side market risk ) and welfare economics (e.g., the low-income population).

- **Using a Boundary Kernel**:

    To modify the kernel $ K\left[\left(x-X_{t}\right) / h\right] $ when (and only when) $ x $ is the boundary regions such that it becomes location-dependent in the boundary region. For example, Hong and Li (2005) use a simple kernel-based density estimator

$$
\hat{g}(x)=\frac{1}{T} \sum_{t=1}^{T} K_{h}\left(x, X_{t}\right)
$$

???		where

$$
K_{h}(x, y) \equiv\left\{\begin{array}{ll}
h^{-1} K\left(\frac{x-y}{h}\right) / \int_{-(x / h)}^{1} K(u) d u, & \text { if } x \in[0, h) \\
h^{-1} K\left(\frac{x-y}{h}\right), & \text { if } x \in[h, 1-h] \\
h^{-1} K\left(\frac{x-y}{h}\right) / \int_{-1}^{(1-x) / h} K(u) d u, & \text { if } x \in(1-h, 1]
\end{array}\right.
$$

and $ K(\cdot) $ is a standard second order kernel. The idea is to modify the kernel function in the boundary regions so that the integral of the kernel function is unity. **Then the bias is $ O\left(h^{2}\right) $ for all $ x \in[a+h, b-h] $ in the interior region and is at most $ O(h) $ for $ x \in[a, a+h) $ and $ (b-h, b] $ in the boundary regions.** The advantage of this method is that it is very simple and always gives positive density estimates. The drawback is that the bias at the boundary region can be as slow as $ O(h), $ which is slower than $ O\left(h^{2}\right) $ in the interior region.

- **Using a Jackknife Kernel**: For $ x $ in the interior region $ [a+h, b-h] $, use the standard positive kernel $ K(\cdot) . $ For $ x $ in the boundary regions $ [a, a+h) $ and $ (b-h, b] $, use the following jackknife kernel

$$
K_{\xi}(u) \equiv(1+r) \frac{K(u)}{\omega_{K}(0, \xi)}-(r / \alpha) \frac{K(u / \alpha)}{\omega_{K}(0, \xi / \alpha)}
$$

where $ \omega_{K}(l, \xi) \equiv \int_{-\xi}^{1} u^{l} K(u) d u $ for $ l=0,1, r \equiv r(\xi) $ and $ \alpha \equiv \alpha(\xi) $ depend on parameter $ \xi \in[0,1] . $ When $ x \in[a, a+h), $ we have $ \xi=(x-a) / h ; $ when $ x \in(b-h, b], $ we have $ \xi=(b-x) / h . $ In both cases, we set

$$
r \equiv \frac{\omega_{K}(1, \xi) / \omega_{K}(0, \xi)}{\alpha \omega_{K}(1, \xi / \alpha) / \omega_{K}(0, \xi / \alpha)-\omega_{K}(1, b) / \omega_{K}(0, \xi)}
$$

As suggested in Rice (1986), we set $ \alpha=2-\xi . $ Given $ \xi \in[0,1], $ the support of $ K_{\xi}(\cdot) $ is $ [-\alpha, \alpha] . $ Consequently, for any $ \xi \in[0,1] $

$$
\begin{aligned}
\int_{-\alpha}^{\alpha \xi} K_{\xi}(u) d u &=\int_{-\alpha \xi}^{\alpha} K_{\xi}(u) d u=1 \\
\int_{-\alpha}^{\alpha \xi} u K_{\xi}(u) d u &=-\int_{-\alpha \xi}^{\alpha} K_{\xi}(u) d u=0 \\
\int_{-\alpha}^{\alpha b} u^{2} K_{\xi}(u) d u &=\int_{-\alpha b}^{\alpha} u^{2} K_{\xi}(u) d u>0 \\
\int_{-\alpha}^{\alpha b} K_{\xi}^{2}(u) d u &=\int_{-\alpha b}^{\alpha} K_{\xi}^{2}(u) d u>0
\end{aligned}
$$

**The bias is $ O\left(h^{2}\right) $ for all points $ x \in[a, b], $ including those in the boundary regions.** We note that the jackknife kernel formula in H??rdle (1990, Section 4.4) is incorrect.

- Data Reflection:

    The reflection method is to construct the kernel density estimate based on an augmented data which combined both the "reflected" data $ \left\{ X_{t}\right\}_{t=1}^{T} $ and the original data $ \left\{X_{t}\right\}_{t=1}^{T} $ with support on $ [0,1] . $ Suppose $ x $ is a boundary point in $ [0, h) $ and $ x \geq 0 . $ Then the reflection method gives an estimator

$$
\hat{g}(x)=\frac{1}{T} \sum_{t=1}^{T} K_{h}\left(x-X_{t}\right)+\frac{1}{T} \sum_{t=1}^{T} K_{h}\left[x-\left(-X_{t}\right)\right]
$$

Note that with the support [-1,1] of kernel $ K(\cdot), $ when $ x $ is away from the boundary, the second term will be zero. Hence, this method only corrects the density estimate in the boundary region. See Schuster (1985, Communications in Statistics: Theory and Methods and Hall and Wehrly (1991, Journal of American Statistical Association ). This method has been extended by Chen and Hong (2012) and Hong, Sun and Wang (2018) to estimate time-varying functions (i.e., deterministic functions of time)

**Question**: What is the general formula for the kernel density estimator when the support of $ X_{t} $ is $ [a, b] $ rather than [0,1]?

Suppose $ x $ is a boundary point in $ [a, a+h) $. Then the density estimator becomes

$$
\hat{g}(x)=\frac{1}{T} \sum_{t=1}^{T} K_{h}\left(x-X_{t}\right)+\frac{1}{T} \sum_{t=1}^{T} K_{h}\left[x-\left(-\left(X_{t}-a\right)\right)\right]
$$

- **Transformation**:

    Put $ Y_{t}=q\left(X_{t}\right), $ where $ q(\cdot) $ is a monotonic increasing function whose values range from $ -\infty $ to $ \infty . $ Then

$$
\hat{g}_{X}(x)=q^{\prime}(x) \hat{g}_{Y}[q(x)]
$$

where $ \hat{g}_{Y}(\cdot) $ is the kernel density estimator for $ Y_{t} $ based on the transformed sample $ \left\{Y_{t}\right\}_{t=1}^{T}, $ which has **infinite support**.

**Question**: Is there any free lunch with the use of the transformation method?

- **Local Polynomial Fitting**

    Local polynomial automatically adapts to the boundary regions and the bias in the boundary region is the same in order of magnitude as the bias in the interior region. This will be discussed later.

### 2.1.3 Asymptotic Variance

**Question**: We have dealt with the bias of $ \hat{g}(x) $. Then, what is the variance of $ \hat{g}(x) $?

For the time being, in order to simplify the analysis, we assume an IID random sample. We will explain that the asymptotic result for the variance of $ \hat{g}(x) $ remains true when $ \left\{X_{t}\right\} $ is not IID under certain regularity restrictions on temporal dependence in $ \left\{X_{t}\right\} $.

**Assumption A.3 [IID Observations]**: The random sample $ \left\{X_{t}\right\}_{t=1}^{T} $ is IID.

The IID assumption simplifies our calculating the asymptotic variance of $ \hat{g}(x) $. Later, we can relax the independence assumption for $ \left\{X_{t}\right\} $ such that $ \left\{X_{t}\right\} $ is an $ \alpha $-mixing process, a condition that allows weak temporal dependence (see Chapter 2). This will not change the asymptotic variance result for $ \hat{g}(x) $.

Given any point $ x $ in the support $ [a, b], $ put

$$
Z_{t} \equiv Z_{t}(x)=K_{h}\left(x-X_{t}\right)-E\left[K_{h}\left(x-X_{t}\right)\right]
$$

Then $ \left\{Z_{t}\right\}_{t=1}^{T} $ is $ \mathrm{IID} $ with mean zero. It follows that the variance of $ \hat{g}(x) $,

$$
\begin{aligned}
E[\hat{g}(x)-E \hat{g}(x)]^{2} &=E\left(T^{-1} \sum_{t=1}^{T} Z_{t}\right)^{2} \\
&=\frac{1}{T^{2}} \sum_{t=1}^{T} \operatorname{var}\left(Z_{t}\right) \\
&=\frac{1}{T} \operatorname{var}\left(Z_{t}\right) \\
&=\frac{1}{T}\left[E\left[K_{h}^{2}\left(x-X_{t}\right)\right]-\left[E K_{h}\left(x-X_{t}\right)\right]^{2}\right] \\
&=\frac{1}{T h^{2}} \int_{a}^{b} K^{2}\left(\frac{x-y}{h}\right) g(y) d y \\
&\quad -\frac{1}{T}\left[\frac{1}{h} \int_{a}^{b} K\left(\frac{x-y}{h}\right) g(y) d y\right]^{2} \\
&=\frac{1}{T h} g(x) \int_{-1}^{1} K^{2}(u) d u[1+o(1)]+O\left(T^{-1}\right) \\
&=\frac{1}{T h} g(x) D_{k}+o\left(T^{-1} h^{-1}\right)
\end{aligned}
$$

where the last second equality follows by change of variable $ \frac{x-y}{h}=u $ and Taylor expansion.

The variance of $ \hat{g}(x) $ is proportional to $ (T h)^{-1}, $ which is the approximate sample size for the observations which fall into the interval $ [x-h, x+h]$.

Next, we discuss the impact of serial dependence in $ \left\{X_{t}\right\} $ on the asymptotic variance of $ \hat{g}(x) $

**Question**: What happens to the variance of $ \hat{g}(x) $ if $ \left\{X_{t}\right\} $ is **serially dependent**.

**Intuition** (strictly proof below can be skipped): Hart (1996) provides a nice intuition for this result. Suppose the kernel $ K(\cdot) $ has support on $ [-1,1], $ as assumed in this chapter. Then the kernel density estimator at the point $ x $ uses only the local data points inside the local interval $ [x-h, x+h] $. **The observations whose values fall into this local interval are generally far away from each other in time**. Thus, although the data $ \left\{X_{t}\right\}_{t=1}^{T} $ in the original sequence may be highly correlated, the dependence for the new subsequence in the local interval around $ x $ can be much weaker. As a result, the local data look like those from an independent sample. Hence, one would expect that the asymptotic variance of the kernel density estimator is the same as that for the independent observations when certain mixing conditions are imposed.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200625171127.png)

Suppose $ \left\{X_{t}\right\} $ is a strictly stationary $ \alpha $-mixing process. Then under suitable conditions on the $ \alpha $-mixing coefficient $ \alpha(j), $ for example, $ \alpha(j) \leq C j^{-\beta} $ for $ \beta>\frac{5}{2}, $ we have the same MSE formula for $ \hat{g}(x) $ as we have when $ \left\{X_{t}\right\} $ is $ \mathrm{IID} $. This is formally established in Robinson $ (1983) . $ See Robinson $ (1983, $ Journal of Time Series Analysis) for details. Intuitively, when a bounded support kernel $ K(u) $ is used, the kernel density estimator is an weighted average of nonlinear functions of observations $ \left\{X_{t}\right\}_{t=1}^{T} $ which fall into the small interval $ [x-h, x+h] . $ The observations that fall into the small interval are determined by the closeness of their values to the value of $ x, $ not by closeness in time. Suppose we re-lable the observations falling into the small interval by a subsequence or subsample $ \left\{\tilde{X}_{t^{*}}\right\}_{t^{r}=1}^{T^{*}} . $ Then the size of the subsample $ T^{*} $ is of the order of $ T h, $ and the time index $ t^{*} $ are not consercative time periods but rather far away from each other in time. This implies that the observations in the subsequence behave like an IID sequence when serial dependence in the original time series $ \left\{X_{t}\right\} $ is not too strong.

We now formally examine the impact of serial dependence of $ \left\{X_{t}\right\} $ on the asymptotic variance of the kernel density estimator $ \hat{g}(x) $. For this aim, we first introduce the strong mixing condition which is called $ \alpha $ -mixing.

**Definition [a-mixing]**: Let $ \left\{X_{t}\right\} $ be a strictly stationary time series process. For $j=1,2, \ldots, \text { define } $
$$
\alpha(j)=\sup _{A \in \mathcal{F}_{-\infty}^{0}, B \in \mathcal{F}^{\infty}_{j}}|P(A \cap B)-P(A) P(B)|
$$

where $ \mathcal{F}_{i}^{j} $ denotes the $ \sigma $-algebra generated by $ \left\{X_{t}, i \leq t \leq j\right\} . $ **Then the process $ \left\{X_{t}\right\} $ is said to be $ \alpha $-mixing if $ \alpha(j) \rightarrow 0 $ as $ j \rightarrow \infty $.**

Similar to ergodicity, the $ \alpha $-mixing condition is a concept for asymptotic independence. A mixing process can be viewed as a sequence of random variables for which the past and distant future are asymptotically independent. The $ \alpha $-mixing condition implies ergodicity. See White (Asymptotic Theory for Econometricians, 2001). In fact, there are several concepts of mixing, such as $ \alpha $-mixing, $ \beta $-mixing, and $ \phi $-mixing. Among them, $ \alpha $-mixing is the weakest condition on serial dependence; it is also called strong mixing.

If $ \left\{X_{t}\right\} $ is a strictly stationary Markov chain, the mixing coefficient $ \alpha(j) $ can be effectively defined with $ \left(\mathcal{F}_{-\infty}^{0}, \mathcal{F}_{j}^{\infty}\right) $ replaced by $ \left(\sigma\left(X_{0}\right), \sigma\left(X_{n}\right)\right), $ and in this case,

$$
\alpha(j) \leq \frac{1}{2} \iint\left|f_{j}(x, y)-g(x) g(y)\right| d x d y
$$

where $ f_{j}(x, y) $ is the joint PDF of $ \left(X_{t}, X_{t-j}\right) $.

We first state a useful lemma.

**Lemma [Doukhan (1994)]**: Let $ X $ and $ Y $ be two real random variables. Define

$$
\alpha=\sup _{A \in \sigma(X), B \in \sigma(Y)}|P(A \cap B)-P(A) P(B)|
$$

(1) Suppose $ E\left(|X|^{p}+|X|^{q}\right)<\infty $ for some $ p, q \geq 1 $, and $ 1 / p+1 / q<1 $. Then

$$
|\operatorname{cov}(X, Y)| \leq 8 \alpha^{1 / r}\left(E|X|^{p}\right)^{1 / p}\left(E|X|^{q}\right)^{1 / q}
$$

where $ r=(1-1 / p-1 / q)^{-1} $.

(2) If $ P\left(|X| \leq C_{1}\right)=1 $ and $ P\left(|Y| \leq C_{2}\right)=1 $ for some constants $ C_{1} $ and $ C_{2}, $ then

$$
|\operatorname{cov}(X, Y)| \leq 4 \alpha C_{1} C_{2}
$$

**Theorem [Asymptotic Variance of $ \hat{g}(x) $ under Mixing Conditions]**: Let $ \left\{X_{t}\right\} $ be a strictly stationary $ \alpha $-mixing process with the mixing coefficient $ \alpha(j) \leq C_{j}^{-\beta} $ for some $ C>0 $ and $ \beta>2 . $ Assume that the pairwise joint density function $ f_{j}(x, y) $ is bounded uniformly in $ (x, y) $ and in lag order $ j . $ Then for $ x \in[a, b], $ where $ a, b $ are finite constants,
$$
\operatorname{var}[\hat{g}(x)]=\frac{1}{T h} g(x) D_{K}+o\left(T^{-1} h^{-1}\right)
$$

**Proof**: Put

$$
Z_{t}=K_{h}\left(x, X_{t}\right)=\frac{1}{h} K\left(\frac{x-X_{t}}{h}\right)
$$

Then by strict stationarity of $ \left\{X_{t}\right\}, $ we have

$$
\begin{aligned}
\operatorname{var}[\hat{g}(x)] &=\operatorname{var}\left(T^{-1} \sum_{t=1}^{T} Z_{t}\right) \\
&=\frac{1}{T} \operatorname{var}\left(Z_{1}\right)+2 \frac{1}{T} \sum_{j=1}^{T-1}(1-j / T) \operatorname{cov}\left(Z_{0}, Z_{j}\right)
\end{aligned}
$$

Note that $ E\left(Z_{1}\right)=E[\hat{g}(x)]=O(1) . $ By change of variable, we have

$$
\begin{aligned}
\operatorname{var}\left(Z_{1}\right) &=E\left[K_{h}^{2}\left(x, X_{1}\right)\right]-\left(E Z_{1}\right)^{2} \\
&=\frac{1}{h} g(x) D_{K}+O(1)
\end{aligned}
$$

where the first term dominates the second term in terms of order of magnitude. Thus, it remains to show

$$
\frac{1}{T} \sum_{j=1}^{T-1} \operatorname{cov}\left(Z_{0}, Z_{j}\right)=o\left(h^{-1}\right)
$$

Because $ \left|Z_{0}\right| \leq C h^{-1}, $ we have

$$
\left|\operatorname{cov}\left(Z_{0}, Z_{j}\right)\right| \leq 4\left(C h^{-1}\right)^{2} \alpha(j)
$$

by Billingsley's inequality. It follows that

$$
\sum_{j=m(T)+1}^{T-1}\left|\operatorname{cov}\left(Z_{0}, Z_{j}\right)\right| \leq 4 C^{2} h^{-2} \sum_{j=m(T)+1}^{T-1} j^{-\beta} \leq C^{3} m(T)^{1-\beta} h^{-2}
$$

where $ m(T) \rightarrow \infty $ as $ T \rightarrow \infty $.

On the other hand,

$$
\begin{aligned}
\left|\operatorname{cov}\left(Z_{0}, Z_{j}\right)\right| &=\left|E\left(Z_{0} Z_{j}\right)-E\left(Z_{0}\right) E\left(Z_{j}\right)\right| \\
& \leq \int K_{h}\left(x, x^{\prime}\right) K_{h}\left(y, y^{\prime}\right) f_{j}\left(x^{\prime}, y^{\prime}\right) d x^{\prime} d y^{\prime}+\left[E\left(Z_{0}\right)\right]^{2} \\
& \leq C\left[\int_{-\infty}^{\infty} K_{h}\left(x, x^{\prime}\right) d x^{\prime}\right]^{2}+\left[E\left(Z_{0}\right)\right]^{2} \\
& \leq C^{2}
\end{aligned}
$$

Hence, we have

$$
\sum_{j=1}^{m(T)}\left|\operatorname{cov}\left(Z_{0}, Z_{j}\right)\right| \leq C m(T)
$$

By setting $ m(T)=h^{-2 / \beta}, $ we have

$$
\sum_{j=1}^{T-1}\left|\operatorname{cov}\left(Z_{0}, Z_{j}\right)\right|=O\left(h^{-2 / \beta}\right)=o\left(h^{-1}\right)
$$

for $ \beta>2 $. This completes the proof.

The asymptotic variance of $ \hat{g}(x) $ is exactly the same as that under the IID assumption on $ \left\{X_{t}\right\} . $ This is a bit surprising, but it is true. It follows because when $ \left\{X_{t}\right\} $ is not IID, the variance of $ \hat{g}(x) $ can be decomposed as the sum of individual variances $ \left\{\operatorname{var}\left[K_{h}\left(x, X_{t}\right)\right]\right\}_{t=1}^{T} $ and the sum of all possible covariance terms $ \left\{\operatorname{cov}\left[K_{h}\left(x, X_{t}\right), K_{h}\left(x, X_{s}\right)\right]\right\}_{t \neq 0} $ together. Given the strong-mixing condition, the sum of all possible covariance terms $ \left\{\operatorname{cov}\left[K_{h}\left(x, X_{t}\right), K_{h}\left(x, X_{s}\right)\right]\right\}_{t \neq 0} $ together is of smaller order in magnitude than the sum of all individual variances $ \left\{\operatorname{var}\left[K_{h}\left(x, X_{t}\right)\right]\right\}_{t=1}^{T}, $ due to the smoothing parameter $ h $.

**References**: Kernel estimation in time series: Robinson (1983, Journal of Time Series Analysis), Fan and Yao (2003, Nonlinear Time series).

### 2.1.4 MSE and Optimal Bandwidth

It follows that the mean squared error (MSE) of $ \hat{g}(x) $ is given by

$$
\begin{aligned}
\operatorname{MSE}[\hat{g}(x)] &=E[\hat{g}(x)-g(x)]^{2} \\
&=\operatorname{var}[\hat{g}(x)]+\operatorname{Bias}^{2}[\hat{g}(x), g(x)] \\
&=\frac{1}{T h} g(x) D_{K}+\frac{1}{4} h^{4}\left[g^{\prime \prime}(x)\right]^{2} C_{K}^{2}+o\left(T^{-1} h^{-1}+h^{4}\right) \\
&=O\left(T^{-1} h^{-1}+h^{4}\right)
\end{aligned}
$$

By Chebyshev's inequality, for any given point $ x $ in the interior region $ [a+h, b-h], $ we have

$$
\hat{g}(x)-g(x)=O_{P}\left(T^{-1 / 2} h^{-1 / 2}+h^{2}\right)
$$

**Therefore, for $ \hat{g}(x) \stackrel{p}{\rightarrow} g(x), $ we need $ T h \rightarrow \infty, h \rightarrow 0 $ as $ T \rightarrow \infty $.** Under the stated assumptions, the estimator $ \hat{g}(x) $ is always consistent for the unknown density $ g(x) $ but at a slower rate than the parametric $ T^{-1 / 2} $. This means that a large sample is needed to obtain a reasonable estimate for $ g(x) $.

Moreover, the bias of $ \hat{g}(x) $ depends on the smoothness of the unknown function $ g(\cdot) $ In particular, **if the second derivative $ g^{\prime \prime}(x) $ has a relatively sharp spike at the point $ x $ it is difficult to obtain a good estimate $ g(\cdot) $ at the point $ x $.**

We can also obtain a r

elative MSE criterion when $ g(x)>0 $
$$
\begin{aligned}
\operatorname{MSE}[\hat{g}(x) / g(x)] &=\frac{M S E[\hat{g}(x)]}{g^{2}(x)} \\
&=E\left[\frac{\hat{g}(x)-g(x)}{g(x)}\right]^{2} \\
&=\frac{1}{T h g(x)} D_{K}+\frac{1}{4} h^{4}\left[\frac{g^{\prime \prime}(x)}{g(x)}\right]^{2} C_{K}^{2} \\
&+o\left(T^{-1} h^{-1}+h^{4}\right) \\
&=O\left(T^{-1} h^{-1}+h^{4}\right)
\end{aligned}
$$

The expression of the relative MSE indicates that **it is very difficult to obtain a reasonable estimate of $ g(x) $ in the sparse area where relatively few observations are available (i.e., when $ g(x) $ is small)**, or in the area where $ g(\cdot) $ changes dramatically (i.e., when the curvature $ g^{\prime \prime}(x) / g(x) $ is large in absolute value).

As can be seen from the MSE formula for $ \hat{g}(x), $ a small bandwidth $ h $ will reduce the bias but inflate the variance, and a large bandwidth will increase the bias but reduce the variance. The bandwidth is a smoothing parameter. When the bandwidth $ h $ is so small such that the squared bias is smaller than the variance, we say that there exists **undersmoothing**; when the bandwidth is so large such that its squared bias is larger than the variance, we say that there exists **oversmoothing**. Optimal smoothing is achieved if the bandwidth balances the squared bias and the variance of $ \hat{g}(x) $. We now consider the optimal choice of the bandwidth $ h . $ The **optimal bandwidth** can be obtained by minimizing $ M S E[\hat{g}(x)] $:

$$
h_{0}=\left[\frac{D_{K}}{C_{K}^{2}} \frac{1 / g(x)}{\left[g^{\prime \prime}(x) / g(x)\right]^{2}}\right]^{\frac{1}{5}} T^{-1 / 5}
$$

**The less smooth the PDF $ g(x) $ is or the more sparse the observations are around the point $ x, $ the smaller the optimal bandwidth $ h_{0} $ for any given sample size $ T $.** 

The optimal bandwidth $ h_{0} $ gives the optimal convergence rate for $ \hat{g}(x) $:
$$
\hat{g}(x)-g(x)=O_{P}\left(T^{-2 / 5}\right)
$$

The convergence rate $ T^{-2 / 5} $ is slower than the parametric rate $ T^{-1 / 2} $.

The optimal bandwidth $ h_{0} $ is unknown, because it depends on the unknown density function $ g(x) $ and its second order derivative $ g^{\prime \prime}(x) $.

**Question**: How to obtain a consistent estimator of this optimal bandwidth in practice?

Since we have obtained a closed form expression for the optimal bandwidth $ h_{0}, $ we can obtain a consistent estimator of $ h_{0} $ by plugging in some preliminary consistent estimators for $ g(x) $ and $ g^{\prime \prime}(x) . $ Suppose we have some initial preliminary estimators, say $ \tilde{g}(x) $ and $ \tilde{g}^{\prime \prime}(x), $ for $ g(x) $ and $ g^{\prime \prime}(x) $ respectively. Then we can plug them into the above formula for $ h_{0} $, obtaining an estimator for $ h_{0} . $ With such a data-dependent bandwidth, we obtain a new kernel estimator which has better statistical properties than an arbitrary choice of $ h . $ This is the well-known **plug-in method**. We note that even if $ \tilde{g}(x) $ and $ \tilde{g}^{\prime \prime}(x) $ are not consistent for $ g(x) $ and $ g^{\prime \prime}(x), $ then the second stage kernel density estimator $ \hat{g}(x) $ is still consistent for $ g(x), $ although it is not optimal. However, **consistency of $ \tilde{g}(x) $ and $ \tilde{g}^{\prime \prime}(x) $ for $ g(x) $ and $ g^{\prime \prime}(x) $ respectively ensures that $ \hat{g}(x) $ is an asymptotically optimal estimator for $ g(x) $.**

In addition to the plug-in method to choose a data-driven bandwidth, there exists other data-driven methods to choose an optimal bandwidth. One example is the cross-validation method. For more discussion, see xxx. 

As can be seen from the MSE formula, both the variance and squared bias of $ \hat{g}(x) $ depend on the kernel function $ K $. We now consider the choice of an optimal kernel.

Using the calculus of variation, it can be shown, as in Epanechnikov (1969, Theory of Probability and Its Applications), that the **optimal kernel that minimizes the MSE** of
$ \hat{g}(x) $ over a class of positive kernel functions is the so-called Epanechnikov kernel:
$$
K(u)=\frac{3}{4}\left(1-u^{2}\right) 1(|u|<1)
$$

In practice, it is found that **the choice of $ h $ is more important than the choice of $ K(u) $.** See also Priestley (1962).

## 2.2 Multivariate Density Estimation

We now extend the kernel method to estimate a multivariate density function when $ X_{t} $ is a strictly stationary vector-valued time series process.

**Question**: How to estimate a joint PDF $ f(x) $ of $ X_{t}=\left(X_{1 t}, X_{2 t}, \ldots, X_{d t}\right)^{\prime} $, where $ x=  \left(x_{1}, x_{2}, \ldots, x_{d}\right)^{\prime} $ is a $ d \times 1 $ vector?

**Example 1**: How to estimate the joint $ \operatorname{PDF} f_{j}(x, y) $ of $ \left(X_{t}, X_{t-j}\right) $?

To estimate $ f(x), $ we define a product kernel density estimator

$$
\begin{aligned}
\hat{f}(x) &=\frac{1}{T} \sum_{t=1}^{T} \prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right) \\
&=\frac{1}{T} \sum_{t=1}^{T} \mathcal{K}_{h}\left(x-X_{t}\right)
\end{aligned}
$$

where

$$
\mathcal{K}_{h}\left(x-X_{t}\right)=\prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)
$$

For simplicity, we have used the same bandwidth $ h $ for every coordinate. Different bandwidths could be used for different coordinates. In practice, before using the same bandwidth $ h, $ one can **standardize** all $ \left\{X_{i t}\right\}_{t=1}^{T} $ by dividing by their sample standard deviations respectively for all $ i=1, \ldots, d $.

### 2.2.1 Asymptotic Bias

We first consider the bias of $ \hat{f}(x) $. Suppose $ x $ is an **interior point** $ x $ such that $ x_{i} \in \left[a_{i}+h, b_{i}-h\right] $ for all $ i=1, \ldots, d $. This implies that $ x $ is in a **$ d $-dimensional box** each side of which is $ \left[a_{i}+h, b_{i}-h\right] $ for $ i=1, \ldots, d $. It follows that the bias of $ \hat{f}(x) $,

$$
\begin{aligned}
E[\hat{f}(x)]-f(x) &=E \mathcal{K}_{h}\left(x-X_{t}\right)-f(x) \\
&=E \prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)-f(x) \\
&=\int \cdots \int\left[\prod_{i=1}^{d} \frac{1}{h} K\left(\frac{x_{i}-y_{i}}{h}\right)\right] f(y) d y-f(x) \\
&=\prod_{i=1}^{d} \int_{\left(a_{i}-x_{i}\right) / h}^{\left(b_{i}-x_{i}\right) / h} K\left(u_{i}\right) f(x+h u) d u-f(x) \\
&=\int_{-1}^{1} \cdots \int_{-1}^{1} \prod_{i=1}^{d} K\left(u_{i}\right) f(x+h u) d u-f(x) \\
&=f(x) \prod_{i=1}^{d} \int_{-1}^{1} K\left(u_{i}\right) d u_{i}-f(x) \\
& +h \sum_{i=1}^{d} f_{i}(x)  \int_{-1}^{1} u_i K\left(u_{i}\right) d u_{i} \prod_{j \neq i}^{d} \int_{-1}^{1} K\left(u_{j}\right) d u_{j}\\
&+\frac{1}{2} h^{2} \sum_{i=1}^{d} \sum_{j=1}^{d} \int_{-1}^{1} \int_{-1}^{1} u_{i} u_{j} K\left(u_{i}\right) K\left(u_{j}\right) f_{i j}(x+\lambda u h) d u_{i} d u_{j}  \prod_{k \neq i,j}^{d} \int_{-1}^{1} K\left(u_{k}\right) d u_{k}\\
&=\frac{1}{2} h^{2} C_{K} \sum_{i=1}^{d} f_{i i}(x)+o\left(h^{2}\right) \text{ (by Cross item=0)} \\
&=O\left(h^{2}\right)
\end{aligned}
$$

where $ u=(u_1,u_2,\ldots, u_d), f_{i}(x)=\frac{\partial}{\partial x_{i}} f(x), f_{i j}(x)=\frac{\partial^{2}}{\partial x_{i} \partial x_{j}} f(x), $ and the quantity $ \sum_{i=1}^{d} f_{i i}(x) $ is called the Laplace of the joint PDF $ f(x) $.

And d-dimension Taylor expenion
$$
f(x+hu)=f(x)+\sum_{i=1}^d hu_i\frac{\partial}{\partial x_{i}} f(x) + \frac{1}{2} \sum_{i=1}^d \sum_{j=1}^d h^2 u_i u_j \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} f(x+\lambda hu)
$$
And the fact that
$$
\begin{aligned}
 \iint u^{2} K^{2}(u) d u d u  &=\int \int u^{2} K(x) d u d K^{*}(u) \\
 &=C_{k} \int d K^{*}(u)=C_k
 \end{aligned}
$$
where $ k^*(u)=K(u) $.

### 2.2.2 Asymptotic Variance

Next, put
$$
\begin{aligned}
Z_{t} & \equiv Z_{t}(x) \\
&=\mathcal{K}_{h}\left(x-X_{t}\right)-E \mathcal{K}_{h}\left(x-X_{t}\right) \\
&=\prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)-E \prod_{i=1}^{d} K_{h}\left(x-X_{i t}\right)
\end{aligned}
$$

Then $ \left\{Z_{t}\right\} $ is IID with mean zero given that $ \left\{X_{t}\right\} $ is $ \mathrm{IID} $. It follows that the variance of $ \hat{f}(x) $

$$
\begin{aligned}
E[\hat{f}(x)-E \hat{f}(x)]^{2} &=E\left[T^{-1} \sum_{t=1}^{T}\left[\mathcal{K}_{h}\left(x-X_{t}\right)-E \mathcal{K}_{h}\left(x-X_{t}\right)\right]\right]^{2} \\
&=\frac{1}{T^{2}} \sum_{t=1}^{T} E\left(Z_{t}^{2}\right)(\text { by independence }) \\
&=\frac{1}{T} E\left[\prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)-E \prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)\right]^{2} \\
&=\frac{1}{T}\left[E \prod_{i=1}^{d} K_{h}^{2}\left(x_{i}-X_{i t}\right)-\left[E \prod_{i=1}^{d} K_{h}\left(x_{i}-X_{i t}\right)\right]^{2}\right] \\
&=\frac{1}{T h^{d}} f(x) D_{K}^{d}+o\left(T^{-1} h^{-d}\right)
\end{aligned}
$$

We note that the asymptotic variance of $ \hat{f}(x) $ is proportional to the inverse of $ T h^{d} $ where $ T h^{d} $ is approximately **the effective sample size** for observations falling into a $ d $-dimensional subspace centered at point $ x, $ with each size equal to $ 2 h $. The asymptotic variance of $ \hat{f}(x) $ remains valid under a suitable $ \alpha $-mixing condition for the time series $ \left\{X_{t}\right\} $.

### 2.2.3 MSE and Optimal Bandwidth

It follows that the MSE of $ f(x) $ is
$$
\begin{aligned}
 M S E[\hat{f}(x)] 
=& \frac{1}{T h^{d}} f(x) D_{K}^{d}+\frac{1}{4} C_{K}^{2} h^{4}\left[\sum_{i=1}^{d} f_{i i}(x)\right]^{2} \\
&+o\left(T^{-1} h^{-d}+h^{4}\right) \\
=& O\left(T^{-1} h^{-d}+h^{4}\right)
\end{aligned}
$$

With a suitable choice of bandwidth $ h, $ the optimal MSE convergence rate of $ \hat{f}(x) $ to $ f(x) $ is $ T^{-\frac{4}{4+a}}, $ which can be obtained by setting the bandwidth

$$
h_{0}=\left[\frac{d D_{K}^{2}}{C_{K}^{2}} \frac{1 / f(x)}{\left[\sum_{i=1}^{d} f_{i i}(x) / f(x)\right]^{2}}\right]^{\frac{1}{d+4}} T^{-\frac{1}{d+4}}
$$

#### Curse of dimensionality

Thus, the MSE convergence rate is $ T^{-4/(d+4)}$

- $ \operatorname{MSE}[\hat{f}(x)] \propto T^{-\frac{4}{3}} $ if $ d=1 $
- $ \operatorname{MSE}[\hat{f}(x)] \propto T^{-\frac{2}{3}} $ if $ d=2 $
- $ \operatorname{MSE}[\hat{f}(x)] \propto T^{-\frac{4}{7}} $ if $ d=3 $

The larger dimension $ d $, the slower convergence of $ \hat{f}(x) $. This is the so-called "**curse of dimensionality**" associated with multivariate nonparametric estimation. It implies that a large sample size is needed in order to have a reasonable estimation for $ f(x) $. In particular, the same size $ T $ has to be increased exponentially fast as the dimension $ d $ increases in order to achieve the same level of estimation accuracy and precision.
For most typical sample sizes encountered in economics and finance, it is rare to see nonparametric estimation with dimension $ d>5 $.

**Question**: How to deal with the curse of dimensionality?

There are various methods to deal with the curse of dimensionality. For example,

- **Imposing Multiplicability or Additicability Conditions**

Suppose multiplicability conditions for $ f(x) $ holds such as

$$
f(x)=\prod_{i=1}^{d} g_{i}\left(x_{i}\right)
$$

Then one can estimate $ g_{i}\left(x_{i}\right) $ separately. When $ f(x) $ is a joint density function, multiplicability occurs when and only when $ X_{1 t}, X_{2 t}, \ldots, X_{d t} $ are mutually independent. For functions other than probability densities, an additivity condition can be imposed to reduce the dimension of estimation.

- **Projection Pursuit**

This approach *assumes that a multivariate function is an unknown function of the linear combination of $ d $ explanatory variables*, and then use a nonparametric method to estimate the unknown function and the combination coefficients. A well-known class of models in econometrics is **single-index models** for which a function of $ X_{t} $ is assumed to be an unknown function of a linear combination of the components of $ X_{t}, $ where the combination coefficients are also unknown.

- **Imposing the Markov Condition**

Suppose the time series $ \left\{X_{t}\right\} $ is a Markov process. Namely,

$$
\begin{aligned}
f\left(X_{t} | I_{t-1}\right) &=f\left(X_{t} | X_{t-1}\right) \\
&=\frac{f\left(X_{t}, X_{t-1}\right)}{g\left(X_{t-1}\right)}
\end{aligned}
$$

where $ I_{t-1}=\left(X_{t-1}, X_{t-2}, \ldots\right) $ is the set of infinite dimension. Here, $ f\left(X_{t}, X_{t-1}\right) $ depends on only $ X_{t} $ and $ X_{t-1} $.

## 2.3 Application

Kernel density estimators have been widely used in time series econometrics and financial econometrics. For example,

- Ait-Sahalia (1996, *Review of Financial Studies*) uses the kernel-based marginal density estimator $ \hat{g}(x) $ to test the adequacy of a diffusion model for short-term interest rates, i.e., **to test whether model is correctly specified**.
- Gallant and Tauchen (1996, *Econometric Theory*) use the Hermite polynomial-based estimator for the conditional PDF of $ X_{t} $ given $ I_{t-1} $ to estimate continuous-time models efficiently.
- Hong and Li (2005, *Review of Financial Studies*) use the kernel-based joint density estimator $ \hat{f}_{j}(x, y) $ to test the adequacy of continuous-time models and consider an application to affine term structure models of interest rates.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200708175316.png)

- Hong and White (2005, *Econometrica*) use the kernel-based joint density estimator $ \hat{f}_{j}(x, y) $ to construct a nonparametric entropy-density measure for serial dependence with a well-defined asymptotic distribution.
- Su and White (2008, *Econometric Theory*) propose a Hellinger metric-based test for conditional dependence test which is applicable to **test for general Granger causality by checking whether**

$$
f\left(X_{t} | X_{t-1}, \ldots, X_{t-p}\right)=f\left(X_{t} | X_{t-1}, \ldots, X_{t-p}, Y_{t-1}, \ldots, Y_{t-q}\right)
$$

*where the conditional PDFs are estimated using the kernel method*, and the lag orders $ p $ and $ q $ are given in advance.

Granger causality:

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200708175930.png)

- de Matos and Fernandes (2007, Journal of Econometrics) propose a **test for the Markov property** of a time series process:

$$
f\left(X_{t} | I_{t-1}\right)=f\left(X_{t} | X_{t-1}\right)
$$

They **compare two kernel estimators for the conditional PDFs**,

$$
f\left(X_{t} | X_{t-1}, X_{t-j}\right)=\frac{f\left(X_{t}, X_{t-1}, X_{t-j}\right)}{f\left(X_{t-1}, X_{t-j}\right)}
$$

and

$$
f\left(X_{t} | X_{t-1}\right)=\frac{f\left(X_{t}, X_{t-1}\right)}{f\left(X_{t-1}\right)}
$$

- Wang and Hong (2017, *Econometric Theory*) propose a test for conditional independence which is applicable to test the Markov property and Granger causality in distribution. They **estimate the conditional characteristic function rather than the conditional density function** of $ \left\{X_{t}\right\}, $ thus *avoiding the curse of dimensionality problem* when the dimension $ d $ of $ X_{t} $ is large.

There are other possible approaches to testing the Markov property.

In general, this requires checking whether
$$
f\left(X_{t}=x | I_{t-1}\right)=f\left(X_{t}=x | X_{t-1}\right)
$$

where $ I_{t-1}=\left\{X_{t}, X_{t-1}, \ldots,\right\} . $ A possible approach to testing the Markov property of a time series can be based on the following lemma.

**Lemma [Probability Integral Transforms of Markov Process]**: Suppose $ \left\{X_{t}\right\} $ is a strictly stationary process. Denote the conditional PDF of $ X_{t} $ given $ X_{t-1} $ as

$$
f(x | y)=f\left(X_{t}=x | X_{t-1}=y\right)
$$

Define the probability integral transform

$$
Z_{t}=\int_{-\infty}^{X_{t}} f\left(x | X_{t-1}\right) d x=F_{t}\left(X_{t}\right)
$$

where $ F_{t}(x)=P\left(X_{t} \leq x | X_{t-1}\right) . $ If $ \left\{X_{t}\right\} $ is Markovian, then

$$
\left\{Z_{t}\right\} \sim \text { IID } U[0,1].
$$
