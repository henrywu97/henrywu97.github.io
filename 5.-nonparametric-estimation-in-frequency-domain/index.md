# 

5 Nonparametric Estimation in Frequency Domain

Questions: Given a time series random sample $ \left\{X_{t}\right\}_{t=1}^{\text {of }} $ size $ T $,
How to estimate the power spectral density $ h(\omega) $ of $ \left\{X_{t}\right\} ? $
How to estimate the bispectral density $ b\left(\omega_{1}, \omega_{2}\right) $ of $ \left\{X_{t}\right\} ? ? ? ? ? ? $
How to estimate the generalized spectral density $ f(\omega, u, v) $ of $ \left\{X_{t}\right\} ? $

5.1 Sample Periodogram
Suppose $ \left\{X_{t}\right\} $ is a weakly stationary time series with autocovariance function $ \gamma(j) $ and $ d $ it. Then we can estimate $ \gamma(j) $ the sample autocovariance function

$$
\hat{\gamma}(j)=T^{-1} \sum_{t=j+1}^{T} X_{t} X_{t-j j}, \quad j=0,\pm 1, \ldots, \pm(T-1)
$$

If $ \mu $ is unknown, we should use the sample autooovariance function

$$
\hat{\gamma}(j)=T^{-1} \sum_{t=j j+1}^{t}\left(X_{t}-\bar{X}\right)\left(X_{t-j j}-\bar{X}\right)
$$

where $ \bar{X} $ is the sample mean. The asymptotic analysis is a bit more tedious but the same results can be obtained since the replacement of $ \mu $ by $ \bar{X} $ has no impact on the $ e e $ asymptotic results below.

In this section, our interest is in consistent estimation of the spectral density function
$ h(\omega) $ based on an observed random sample $ \left\{X_{t}\right\}_{t 1}^{1} $. Recall the spectral density function

$$
h(\omega)=\frac{1}{2 \pi} \sum_{j=-\infty}^{\infty} \gamma(j) e^{-i j \omega}
$$

For a $ \mathrm{WN}\left(0, \sigma^{2}\right) $ process, the spectral density

$$
h(\omega)=\frac{1}{2 \pi} \gamma(0), \quad \omega \in[-\pi, \pi]
$$

where $ \gamma(0)=\operatorname{var}\left(X_{t}\right) . $ In this case, a spectral density estimator is

$$
\hat{h}(\omega)=\frac{1}{2 \pi} \hat{\gamma}(0)
$$

For an MA(1) process, the spectral density

$$
h(\omega)=\frac{1}{2 \pi} \gamma(0)+\frac{1}{\pi} \gamma(1) \cos (\omega)
$$

The corresponding spectral estimator is

$$
\hat{h}(\omega)=\frac{1}{2 \pi} \hat{\gamma}(0)+\frac{1}{\pi} \hat{\gamma}(1) \cos (\omega)
$$

For an ARMA $ (p, q) $ process, the spectral density function

$$
h(\omega)=\frac{\sigma^{2}}{2 \pi}\left|\frac{1+\sum_{j=1}^{q} \theta_{j} e^{-i j \omega}}{1-\sum_{j=1}^{p} \phi_{j} e^{-i j \omega}}\right|^{2}
$$

where $ \sigma^{2}=E\left(\varepsilon_{t}^{2}\right) $ is the variance of innovation $ \varepsilon_{t} $
A spectral density estimator is
$$
\hat{h}(\omega)=\frac{\hat{\sigma}^{2}}{2 \pi}\left|\frac{1+\sum_{j=1}^{q} \hat{\theta}_{j} e^{-i j \omega}}{1-\sum_{j=1}^{p} \hat{\phi}_{j} e^{-i j \omega}}\right|^{2}
$$
where $ \left(\hat{\theta}_{j}, \hat{\phi}_{j}\right) $ are consistent parameter estimators, and
$$
\hat{\sigma}^{2}=\frac{1}{T} \sum_{t=\max (p, q)+1}^{T} \hat{\varepsilon}_{t}^{2}
$$
where
$$
\hat{\varepsilon}_{t}=X_{t}-\sum_{j=1}^{p} \hat{\phi}_{j} X_{t-j}-\sum_{j=1}^{q} \hat{\theta}_{j} \hat{\varepsilon}_{t-j}
$$
with the initial values $ \hat{\varepsilon}_{t}=0 $ for all $ t \leq 0 $.
For a general linear process (or when we do not know what process $ X_{t} $ is), we may
like to use the sample periodogram as a spectral density estimator:
$$
\begin{aligned}
\hat{I}(\omega) &=\left.\frac{1}{2 \pi T} \sum_{t=1}^{T} X_{t} e^{i t \omega}\right|^{2} \\
&=\frac{1}{2 \pi} \sum_{j=1-T}^{T-1}\left(1-\frac{|j|}{T}\right) \hat{\gamma}(j) e^{-i j \omega} \\
&=\frac{1}{2 \pi} \hat{\gamma}(0)+\frac{1}{\pi} \sum_{j=1}^{T-1}\left(1-\frac{j}{T}\right) \hat{\gamma}(j) \cos (j \omega)
\end{aligned}
$$

The sample periodogram $ \hat{I}(\omega), $ based on the time series random sample $ \left\{X_{t}\right\}_{t=1}^{T}, $ is
the squared modulus of the discrete Fourier transform of $ \left\{X_{t}\right\}_{t=1}^{T} $.

Unfortunately, this sample periodogram $ \hat{I}(\omega) $ is not consistent for the spectral density
$ h(\omega) . $ Why?
To explain, let us consider the simplest case when $ \left\{X_{t}\right\} $ is IID. Then we have $ h(\omega)= $
$$
\begin{array}{l}
\frac{1}{2 \pi} \gamma(0), \text { and } \\
\qquad E \hat{I}(\omega)=\frac{1}{2 \pi} \gamma(0)=h(\omega)
\end{array}
$$
so the bias $ E[\hat{I}(\omega)]-h(\omega)=0 $ for all $ \omega \in[-\pi, \pi] $
On the other hand, under the IID condition, we have
$$
\operatorname{cov}[\sqrt{T} \hat{\gamma}(i), \sqrt{T} \hat{\gamma}(j)]=\left\{\begin{array}{cl}
(1-|i| / T) \gamma^{2}(0) & \text { if } i=j \\
0 & \text { if } i \neq j
\end{array}\right.
$$
It follows that
$$
\begin{aligned}
\operatorname{var}[\hat{I}(\omega)]=& \frac{1}{(2 \pi)^{2}} \operatorname{var}[\hat{\gamma}(0)] \\
&+\frac{1}{(\pi)^{2}} \sum_{j=1}^{T-1}\left(1-\frac{j}{T}\right)^{2} \operatorname{var}[\hat{\gamma}(j)] \cos ^{2}(j \omega) \\
&=C_{0} \frac{1}{T}+C_{1} \frac{1}{T} \sum_{j=1}^{T-1}\left(1-\frac{j}{T}\right)^{2} \cos ^{2}(j \omega) \\
& \leq C_{0} \frac{1}{T}+C_{1} \cdot \frac{1}{2} \\
&=O(1)
\end{aligned}
$$
The variance $ \operatorname{var}[\hat{I}(\omega)] $ never decays to 0 as $ T \rightarrow \infty, $ and so $ \hat{I}(\omega) $ is not consistent for
$ h(\omega) $
Why? There are too many estimated coefficients $ \{\hat{\gamma}(j)\}_{j=0}^{T-1} ! $ There is a total of $ T $
estimated coefficients, where $ T $ is the sample size.

We now offer an alternative explanation why the sample periodogram $ \hat{I}(\omega) $ is not

consistent for $ h(\omega) . $ Consider the Integrated MSE (IMSE) of $ \hat{I}(\omega), $
$$
\begin{aligned}
& \operatorname{IMSE}(\hat{I}) \\
=& E \int_{-\pi}^{\pi}|\hat{I}(\omega)-h(\omega)|^{2} d \omega \\
=& E \int_{-\pi}^{\pi}|\hat{I}(\omega)-E \hat{I}(\omega)|^{2} d \omega \\
&+\int_{-\pi}^{\pi}|E \hat{I}(\omega)-h(\omega)|^{2} d \omega \\
=& E\left[\frac{1}{2 \pi} \sum_{j=1-T}^{T-1}\left(1-\frac{|j|}{T}\right)^{2}[\hat{\gamma}(j)-E \hat{\gamma}(j)]^{2}\right] \\
&+\left[\frac{1}{2 \pi} \sum_{|j|<T}\left[\left(1-\frac{|j|}{T}\right) E \hat{\gamma}(j)-\gamma(j)\right]^{2}+\frac{1}{2 \pi} \sum_{|j| \geq T} \gamma^{2}(j)\right]
\end{aligned}
$$
by orthogonality of exponential bases $ \left\{e^{\mathrm{i} j \omega}\right\}, $ or the so-called Parseval's identity.
Note that given $ E\left(X_{t}\right)=0 $
$$
\begin{aligned}
E \hat{\gamma}(j) &=T^{-1} \sum_{t=j \mid+1}^{T} E\left(X_{t} X_{t-|j|}\right) \\
&=(1-|j| / T) \gamma(j)
\end{aligned}
$$
so we have the squared bias
$$
\sum_{j \mid<T}[E \hat{\gamma}(j)-\gamma(j)]^{2}=\sum_{|j|<T}(j / T)^{2} \gamma^{2}(j) \rightarrow 0
$$
if $ \sum_{j=-\infty}^{\infty} \gamma^{2}(j)<\infty . $ For the last term, we also have $ \sum_{|j|>T} \gamma^{2}(j) \rightarrow 0 $ as $ T \rightarrow \infty $
For the first term of IMSE $ (\hat{I}), $ we have
$$
\begin{aligned}
\sum_{j=1-T}^{T-1} E[\hat{\gamma}(j)-E \hat{\gamma}(j)]^{2} &=\sum_{j=1-T}^{T-1} \operatorname{var}[\hat{\gamma}(j)] \\
&=O(1)
\end{aligned}
$$
because $ \operatorname{var}[\hat{\gamma}(j)]=C T^{-1} $ as $ T \rightarrow \infty $ under certain regularity conditions (e.g., a mix-
ing condition with a suitable rate), for some $ C>0 $. Therefore, the variance of the periodogram $ \hat{I}(\omega) $ does not vanish as $ T \rightarrow \infty $
5.2 Kernel Spectral Estimation
Question: What is a solution to the inconsistency of the sample periodogram $ \hat{I}(\omega) ? $

In response to the fact that the sample periodogram $ \hat{I}(\omega) $ is not a consistent estimator
for the spectral density $ h(\omega) $ because it contains "too many" estimated parameters, one
can consider a truncated spectral density estimator,
$$
\hat{h}(\omega)=\frac{1}{2 \pi} \sum_{j=-p}^{p} \hat{\gamma}(j) e^{-i j \omega}, \quad \omega \in[-\pi, \pi]
$$
where $ p $ is the maximum truncation lag order such that $ p=p(T) \rightarrow \infty, p / T \rightarrow 0 $ as
$ T \rightarrow \infty . $ Thus, the number $ p+1 $ of the estimated parameters $ \{\hat{\gamma}(j)\}_{j=0}^{p} $ is substantially smaller than the sample $ T $ when $ T \rightarrow \infty . $ As a result, the variance of $ \hat{h}(\omega) $ is expected
to vanish to zero as $ T \rightarrow \infty $

The truncated spectral density estimator was used by Hansen (1980) and White and
Domowitz (1984) to consistently estimate the asymptotic variance-covariance matrix of
econometric estimators (e.g., GMM, OLS) in time series contexts, which is proportional
to the spectral density of certain time series process at frequency zero (see Chapter 3 ).
However, such an estimator may not be positive semi-definite in finite samples. This
may cause some trouble in applications.

To ensure a positive semi-definite variance-covariance matrix estimator, we can use
a weighted estimator
$$
\hat{h}(\omega)=\frac{1}{2 \pi} \sum_{j=-p}^{p} k(j / p) \hat{\gamma}(j) e^{-i j \omega}
$$
where $ k(\cdot) $ is a kernel function for the lag order, and so it is also called a lag window.
An example is the Bartlett kernel
$$
k(z)=(1-|z|) \mathbf{1}(|z| \leq 1)
$$
where $ 1(\bullet) $ is the indicator function. This is used in Newey and West (1987,1994)
The Bartlett kernel-based spectral density estimator at frequency zero is always positive
semi-definite (why?). We note that the sample periodogram $ \hat{I}(\omega) $ can be viewed as a
spectral density estimator based on the Bartlett kernel with the choice of the maximum
truncation lag order $ p=T $
Question: What is the advantage of introducing the kernel function $ k(\cdot) ? $
Most kernel functions are downward weighting, i.e., they discount higher order lags. As
a result, they help reduce the variance of $ \hat{h}(\omega) $

For a weakly stationary process with square-summable autocovariances, serial correlation
decays to zero as lag $ j $ increases. This is consistent with the stylized fact that the remote
past events have smaller impacts on the current economic systems and financial markets
than the recent events. Given this, it makes sense to discount higher order lags, namely
to discount remote past events.
More generally, we can consider
$$
\hat{h}(\omega)=\frac{1}{2 \pi} \sum_{j=1-T}^{T-1} k(j / p) \hat{\gamma}(j) e^{-i j \omega}, \quad \omega \in[-\pi, \pi]
$$
where $ k(\cdot) $ is allowed to have unbounded support, so that all $ T-1 $ sample autocovariances
are used in spectral estimation. An example is the Daniell kernel
$$
k(z)=\frac{\sin (\pi z)}{\pi z}, \quad z \in \mathbb{R}
$$
As will be seen below, the optimal kernel that minimizes the MSE of the kernel
spectral density estimator $ \hat{h}(\omega) $ also has an unbounded support (see the Quadratic-
Spectral kernel below).

When $ k(\cdot) $ has an unbounded support, $ p $ can no longer be viewed as a maximum lag
truncation order but a smoothing parameter.
We impose the following regularity condition on the kernel function.
Assumption [Kernel Function]: $ k(\cdot) $ is a symmetric function that is continuous at all but a finite number of points, such that (i) $ |k(z)| \leq 1,(\text { ii }) k(0)=1,(\text { iii }) \int_{-\infty}^{\infty} k^{2}(z) d z<\infty $
and (iv) there exists a positive real number $ q $ such that
$$
0<k_{q}=\lim _{z \rightarrow 0} \frac{k(0)-k(z)}{|z|^{q}}<\infty
$$
The quantity $ k_{q} $ characterizes the speed at which $ k(z) $ converges to $ k(0) $ in the neigh-
borhood of $ 0 . $ For the Bartlett kernel, $ q=1 . $ For the Daniell kernel, $ q=2 $

Question: What is the relationship between the kernel function or lag window $ k(\cdot) $ and
the kernel function $ K(\cdot) $ used for density and regression estimation?

In terms of mathematical properties, the kernel function or lag window $ k(\cdot) $ used for
spectral density estimation is the Fourier transform of a kernel function $ K(\cdot) $ used in

probability density and regression estimation, namely
$$
K(u)=\frac{1}{2 \pi} \int_{-\infty}^{\infty} k(z) e^{-\mathrm{i} z u} d z
$$
and
$$
k(z)=\int_{-\infty}^{\infty} K(u) e^{\mathrm{iuz}} d u
$$
When $ K(u) $ is a positive kernel (i.e., a symmetric probability density function), $ k(z) $
is the characteristic function of the probability distribution $ K(u) $. Thus, it is straight-
forward to understand the conditions imposed on $ k(z) $ and $ K(u) $ are essentially the
same:
- [Unity Integral]: $ k(0)=1 $ is equivalent to $ \int_{-\infty}^{\infty} K(u) d u=1 $
- [Square-Integratability]: $ \int_{-\infty}^{\infty} k^{2}(z) d z=2 \pi \int_{-\infty}^{\infty} K^{2}(u) d u<\infty $
- [Finite Variance]: For $ q=2 $
$$
k_{2}=-\frac{1}{2} k^{\prime \prime}(0)=\frac{1}{2} \int_{-\infty}^{\infty} u^{2} K(u) d u<\infty
$$
- [Symmetry]: The symmetry of $ k(z) $ is equivalent to the symmetry of $ K(u), $ so
$$
\int_{-\infty}^{\infty} u K(u) d u=0
$$
We now provide some commonly used kernels in practice. They include:

Truncated kernel
$$
k(z)=\mathbf{1}(|z| \leq 1)
$$
Its Fourier transform
$$
K(u)=\frac{1}{\pi} \frac{\sin u}{u}, \quad-\infty<u<\infty
$$
$ \bullet $ Bartlett kernel
$$
k(z)=(1-|z|) \mathbf{1}(|z| \leq 1)
$$
Its Fourier transform
$$
K(u)=\frac{1}{2 \pi}\left[\frac{\sin (u / 2)}{u / 2}\right]^{2}, \quad-\infty<u<\infty
$$

- Daniell kernel
$$
k(z)=\frac{\sin (\pi z)}{\pi z}, \quad-\infty<z<\infty
$$
Its Fourier transform
$$
K(u)=\frac{1}{2 \pi} 1(|u| \leq \pi)
$$
Parzen kernel
$$
k(z)=\left\{\begin{array}{ll}
1-6 z^{2}+6|z|^{3} & \text { if }|z| \leq \frac{1}{2} \\
2(1-|z|)^{3} & \text { if } \frac{1}{2}<|z| \leq 1 \\
0 & \text { otherwise }
\end{array}\right.
$$
Its Fourier transform
$$
K(u)=\frac{3}{8 \pi}\left[\frac{\sin (u / 4)}{u / 4}\right]^{4}, \quad-\infty<u<\infty
$$
- Quadratic-Spectral kernel (i.e., Priestley)
$$
k(z)=\frac{3}{(\pi z)^{2}}\left[\frac{\sin \pi z}{\pi z}-\cos (\pi z)\right], \quad-\infty<z<\infty
$$
Its Fourier transform
$$
K(u)=\frac{3}{4 \pi}\left[1-(u / \pi)^{2}\right] \mathbf{1}(|u| \leq \pi)
$$
5.3 Consistency of Kernel Spectral Estimator
Question: Why is the kernel spectral estimator $ \hat{h}(\omega) $ consistent for $ h(\omega) ? $
We consider the integrated MSE criterion
$$
\begin{aligned}
I M S E(\hat{h})=& E \int_{-\pi}^{\pi}|\hat{h}(\omega)-h(\omega)|^{2} d \omega \\
=& E \int_{-\pi}^{\pi}|\hat{h}(\omega)-E \hat{h}(\omega)|^{2} d \omega \\
&+\int_{-\pi}^{\pi}|E \hat{h}(\omega)-h(\omega)|^{2} d \omega
\end{aligned}
$$
We first consider the bias of $ \hat{h}(\omega) $

Given $ E[\hat{\gamma}(j)]=(1-|j| / T) \gamma(j), $ we have
$$
\begin{aligned}
E \hat{h}(\omega)-h(\omega)=& \frac{1}{2 \pi} \sum_{j=1-T}^{T-1} k(j / p) E \hat{\gamma}(j) e^{-i j \omega} \\
&-\frac{1}{2 \pi} \sum_{j=-\infty}^{\infty} \gamma(j) e^{-i j \omega} \\
=& \frac{1}{2 \pi} \sum_{j=1-T}^{T-1}[(1-|j| / T) k(j / p)-1] \gamma(j) e^{-i j \omega} \\
&-\frac{1}{2 \pi} \sum_{|j|>T-1} \gamma(j) e^{-i j \omega} \\
=& \frac{1}{2 \pi} \sum_{j=1-T}^{T-1}[k(j / p)-1] \gamma(j) e^{-i j \omega} \\
&-\frac{1}{2 \pi T} \sum_{j=1-T}^{T-1} k(j / p)|j| \gamma(j) e^{-i j \omega} \\
&-\frac{1}{2 \pi} \sum_{|j|>T-1} \gamma(j) e^{-i j \omega} \\
=&-p^{-q} k_{q} h^{(q)}(\omega)+o\left(p^{-q}\right)
\end{aligned}
$$
where $ o\left(p^{-q}\right) $ is uniform in $ \omega \in[-\pi, \pi] . $ Here, for the first term,
$$
\begin{aligned}
& \frac{1}{2 \pi} \sum_{j=1-T}^{T-1}[k(j / p)-1] \gamma(j) e^{-i j \omega} \\
=&-p^{-q} \frac{1}{2 \pi} \sum_{j=1-T}^{T-1}\left\{\frac{[1-k(j / p)]}{|j / p|^{q}}\right\}|j|^{q} \gamma(j) e^{-i j \omega} \\
=&-p^{-q} k_{q} h^{(q)}(\omega)[1+o(1)]
\end{aligned}
$$
as $ p \rightarrow \infty, $ where $ k_{q}=\lim _{z \rightarrow 0}[1-k(z)] /|z|^{q}, $ and the function
$$
h^{(q)}(\omega)=\frac{1}{2 \pi} \sum_{j=-\infty}^{\infty}|j|^{q} \gamma(j) e^{-i j \omega}, \quad \omega \in[-\pi, \pi]
$$
is called the $ q $ -th order generalized derivative of $ h(\omega) $. Note that $ h^{(q)}(\omega) $ differs from the
usual derivative. When $ q $ is even, we have
$$
h^{(q)}(\omega)=\frac{1}{q !} \frac{d^{q}}{d \omega q} h(\omega)
$$
Note that a spectral peak will arise when $ \gamma(j) $ decays to zero slowly as the lag order
$$
j \rightarrow \infty
$$

Next, we consider the second term of the bias. For the second term, we have
$$
\begin{aligned}
\frac{1}{2 \pi T}\left|\sum_{j=1-T}^{T-1} k(j / p)\right| j \mid \gamma(j) e^{-i j \omega \mid} & \leq \frac{1}{2 \pi T} \sum_{j=1-T}^{T-1}|j \gamma(j)| \\
&=O\left(T^{-1}\right)
\end{aligned}
$$
if $ \sum_{j=-\infty}^{\infty}|j \gamma(j)|<\infty $
Similarly, for the last term of the bias,
$$
\begin{aligned}
\sum_{|j|>T} \gamma(j) e^{-i j \omega} \mid & \leq \sum_{|j|>T}|\gamma(j)| \\
& \leq T^{-1} \sum_{|j|>T}|j \gamma(j)| \\
&=o\left(T^{-1}\right)
\end{aligned}
$$
given $ \sum_{j=-\infty}^{\infty}|j \gamma(j)|<\infty, $ which implies $ \sum_{|j|>T}|j \gamma(j)| \rightarrow 0 $ as $ T \rightarrow \infty $
Thus, suppose $ p^{q} / T \rightarrow 0 $ such that $ T^{-1}=o\left(p^{-q}\right) $, which can be satisfied by choosing
a suitable bandwidth $ p=p(T) \rightarrow \infty, $ we have
$$
E \hat{h}(\omega)-h(\omega)=-p^{-q} k_{q} h^{(q)}(\omega)+o\left(p^{-q}\right)
$$
and the squared bias
$$
\begin{aligned}
& \int_{-\pi}^{\pi}[E \hat{h}(\omega)-h(\omega)]^{2} d \omega \\
=& p^{-2 q} k_{q}^{2} \int_{-\pi}^{\pi}\left[h^{(q)}(\omega)\right]^{2} d \omega+o\left(p^{-2 q}\right) \\
=& p^{-2 q} k_{q}^{2} \frac{1}{2 \pi} \sum_{j=-\infty}^{\infty}|j|^{2 q} \gamma^{2}(j)+o\left(p^{-2 q}\right)
\end{aligned}
$$
If $ h^{(q)}(\omega)>0, $ which can arise when (e.g.) the autocovariance $ \gamma(j) $ is always positive
for all $ j, $ then the bias is always negative. In other words, the kernel method always
underestimates a spectral peak.

Unlike nonparametric estimation in time domain or space domain, there is no boundary bias problem, because $ \hat{h}(\cdot) $ is a symmetric periodic function.

Next, for the integrated variance of $ \hat{h}(\omega), $ we have
$$
\begin{aligned}
E[\hat{\gamma}(j)-E \hat{\gamma}(j)]^{2} &=\operatorname{var}[\hat{\gamma}(j)] \\
&=\frac{1}{T}\left[\sum_{j=-\infty}^{\infty} \gamma^{2}(j)\right][1+o(1)] \\
&=\frac{1}{T} \int_{-\pi}^{\pi} h^{2}(\omega) d \omega[1+o(1)]
\end{aligned}
$$
Here, we have used the identity (see Priestley, $ 1981, $ p.xxx) that for any given lag order $ r $
$ j>0 $
$$
\operatorname{var}[\hat{\gamma}(j)]=T^{-1} \sum_{m=1-(T-j)}^{T-j-1}\left(1-\frac{|m|+j}{T}\right)\left[\gamma^{2}(m)+\gamma(m+j) \gamma(m-j)+\kappa_{4}(m, j, m+j)\right]
$$
where $ \kappa_{4}(i, j, k) $ is called the fourth order cumulant of the process $ \left\{X_{t}\right\}, $ defined as
$$
\kappa_{4}(i, j, k)=E\left(X_{t} X_{t+i} X_{t+j} X_{t+k}\right)-E\left(\tilde{X}_{t} \tilde{X}_{t+i} \tilde{X}_{t+j} \tilde{X}_{t+k}\right)
$$
where $ \left\{\tilde{X}_{t}\right\} $ is a Gaussian process with the same mean and autocovariance function as $ \left\{X_{t}\right\} . $ It follows that
$$
\begin{aligned}
\frac{1}{(2 \pi)} \sum_{j=1-T}^{T-1} k^{2}(j / p) \operatorname{var}[\hat{\gamma}(j)] \\
=\frac{1}{(2 \pi)} \sum_{j=1-T}^{T-1} k^{2}(j / p) T^{-1} \sum_{m=1-(T-j)}^{T-j-1}\left(1-\frac{|m|+j}{T}\right) \gamma^{2}(m) \\
+\frac{1}{(2 \pi)} \sum_{j=1-T}^{T-1} k^{2}(j / p) T^{-1} \sum_{m=1-(T-j)}^{T-j-1}\left(1-\frac{|m|+j}{T}\right) \gamma(m+j) \gamma(m-j) \\
+\frac{1}{(2 \pi)} \sum_{j=1-T}^{T-1} k^{2}(j / p) T^{-1} \sum_{m=1-(T-j)}^{T-j-1}\left(1-\frac{|m|+j}{T}\right) \kappa_{4}(m, j, m+j) \\
=\hat{V}_{1}+\hat{V}_{2}+\hat{V}_{3}, \text { say, }
\end{aligned}
$$
where
$$
\begin{aligned}
\hat{V}_{1}=\frac{p}{T} \frac{1}{2 \pi}\left[\sum_{m=-\infty}^{\infty} \gamma^{2}(m)\right]\left[\frac{1}{p} \sum_{j=1-T}^{T-1} k^{2}(j / p)\right][1+o(1)] \\
=& \frac{p}{T} \int_{-\pi}^{\pi} h^{2}(\omega) d \omega \int_{-\infty}^{\infty} k^{2}(z) d z[1+o(1)] \\
\left|\hat{V}_{2}\right| & \leq \frac{1}{T} \sum_{j=-\infty}^{\infty}|\gamma(j)| \sum_{m=-\infty}^{\infty}|\gamma(m)|=O\left(T^{-1}\right)
\end{aligned}
$$

if $ \sum_{j=-\infty}^{\infty}|\gamma(j)|<\infty, $ and finally, for the last term,
$$
\left|\hat{V}_{3}\right| \leq \frac{1}{T} \sum_{j=-\infty}^{\infty} \sum_{l=-\infty}^{\infty} \sum_{k=-\infty}^{\infty}\left|\kappa_{4}(i, j, k)\right|=O\left(T^{-1}\right)
$$
if $ \sum_{j=-\infty}^{\infty} \sum_{l=-\infty}^{\infty} \sum_{k=-\infty}^{\infty}\left|\kappa_{4}(i, j, k)\right|<\infty $
It follows that the IMSE
$$
\begin{aligned}
\operatorname{IMSE}(\hat{h})=& \frac{p}{T} \int_{-\pi}^{\pi} h^{2}(\omega) d \omega \int_{-\infty}^{\infty} k^{2}(z) d z \\
&+p^{-2 q} k_{q}^{2} \int_{-\pi}^{\pi}\left[h^{(q)}(\omega)\right]^{2} d \omega \\
&+o\left(p / T+p^{-2 q}\right) \\
=& \frac{p}{T} \frac{1}{2 \pi}\left[\sum_{j=-\infty}^{\infty} \gamma^{2}(j)\right] \int_{-\infty}^{\infty} k^{2}(z) d z \\
&+\frac{1}{p^{2 q}} k_{q}^{2} \frac{1}{2 \pi} \sum_{j=-\infty}^{\infty}|j|^{2 q} \gamma^{2}(j) \\
&+o\left(T^{-1} p+p^{-2 q}\right) \\
=& O\left(p / T+p^{-2 q}\right)
\end{aligned}
$$
Therefore, $ \hat{h}(\omega) $ is consistent for $ h(\omega) $ for any $ \omega \in[-\pi, \pi] $ if $ p \rightarrow \infty, p / T \rightarrow 0 $ as $ T \rightarrow \infty . $ Differentiating the asymptotic IMSE $ (\hat{h}), $ we obtain the optimal bandwidth
$$
\begin{aligned}
p_{0} &=\left[\frac{2 q k_{q}^{2}}{\int_{-\infty}^{\infty} k^{2}(z) d z} \frac{\int_{-\pi}^{\pi}\left[h^{(q)}(\omega)\right]^{2} d \omega}{\int_{-\pi}^{\pi} h^{2}(\omega) d \omega}\right]^{\frac{1}{2 q+1}} T^{\frac{1}{2 q+1}} \\
&=c_{0} T^{\frac{1}{2 q+1}}, \text { say. }
\end{aligned}
$$
With this rate for $ p, $ the optimal convergence rate for $ h(\omega) $ is $ I M S E(\hat{h}) \propto T^{-\frac{2 \theta}{2 q+1}} $ This optimal bandwidth is unknown because the optimal tuning parameter $ c_{0} $ involves
the unknown spectral density $ h(\omega) $ and its generalized $ q $ -order derivative $ h^{(q)}(\omega) $. Again,
a plug-in or cross-validation method can be used.
It is shown that the optimal kernel is the Quadratic-Spectral kernel
$$
k(z)=\frac{z}{(\pi z)^{2}}\left[\frac{\sin (\pi z)}{\pi z}-\cos (\pi z)\right], \quad-\infty<z<\infty
$$
Note that the Fourier transform of the QS kernel is the Epanechnikov kernel
$$
K(u)=\frac{1}{4 \pi}\left[1-\left(\frac{u}{\pi}\right)^{2}\right] \mathbf{1}(|u| \leq \pi)
$$

The latter is the optimal kernel for kernel density and regression estimation.
Question: Is there any equivalent expression for $ \hat{h}(\omega) $ using the Fourier transform $ K(u) ? $
Yes, recall the formula
$$
\hat{h}(\omega)=\frac{1}{2 \pi} \sum_{t=1-T}^{T-1} k(j / p) \hat{\gamma}(j) e^{-i j \omega}, \quad \omega \in[-\pi, \pi]
$$
and the well-known result that the Fourier transform of the product between $ \hat{\gamma}(j) $ and
$ k(j / p) $ is the convolution of their Fourier transforms, we can obtain
$$
\begin{aligned}
\hat{h}(\omega) &=\frac{1}{2 \pi} \sum_{j=1-T}^{T-1} k(j / p) \hat{\gamma}(j) e^{-\mathrm{i} j \omega} \\
&=\int_{-\pi}^{\pi} \hat{I}(\lambda) W_{T}(\omega-\lambda) d \lambda \\
&=\int_{-\pi}^{\pi} \hat{I}(\lambda) p K[p(\omega-\lambda)] d \lambda \\
&=\int_{-\pi}^{\pi} \hat{I}(\lambda) \frac{1}{h} K\left(\frac{\omega-\lambda}{h}\right) d \lambda
\end{aligned}
$$
where $ h=p^{-1} $ is a bandwdith, $ \hat{I}(\lambda) $ is the sample periodogram, namely,
$$
\begin{aligned}
\hat{I}(\lambda) &=\frac{1}{2 \pi T}\left|\sum_{t=1}^{T} X_{t} e^{\mathrm{i} t \lambda}\right|^{2} \\
&=\frac{1}{2 \pi} \sum_{j=1-T}^{T-1}\left(1-\frac{|j|}{T}\right) \hat{\gamma}(j) e^{-\mathrm{i} j \lambda}
\end{aligned}
$$
which is the discrete Fourier transform of $ \hat{\gamma}(j), $ and the weighting function $ W_{T}(\lambda) $ is the
discrete Fourier transform of $ k(j / p), $ namely,
$$
\begin{aligned}
W_{T}(\lambda) &=\frac{1}{2 \pi} \sum_{j=-(T-1)}^{T-1} k(j / p) e^{-i j \lambda} \\
&=p\left[\frac{1}{2 \pi p} \sum_{j=-\infty}^{\infty} k(j / p) e^{-i(j / p) p \lambda}\right] \\
&=p \sum_{j=-\infty}^{\infty} K[p(\lambda+2 \pi j)] \\
& \sim p K(p \lambda)
\end{aligned}
$$

Question: When
$$
p \sum_{j=-\infty}^{\infty} K[p(\lambda+2 \pi j)]=p K(p \lambda), \lambda \in[-\pi, \pi] ?
$$
When $ K(\cdot) $ has bounded support on $ [-\pi, \pi] $ and $ p $ is large, then the terms with $ j \neq 0 $
will all vanish to zero.
since the periodogram $ \hat{I}(\lambda) $ is the discrete Fourier transform of $ \hat{\gamma}(j) $ and the weighting
function $ W_{T}(\lambda) $ is the discrete Fourier transform of $ k(j / p), $ the Fourier transform of the
product between $ \hat{\gamma}(j) $ and $ k(j / p) $ is the convolution of their Fourier transforms.

The weighting function $ W_{T}(\lambda) $ plays a crucial role of local weighting and smoothing. We now provide a geometric interpretation of $ \hat{h}(\omega) $. Put $ h=p^{-1} $ so that $ h \rightarrow 0 $ as
$ T \rightarrow \infty . $ Then
$$
\begin{aligned}
\hat{h}(\omega) &=\int_{-\pi}^{\pi} \hat{I}(\lambda) p K[p(\omega-\lambda)] d \lambda \\
&=\int_{-\pi}^{\pi} \hat{I}(\lambda) \frac{1}{h} K\left(\frac{\omega-\lambda}{h}\right) d \lambda
\end{aligned}
$$
Therefore, $ \hat{h}(\omega) $ is a smoothed version of the sample periodogram $ \hat{I}(\lambda) $ over frequencies in a small neighborhood $ [\omega-\pi h, \omega+\pi h] $, if $ K(\cdot) $ has a support $ [-\pi, \pi] $.
Suppose $ q=2 . $ Then
$$
E \hat{h}(\omega)-h(\omega)=-p^{-q} k_{q} h^{(q)}(\omega)+o\left(p^{-q}\right)
$$
This can be relatively large when there is a spectral speak at frequency $ \omega . $ Granger
(1966) points out that the typical spectral shape of most economic time series is that it
has a peak at frequency zero and then decays to zero as frequency increases.
Question: How to reduce the bias of $ \hat{h}(\omega) ? $
There are several approaches to reducing the bias of spectral density estimation.
One popular approach is the pre-whitening procedure. Tukey (1957) and Andrews and
Monahan (1992) consider this approach. To describe the basic idea, we consider an AR

approximation:
$$
\begin{aligned}
X_{t} &=\sum_{j=1}^{m} \psi_{j} X_{t-j}+u_{t} \\
&=\Psi(L) X_{t}+u_{t}
\end{aligned}
$$
Then the innovation or residual $ \left\{u_{t}\right\} $ will have weaker serial dependence. Put
$$
\Psi(L)=1-\sum_{j=1}^{m} \psi_{j} L^{j}
$$
Then
$$
u_{t}=\Psi(L) X_{t}
$$
and it follows from Chapter 3 that the spectral density function of $ u_{t} $
$$
h_{u}(\omega)=\left|\Psi\left(e^{-i \omega}\right)\right|^{2} h_{X}(\omega)
$$
Thus, the spectral density of $ X_{t} $ is given by
$$
h_{X}(\omega)=\left|\Psi\left(e^{-i \omega}\right)\right|^{-2} h_{u}(\omega)
$$
In practice, we can first run a prewhitening regression, and obtain the parameter estimators $ \left\{\hat{\psi}_{j}\right\}_{j=1}^{m} $. Then use the kernel method to estimate $ h_{u}(\omega) $ using the prewhitening residual $ \left\{\hat{u}_{t}\right\} . $ Finally, obtain $ \hat{h}_{X}(\omega)=\left|\hat{\Psi}\left(e^{-i \omega}\right)\right|^{-2} \hat{h}_{u}(\omega) . $ This is called "recoloring". We
note that the spectral density $ h_{u}(\omega) $ of $ u_{t} $ is easier to estimate because it is "flatter"
than the spectral density $ h_{X}(\omega) $ of $ X_{t} $

For the prewhitening procedure, the bias can be reduced substantially but the vari-
ance is increased at the same time. As a result, MSE of $ \hat{h}_{X}(\omega) $ may be larger than that
without using prewhitening.
Another approach is to use the logarithmic transformation. Put
$$
\lambda_{k}=\frac{2 \pi k}{T} \text { for } k=0, \ldots,\left[\frac{T-1}{2}\right]
$$
These are called Fourier frequencies. Then the sample periodogram of $ \left\{X_{t}\right\}_{t=1}^{T} $
$$
\hat{I}_{X}\left(\lambda_{k}\right)=f\left(\lambda_{k}\right) \hat{I}_{\varepsilon}(\hat{\lambda})+\hat{R}_{k}
$$
where
$$
\hat{I}_{\epsilon}\left(\lambda_{k}\right)=\frac{1}{2 \pi T}\left|\sum_{t=1}^{T} \varepsilon_{t} e^{i t \lambda_{k}}\right|^{2}
$$

is the sample periodogram of an innovation sequence $ \left\{\varepsilon_{t}\right\}_{t=1}^{T}, $ and $ R_{k} $ is an asymptotically
negligible term. For $ 0<k<\left[\frac{T-1}{2}\right] $

A third approach is to use the wavelet approach, which can estimate the spectral peak
more efficiently than the kernel method. For more discussions, see H??rdle, Kerkyachar-
ian, Picard and Tsybakov (1998), Wavelets, Approximation and Statistical Applications,
Lecture Notes in Statistics Volume $ 129, $ Hong and Kao $ (2004, \text { Econometrica}), $ Hong and Lee $ (2001, \text { Econometric Theory }), $ and Lee and Hong $ (2001, \text { Econometric Theory}) $.

Kernel-based estimation for the spectral density function has been widely used in
time series econometrics. The most well-known application is consistent estimation of
the long-run variance-covariance matrix of a time series process (see Chapter 3 ). Observing that the long-run variance-covariance matrix is equal to $ 2 \pi $ times the spectral
density function at frequency zero, one can consistently estimate the long-run variance-
covariance matrix by estimating the spectral density at frequency zero. Newey and
West (1987,1994) propose to use the Bartlett kernel to estimate the spectral density.
Andrews (1991) propose a general class of kernel estimators for the long-run variance-
covariance matrix, and show that the Quadratic-Spectral kernel is the optimal kernel
that minimizes the asymptotic mean squared error of the kernel estimator. A key is-
sue for kernel-based estimation of a long-run variance-covariance matrix is the choice of
the smoothing parameter $ p . $ Newey and West (1994) and Andrews (1991) propose some
data-driven plug-in methods to select $ p $. In practice, kernel estimators often tend to dis-
play overrejections when used to construct test statistics. This arises particularly when
data displays strong or persistent serial dependence. The main reason is that the kernel-
based estimator tends to underestimate the true long-run variance-covariance matrix,
as the asymptotic bias formula has indicated. Alternative approaches have been pro-
posed, including the high-power kernel estimator (Phillips and Sun 1999 ), the so-called
fixed $ b $ asymptotic method (Kiefer and Vogelsang 2005), and various self-normalization
methods (e.g., Shao 2010, 2015). The basic idea of the self-normalization methods is
to use a normalization factor that avoids choosing a smoothing parameter like $ p $. The
normalization factors are not consistent for the long-run variance-covariance matrix but
are proportional to the long-run variance-covariance matrix up to a stochastic factor,
which lead to a nonstandard asymptotic distribution for the proposed test statistics that
is heavier than the normal distribution. These self-normalization methods can improve
size of the proposed tests in finite sample, but they suffer from some power loss up to

various degrees, due to the heavy-tailed asymptotic distribution.
Another application of the kernel estimation of the spectral density function is to
test for serial correlation of unknown form. In a time series linear regression model, it
is often of interest to test the null hypothesis that the regression disturbance has no
serial correlation of unknown form. Under the null hypothesis, the regression distur-
bance sequence is a white noise, and its spectral density function is a flat spectrum.
Under the alternative hypothesis that there exists serial correlation, the spectral density
of the disturbance is not flat and can be consistently estimated by the kernel method.
Therefore, one can construct a consistent test for serial correlation of unknown form by
comparing a kernel-based spectral density estimator with the flat spectrum. To compare
the two spectral density estimators under the null and alternative hypotheses, one can
use the squared $ L_{2} $ -norm, the squared Hellinger metric, or the Kullback-Leibler informa-
tion criterion. As the sample size $ T \rightarrow \infty, $ these distance or divergence measures vanish
to zero under the null hypothesis and converge to nonzero limits under the alternative
hypothesis, giving the tests their asymptotic unit power. Therefore, if these distance or
divergence measures are close to zero, then the null hypothesis holds; if they are not
close to zero, then the alternative hypothesis must be true. How large these distance or
divergence measures should be in order to be considered as significantly large is deter-
mined by their sampling distributions. For more discussion, see Hong (1996) or Chapter
7 for the $ L_{2} $ -norm-based test.

6 Conclusion
In this chapter, we have introduced some smoothed nonparametric estimation methods
in both time domain and frequency domain. The functions of interest include but are not
restricted to probability density functions, regression functions, trend functions of time,
time-varying functional coefficients, and spectral density functions. Associated with
the first three functions of interest are nonparametric methods in time domain, and
associated with the spectral density estimation are nonparametric methods in frequency
domain.

Nonparametric methods can be divided into two categories: global smoothing and
local smoothing. In this chapter, we consider local smoothing. In particular, we introduce the kernel smoothing methods for density function, regression function and
spectral density functions, and local polynomial smoothing methods for regression function, functional coefficient models, functional coefficient models in a linear or nonlinear
setup. Relationships between these methods are also discussed, including the Fourier
transform relationship between the nonparametric estimation methods in time domain
and frequency domain. Nonparametric methods have been widely applied in economics
and finance.
