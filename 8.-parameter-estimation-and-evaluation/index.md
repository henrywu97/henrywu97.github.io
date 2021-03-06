# 

# 8. Parameter Estimation and Evaluation

## 8.1 Population and Distribution Model

A random sample $\mathbf{X}^{n}=\left(X_{1}, \cdots, X_{n}\right)$ is from a population distribution $f_{X}(x)$.

A realization $\mathrm{x}^{n}$ of the random sample $\mathrm{X}^{n}$ constitutes a data set with sample size $n$.

【Sampling Inference】The primary purpose of statistical inference is to make inference of the population distribution $f_{X}(x)$ using an observed data $\mathbf{x}^{n}$.

【Parametric Approach】Consider a class of **parametric candidate distributions**
$$
\mathbb{F}=\{f(\cdot, \theta): \theta \in \Theta\}
$$

where $f: \Omega \times \Theta \rightarrow \mathbb{R}^{+}$ is a known PMF/PDF function, $\Omega$ is the support of $X_{i}, \Theta$ is a parameter space that contains all plausible values for a $p \times 1$ parameter vector $\theta,$ with $p$ a fixed integer. Each value of $\theta \in \Theta$ gives a distribution model for $f_{X}(x)$.

【Correct Model Specification】Assume that the class of functions $\mathbb{F}$ contains the population distribution $f_{X}(x)$ that generates the observed data. That is, there exists some unknown parameter value $\theta_{0} \in \Theta$ such that

$$
f_{X}(x)=f\left(x, \theta_{0}\right) \text { for all } x \in \Omega
$$

- If $\mathbb{F}$ contains $f_{X}(\cdot),$ we call that the class of models $\mathbb{F}$ is correctly specified for the population distribution $f_{X}(\cdot),$ and $\theta_{0}$ is called the true value of $\theta$.

- In contrast, $\mathbb{F}$ is said to be **misspecified** for $f_{X}(\cdot)$ if there exists no value for $\theta \in \Theta$ such that $f_{X}(x)=f(x, \theta)$ for all $x \in \Omega .$ This can occur when, e.g., we specify a class of normal distribution models but the true population is a Gamma distribution.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200523091516.png)

【Example 8.1】**Discrete Choice Probit and Logit Models**: The Probit and Logit models are popularly used when a dependent variable has binary outcomes, i.e., there are two possible outcomes 0 and 1. Examples include whether or not an individual is employed, whether or not a consumer makes a purchase, and whether or not a financial crisis (e.g., default risk) occurs.

A probit model assumes

$$
P\left(Y_{i}=1 | X_{i}\right)=\Phi\left(\theta_{1}+\theta_{2} X_{i}\right), \quad i=1, \cdots, n
$$

where $\Phi(\cdot)$ is the $N(0,1)$ CDF, and $X_{i}$ is an explanatory variable.

A logit model assumes

$$
P\left(Y_{i}=1 | X_{i}\right)=\frac{1}{1+e^{-\left(\theta_{1}+\theta_{2} X_{i}\right)}}
$$

【Example 8.2】**Survival/Duration Analysis**: Suppose we are interested in the time length it takes for an unemployed person to find a job, the time length that elapses between two trades or two price changes, the length of a strike, the length before a cancer patient dies, and the length before a financial crisis (e.g., credit default risk) comes out. Such analysis is called duration analysis or survival analysis.

In practice, the main interest often lies in the question of how long a duration will continue, given that it has not finished yet. The **hazard rate** measures the chance that the duration will end now, given that it has not ended before. This hazard rate can be interpreted as the chance to find a job, to trade, to end a strike, etc.

Suppose $T_{i}$ is the duration from a population with $\operatorname{PDF} f(t)$ and $\operatorname{CDF} F(t)$. Then the survival function is

$$
S(t)=P\left(T_{i}>t\right)=1-F(t)
$$

and the hazard rate

$$
\begin{aligned}
\lambda(t) &=\lim _{\delta \rightarrow 0^{+}} \frac{P\left(t<T_{i} \leq t+\delta | T_{i}>t\right)}{\delta} \\
&=\frac{f(t)}{S(t)}
\end{aligned}
$$

Intuitively, the hazard rate $\lambda(t)$ is the **instantaneous probability** that an event of interest will end at time t given that it has lasted for period t. Note that the specification of $\lambda(t)$ is equivalent to a specification of PDF $f(t),$ but $\lambda(t)$ is more interpretable from an economic point of view. 

The hazard rate may not be the same for all individuals. To control heterogeneity across individuals, we assume that the individual-specific hazard rate depends on some individual characteristics $X_{i}$ (e.g., age, gender, race, education, work experience) via the form
$$
\lambda_{i}(t)=e^{X_{i}^{\prime} \theta} \lambda_{0}(t)
$$

where $\lambda_{0}(t)$ is called a baseline hazard function, and exponential form of $X_i$ is to keep non-negative (according to definition). This model, proposed by cox (1972), is called a proportional hazard model. When the model is correctly specified, the true parameter value

$$
\begin{aligned}
\theta_{0} &=\frac{\partial \ln \lambda_{i}(t)}{\partial X_{i}} \\
&=\frac{1}{\lambda_{i}(t)} \frac{\partial \lambda_{i}(t)}{\partial X_{i}}
\end{aligned}
$$

can be interpreted as the relative marginal effects of $X_{i}$ on the hazard rate of individual i. Inference of $\theta_{0}$ will allow one to examine how individual characteristics affect the duration of interest.

For example, suppose $T_{i}$ is the unemployment duration for individual $i,$ then the inference of $\theta_{0}$ will allow us to examine how individual characteristics, such as age, education, gender, job training, etc, can affect the unemployment duration. This will provide important policy implications on labor markets. Because one can obtain the conditional PDF of $Y_{i}$ given $X_{i}$ as follows:
$$
f_{i}(t)=\lambda_{i}(t) S_{i}(t)
$$

where the survival function

$$
S_{i}(t)=e^{-\int_{0}^{t} \lambda_{i}(s) d s}
$$

can estimate $\theta_{0}$ by the so-called maximum likelihood estimation (MLE) method.

**Remarks:**

- Usually, the true parameter value $\theta_{0}$ is unknown, and one is interested in making inference of $\theta_{0}$ using an observed data $\mathbf{x}^{n}$
- Traditionally, problems of statistical inference are divided into problems of estimation and hypothesis testing. In this chapter, we are interested in estimating $\theta_{0}$
- We shall introduce two most commonly used estimation methods, namely the maximum likelihood estimation (MLE) and the generalized method of moments estimation (GMM)

## 8.2 Maximum Likelihood Estimation

### 8.2.1 Maximum Likelihood Estimator

Question: How to estimate $\theta_{0}$ based on a data set $\mathbf{x}^{n}$ under Correct Model Specification?

R. Fisher proposed a general method of estimation called MLE. He demonstrated the advantage of this method by showing that it yields a sufficient estimator for parameter $\theta$ whenever it exists and the MLE is asymptotically most efficient in terms of some sensible criterion.

【Definition (8.1)】**Likelihood Function**: Given $\mathrm{X}^{n}=\mathrm{x}^{n}$, the joint $P M F / P D F$ of the random sample $\mathrm{X}^{n}$ as a function of $\theta$

$$
\hat{L}\left(\theta | \mathbf{x}^{n}\right)=f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)
$$

is called the likelihood function of the random sample $\mathrm{X}^{n}$ when $\mathrm{x}^{n}$ is observed. Also, $\ln \hat{L}\left(\theta | \mathrm{x}^{n}\right)$ is called the **log-likelihood function** of the random sample $\mathrm{X}^{n}$ when $\mathrm{x}^{n}$ is observed.

**Likelihood Function & PDF/PMF**

- The likelihood function $L\left(\theta | \mathbf{x}^{n}\right)$ is algebraically equal to the joint PDF or PMF of the random sample $\mathbf{X}^{n}$ when $\mathbf{X}^{n}=\mathbf{x}^{n}$
- The conceptual difference between them is that the likelihood $L\left(\theta | \mathbf{x}^{n}\right)$ is a function of $\theta,$ with $\mathbf{x}^{n}$ held fixed. Given $\theta,$ the likelihood $L\left(\theta | \mathbf{x}^{n}\right)$ is a measure of the probability or probability density with which the observed sample $\mathbf{x}^{n}$ will occur.

- The joint PDF/PMF of the random sample $\mathbf{X}^{n}, f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right),$ is different from the population distribution $f(x, \theta) .$ The latter is the PDF/PMF of each random variable $X_{i}$

【Definition 8.2】**Maximum Likelihood Estimator (MLE)**:  Suppose the statistic $\hat{\theta}=\hat{\theta}_{n}\left(\mathbf{X}^{n}\right)$ maximizes $\hat{L}\left(\theta | \mathbf{X}^{n}\right)$ over $\theta \in \Theta,$ conditional on $\mathbf{X}^{n},$ where $\Theta$ is a finite-dimensional parameter space. That is

$$
\hat{\theta} \equiv \hat{\theta}_{n}\left(\mathbf{X}^{n}\right)=\arg \max _{\theta \in \Theta} \hat{L}\left(\theta | \mathbf{X}^{n}\right)
$$

Then, when exists, $\hat{\theta} \equiv \hat{\theta}_{n}\left(\mathbf{X}^{n}\right)$ is called the MLE (**estimator**) for parameter $\theta$. Given a sample point (or a a data set) $ \mathbf{x}^{n}$ for the random sample $\mathbf{X}^{n}, \theta\left(\mathbf{x}^{n}\right)$ is called a maximum likelihood **estimate** for $\theta$.

- Estimator——估计量

- Estimate——估计量的实现值，即估计值

MLE is the parameter estimate which makes the observed data $x^{n}$ most likely to occur. In other words, by choosing a parameter estimate $\hat{\theta}_{n}\left(\mathbf{x}^{n}\right),$ MLE maximizes the probability that $\mathrm{X}^{n}=\mathrm{x}^{n}$, that is, the probability that $\mathrm{X}^{n}$ takes the value of the observed data $\mathbf{x}^{n}$.

### 8.2.2 MLE procedure

【Theorem 8.1】**Existence of MLE**: Suppose, **with probability one, $\hat{L}\left(\theta | X^{n}\right)$ is a continuous function of $\theta \in \Theta$,** and $\Theta$ is a compact set (close and bounded, e.g., $a \leq x \leq b$). Then there exists a global maximizer $\hat{\theta}$ that solves the problem

$$
\hat{\theta} \equiv \hat{\theta}_{n}\left(\mathbf{X}^{n}\right)=\arg \max _{\theta \in \Theta} \hat{L}\left(\theta | \mathbf{X}^{n}\right)
$$

**Remarks:**

It is often convenient to solve $\max _{\theta \in \Theta} \ln \hat{L}\left(\theta | \mathrm{X}^{n}\right)$, where $\ln \hat{L}\left(\theta | \mathrm{X}^{n}\right)$ is called the log-likelihood function, which is a strictly monotonic increasing function of $\hat{L}\left(\theta | \mathbf{X}^{n}\right)$.

MLE may not be unique. Given an observed data set $\mathbf{x}^{n}$, MLE may be obtained at more than one point in $\Theta$. Thus, multiple solutions for MLE are possible.

The maximum is obtained over parameter space $\Theta$, where $\Theta$ may be subject to restriction. For example, when estimating a Generalized AutoRegressive Conditional Heteroskedasticity (GARCH) model (Bollerslev 1986), $\theta$ may be subject to strictions to ensure that the conditional variance is always nonnegative.

When $\ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)$ is twice continuously differentiable with respect to $\theta \in \Theta,$ MLE solution will be easy to find. A necessary condition for MLE is that $\theta$ must satisfy the first order conditions (FOC)
$$
\left.\frac{\partial \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta}\right|_{\theta=\hat{\theta}}=0
$$
which consists of $p$ equations if $\theta$ is a $p \times 1$ parameter vector. From this set of first order conditions, we can solve for $\hat{\theta}$. Graphically, MLE $\hat{\theta}$ responds to a zero slope for the likelihood function.

To find a global maximum, we need to check the second order condition (SOC): If the $p \times p$ sample Hessian matrix

$$
\hat{H}(\theta)=\frac{\partial^{2} \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta \partial \theta^{\prime}}
$$

is negative definite for all $\theta \in \Theta,$ then $\hat{\theta}$ is the **global maximum**.

- In many cases, it may be difficult to verify that $\hat{H}(\theta)$ is negative definite for all $\theta \in \Theta$
- It is relatively straightforward to verify that $\hat{H}(\hat{\theta})$ is negative definite, which will imply that $\hat{\theta}$ is a **local maximizer**.

It may be emphasized that the zeros of the first derivatives only locate extreme points in the interior of the domain of a function. If the extrema occur on the boundary, the first derivative may not be zero. Thus, the boundary must be checked separately for extrema. This can be done by using the Kuhn-Tucker theorem.

**The MLE procedure:**

1. Find the log-likelihood function, $\ln \hat{L}\left(\theta | \mathbf{X}^{n}\right) .$ For an IID random sample with population PDF/PMF $f(x, \theta),$ we have $\ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)=\sum_{i=1}^{n} \ln f\left(X_{i}, \theta\right)$.
2. Solve for the FOC and find $\hat{\theta}$.
3. Check the second order conditions (SOC) to ensure $\hat{\theta}$ is a global maximizer or at least a local maximizer.

【Example (8.3)】Let $\mathbf{X}^{n}$ be an IID $N(\mu, 1)$ random sample. Find the MLE for $\mu$.

**Solution:**

Put $ \theta=\mu .$ Because $\mathbf{X}^{n}$ is an IID $N(\mu, 1)$ random sample, the likelihood function of the sample $\mathbf{X}^{n}$
$$
\begin{aligned}
\hat{L}\left(\mu | \mathbf{X}^{n}\right) &=\prod_{i=1}^{n} f\left(X_{i}, \theta\right) \\
&=\prod_{i=1}^{n} \frac{1}{\sqrt{2 \pi}} e^{-\frac{1}{2}\left(X_{i}-\mu\right)^{2}} \\
&=(2 \pi)^{-n / 2} e^{-\frac{1}{2} \Sigma_{i=1}^{n}\left(X_{i}-\mu\right)^{2}}
\end{aligned}
$$

It follows that the log-likelihood function

$$
\ln \hat{L}\left(\mu | \mathbf{X}^{n}\right)=-\frac{n}{2} \ln (2 \pi)-\frac{1}{2} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2}
$$

The FOC is given by

$$
\begin{aligned}
\frac{d \ln \hat{L}\left(\hat{\mu} | \mathbf{X}^{n}\right)}{d \mu} &\left.\equiv \frac{d \ln \hat{L}\left(\mu | \mathbf{X}^{n}\right)}{d \mu}\right|_{\mu=\hat{\mu}} \\
&=\sum_{i=1}^{n}\left(X_{i}-\hat{\mu}\right)=0
\end{aligned}
$$

This gives the sample mean estimator

$$
\hat{\mu}=\bar{X}_{n}
$$

For the SOC, we have
$$
\frac{d^{2} \ln \hat{L}\left(\mu, \mathbf{X}^{n}\right)}{d \mu^{2}}=-n<0 \text { for all } \mu
$$

It follows that $\hat{\mu}=\bar{X}_{n}$ is the global maximizer.

【Example 8.4】Suppose $\mathbf{X}^{n}$ is an IID $N\left(\mu, \sigma^{2}\right)$ random sample. Find the MLE for $\left(\mu, \sigma^{2}\right)$.

**Solution**:

Put $\theta=\left(\mu, \sigma^{2}\right) .$ Then the log-likelihood function of $\mathbf{X}^{n}$
$$
\ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)=-\frac{n}{2} \ln (2 \pi)-\frac{n}{2} \ln \sigma^{2}-\frac{1}{2 \sigma^{2}} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2}
$$

The FOC:

$$
\begin{aligned}
\frac{\partial \ln \hat{L}\left(\hat{\theta} | \mathbf{X}^{n}\right)}{\partial \mu}&=\frac{1}{2\hat{\sigma}^{2}} \sum_{i=1}^{n}\left(X_{i}-\hat{\mu}\right)=0 \\
\frac{\partial \ln \hat{L}\left(\hat{\theta} | \mathbf{X}^{n}\right)}{\partial \sigma^{2}}&=-\frac{n}{2 \hat{\sigma}^{2}}+\frac{1}{2 \hat{\sigma}^{4}} \sum_{i=1}^{n}\left(X_{i}-\hat{\mu}\right)^{2}=0
\end{aligned}
$$

where $\hat{\theta}=\left(\hat{\mu}, \hat{\sigma}^{2}\right) .$ Note that here, we treat $\sigma^{2}$ instead of $\sigma$ as a parameter.

It follows that
$$
\begin{aligned}
\hat{\mu} &=\bar{X}_{n} \\
\hat{\sigma}^{2} &=n^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2}
\end{aligned}
$$

Note that the MLE $\hat{\sigma}^{2}$ for $\sigma^{2}$ differs slightly from the sample variance $S_{n}^{2}=(n-1)^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2}$. 

To check the SOC, we compute the sample Hessian matrix
$$
\hat{H}(\theta)=\left[\begin{array}{cc}
-\frac{n}{\sigma^{2}} & -\frac{1}{\sigma^{4}} \sum_{i=1}^{n}\left(X_{i}-\mu\right) \\
-\frac{1}{\sigma^{4}} \sum_{i=1}^{n}\left(X_{i}-\mu\right) & \frac{n}{2 \sigma^{4}}-\frac{1}{\sigma^{6}} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2}
\end{array}\right]
$$

When $\theta=\hat{\theta},$ we have

$$
\hat{H}(\hat{\theta})=\left[\begin{array}{cc}
-\frac{n}{\sigma^{2}} & 0 \\
0 & -\frac{n}{2 \tilde{\sigma}^{4}}
\end{array}\right]
$$

which is negative definite. Hence, $\hat{\theta}$ is a local maximizer. Note that the $\operatorname{MLE} \hat{\theta}=$ $\left(\hat{\mu}, \hat{\sigma}^{2}\right)$ is a sufficient statistic for $\theta=\left(\mu, \sigma^{2}\right)$

**Remarks:**

Unlike example above,it is possible that the FOC can't deliver a closed form solution for $\hat{\theta}$. In this case numerical solutions for $\hat{\theta}$ will be needed.

### 8.2.3 Properties of MLE

**Question**: Suppose we treat $\sigma$ instead of $\sigma^{2}$ as a parameter. Can we obtain the same MLE solution in the above example?
The answer is yes. We will obtain
$$
\hat{\sigma}=\sqrt{\hat{\sigma}^{2}}
$$

This follows from the invariance property of MLE.

【Theorem 8.2】**Invariance Property of MLE**: Suppose $\hat{\theta}$ is the MLE of $\theta \in \Theta,$ and $g(\cdot)$ is a one-to-one function over parameter space $\Theta .$ Then $g(\hat{\theta})$ is a MLE of $g(\theta)$.

**Proof:**

Because $g(\theta)$ is a one-to-one function over $\Theta$, there exists a unique inverse function $h(\cdot)$ such that $h[g(\theta)]=\theta$ for all $\theta \in \Theta$.

Define a new parameter $\tau=g(\theta)$ and we are interested in MLE for $\tau .$ Then $\theta=h(\tau)$.

It follows that the likelihood function of the random sample $\mathbf{X}^{n}$
$$
\begin{aligned}
\hat{L}\left(\theta | \mathbf{X}^{n}\right) &=\hat{L}\left[h(\tau) | \mathbf{X}^{n}\right] \\
&=\tilde{L}\left(\tau | \mathbf{X}^{n}\right)
\end{aligned}
$$

where $\tilde{L}\left(\tau | \mathbf{X}^{n}\right)$ is the likelihood function of $\mathbf{X}^{n}$ with respect to the transformed parameter $\tau$.

Now suppose $\hat{\theta}$ is a global $\mathrm{MLE}$ of $\theta \in \Theta$. Then we have
$$
\hat{L}\left(\hat{\theta} | \mathbf{X}^{n}\right) \geq \hat{L}\left(\theta | \mathbf{X}^{n}\right) \text { for all } \theta \in \Theta
$$
Put $\hat{\tau}=g(\hat{\theta}) .$ Then $\hat{\theta}=h(\hat{\tau}),$ and for any $\theta \in \Theta$

$$
\begin{aligned}

\tilde{L}\left(\hat{\tau} | \mathbf{X}^{n}\right) 
&=\hat{L}\left[h(\hat{\tau}) | \mathbf{X}^{n}\right] \\
&= \hat{L}\left(\hat{\theta} | \mathbf{X}^{n}\right) \\
& \geq \hat{L}\left(\theta | \mathbf{X}^{n}\right)=\hat{L}\left[h(\tau) | \mathbf{X}^{n}\right]
\end{aligned}
$$

where $\tau=g(\theta) .$ It follows that

$$
\tilde{L}\left(\hat{\tau} | \mathbf{X}^{n}\right) \geq \tilde{L}\left(\tau | \mathbf{X}^{n}\right) \text { for all } \tau \in \Gamma
$$

where $\Gamma=\{\tau: \tau=g(\theta) \text { for all } \theta \in \Theta\}$ is the parameter space for the transformed parameter $\tau .$ Therefore, $\hat{\tau}$ is an MLE for $\tau$.

【Theorem 8.3】**Sufficiency of MLE**: Suppose $\mathbf{X}^{n}$ is a random sample with the likelihood function $f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right),$ and $T\left(\mathbf{X}^{n}\right)$ is a sufficient statistic for parameter $\theta \in \Theta .$ Then the MLE $\hat{\theta}$ that maximizes the likelihood function $f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)$ of the random sample $\mathbf{X}^{n}$ is also the MLE that maximizes the likelihood function $f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right]$ of the sufficient statistic $T\left(\mathbf{X}^{n}\right)$.

**Proof:**

By definition, we have $\hat{\theta}=\arg \max _{\theta \in \Theta} \ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)$

Because $T\left(\mathbf{X}^{n}\right)$ is a sufficient statistic for $\theta,$ we have
$$
\begin{aligned}
f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) &=f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right] f_{\mathbf{X}^{n} | T\left(\mathbf{X}^{n}\right)}\left[\mathbf{x}^{n} | T\left(\mathbf{x}^{n}\right)\right] \\
&=f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right] h\left(\mathbf{x}^{n}\right)
\end{aligned}
$$

where the conditional distribution $f_{\mathbf{X}^{n} | T\left(\mathbf{X}^{n}\right)}\left[\mathbf{x}^{n} | T\left(\mathbf{x}^{n}\right)\right]$ of $\mathbf{X}^{n}=\mathbf{x}^{n}$ given $T\left(\mathbf{X}^{n}\right)=T\left(\mathbf{x}^{n}\right)$ does not depend on $\theta$ and is denoted as function $h\left(\mathbf{x}^{n}\right)$.

It follows that
$$
\ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)=\ln f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right]+\ln h\left(\mathbf{x}^{n}\right)
$$

and maximizing $\ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)$ by choosing $\theta \in \Theta$ is equivalent to maximizing $\ln f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right]$ by choosing $\theta \in \Theta$. That is,
$$
\begin{aligned}
\hat{\theta} &=\arg \max _{\theta \in \Theta} \ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) \\
&=\arg \max _{\theta \in \Theta} \ln f_{T\left(\mathbf{X}^{n}\right)}\left[T\left(\mathbf{x}^{n}\right), \theta\right]
\end{aligned}
$$

## 8.3 Asymptotic Properties of MLE

Because MLE $\hat{\theta}_{n}$ is generally a highly nonlinear function of the random sample $\mathbf{X}^{n},$ it is a prohibitive task to compute the mean, variance and sampling distribution of MLE $\hat{\theta}_{n}$ for any given sample size $n,$ when the random sample $X^{n}$ is not generated from a normal population. Below, we use the asymptotic theory developed in Chapter 7 to investigate the asymptotic properties (i.e., when $n \rightarrow \infty$ ) of MLE $\hat{\theta}_{n}$. In particular, we will show that MLE $\hat{\theta}_{n}$ is consistent for the true parameter value $\theta_{0} \in \Theta$ and will converge to a normal distribution, after proper standardization.

### 8.3.1 Regularity Conditions / Assumption

【Assumption M.1】**IID**:$\mathrm{X}^{n}=\left(X_{1}, \cdots, X_{n}\right)$ is an IID random sample from some unknown population distribution $f_{X}(x)$.

【Assumption M.2】**Correct Model Specification**

1. For each $\theta \in \Theta, f(x, \theta)$ is a probability PMF/PDF model with $f(x, \theta)>0$ for all $x,$ where $\Theta$ is a finite-dimensional parameter space
2. there exists a parameter value $\theta_{0} \in \Theta$ such that $f\left(x, \theta_{0}\right)$ coincides with the population distribution $f_{X}(x)$
3. the function $\ln f(x, \theta)$ is continuous in $(x, \theta)$ and its absolute value is bounded by a nonnegative function $b(x)$ with $E\left[b\left(X_{i}\right)\right]<\infty,$ where the expectation $E(\cdot)$ is taken under the population distribution $f_{X}(x)$

【Assumption M.3】**Compact Parameter Space**: $\Theta$ is closed and bounded, or equivalently $\Theta$ is compact.

Assumption M.3 helps ensure the existence of MLE.

【Assumption M.4】**Unique Identification**: The parameter value $\theta_{0}$ is the unique maximizer of $E\left[\ln f\left(X_{i}, \theta\right)\right]$.

Assumption M.4 ensures that the true parameter value $\theta_{0}$ is the well-defined probability limit of MLE $\hat{\theta}$. It is important to note that
$$
\begin{aligned}E\left[\ln f\left(X_{i}, \theta\right)\right] &=\int_{-\infty}^{\infty} \ln f(x, \theta) f_{X}(x) d x \\& \neq \int_{-\infty}^{\infty} \ln f(x, \theta) f(x, \theta) d x\end{aligned}
$$
unless $\theta=\theta_{0}$.

**Proof:**

Jensen's inequality: If $g(\cdot)$ is concave, then $g[E(X)] \geqslant E[g(X)]$ 

Because $\ln x$ is a concave function, we have for any $\theta \in \Theta$

$$
\begin{aligned}
E\left[\ln f\left(X_{i}, \theta\right)\right]-E\left[\ln f\left(X_{i}, \theta_{0}\right)\right] &=\int_{\Omega_{X}}\left[\ln \frac{f(x, \theta)}{f\left(x, \theta_{0}\right)}\right] f\left(x, \theta_{0}\right) d x \\
& \leqslant \ln \left[\int_{\Omega_{X}} \frac{f(x, \theta)}{f\left(x, \theta_{0}\right)} f\left(x, \theta_{0}\right) d x\right] \\
&=\ln \int_{\Omega_{X}} f(x, \theta) d x \\
&=\ln 1=0
\end{aligned}
$$

Hence, $E\left[\ln f\left(X_{i}, \theta_{0}\right)\right] \geqslant E\left[\ln f\left(X_{i}, \theta\right)\right]$ for all $\theta \in \Theta$.

【Assumption M.5】**Interior Solution**: $\theta_{0}$ is in the interior of parameter space $\Theta$.

【Assumption M.6】**Smoothness and Moment Conditions**: For each interior point $\theta \in \Theta, f(x, \theta)$ is twice continuously differentiable with respect to $\theta$ such that

1. the functions $\frac{\partial}{\partial \theta} \ln f(x, \theta), \frac{\partial^{2}}{\partial \theta^{2}} \ln f(x, \theta)$ are continuous in $(x, \theta),$ and their absolute values are bounded by a nonnegative function $b(x)$ with $E\left[b\left(X_{i}\right)\right]<\infty$ and $E\left[b^{2}\left(X_{i}\right)\right]<$ $\infty$
2. the absolute value of the function $H(\theta)=E\left[\frac{\partial^{2}}{\partial \theta^{2}} \ln f\left(X_{i}, \theta\right)\right]$ is bounded by some constant and is nonzero.

Assumptions M.5 and M.6 facilitate the application of the Taylor series expansion in order to derive the asymptotic distribution of MLE $\hat{\theta}$.

- The function $\frac{\partial}{\partial \theta} \ln f(x, \theta)$ is called the score function;
- The function $H(\theta)$ is called the Hessian matrix (it is a square matrix when $\theta$ is a parameter vector).

**Remarks:**

The **scalar parameter assumption** is made for simplicity. The results obtained below can be extended to the case of a parameter vector in a straightforward manner, but it does not offer much additional insight into the asymptotic properties of MLE.

### 8.3.2 Consistency of MLE

【Lemma 8.4】**Extreme Estimator Lemma**; White (1994, Theorem 3.4): Suppose

1. $Q(\theta)$ is a nonstochastic function continuous in $\theta \in \Theta,$ and $\theta_{0} \in \Theta$ is the unique maximizer of $Q(\theta)$ over $\Theta,$ where $\Theta$ is a compact set,
2. with probability one, $\hat{Q}_{n}(\theta)$ is a sequence of random functions continuous in $\theta \in \Theta$
3. $ \lim _{n \rightarrow \infty} \sup _{\theta \in \Theta}\left|\hat{Q}_{n}(\theta)-Q(\theta)\right|=0$ almost surely.

Then $\hat{\theta}=\arg \max _{\theta \in \Theta} \hat{Q}_{n}(\theta)$ exists and $\hat{\theta} \rightarrow \theta_{0}$ a.s. $n \rightarrow \infty$.

Proof: See White (1994, Proof of Theorem 3.4).

**Remarks:**

It implies that the largest difference between $\hat{Q}_{n}(\theta)$ and $Q(\theta)$ over the parameter space $\Theta$ vanishes to zero as $n \rightarrow \infty$ almost surely.

【Theorem 8.5】**Consistency of MLE**: Suppose Assumptions **M.1-M.4** hold, and $\hat{\theta}=$ $\arg \max _{\theta \in \Theta} \sum_{i=1}^n \ln f\left(X_{i}, \theta\right) .$ Then as $n \rightarrow \infty$

$$
\hat{\theta} \rightarrow \theta_{0} \text { a.s.}
$$

**Proof:** 

We apply the extreme estimator lemma.

Given Assumption M.2, we have $Q(\theta)=E\left[\ln f\left(X_{i}, \theta\right)\right]$ is a continuous function of $\theta \in \Theta,$ and $\theta_{0}$ is the unique maximizer of $Q(\theta)$ over the compact set $\Theta$ by Assumptions M.3 and M.4.​

Now, put
$$
\begin{aligned}
\hat{Q}_{n}(\theta)&= \frac{1}{n} \ln \hat{L}(\theta | \mathbf{X}^n) \\
&=n^{-1} \ln \prod^n_{i=1} f(X_i, \theta) \\
&=n^{-1} \sum_{i=1}^{n} \ln f\left(X_{i}, \theta\right)
\end{aligned}
$$
Then, given Assumptions M.1-M.3 and USLLN in Lemma 7.10, Chapter 7, we have $\sup_{\theta \in \Theta}\left|\hat{Q}_{n}(\theta)-Q(\theta)\right| \rightarrow 0$ as $n \rightarrow \infty$ almost surely.

It follows from the extreme estimator lemma that MLE $\hat{\theta} \rightarrow \theta_{0}$ almost surely $n \rightarrow \infty$.

**Remarks:**

We do not require $\theta_{0}$ to be an interior point of parameter space $\Theta$ in establishing the consistency of MLE $\hat{\theta}$. The consistency theorem allows that $\theta_{0}$ is a corner solution (i.e., $\theta_{0}$ can be on the boundary of $\Theta$).

There is no need to assume differentiability of the log-likelihood function $\ln f(x, \theta)$ with respect to $\theta$. In fact, the FOC may fail when there exists a corner solution even if $\ln f(x, \theta)$ is differentiable with respect to $\theta$.

### 8.3.3 Asymptotic Normality

【Lemma 8.6】**Zero Expectation for Score Function**: Suppose $f(x, \theta)$ is a PDF model and $f(x, \theta)$ is continuously differentiable with respect to $\theta \in \Theta,$ where $\theta$ is an interior point in parameter space$\Theta .$ Then for all $\theta$ in the interior of $\Theta$

$$
E_{\theta}[S(x, \theta)]=\int_{-\infty}^{\infty} \frac{\partial \ln f(x, \theta)}{\partial \theta} f(x, \theta) d x=0
$$

where Score function
$$
S(X_i,\theta) = \frac{\partial \ln f(X_i, \theta)}{\partial \theta}
$$
A similar result holds for a PMF model.

**Proof:**

Given $f(x, \theta)$ is a PDF model, $f(x, \theta)$ is a PDF for any $\theta \in \Theta .$ It follows that for any $\theta$ in the interior of $\Theta$
$$
\int_{-\infty}^{\infty} f(x, \theta) d x=1
$$
Differentiating this equation and exchanging the order of integration and differentiation, we have

$$
\begin{aligned}
& \frac{d}{d \theta} \int_{-\infty}^{\infty} f(x, \theta) d x =\frac{d}{d \theta}(1)=0 \\
\implies & \int_{-\infty}^{\infty} \frac{\partial f(x, \theta)}{\partial \theta} d x =0 \\
\implies & \int_{-\infty}^{\infty}\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right] f(x, \theta) d x =0
\end{aligned}
$$

**Remarks:**

It should be noted that

$$
\begin{aligned}
& E_{\theta}\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right] \\
=& \int_{-\infty}^{\infty}\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right] f(x, \theta) d x \\
\neq & E\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right]
\end{aligned}
$$

unless $\theta=\theta_{0},$ where $E_{\theta}(\cdot)$ is the expectation with respect to the model distribution $f(x, \theta),$ while $E(\cdot)$ is the expectation with respect to the population distribution $f_{X}(x)$.

【Lemma 8.7】**Information Matrix Equality**: Suppose a PDF model $f(x, \theta)$ is twice continuously differentiable with respect to $\theta \in \Theta,$ where $\theta$ is an interior point in parameter space
$\Theta .$ Define
$$
\begin{aligned}
I(\theta) & \equiv E_{\theta}\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right]^2 =\int_{-\infty}^{\infty}\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right]^{2} f(x, \theta) d x \\
H(\theta) & \equiv E_{\theta}\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right] =\int_{-\infty}^{\infty}\left[\frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}}\right] f(x, \theta) d x
\end{aligned}
$$

Then for all $\theta$ in the interior of $\Theta$
$$
I(\theta)+H(\theta)=0
$$
A similar result holds for a PMF model.

**Proof:**

By differentiating the identity $\int_{-\infty}^{\infty} f(x, \theta) d x=1$ with respect to $\theta,$ we then obtain

$$
\int_{-\infty}^{\infty} \frac{\partial}{\partial \theta} f(x, \theta) d x=0
$$

This can be rewritten as

$$
\int_{-\infty}^{\infty} \frac{\partial \ln f(x, \theta)}{\partial \theta} f(x, \theta) d x=0
$$

If we further differentiate this equation with respect to $\theta,$ we obtain

$$
\int_{-\infty}^{\infty}\left\{\left[\frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}}\right] f(x, \theta)+\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right] \frac{\partial f(x, \theta)}{\partial \theta}\right\} d x=0
$$

or equivalently

$$
\int_{-\infty}^{\infty}\left[\frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}}\right] f(x, \theta) d x+\int_{-\infty}^{\infty}\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right]^{2} f(x, \theta) d x=0
$$

**Remarks:**

$ I(\theta) $ is called Fisher's Information Matrix, indicates average of squared slopes of likelihood function. By intuition, we can find MLE more easily when $ I(\theta) $ is larger(i.e., the likelihood function is steeper).

$ H(\theta) $ is called the Hessian matrix of the PMF/PDF model $f(x, \theta)$. This function is negative definite and its absolute value magnitude measures the average degree of the **curvature** of the likelihood function at $\theta$.

At MLE $ \hat{\theta} $, $H({\hat{\theta}})$ should be negative definite, by Information Matrix Equality, $I(\hat{\theta})$ is positive definite.

In econometrics, a well-known information matrix test (White 1982 ) checks correct specification of a parametric likelihood model $f(x, \theta)$ by testing whether the following equality holds:
$$
E\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right]^{2}+E\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right]=0
$$

where the expectation $E(\cdot)$ is taken over the population distribution $f_{X}(x)$ This equality is not the same as the information matrix equality in Lemma 8.7 (why?). It holds when the model $f(x, \theta)$ is correctly specified for the population distribution $f_{X}(x)$ but it generally does not hold when $f(x, \theta)$ is misspecified for $f_{X}(x) .$ (Please verify!)

【Theorem 8.8】**Asymptotic Normality of MLE**: Suppose Assumptions M.1-M.6 hold. Then as $n \rightarrow \infty$

$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left[0,-H\left(\theta_{0}\right)^{-1}\right]
$$

**Proof:**

Because $\hat{\theta} \rightarrow \theta_{0}$ as $n \rightarrow \infty$ almost surely, and $\theta_{0}$ is an interior point of $\Theta, \hat{\theta}$ will be also an interior point of $\Theta$ for $n$ sufficiently large with probability one.

Thus, we have the FOC:

$$
\left.\frac{d \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{d \theta}\right|_{\theta=\hat{\theta}}=0
$$

or equivalently,

$$
\frac{d}{d \theta} \sum_{i=1}^{n} \ln f\left(X_{i}, \hat{\theta}\right)=0
$$

By exchanging the differentiation and summation, we obtain

$$
g(\hat{\theta})=\frac{1}{n} \sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \hat{\theta}\right)}{\partial \theta}=0
$$

By the **mean value theorem / Taylor expansion**, 
$$
g(\hat{\theta})=g(\theta_0)+g'(\bar{\theta}) \cdot(\hat{\theta}- \theta_0)
$$
we have,
$$
\frac{1}{n} \sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta_{0}\right)}{\partial \theta}+\left[\frac{1}{n} \sum_{i=1}^{n} \frac{\partial^{2} \ln f\left(X_{i}, \bar{\theta}\right)}{\partial \theta^{2}}\right]\left(\hat{\theta}-\theta_{0}\right)=0 \quad \text{(8.1)}
$$

where $\bar{\theta}$ lies on the segment between $\hat{\theta}$ and $\theta_{0},$ that is, $\bar{\theta}=\lambda \hat{\theta}+(1-\lambda) \theta_{0}$ for some $\lambda \in(0,1) .$ Note that $\left|\bar{\theta}-\theta_{0}\right|=\left|\lambda\left(\hat{\theta}-\theta_{0}\right)\right| \leq\left|\hat{\theta}-\theta_{0}\right| \rightarrow 0$ as $n \rightarrow \infty$ almost surely.

Now, define the sample Hessian matrix
$$
\hat{H}(\theta)=\frac{1}{n} \sum_{i=1}^{n} \frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}
$$

By matrix operation from equality 8.1, we have
$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right)=[-\hat{H}(\bar{\theta})]^{-1} \frac{1}{\sqrt{n}} \sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta_{0}\right)}{\partial \theta}
$$

**Step 1**: show that the second term
$$
\frac{1}{\sqrt{n}} \sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta_{0}\right)}{\partial \theta} \stackrel{d}{\rightarrow} N\left(0, I\left(\theta_{0}\right)\right) \text { as } n \rightarrow \infty
$$

Define the score function

$$
S_{i}(\theta)=\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}, \quad i=1, \cdots, n
$$

Then $\left\{S_{i}\left(\theta_{0}\right)\right\}_{i=1}^{n}$ is an IID sequence given the IID assumption of the random sample $\mathbf{X}^{n} $. Under correct model specification in Assumption M.2 (so $ f_{X}(x)=f(x, \theta_{0}) $ ), we have

$$
\begin{aligned}
E\left[S_{i}\left(\theta_{0}\right)\right] &=\int_{-\infty}^{\infty} \frac{\partial \ln f\left(x, \theta_{0}\right)}{\partial \theta} f_{X}(x) d x \\
&=\int_{-\infty}^{\infty} \frac{\partial \ln f\left(x, \theta_{0}\right)}{\partial \theta} f\left(x, \theta_{0}\right) d x \\
&=0
\end{aligned}
$$

where the last equality follows by Lemma $8.6 .$ This is actually the FOC of max $_{\theta \in \Theta} E\left[\ln f\left(X_{i}, \theta\right)\right]$ when $\theta_{0}$ is an interior point of $\Theta$.

Furthermore, given $E\left[S_{i}\left(\theta_{0}\right)\right]=0,$ the variance
$$
\begin{aligned}
\operatorname{var}\left[S_{i}\left(\theta_{0}\right)\right] &=E\left[S_{i}\left(\theta_{0}\right)^{2}\right] \\
&=E\left[\frac{\partial \ln f\left(X_{i}, \theta_{0}\right)}{\partial \theta}\right]^{2} \\
&=\int_{-\infty}^{\infty}\left[\frac{\partial \ln f\left(x, \theta_{0}\right)}{\partial \theta}\right]^{2} f\left(x, \theta_{0}\right) d x \\
&=I\left(\theta_{0}\right)<\infty
\end{aligned}
$$
by Assumption M.6, where the third equality follows from correct model specification.

It follows from CLT for an IID sequence that as $n \rightarrow \infty$
$$
\begin{aligned}
\frac{1}{\sqrt{n}} \sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta_{0}\right)}{\partial \theta}=& \frac{1}{\sqrt{n}} \sum_{i=1}^{n} S\left(X_{i}, \theta_{0}\right) \\
& \stackrel{d}{\rightarrow} N\left(0, I\left(\theta_{0}\right)\right)
\end{aligned}
$$
Next we show $\hat{H}(\bar{\theta}) \rightarrow H\left(\theta_{0}\right)$ as $n \rightarrow \infty$ almost surely, where $H(\theta)$ is defined in Lemma 8.7

**Step 2:**

Put
$$
\begin{aligned}
\bar{H}(\theta) &=E\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right] \\
&=\int_{-\infty}^{\infty} \frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}} f_{X}(x) d x
\end{aligned}
$$

Note that $\bar{H}(\theta) \neq H(\theta)$ unless $\theta=\theta_{0},$ where $H(\theta)$ is defined as in Lemma 8.7. We write

$$
\hat{H}(\bar{\theta})-H\left(\theta_{0}\right)=[\hat{H}(\bar{\theta})-\bar{H}(\bar{\theta})]+\left[\bar{H}(\bar{\theta})-H\left(\theta_{0}\right)\right]
$$

For the second term, we have

$$
\begin{aligned}
\bar{H}(\bar{\theta})-H\left(\theta_{0}\right) &=\bar{H}(\bar{\theta})-\bar{H}\left(\theta_{0}\right) \\
& \rightarrow 0 \text { a.s. }
\end{aligned}
$$

by Lemma 7.8, the continuity of the function $\bar{H}(\theta)=E\left[\frac{\partial^{2}}{\partial \theta^{2}} \ln f\left(X_{i}, \theta\right)\right]$ given Assumption M.6, and $\bar{\theta}-\theta_{0} \rightarrow 0$ as $n \rightarrow \infty$ almost surely.

For the first term, we have

$$
\begin{array}{l}
\quad|\hat{H}(\bar{\theta})-\bar{H}(\bar{\theta})| \\
=\left|\frac{1}{n} \sum_{i=1}^{n} \frac{\partial^{2} \ln f\left(X_{i}, \bar{\theta}\right)}{\partial \theta^{2}}-\left\{E\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right]\right\}_{\theta=\bar{\theta}}\right| \\
\leq \sup _{\theta \in \Theta}\left|\frac{1}{n} \sum_{i=1}^{n} \frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}-E\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right]\right| \\
=\sup _{\theta \in \Theta}|\hat{H}(\theta)-\bar{H}(\theta)| \\
\rightarrow 0 \text { a.s. }
\end{array}
$$

as $n \rightarrow \infty$ by USLLN in Lemma 7.10 . It follows that as $n \rightarrow \infty,$ we have $\hat{H}(\bar{\theta})-$ $H\left(\theta_{0}\right) \rightarrow 0$ as $n \rightarrow \infty$ almost surely, and so

$$
\hat{H}(\bar{\theta})^{-1} \rightarrow H\left(\theta_{0}\right)^{-1} \text {a.s. }
$$

given that $H\left(\theta_{0}\right)$ is not zero.

It follows from Slutsky's theorem that as $n \rightarrow \infty$
$$
\begin{aligned}
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right)=&[-\hat{H}(\bar{\theta})]^{-1} \frac{1}{\sqrt{n}} \sum_{i=1}^{n} S\left(X_{i}, \theta_{0}\right) \\
& \stackrel{d}{\rightarrow} N\left(0, H\left(\theta_{0}\right)^{-1} I\left(\theta_{0}\right) H\left(\theta_{0}\right)^{-1}\right)
\end{aligned}
$$
since $I\left(\theta_{0}\right)=-H\left(\theta_{0}\right)$ by Lemma 8.7 (the IM equality), we have

$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0,-H\left(\theta_{0}\right)^{-1}\right)
$$

**Remarks:**

The function
$$
H(\theta) \equiv E_{\theta}\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right]=\int_{-\infty}^{\infty} \frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}} f(x, \theta) d x
$$

is called the Hessian matrix of the PMF/PDF model $f(x, \theta)$, where the expectation $E_{\theta}(\cdot)$ is taken under the PDF model $f(x, \theta)$. This function is negative definite and its absolute value magnitude measures the degree of the curvature(曲率) of the likelihood function at $\theta .$ 

Thus, the efficiency of the MLE estimator $\hat{\theta}_{n}$ depends on the curvature of the likelihood function at the true parameter value $\theta_{0} .$ 

- If the degree of the curvature of the log-likelihood function is large so that the likelihood function has a sharp peak, it will be easy to estimate $\theta_{0}$ precisely. 
- On the other hand, if the degree of the curvature is small so that the likelihood function is flat, it will be difficult to estimate $\theta_{0}$ precisely. 

Figure 8.3 below plots the population likelihood function $E\left[\ln f\left(X_{i}, \theta\right)\right]$ for the cases where there is a sharp peak and there is a flat peak for $E\left[\ln f\left(X_{i}, \theta\right)\right]$ at the true parameter value $\theta_{0}$ respectively:

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200524211347.png)

The asymptotic normality $\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0,-H\left(\theta_{0}\right)^{-1}\right)$ implies that the asymptotic mean of $\sqrt{n}\left(\hat{\theta}-\theta_{0}\right)$ is zero, and the asymptotic variance of $\sqrt{n}\left(\hat{\theta}-\theta_{0}\right)$ is equal to $-H\left(\theta_{0}\right)^{-1}$.

$-\hat{H}\left(\hat{\theta}\right)^{-1}$ can be used as asymptotic variance estimator.

**Question:** Why is the asymptotic normality result for MLE useful in practice?

It can be used to construct confidence interval estimators and hypothesis test statistics, among other things.

For example, an asymptotic $100(1-\alpha) \%$ confidence interval estimator for $\theta_{0}$ is given by a random interval $\left[\theta_{L}, \theta_{U}\right],$ where $\theta_{L}=\theta_{L}\left(\mathbf{X}^{n}\right)$ and $\theta_{U}=\theta_{U}\left(\mathbf{X}^{n}\right),$ such that

$$
\lim _{n \rightarrow \infty} P\left(\theta_{L} \leq \theta_{0} \leq \theta_{U}\right)=1-\alpha
$$

Given $\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0,-H\left(\theta_{0}\right)^{-1}\right)$ and $\hat{H}(\hat{\theta}) \rightarrow H\left(\theta_{0}\right)$ as $n \rightarrow \infty$ almost surely, we
have
$$
\sqrt{-n \hat{H}(\hat{\theta})}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N(0,1)
$$

by Slutsky's theorem. Therefore, as $n \rightarrow \infty$

$$
P\left[-z_{\alpha / 2} \leq \sqrt{-n \hat{H}(\hat{\theta})}\left(\hat{\theta}-\theta_{0}\right) \leq z_{\alpha / 2}\right] \rightarrow 1-\alpha
$$

where $z_{\alpha / 2}$ is the upper-tailed $\mathrm{N}(0,1)$ critical value at level $\alpha / 2,$ namely

$$
P\left(Z \geq z_{\alpha / 2}\right)=\frac{\alpha}{2}
$$

where $Z \sim N(0,1)$.

This can be equivalently written as
$$
P\left[\hat{\theta}-\frac{z_{\alpha / 2}}{\sqrt{n}} \sqrt{\frac{1}{-\hat{H}(\hat{\theta})}} \leq \theta_{0} \leq \hat{\theta}+\frac{z_{\alpha / 2}}{\sqrt{n}} \sqrt{\frac{1}{-\hat{H}(\hat{\theta})}}\right] \rightarrow 1-\alpha
$$

as $n \rightarrow \infty$.

We then obtain the asymptotic $(1-\alpha) 100 \%$ confidence interval as follows:
$$
\theta-\sqrt{-\frac{1}{n H(\theta)}} z_{\frac{a}{2}} \leq \theta_{0} \leq \theta+\sqrt{-\frac{1}{n H(\theta)}} z_{\frac{a}{2}}
$$

where $z_{\alpha / 2}$ is the upper-tailed critical value of $N(0,1)$ at level $\frac{\alpha}{2}$.

## 8.4 Method of Moments and Generalized Method of Moments

### 8.4.1 Method of Moments Estimation

Suppose $f(x, \theta),$ where $\theta \in \Theta,$ is a parametric PMF/ PDF model for the unknown population distribution $f_{X}(x)$ and $f_{X}(x)=f\left(x, \theta_{0}\right)$ for some parameter value $\theta_{0} \in \Theta$. This implies that the parametric probability model $f(x, \theta)$ is correctly specified for the population distribution $f_{X}(x)$.

Suppose $\mathrm{X}^{n}$ is an IID random sample from the population distribution $f_{X}(x)$.

【sample moment】We first define a $q \times 1$ statistic vector
$$
\hat{m}=\frac{1}{n} \sum_{i=1}^{n} m\left(\mathbf{X}^{n}\right)
$$

which will converge in probability to $E\left[m\left(\mathbf{X}^{n}\right)\right]$ where $E(\cdot)$ is under the unknown true joint distribution of $\mathrm{X}^{n}$.

【Population moment】Next, we compute its mathematical expectation under the **model distribution**:

$$
\begin{aligned}
M(\theta) &=E_{\theta}\left[m\left(\mathbf{X}^{n}\right)\right] \\
&=\int_{\mathbb{R}^{n}} m\left(\mathbf{x}^{n}\right) f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n}
\end{aligned}
$$

where the mathematical expectation $E_{\theta}(\cdot)$ is taken under the joint distribution $f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)$ of $\mathbf{X}^{n},$ where $f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)=\Pi_{i=1}^{n} f\left(x_{i}, \theta\right)$ when $\mathbf{X}^{n}$ is an IID random sample

【Moment matching】Then we solve the system of $q$ equations
$$
\hat{m}=M(\hat{\theta})
$$

That is, we choose a parameter value $\hat{\theta}=\hat{\theta}_{n}\left(\mathrm{X}^{n}\right)$ to match the sample moment $\hat{m}$ with the population moment $M(\theta)$.

The solution $\hat{\theta}$ is called the **method of moments estimator (MME)** for the true parameter value $\theta_{0}$.

Alternatively, we can define a vector-valued sample moment function

$$
\hat{m}(\theta)=m\left(\mathbf{X}^{n}\right)-M(\theta), \quad \theta \in \Theta
$$

The method of moments estimator $\hat{\theta}$ is the solution of the equations

$$
\hat{m}(\theta)=0
$$
【MME Procedure】Often, when $\mathbf{X}^{n}$ is an IID random sample from population $f_{X}(x)=$ $f\left(x, \theta_{0}\right)$ for some parameter value $\theta_{0},$ we have the following procedures:

1) Compute population moments $E_{\theta}\left(X_{i}^{k}\right), k=1,2, \cdots,$ under the PMF/PDF model $f(x, \theta)$
$$
\begin{aligned}
M_{k}(\theta) &=E_{\theta}\left(X_{i}^{k}\right) \\
&=\left\{\begin{array}{ll}
\sum_{x \in \Omega_{X}} x^{k} f(x, \theta) & \text { if } X \text { is a DRV } \\
\int_{-\infty}^{\infty} x^{k} f(x, \theta) d x & \text { if } X \text { is a CRV }
\end{array}\right.
\end{aligned}
$$

Note that the population moment $M_{k}(\theta)$ depends on parameter $\theta$.

2) Compute the sample moments from random sample $\mathbf{X}^{n}=\left(X_{1}, \cdots, X_{n}\right)$
$$
\hat{m}_{k}=n^{-1} \sum_{i=1}^{n} X_{i}^{k}, \quad k=1,2, \cdots
$$

3) For each $n,$ match the sample moments and the population moments by choosing some parameter value $\hat{\theta}$. In general, if $\theta$ is a $p \times 1$ parameter vector, we need $p$ equations:
$$
\left\{\begin{array}{l}
\hat{m}_{1}=M_{1}(\hat{\theta}) \\
\hat{m}_{2}=M_{2}(\hat{\theta}) \\
\qquad \dots \\
\hat{m}_{p}=M_{p}(\hat{\theta})
\end{array}\right.
$$

Solving for these $p$ equations will yield MME $\hat{\theta}=\hat{\theta}_{n}\left(\mathbf{X}^{n}\right)$

【Consistency of MME】MME $\hat{\theta}$ **consistently** estimate the true parameter value $\theta_{0} $.

**Proof:**

By WLLN, the sample moment

$$
\begin{aligned}
\hat{m}_{k} = \frac{1}{n} \sum^n_{i=1} X_i^k\stackrel{p}{\rightarrow} E\left(X_{i}^{k}\right) &=\int_{-\infty}^{\infty} x^{k} f_{X}(x) d x \\
&=\int_{-\infty}^{\infty} x^{k} f\left(x, \theta_{0}\right) d x \\
&=M_{k}\left(\theta_{0}\right)
\end{aligned}
$$

where the second equality follows by correct model specification.

If we set

$$
\hat{m}_{k}=M_{k}(\hat{\theta}) \text { for any } n
$$

we will have

$$
\hat{m}_{k} =M_{k}(\hat{\theta}) \stackrel{p}{\rightarrow} M_{k}\left(\theta_{0}\right) \text { as } n \rightarrow \infty
$$

By continuous mapping theorem, we expect that $\hat{\theta}$ will converge in probability to $\theta_{0}$ as $n \rightarrow \infty$.

**Remarks:**

Although the population moment function $ M_{k}(\theta) $ is calculated using the population distribution model $ f(x, \theta)$,  MME only uses a finite number of sample moments, which may not capture all information about $ \theta $ that is contained in the random sample $ \mathbf{X}^{n} $ (this occurs when the sample moments used are not sufficient statistics for $ \theta $ ). As a result, it may not be a most efficient estimator of $ \theta $.

In contrast, MLE captures all information about $ \theta $ that is contained in $ \mathbf{X}^{n} $ because it uses the entire joint  PMF/ PDF of the random sample $ \mathrm{X}^{n} $.

Therefore, MME may not be as efficient as MLE, unless the sample moments used are sufficient statistics for the parameters of interest.

But sometimes, population distribution is unknown, or distribution is known but PMF/ PDF is unknown (some distribution's PMF/ PDF can't be expressed). In these situation, MLE is unavailable, MME can be used to do estimation.

【Example 8.5】Suppose $\mathbf{X}^{n}$ is an IID $E X P(\theta)$ random sample. Find an estimator for $\theta$ using MME​ and MLE, respectively.

**Solution:**

1) MME: Because the exponential PDF
$$
f(x, \theta)=\left\{\begin{array}{cl}
\frac{1}{\theta} e^{-x / \theta}, & \text { if } x>0 \\
0, & \text { if } x \leq 0
\end{array}\right.
$$

it can be shown that

$$
\begin{aligned}
M_{1}(\theta) &=E_{\theta}\left(X_{i}\right) \\
&=\int_{-\infty}^{\infty} x f(x, \theta) d x \\
&=\int_{0}^{\infty} x \frac{1}{\theta} e^{-x / \theta} d x \\
&=\theta
\end{aligned}
$$

On the other hand, the first sample moment is the sample mean:

$$
\hat{m}_{1}=\bar{X}_{n}
$$

Moment matching yields

$$
\hat{m}_{1}=M_{1}(\hat{\theta})=\hat{\theta}
$$

We then obtain MME

$$
\hat{\theta}=\hat{m}_{1}=\bar{X}_{n}
$$

2) MLE: Given the IID $\operatorname{EXP}(\theta)$ assumption, the likelihood function of $\mathbf{X}^{n}$
$$
\begin{aligned}
\hat{L}\left(\theta | \mathbf{X}^{n}\right) &=\prod_{i=1}^{n} f\left(X_{i}, \theta\right) \\
&=\left(\frac{1}{\theta}\right)^{n} e^{-\frac{1}{\theta} \Sigma_{i=1}^{n} X_{i}}
\end{aligned}
$$

Therefore, the log-likelihood function is

$$
\ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)=-n \ln \theta-\frac{1}{\theta} \sum_{i=1}^{n} X_{i}
$$

The FOC:

$$
\frac{\partial \ln \hat{L}\left(\hat{\theta} | \mathbf{X}^{n}\right)}{\partial \theta}=-\frac{n}{\hat{\theta}}+\frac{1}{\hat{\theta}} \sum_{i=1}^{n} X_{i}=0
$$

It follows that MLE

$$
\hat{\theta}=\bar{X}_{n}
$$

Both MME and MLE give the same estimator in this example. Therefore, they are equally efficient in estimating $\theta_{0} .$ The reason that MME is as efficient as MLE is that the sample mean or the first sample moment $\bar{X}_{n}$ is a sufficient statistic for $\theta$

【Example 8.6】Suppose $\mathbf{X}^{n}$ is an IID $N\left(\mu, \sigma^{2}\right)$ random sample. Find MME for $\theta=\left(\mu, \sigma^{2}\right)$.

**Solution:**

The first two population and sample moments are given respectively:

$$
\begin{aligned}
M_{1}(\theta) &=E_{\theta}\left(X_{i}\right)=\mu \\
M_{2}(\theta) &=E_{\theta}\left(X_{i}^{2}\right)=\sigma^{2}+\mu^{2} \\
\hat{m}_{1} &=\bar{X}_{n} \\
\hat{m}_{2} &=n^{-1} \sum_{i=1}^{n} X_{i}^{2}
\end{aligned}
$$

We match the first two sample moments with their population counterparts respectively:

$$
\begin{aligned}
\bar{X}_{n} &=\hat{\mu} \\
n^{-1} \sum_{i=1}^{n} X_{i}^{2} &=\hat{\sigma}^{2}+\hat{\mu}^{2}
\end{aligned}
$$


It follows that

$$
\begin{aligned} 
\hat { \mu } & = \bar { X } _ { n } 
\\ \hat { \sigma } ^ { 2 } = & n ^ { - 1 } \sum _ { i = 1 } ^ { n } \left( X _ { i } - \bar { X } _ { n } \right) ^ { 2 } 
\end{aligned}
$$

These MME are the same as MLE. Again, this is due to the fact that $ \left( \bar { X } _ { n } , S _ { n } ^ { 2 } \right) $ is a sufficient statistic for $ \theta = \left( \mu , \sigma ^ { 2 } \right) $ for the normal random sample $ \mathbf { X } ^ { n } $.

### 8.4.2 Generalized Method of Moments Estimation

Often in econometrics, the population moment function $ M ( \theta ) = E _ { \theta } \left[ m \left( X ^ { n } \right) \right] $ is not attainable, due to the fact that the population distribution of an economic process is usually not specified.

However, economic and financial theory often implies that certain moment conditions must hold when evaluated at the true parameter value $ \theta _ { 0 } . $ In other words, economic theories or hypotheses are often characterized by a set of moment conditions.

Specifically, suppose $ \theta $ is a $ p \times 1 $ parameter vector, and there exists a $ p \times 1 $ moment function $ m ( X , \theta ) $ such that
$$
 E \left[ m \left( X , \theta _ { 0 } \right) \right] = 0 \text { for some } \theta _ { 0 } \in \Theta 
$$
where the expectation is taken over the unknown true distribution of $X$: This may follow from economic theory (e.g., the equilibrium condition in a rational expectations model).

【Example 8.7】An investor who maximizes an intertemporal utility function

$$
\max _{\left\{C_{t}\right\}} U\left(C_{t}, C_{t+1}\right)=u\left(C_{t}\right)+\beta E\left[u\left(C_{t+1}\right) | I_{t}\right]
$$

subject to an inter-temporal budget constraint will choose a sequence of consumptions $ \left\{C_{t}\right\} $ that satisfies the first order condition

$$
P_{t}=\beta E\left[\frac{u^{\prime}\left(C_{t+1}\right)}{u^{\prime}\left(C_{t}\right)} Y_{t+1} | I_{t}\right]
$$

where $ \beta $ is a time discount factor parameter, $ Y_{t+1} $ is the random payoff of an asset at time $ t+1 $ and $ P_{t} $ is the price of the asset at time $ t $, and $ E_{t}(\cdot)=E\left(\cdot | I_{t}\right) $ is the conditional expectation given the information set $ I_{t} $ available at time $t$. The FOC is also called the Euler equation. 

It states that in the equilibrium, the current asset price should be equal to the expected future payoff of the asset after risk compensation. Here, the factor $ \beta \frac{u^{\prime}\left(C_{t+1}\right)}{u^{\prime}\left(C_{t}\right)} $ is called the stochastic discount factor;

it charcterizes the risk attitude of the representative economic agent. Define the stochastic pricing error

$$
\varepsilon_{t+1}(\theta)=\beta \frac{u^{\prime}\left(C_{t+1}\right)}{u^{\prime}\left(C_{t}\right)} Y_{t+1}-P_{t}
$$

where parameter $ \theta $ contains time discount factor $ \beta $ and any other structral parameters. The Euler equation can be equivalently characterized by the following conditional moment condition:

$$
E\left[\varepsilon_{t+1}\left(\theta_{0}\right) | I_{t}\right]=0
$$

This implies that a rational economic agent does not make any systematic pricing error in each time period.

Now define a moment function
$$
m\left(X_{t+1}, \theta\right)=\left[\beta \frac{u^{\prime}\left(C_{t+1}\right)}{u^{\prime}\left(C_{t}\right)} Y_{t+1}-P_{t}\right] Z_{t}
$$
where $ X_{t+1}=\left(C_{t}, C_{t+1}, P_{t}, Y_{t+1}, Z_{t}^{\prime}\right)^{\prime} $ and $ Z_{t} \in I_{t} $ is the vector of so-called instrumental variables available to the economic agent at time $t$. Then by the law of iterated expectations, we have
$$
\begin{aligned}
E\left[m\left(X_{t+1}, \theta_{0}\right)\right] &=E\left\{E\left[m\left(X_{t+1}, \theta_{0}\right) | I_{t}\right]\right\} \\
&=0
\end{aligned}
$$
where $ E(\cdot) $ is the unconditional expectation under the unknown population distribution.

Question: In this example, where does parameter $ \theta $ come from?

Besides the time discount parameter $ \beta, $ some parameter(s) may arise from the utility function to characterize risk aversion of the economic agent.

For example, when the economic agent has a constant relative risk aversion utility function
$$
u\left(C_{t}\right)=\frac{C_{t}^{\gamma}-1}{\gamma}
$$
the parameter
$$
\gamma=-C_{t} \frac{u^{\prime \prime}\left(C_{t}\right)}{u^{\prime}\left(C_{t}\right)}
$$
measures the degree of risk aversion of the economic agent. In this case, $ \theta=(\beta, \gamma)^{\prime} $.

【Example 8.8】**Capital Asset Pricing Model CAPM**: Define $ Y_{t} $ as an $ l \times 1 $ vector of excess returns for $ l $ assets (or portfolios of assets) in period $t$. For these $l$ assets, the excess returns can be described using the excess-return market model:
$$
\begin{aligned}
Y_{t} &=\alpha_{0}+\beta_{1} R_{m t}+\varepsilon_{t} \\
&=\theta_{0}^{\prime} W_{t}^{\prime}+\varepsilon_{t}
\end{aligned}
$$
where $ W_{t}=\left(1, R_{m t}\right)^{\prime} $ is a bivariate vector, $ R_{m t} $ is the excess market portfolio return, $ \theta_{0} $ is a $ 2 \times l $ parameter matrix, and $ \varepsilon_{t} $ is an $ l \times 1 $ disturbance representing the idiosyncratic risk, with
$ E\left(\varepsilon_{t} | W_{t}\right)=0 $.

Put $ X_{t}=\left(Y_{t}, W_{t}^{\prime}\right)^{\prime} . $ Define the $ q \times 1 $ moment function
$$
m\left(X_{t}, \theta\right)=W_{t} \otimes\left(Y_{t}-\theta^{\prime} W_{t}\right)
$$
where $ q=2 l $ and $ \otimes $ denotes the Kronecker product. When CAPM holds, we have
$$
E\left[m\left(X_{t}, \theta_{0}\right)\right]=0
$$
These $ q \times 1 $ moment conditions form a basis to estimate and test CAPM.

#### Basic Idea

Suppose we are given $ q $ population moment conditions:
$$
E\left[m\left(X_{i}, \theta_{0}\right)\right]=0
$$
where $ m\left(X_{i}, \theta\right) $ is a $ q \times 1 $ random vector, $ \theta_{0} $ is a $ p \times 1 $ true parameter vector, $ E(\cdot) $ is taken over the unknown population distribution of $ X_{i}, $ and 0 is a $ q \times 1 $ zero vector.

We could estimate $ \theta_{0} $ by finding an estimator $ \hat{\theta} $ which matches the sample moment to the population moment $ E\left[m\left(X_{i}, \theta_{0}\right)\right]=0 $
$$
\hat{m}(\hat{\theta})=n^{-1} \sum_{i=1}^{n} m\left(X_{i}, \hat{\theta}\right)=0
$$
In practice, we can use $ q $ moment conditions, where $ q \geq p, $ namely the number of moment conditions is larger than or at least equal to the number of unknown parameters. 

In this case, it is generally impossible to find a solution that satisfies the equation $ \hat{m}(\theta)=0 $ exactly. We can choose an estimator $ \hat{\theta} $ to make $ \hat{m}(\theta) $ as close to a zero vector as possible. More specifically, we observe the estimator that solves the following minimization problem
$$
\hat{\theta}=\arg \min _{\theta \in \Theta} \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)
$$

where $ \hat{W} $ is a $ q \times q $ random nonsingular symmetric matrix such that $ \hat{W} \stackrel{p}{\rightarrow} W $ as $ n \rightarrow \infty, $ and $ W $ is a $ q \times q $ nonstochastic, nonsingular and symmetric matrix. 

One can choose $ \hat{W}=I, $ a $ q \times q $ identity matrix, which yields a convenient procedure. In this case, the objective function
$$
\hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)=\sum_{k=1}^{q} \hat{m}_{k}^{2}(\theta)
$$
where each component is equally weighted. **The classical MME is a special case of the GMM estimation with $ q=p $ and $ \hat{W}=I $**.

There may exist some optimal choice of the weighting matrix $ \hat{W} $ which can give an asymptotically most efficient estimator within a class of estimators, at least asymptotically. Intuitively, the $ q $ components in the sample moment vector $ \hat{m}(\theta) $ may have different sampling variabilities and may be correlated with each other as well. If the **weighting matrix $ \hat{W} $ can downweight the components with larger variances** and eliminate their correlations, the resulting estimator will be efficient.

The resulting estimator $ \hat{\theta} $ is called the **generalized method of moments (GMM)** estimator. It is also called the minimum chi-square estimator in the statistical literature, because the minimized objective function $ n \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta) $ follows an asymptotic $ \chi^{2} $ distribution with a suitable choice of $ \hat{W} $.

Most often, GMM estimation is used in connection with instrumental variables $ Z_{t} $ which define the vector-valued moment function $ m\left(X_{i}, \theta\right) $.

【Theorem 8.9】**Existence of a GMM Estimator**: Suppose that with probability one, the quadratic form $ \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta) $ is continuous in $ \theta \in \Theta, $ and that $ \Theta $ is a compact set. Then there exists a global minimizer $ \hat{\theta} $ that solves the minimization problem
$$
\hat{\theta}=\arg \min _{\theta \in \Theta} \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)
$$
**Remarks:**

Most economic theories can be characterized by a set of moment conditions or conditional moment conditions. Thus, GMM has been rather popularly used in econometrics.

For the reason analogous to that for MME, GMM may be less efficient than MLE if MLE assumes the correct functional form of the population distribution $ f(x, \theta) $.

## 8.5 Asymptotic Properties of GMM

### 8.5.1 Regularity Conditions/ Assumption 

【Assumption G.1】**IID**: $ \mathrm{X}^{n}=\left(X_{1}, \cdots, X_{n}\right) $ is an IID random sample from some unknown population distribution $ f_{X}(x) $.

【Assumption G.2】**Moment Function**: The $ q \times 1 $ moment function $ m(x, \theta) $ is continuous in $ (x, \theta) $ and the absolute values of its components are bounded by a nonnegative function $ b(x) $ with $ E\left[b\left(X_{i}\right)\right]<\infty, $ where the expectation $ E(\cdot) $ is taken under the unknown population distribution $ f_{X}(x) $
$$
\sup_{\theta \in \Theta}|m_k(X_i, \theta)| \leq b(X_i)
$$
which will be used as condition for USLLN.

【Assumption G.3】**Unique Identification**: There exists one and only one $ p \times 1 $ parameter value $ \theta_{0} $ in $ \Theta $ such that $ E\left[m\left(X_{i}, \theta_{0}\right)\right]=0 $.

Assumption G. 3 is an identification condition for $ \theta_{0}, $ which is called the true parameter value of the model characterized by the population moment condition $ E\left[m\left(X_{i}, \theta_{0}\right)\right]= 0$.

The identification condition ensures that $ \theta_{0} $ is the unique probability limit of the GMM estimator $ \hat{\theta} $.

【Assumption G.4】**Compact Parameter Space**: The $ p $-dimensional parameter space $ \Theta $ is closed and bounded.

【Assumption G.5】**Weighting**: The $ q \times q $ stochastic weighting matrix $ \hat{W} \rightarrow W $ as $ n \rightarrow \infty $ almost surely, where $ W $ is symmetric, bounded and nonsingular.

【Assumption G.6】**Interior Solution**: The parameter value $ \theta_{0} $ is an interior point of the parameter space $ \Theta $.

The interior solution assumption for $ \theta_{0} $ is not needed for the consistency of the GMM estimator $ \hat{\theta}, $ but is needed when we derive the asymptotic normality of the GMM estimator $ \hat{\theta}, $ where we will use a Taylor series expansion of the FOC of the GMM estimation.

【Assumption G.7】**Smoothness and Moment Conditions**:

1. The functions/ matrix $ \frac{\partial}{\partial \theta} m(x, \theta) $ and $ \frac{\partial^{2}}{\partial \theta \partial \theta^{\prime}} m(x, \theta) $ are continuous in $ (x, \theta) $ and the absolute values of their component functions are bounded by a nonnegative function $ b(x) $ with $ E\left[b\left(X_{i}\right)\right]<\infty $.
2. The $ q \times q $ symmetric matrix $ V=E\left[m\left(X_{i}, \theta_{0}\right) m\left(X_{i}, \theta_{0}\right)^{\prime}\right] $ is bounded and nonsingular;
3. The $ q \times p $ gradient matrix $ G\left(\theta_{0}\right)=E\left[\frac{\partial}{\partial \theta} m\left(X_{i}, \theta_{0}\right)\right] $ is of full rank (equal to $ p $ given $ p \leq q) $

With assumption G.3 $ E\left[m\left(X_{i}, \theta_{0}\right)\right]= 0$,we have
$$
\begin{aligned}
 V&=E\left[m\left(X_{i}, \theta_{0}\right) m\left(X_{i}, \theta_{0}\right)^{\prime}\right]\\
 &=Var [m(X_i, \theta_0)] \\
\end{aligned}
$$
i.e., $V$ is variance-covariance matrix of $m(X_i, \theta)$.

### 8.5.2 Consistency of GMM

【Theorem 8.10】**Consistency of GMM**: Suppose Assumptions G.1-G.5 hold. Then as $ n \rightarrow \infty $
$$
\hat{\theta} \rightarrow \theta_{0} \text { a.s.}
$$
**Proof:** 

The proof is similar to the consistency proof of the MLE. 

We apply the Lemma 8.4 (Extreme Estimator Lemma).

Suppose 
$$
\begin{aligned}
Q(\theta) &= -[Em(X_i,\theta)]'W^{-1}[Em(X_i,\theta)] \\
\hat{Q}(\theta) &= - \hat{m}(\theta)'\hat{W}^{-1} \hat{m}(\theta)
\end{aligned}
$$
where $\hat{m}(\theta) = n^{-1} \sum^n_{i=1} m(X_i,\theta)$.

With Assumption G.3 (unique identification), $\theta_0$ is the unique maximizer of $Q(\theta)$. While in GMM
$$
\begin{aligned}
\hat{\theta}&=\arg \min _{\theta \in \Theta} \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)\\
&=\arg \max _{\theta \in \Theta}- \hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)
\end{aligned}
$$
Under assumption G.1, G.2 and G.4, by USLLN, we have
$$
\sup_{\theta \in  \Theta} |\hat{m}(\theta)-Em(X_i,\theta)| \stackrel{a.s.}{\rightarrow} 0
$$
By continuity, 
$$
\sup_{\theta \in  \Theta} |\hat{Q}(\theta)-Q(\theta)| \stackrel{a.s.}{\rightarrow} 0
$$
With, lemma 8.4
$$
\hat{\theta}\stackrel{a.s.}{\rightarrow} \theta 
$$
Note that $ \theta_{0} $ could be a corner solution so that the FOC may not hold.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200601115151.png)

### 8.5.3 Asymptotic Normality

【Theorem 8.11】**Asymptotic Normality**: Suppose Assumptions G.1-G.7 hold. Then

1) **Asymptotic Normality**: as $ n \rightarrow \infty $,
$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N(0, \Omega)
$$
where
$$
\begin{array}{c}
\Omega=\Psi V \Psi^{\prime} 
\end{array}
$$

$V=E\left[m\left(X_{1}, \theta_{0}\right) m\left(X_{1}, \theta_{0}\right)^{\prime}\right]$, and $ \Psi=\left[G\left(\theta_{0}\right) W^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} G\left(\theta_{0}\right) W^{-1}$, and $ G\left(\theta_{0}\right)=E\left[\frac{\partial}{\partial \theta} m\left(X_{i}, \theta_{0}\right)\right] $

2) **Optimal Weighting Matrix**: Moreover, if $ W=V $, then as $ n \rightarrow \infty $,
$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0,\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1}\right)
$$
**Proof:**

1) Define the objective function
$$
\hat{Q}_{n}(\theta)=\hat{m}(\theta)^{\prime} \hat{W}^{-1} \hat{m}(\theta)
$$
Noting that the prespecified weighting matrix $ \hat{W} $ is not a function of $ \theta $. With assumption G.6 (Interior Solution) and $ \hat{\theta}\stackrel{a.s.}{\rightarrow} \theta $, we can obtain the FOC as follows:
$$
\frac{d \hat{Q}_{n}(\hat{\theta})}{d \theta}=2 \hat{G}(\hat{\theta}) \hat{W}^{-1} \hat{m}(\hat{\theta})=0
$$
where the $ p \times q $ sample matrix
$$
\begin{aligned}
\hat{G}(\theta) &=\frac{d \hat{m}(\theta)}{d \theta^{\prime}} \\
&=\frac{1}{n} \sum_{i=1}^{n} \frac{\partial m\left(X_{i}, \theta\right)}{\partial \theta^{\prime}}
\end{aligned}
$$

By the mean value theorem/ 中值定理, we have
$$
\hat{m}(\hat{\theta})=\hat{m}\left(\theta_{0}\right)+\hat{G}(\bar{\theta})^{\prime}\left(\hat{\theta}-\theta_{0}\right)
$$
where $ \bar{\theta} $ lies on the segment between $ \hat{\theta} $ and $ \theta_{0}, $ i.e., $ \bar{\theta}=\lambda \hat{\theta}+(1-\lambda) \theta_{0} $ for some $ \lambda \in[0,1] $.

Substituting this expression into the FOC, we obtain
$$
\hat{G}(\hat{\theta}) \hat{W}^{-1} \hat{m}\left(\theta_{0}\right)+\hat{G}(\hat{\theta}) \hat{W}^{-1} \hat{G}(\bar{\theta})^{\prime}\left(\hat{\theta}-\theta_{0}\right)=0
$$
Following the reasoning similar to that for the sample Hessian matrix $ \hat{H}(\bar{\theta}) $ in the proof for the asymptotic normality of the MLE, we can show that as $ n \rightarrow \infty $
$$
\begin{array}{l}
\hat{G}(\hat{\theta}) \rightarrow G\left(\theta_{0}\right) \text { a.s. } \\
\hat{G}(\bar{\theta}) \rightarrow G\left(\theta_{0}\right) \text { a.s. }
\end{array}
$$
First, We write

$$
\hat{G}(\hat{\theta})-G\left(\theta_{0}\right)=[\hat{G}(\hat{\theta})-G(\hat{\theta})]+\left[G(\hat{\theta})-G\left(\theta_{0}\right)\right]
$$

For the second term, we have

$$
G(\hat{\theta})-G\left(\theta_{0}\right) \rightarrow 0 \text { a.s. }
$$

by Lemma 7.8, the continuity of the function $ G\left(\theta\right)=E\left[\frac{\partial}{\partial \theta} m\left(X_{i}, \theta\right)\right] $ given Assumption G.7, and $\bar{\theta}-\theta_{0} \rightarrow 0$ as $n \rightarrow \infty$ almost surely.

For the first term, we have
$$
\begin{array}{l}
\quad|\hat{G}(\hat{\theta})-G(\hat{\theta})| \\
=\left|\frac{1}{n} \sum_{i=1}^{n} \frac{\partial m\left(X_{i}, \hat{\theta}\right)}{\partial \theta}-\left\{E\left[\frac{\partial m\left(X_{i}, \theta\right)}{\partial \theta}\right]\right\}_{\theta=\hat{\theta}}\right| \\
\leq \sup _{\theta \in \Theta}\left|\frac{1}{n} \sum_{i=1}^{n} \frac{\partial m \left(X_{i}, \theta\right)}{\partial \theta}-E\left[\frac{\partial m \left(X_{i}, \theta\right)}{\partial \theta}\right]\right| \\
\rightarrow 0 \text { a.s. }
\end{array}
$$

as $n \rightarrow \infty$ by USLLN in Lemma 7.10 . It follows that as $n \rightarrow \infty,$ we have $ \hat{G}(\hat{\theta}) \rightarrow G\left(\theta_{0}\right) $ as $n \rightarrow \infty$ almost surely, and so

$$
\hat{G}(\bar{\theta})-G\left(\theta_{0}\right)=[\hat{G}(\bar{\theta})-\hat{G}(\hat{\theta})]+\left[\hat{G}(\hat{\theta})-G\left(\theta_{0}\right)\right]\rightarrow 0 \text { a.s. }
$$
where $ \hat{G}(\bar{\theta})-\hat{G}(\hat{\theta}) \rightarrow 0 \text { a.s. }$by continuity of $ \hat{G}(\cdot) $.

using USLLN, continuity of the gradient function $ G(\theta)=E\left[\frac{\partial}{\partial \theta} m\left(X_{i}, \theta\right)\right], $ and $ \| \bar{\theta}- $ $ \theta_{0}\|\leq\| \hat{\theta}-\theta_{0} \| \rightarrow 0 $ as $ n \rightarrow \infty $ almost surely. Also, we have $ \hat{W} \rightarrow W $ as $ n \rightarrow \infty $
almost surely by Assumption G.5. It follows that as $ n \rightarrow \infty $
$$
\hat{G}(\hat{\theta}) \hat{W}^{-1} G(\bar{\theta})^{\prime} \rightarrow G\left(\theta_{0}\right) W^{-1} G\left(\theta_{0}\right)^{\prime} \text { a.s. }
$$
where $ G\left(\theta_{0}\right) W^{-1} G\left(\theta_{0}\right)^{\prime} $ is a $ p \times p $ nonsingular matrix given Assumptions $ \mathrm{G} .5 $ and $ \mathrm{G} .7(3) . $ Therefore, the stochastic inverse matrix $ \left[\hat{G}(\hat{\theta}) \hat{W}^{-1} G(\bar{\theta})^{\prime}\right]^{-1} $ exists for $ n $ sufficiently large because
$$
\left[\hat{G}(\hat{\theta}) \hat{W}^{-1} G(\bar{\theta})^{\prime}\right]^{-1} \rightarrow\left[G\left(\theta_{0}\right) W^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} \text {a.s. }
$$

as $ n \rightarrow \infty $.

It follows from the FOC that
$$
\begin{aligned}
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) &=-\left[\hat{G}(\hat{\theta}) \hat{W}^{-1} \hat{G}(\bar{\theta})^{\prime}\right]^{-1} \hat{G}(\hat{\theta}) \hat{W}^{-1} \sqrt{n} \hat{m}\left(\theta_{0}\right) \\
&=-\hat{\Psi} \sqrt{n} \hat{m}\left(\theta_{0}\right), \text { say. }
\end{aligned}
$$
By CLT for an IID random sample and the Cramer-Wold device, we have
$$
\begin{aligned}
\sqrt{n} \hat{m}\left(\theta_{0}\right)=& \frac{1}{\sqrt{n}} \sum_{i=1}^{n} m\left(X_{i}, \theta_{0}\right) \\
& \stackrel{d}{\rightarrow} N(0, V)
\end{aligned}
$$
where $ V=E\left[m\left(X_{i}, \theta_{0}\right) m\left(X_{i}, \theta_{0}\right)^{\prime}\right] . $ Furthermore
$$
\left[\hat{G}(\hat{\theta}) \hat{W}^{-1} \hat{G}(\bar{\theta})^{\prime}\right]^{-1} \hat{G}(\hat{\theta}) \hat{W}^{-1} \stackrel{a . s .}{\rightarrow}\left[G\left(\theta_{0}\right) W^{-1} G\left(\theta_{0}\right)\right]^{-1} G\left(\theta_{0}\right) W^{-1} \equiv \Psi
$$

as $ n \rightarrow \infty $. It follows from Slutsky's theorem (Theorem 7.18 ) that as $ n \rightarrow \infty $
$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0, \Psi V \Psi^{\prime}\right)
$$
(2) Suppose $ W=V $. Then we have
$$
\begin{aligned}
\Psi V \Psi^{\prime} &=\left\{\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} G\left(\theta_{0}\right) V^{-1}\right\} V\left\{\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} G\left(\theta_{0}\right) V^{-1}\right\}^{\prime} \\
&=\left\{\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} G\left(\theta_{0}\right) V^{-1}\right\} V\left\{V^{-1} G\left(\theta_{0}\right)^{\prime}\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1}\right\} \\
&=\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1}
\end{aligned}
$$
It follows that when $ W=V $, we have as $ n \rightarrow \infty $
$$
\sqrt{n}\left(\hat{\theta}-\theta_{0}\right) \stackrel{d}{\rightarrow} N\left(0,\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1}\right)
$$
### 8.5.4 Asymptotic Efficiency of  GMM

【Theorem 8.12】**Asymptotic Efficiency of  GMM**: Put $ \Omega_{0}=\left[G\left(\theta_{0}\right) V^{-1} G\left(\theta_{0}\right)^{\prime}\right]^{-1} $ i.e., let $ W=V $. Then $ \Omega-\Omega_{0} $ is positive semi-definite (PSD) for all finite and nonsingular matrix $ W $, where $ \Omega $ is given in Theorem 8.11.

**Proof:**

Observe that $ \Omega-\Omega_{0} $ is PSD if and only if $ \Omega_{0}^{-1}-\Omega^{-1} $ is PSD.

For notational simplicity, put $ G_{0}=G\left(\theta_{0}\right) $ and decompose $ V=V^{1 / 2} V^{1 / 2} , V^{-1}= V^{-1/2}V^{-1/2}$, where $ V $ is a $ q \times q $ symmetric and nonsingular matrix. 

Noting $ (A B C)^{-1}=C^{-1} B^{-1} A^{-1} $ for nonsingular matrices $ A, B, $ and $ C $, we therefore consider
$$
\begin{aligned}
\Omega_{0}^{-1}-\Omega^{-1} &=G_{0}^{\prime} V^{-1} G_{0}-G_{0}^{\prime} W^{-1} G_{0}\left[G_{0}^{\prime} W^{-1} V W^{-1} G_{0}\right]^{-1} G_{0}^{\prime} W^{-1} G_{0} \\
&=G_{0}^{\prime} V^{-\frac{1}{2}}\left[I-V^{\frac{1}{2}} W^{-1} G_{0}\left[G_{0}^{\prime} W^{-1} V W^{-1} G_{0}\right]^{-1} G_{0}^{\prime} W^{-1} V^{\frac{1}{2}}\right] V^{-\frac{1}{2}} G_{0} \\
&=G_{0}^{\prime} V^{-\frac{1}{2}} \Pi V^{-\frac{1}{2}} G_{0}
\end{aligned}
$$
where $G_0 = G(\theta_0)$ and the $ q \times q $ matrix
$$
\Pi \equiv I-V^{\frac{1}{2}} W^{-1} G_{0}\left[G_{0}^{\prime} W^{-1} V W^{-1} G_{0}\right]^{-1} G_{0}^{\prime} W^{-1} V^{\frac{1}{2}}
$$
is a symmetric and idempotent matrix (i.e., $ \Pi=\Pi^{\prime}, \Pi^{2}=\Pi $).

It follows that we have
$$
\begin{aligned}
\Omega_{0}^{-1}-\Omega^{-1} &=\left(G_{0}^{\prime} V^{-\frac{1}{2}} \Pi\right)\left(\Pi V^{-\frac{1}{2}} G_{0}\right) \\
&=\left(\Pi V^{-\frac{1}{2}} G_{0}\right)^{\prime}\left(\Pi V^{-\frac{1}{2}} G_{0}\right)
\end{aligned}
$$
which is always PSD (why?). 

For any $\lambda$, we always have
$$
\begin{aligned}
\lambda'(D'D)\lambda&=(\lambda D)'(\lambda D)'
\\ & \geq 0
\end{aligned}
$$
Thus matrix like $D'D$ is always PSD. This completes the proof.

In practice, we make $\hat{W} \stackrel{a.s.}{\rightarrow} V $, then the GMM is asymptotic efficient.

## 8.6 Criterion for Estimators

Question: Which is the best estimator for $ \theta $ ?

For example, we have obtained two different estimators for population variance $ \sigma^{2} $ one is the sample variance
$$
S_{n}^{2}=(n-1)^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2}
$$
and the other is the MLE estimator
$$
\hat{\sigma}^{2}=n^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2}
$$
Which estimator is better?

### 8.6.1 Mean Squared Error Criterion

【Definition 8.3】**Mean Squared Error (MSE)**: Let $\theta$ be a population parameter. The MSE of an estimator $ \hat{\theta}=\hat{\theta}_{n}\left(\mathrm{X}^{n}\right) $ of parameter $ \theta $ is defined as
$$
M S E_{\theta}(\hat{\theta})=E_{\theta}(\hat{\theta}-\theta)^{2}
$$

where $ E_{\theta}(\cdot) $ denotes the expectation which is taken under the joint distribution $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ of the random sample $X_n$; or equivalently under the sampling distribution of $X_n$.

If $MSE_{\theta}(\hat{\theta}) \rightarrow 0$, then $\hat{\theta} \stackrel{q.m.}{\rightarrow} \theta $ as $n \to \infty $.

### 后期再精细化整理

**Remarks:**

$ \operatorname{MSE}_{\theta}(\hat{\theta}) $ measures the average of variations or deviations of the estimator $ \hat{\theta} $ from the parameter $ \theta $ The difference $ \hat{\theta}-\theta $ is usually called the estimation error, so $ \mathrm{MSE}_{\theta}(\hat{\theta}) $ is a measure of the magnitude of the estimation error.

MSE is not the only criterion, but it is intuitive and analytically simple, and therefore is most commonly used in practice.

【Definition 8.4】**Bias**: The bias of a point estimator $ \hat{\theta} $ of parameter $ \theta $ is defined as
$$
\operatorname{Bias}_{\theta}(\hat{\theta})=E_{\theta}(\hat{\theta})-\theta
$$
An estimator $ \hat{\theta} $ for $ \theta $ is called an unbiased estimator for $ \theta $ if $ \operatorname{Bias}_{\theta}(\hat{\theta})=0 $

**Remarks:**

The bias $ \operatorname{Bias}_{\theta}(\hat{\theta}) $ measures the accuracy of estimator $ \hat{\theta} $. More specifically, the bias measures the closeness of all possible estimates on average to the true parameter value. It characterizes the degree of a systematic estimation error.

An unbiased estimator gives the right answer on average in a large number of repeated estimates. That is, there is no systematic upward or downward estimation for the parameter $ \theta $

【Example 8.9】Suppose $ \mathbf{X}^{n} $ is an IID random sample from some population with mean $ \mu $ and variance $ \sigma^{2} . $ Find an unbiased estimator for $ \operatorname{var}_{\theta}\left(\bar{X}_{n}\right) $

**Solution:** $ \operatorname{Put} \theta=\left(\mu, \sigma^{2}\right) $ and $ \tau=\frac{\sigma^{2}}{n} $
$ - $ Because $ \operatorname{var}_{\theta}\left(\bar{X}_{n}\right)=\frac{\sigma^{2}}{n}, $ an unbiased estimator of $ \tau $ can be given as follows:
$$
\hat{\tau}=\frac{S_{n}^{2}}{n}
$$
because $ E_{\theta}(\hat{\tau})=n^{-1} E_{\theta}\left(S_{n}^{2}\right)=\operatorname{var}_{\theta}\left(\bar{X}_{n}\right)=\tau $
$ - $ It follows that $ \operatorname{Bias}_{\theta}(\hat{\tau})=E_{\theta}(\hat{\tau})-\tau=0 $

【Example 8.10】Suppose $ \mathbf{X}^{n} $ is an IID random sample from some population with mean $ \mu $ and variance $ \sigma^{2} $. Find an unbiased estimator for $ \mu^{2} $

Solution: $ \operatorname{Put} \theta=\left(\mu, \sigma^{2}\right) $

$ - $ For parameter $ \tau=\mu^{2}, $ an unbiased estimator is
$$
\hat{\tau}=\bar{X}_{n}^{2}-\frac{S_{n}^{2}}{n}
$$

This follows because
$$
\begin{aligned}
E(\hat{\tau}) &=E_{\theta}\left(\bar{X}_{n}^{2}\right)-\frac{E_{\theta}\left(S_{n}^{2}\right)}{n} \\
&=\operatorname{var}_{\theta}\left(\bar{X}_{n}\right)+\left[E_{\theta}\left(\bar{X}_{n}\right)\right]^{2}-\frac{E_{\theta}\left(S_{n}^{2}\right)}{n} \\
&=\frac{\sigma^{2}}{n}+\mu^{2}-\frac{\sigma^{2}}{n} \\
&=\mu^{2}=\tau
\end{aligned}
$$
Intuitively, since the sample mean $ \bar{X}_{n} $ is a good estimator for $ \mu, $ so we expect that $ \bar{X}_{n}^{2} $ is a good estimator for $ \mu^{2} $. However, $ \bar{X}_{n}^{2} $ is a nonlinear function of $ \bar{X}_{n} $ which introduces a bias $ \frac{\sigma^{2}}{n} . $ This bias can be corrected by subtracting the unbiased estimator $ \frac{S_{n}^{2}}{n} $ for $ \frac{\sigma^{2}}{n} $.

【Theorem 8.13】**MSE Decomposition**:
$$
E_{\theta}(\hat{\theta}-\theta)^{2}=\operatorname{var}_{\theta}(\hat{\theta})+\left[\operatorname{Bias}_{\theta}(\hat{\theta})\right]^{2}
$$

**Proof:**
$$
\begin{aligned}
E_{\theta}(\hat{\theta}-\theta)^{2} &=E_{\theta}\left[\hat{\theta}-E_{\theta}(\hat{\theta})+E_{\theta}(\hat{\theta})-\theta\right]^{2} \\
&=E_{\theta}\left[\hat{\theta}-E_{\theta}(\hat{\theta})\right]^{2}+\left[E_{\theta}(\hat{\theta})-\theta\right]^{2}+2 E_{\theta}\left\{\left[\hat{\theta}-E_{\theta}(\hat{\theta})\right]\left[E_{\theta}(\hat{\theta})-\theta\right]\right\} \\
&=E_{\theta}\left[\hat{\theta}-E_{\theta}(\hat{\theta})\right]^{2}+\left[E_{\theta}(\hat{\theta})-\theta\right]^{2}
\end{aligned}
$$
where the cross-product term
$$
\begin{aligned}
E_{\theta}\left\{\left[\hat{\theta}-E_{\theta}(\hat{\theta})\right]\left[E_{\theta}(\hat{\theta})-\theta\right]\right\} &=E_{\theta}\left\{\left[\hat{\theta}-E_{\theta}(\hat{\theta})\right]\right\}\left[E_{\theta}(\hat{\theta})-\theta\right] \\
&=0 \cdot\left[E_{\theta}(\hat{\theta})-\theta\right] \\
&=0
\end{aligned}
$$
**Remarks:**

$ \operatorname{MSE}_{\theta}(\hat{\theta}) $ can be decomposed into $ \operatorname{var}_{\theta}(\hat{\theta}) $ and $ \operatorname{Bias}_{\theta}(\hat{\theta})^{2} $

- $ \operatorname{var}_{\theta}(\hat{\theta}) $ measures the variability (or **precision**) of the estimator $ \hat{\theta} $ due to the sampling variation. Precision is a description of random errors, a measure of statistical variability.
- $  \operatorname{Bias}_{\theta}(\hat{\theta}) $ measures the **accuracy** of the estimator due to the procedure. Accuracy is a description of systematic errors, a measure of statistical bias.

For any unbiased estimator $ \hat{\theta}, $ we have $ \operatorname{MSE}_{\theta}(\hat{\theta})=E_{\theta}(\hat{\theta}-\theta)^{2}=\operatorname{var}_{\theta}(\hat{\theta}) . $ Thus, **a best unbiased estimator is the one with the smallest variance**.

A best unbiased estimator may be dominated by a biased estimator if the latter has a substantially smaller variance that can compensate the bias. This is indeed the case for many machine learning predicting algorithms (e.g., the LASSO estimator).

MSE can be understood intuitively by the example of shooting a target.

- A high cumulative score will be obtained if most shots are close to the target. This corresponds to a small MSE, with a high accuracy and a high precision.

- In contrast, a low score will result if
    * The shots center the target (so high accuracy) but they spread over widely around the target (so low precision)
    * the shots center at a point which is far away from the target (so low accuracy) although they do not spread widely (high precision)

【Definition 8.5】**Relative Efficiency**: An estimator $ \hat{\theta} $ for parameter $ \theta $ is said to be more efficient than another estimator $ \theta $ for the same parameter $ \tilde{\theta} $ in terms of MSE if
$$
M S E_{\theta}(\hat{\theta}) \leq M S E_{\theta}(\tilde{\theta})
$$

It may be emphasized that there exists different criteria to evaluate relative efficiency of estimators, and a different criterion will generally lead to a different ranking between or among different estimators. In this book, we use MSE criterion, which is most commonly used in practice.

【Example 8.11】Suppose $ \left\{X_{i}\right\}_{i=1}^{2 n} $ is an IID random sample from a population with mean $ \mu $ and variance $ \sigma^{2} $. Define $ \hat{\mu}_{1}=n^{-1} \sum_{i=1}^{n} X_{i} $ and $ \hat{\mu}_{2}=(2 n)^{-1} \sum_{i=1}^{2 n} X_{i} . $ Which estimator is better in terms of MSE?

**Solution:**

Using the results in Chapter 6, we have $ E_{\theta}\left(\hat{\mu}_{1}\right)=\mu $, $ \operatorname{var}_{\theta}\left(\hat{\mu}_{1}\right)=\frac{\sigma^{2}}{n} $, $ E_{\theta}\left(\hat{\mu}_{2}\right)=\mu $ and
$$
\operatorname{var}_{\theta}\left(\hat{\mu}_{2}\right)=\frac{\sigma^{2}}{2 n}
$$
It follows that $ \operatorname{MSE}_{\theta}\left(\hat{\mu}_{1}\right)=2 \mathrm{MSE}_{\theta}\left(\hat{\mu}_{2}\right) . $ Therefore, $ \hat{\mu}_{2} $ is more efficient.

**Remarks:**

**It is always better to use more sample information in estimation**. Sample splitting or sample truncation is generally not a good idea from a statistical point of view because it does not fully utilize the whole sample information contained in $ \left\{X_{i}\right\}_{i=1}^{2 n} $

【Example 8.12】Let $ \left(X_{1}, X_{2}\right) $ be an IID random sample from a population with mean $ \mu $ and variance $ \sigma^{2} . $ Two estimators for $ \mu $ are
$$
\begin{array}{l}
\hat{\mu}_{1}=\bar{X}_{n}=\frac{1}{2}\left(X_{1}+X_{2}\right) \\
\hat{\mu}_{2}=\frac{1}{3}\left(X_{1}+2 X_{2}\right)
\end{array}
$$

Which estimator is better?

**Solution:** 

Put $ \theta=\left(\mu, \sigma^{2}\right) . $ We can check that both estimators are unbiased for $ \mu . $ Also,
$$
\begin{aligned}
\operatorname{var}_{\theta}\left(\hat{\mu}_{1}\right) &=\frac{1}{2} \sigma^{2} \\
\operatorname{var}_{\theta}\left(\hat{\mu}_{2}\right) &=\frac{1}{9} \sigma^{2}+\frac{4}{9} \sigma^{2} \\
&=\frac{5}{9} \sigma^{2} \\
&>\frac{1}{2} \sigma^{2}
\end{aligned}
$$
Therefore, $ \hat{\mu}_{1} $ is more efficient than $ \hat{\mu}_{2} $ in terms of MSE.

**Remarks:**

Since two random variables $ X_{1} $ and $ X_{2} $ are identical distributed, there is no reason to discriminate $ X_{1} $ and $ X_{2} $ (i.e. putting different weights on observations which have identical distributions). Equal weighting for each observation will be most efficient for estimation of $ \mu $.

### 8.6.2 Best Unbiased Estimators

Question: What is the best estimator if a class of estimators of parameter $ \theta $ is available?

We could define the best estimator as the one that has the smallest MSE. Unfortunately, such a best estimator is very difficult to obtain, because the class of estimators we have to compare is very huge.

For simplicity, we focus on a class of unbiased estimators and find the best estimator within this class.

【Definition 8.6】**Generalized Unbiased Estimator**: $ \hat{\tau}=\hat{\tau}_{n}\left(\mathrm{X}^{n}\right) $ is an unbiased estimator for the parameter $ \tau(\theta) $ if
$$
E_{\theta}(\hat{\tau})=\tau(\theta) \text { for all } \theta \in \Theta
$$
When $ \tau(\theta)=\theta, $ we return to Definition 8.4 of the unbiased estimator for parameter $ \theta $.

Example $ 13(8.13) . $ Suppose $ \mathbf{X}^{n} $ is an IID $ \left(\mu, \sigma^{2}\right) $ random sample. Put $ \theta=\left(\mu, \sigma^{2}\right) $ and $ \tau(\theta)= $ $ (\mu-2)^{2} . $ Find an unbiased estimator for $ \tau(\theta) $
solution:
$ - $ We first try an estimator $ \tilde{\tau}=\left(\bar{X}_{n}-2\right)^{2} $. Then
$$
\begin{aligned}
E_{\theta}(\tilde{\tau}) &=E_{\theta}\left(\bar{X}_{n}-2\right)^{2} \\
&=E_{\theta}\left[\left(\bar{X}_{n}-\mu+\mu-2\right)^{2}\right] \\
&=E_{\theta}\left(\bar{X}_{n}-\mu\right)^{2}+(\mu-2)^{2} \\
&=\frac{\sigma^{2}}{n}+\tau(\theta)
\end{aligned}
$$

It follows that
$$
E_{\theta}(\tilde{\tau})-\tau(\theta)=\frac{\sigma^{2}}{n} \neq 0
$$
We then make a necessary bias correction:
$$
\hat{\tau}=\left(\bar{X}_{n}-2\right)^{2}-\frac{1}{n} S_{n}^{2}
$$
This bias-corrected estimator $ \hat{\tau} $ is unbiased for the transformed parameter $ \tau(\theta)= $
$$
(\mu-2)^{2}
$$

【Definition 8.7】**Uniform Best Unbiased Estimator**: Let $ \Gamma $ be a class of unbiased estimators of parameter $ \tau(\theta), $ where $ \theta \in \Theta $ and $ \Theta $ is a known parameter space. An estimator $ \hat{\tau}^{*} $ $ \in \Gamma $ is a uniformly best unbiased estimator for $ \tau(\theta) $ over parameter space $ \Theta $ within the class $ \Gamma $ of estimators if

1. $ E_{\theta}\left(\hat{\tau}^{*}\right)=\tau(\theta) $ for all $ \theta \in \Theta $
2. $ \operatorname{var}_{\theta}\left(\hat{\tau}^{*}\right) \leq \operatorname{var}_{\theta}(\hat{\tau}) $ for any estimator $ \hat{\tau} $ of $ \tau(\theta) $ in $ \Gamma $ and for all $ \theta \in \Theta $

**Remarks:**

The estimator $ \hat{\tau}^{*} $ is a uniform minimum variance unbiased estimator (UMVUE) of $ \tau(\theta) $ over parameter space $ \Theta $ within the class $ \Gamma $ of estimators for $ \tau(\theta) $

Here, uniformity means that $ \hat{\tau}^{*} $ is always the best unbiased estimator for $ \tau(\theta) $ no matter what value the parameter $ \theta $ will take in $ \Theta $ (not just for a particular value of $ \theta) $

【Example 8.14】Let $ \mathrm{X}^{n} $ be an $ \mathrm{IID}\left(\mu, \sigma^{2}\right) $ random sample. Define a class of linear unbiased estimators of $ \mu $ as follows:
$$
\Gamma=\left\{\hat{\mu}: \mathbb{R}^{n} \rightarrow \mathbb{R} | \hat{\mu}=\sum_{i=1}^{n} c_{i} X_{i} \text { for }\left(c_{1}, \cdots, c_{n}\right)^{\prime} \in \mathbb{R}^{n}\right\}
$$
1) Show that $ \hat{\mu} $ is an unbiased estimator of $ \mu $ for all $ n \geq 1 $ if and only if $ \sum_{i=1}^{n} c_{i}=1 $

2) Find the uniformly most efficient unbiased estimator of $ \mu $ within the class $ \Gamma $ of estimators for $ \mu $

**Solution:** 

Note that we have $ \hat{\tau}=\hat{\mu}, $ and $ \tau(\theta)=\mu $ in this application.

1) Given $ \hat{\mu}=\sum_{i=1}^{n} c_{i} X_{i} $ and $ \theta=\left(\mu, \sigma^{2}\right), $ we have $ E_{\theta}(\hat{\mu})=\mu \sum_{i=1}^{n} c_{i} . $ Therefore, if $ \hat{\mu} $ is an unbiased estimator for $ \mu, $ i.e. if
$$
E_{\theta}(\hat{\mu})=\mu \text { for all } \mu \in \mathbb{R}
$$
we must have
$$
\sum_{i=1}^{n} c_{i}=1
$$

On the other hand, if $ \sum_{i=1}^{n} c_{i}=1, $ then from the fact that $ E_{\theta}(\hat{\mu})=\mu \sum_{i=1}^{n} c_{i}, $ we have
$$
E_{\theta}(\hat{\mu})=\mu \cdot 1=\mu \text { for all } \mu
$$
That is, $ \hat{\mu} $ is unbiased for $ \mu . $ Therefore, $ \hat{\mu} $ is unbiased for $ \mu $ for all possible values of $ \mu $ if and only if $ \sum_{i=1}^{n} c_{i}=1 $

2) To find the uniformly most efficient unbiased estimator for $ \mu $, we only need to find the one with the smallest variance within $ \Gamma $ subject to the constraint that $ \sum_{i=1}^{n} c_{i}=1 $ The variance of $ \hat{\mu} \in \Gamma $ is
$$
\begin{aligned}
\operatorname{var}_{\theta}(\hat{\mu}) &=\operatorname{var}_{\theta}\left(\sum_{i=1}^{n} c_{i} X_{i}\right) \\
&=\sum_{i=1}^{n} c_{i}^{2} \operatorname{var}_{\theta}\left(X_{i}\right) \\
&=\sigma^{2} \sum_{i=1}^{n} c_{i}^{2}
\end{aligned}
$$

Because $ \hat{\mu} $ is unbiased, we have $ \sum_{i=1}^{n} c_{i}=1 . $ Therefore, we can solve for the variance minimization problem

$$
\min _{\left\{c_{i}\right\}_{i=1}^{n}} \sigma^{2} \sum_{i=1}^{n} c_{i}^{2}
$$

subject to the constraint that

$$
\sum_{i=1}^{n} c_{i}=1
$$

Define the Lagrangian function

$$
L(c, \lambda)=\sigma^{2} \sum_{i=1}^{n} c_{i}^{2}+\lambda\left(1-\sum_{i=1}^{n} c_{i}\right)
$$

where $ c=\left(c_{1}, \cdots, c_{n}\right)^{\prime} $ and $ \lambda $ is the Lagrangian multiplier.
The $ n+1 $ first order conditions are given below:

$$
\begin{array}{l}
\frac{\partial L(c, \lambda)}{\partial c_{i}}=2 \sigma^{2} c_{i}-\lambda=0 \text { for } i=1, \cdots, n \\
\frac{\partial L(c, \lambda)}{\partial \lambda}=1-\sum_{i=1}^{n} c_{i}=0
\end{array}
$$

Solving for these equations, we obtain

$$
c_{i}^{*}=\frac{1}{n} \text { for } i=1, \cdots, n
$$

Thus, the uniformly most efficient unbiased estimator
$$
\hat{\mu}^{*}=\sum_{i=1}^{n} \frac{1}{n} X_{i}=\bar{X}_{n}
$$
For completeness, we need to verify the second order conditions to ensure that $ \hat{\mu}^{*} $ is a global minimizer. This is indeed the case because it can be shown that the Hessian matrix of $ L(c, \lambda) $ is positive definite for all $ \mu $ (please verify it!).

**Remarks:**

Because the random variables $ \mathbf{X}^{n}=\left\{X_{i}\right\}_{i=1}^{n} $ are identically distributed, there is no ground to discriminate one against another. The optimal weighting is of course equal weighting for all observation.

This is exactly the same idea for the Gauss-Markov theorem in the classical linear regression model, which says that the Ordinary Least Squares (OLS) estimator for the coefficients in a classical linear regression model with IID disturbances
$$
Y_{i}=X_{i}^{\prime} \theta_{0}+\varepsilon_{i}, \quad i=1, \cdots, n
$$

is the best linear unbiased estimator (BLUE), under the assumption that $ \left\{\varepsilon_{i}\right\}_{i=1}^{n} $ is IID $ \left(0, \sigma_{\varepsilon}^{2}\right) . $ The OLS estimator $ \theta $ is defined as
$$
\theta=\arg \min _{\theta} \sum_{i=1}^{n}\left(Y_{i}-X_{i}^{\prime} \theta\right)^{2}
$$
因为IID，目标函数等权重是最佳的

【Example 8.15】Suppose $ \mathbf{X}^{n}=\left(X_{1}, \cdots, X_{n}\right) $ is an independent but not identically distributed random sample, with $ E\left(X_{i}\right)=\mu $ and $ \operatorname{var}\left(X_{i}\right)=\sigma_{i}^{2}<\infty, i=1, \cdots, n $. Find a uniformly best
linear unbiased estimator of $ \mu $ within the class of estimators
$$
\Gamma=\left\{\hat{\mu}: \mathbb{R}^{n} \rightarrow \mathbb{R} | \hat{\mu}=\sum_{i=1}^{n} c_{i} X_{i},\left(c_{1}, \cdots, c_{n}\right)^{\prime} \in \mathbf{R}^{n}\right\}
$$
where $ \sum_{i=1}^{n} c_{i}=1 $.

**Solution:**

![image-20200531135404356](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531135404356.png)

![image-20200531135514582](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531135514582.png)

![image-20200531135559338](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531135559338.png)

Again, $ \hat{\mu} $ is an unbiased estimator for $ \mu $ if and only if $ \sum_{i=1}^{n} c_{i}=1 $
Now, using the Lagrange multiplier method, we can find that the optimal estimator within the class $ \Gamma $ is
$$
\begin{aligned}
\hat{\mu}^{*} &=\sum_{i=1}^{n} c_{i}^{*} X_{i} \\
&=\frac{1}{\sum_{i=1}^{n} \frac{1}{\sigma_{i}^{2}}} \sum_{i=1}^{n} \frac{1}{\sigma_{i}^{2}} X_{i}
\end{aligned}
$$
where
$$
c_{i}^{*}=\frac{\frac{1}{\sigma_{i}^{2}}}{\sum_{i=1}^{n} \frac{1}{\sigma_{i}^{2}}} \propto \frac{1}{\sigma_{i}^{2}}, \quad i=1, \cdots, n
$$
**Remarks:**

To obtain the most efficient estimator for $ \mu $ in an independent but not identically distributed random sample, one should discount noisy observations.

The optimal weight $ c_{i}^{*} $ is proportional to $ \sigma_{i}^{-2}, $ the inverse of the variance of the random variable $ X_{i} $.

This is similar to the idea behind the Generalized Least Squares (GLS) estimator in econometrics. Consider a linear regression model
$$
Y_{i}=X_{i}^{\prime} \theta+\varepsilon_{i}, \quad i=1, \cdots, n
$$
where $ \left\{\varepsilon_{i}\right\}_{i=1}^{n} $ is an independent but not identically distributed sequence with $ E\left(\varepsilon_{i}\right)= $ 0 and $ \operatorname{var}\left(\varepsilon_{i}^{2}\right)=\sigma_{i}^{2} . $ Here, there may exist unconditional heteroskedasticity because $ \sigma_{i}^{2} $ may be different across $ i . $ We consider the transformed regression model

$$
\frac{Y_{i}}{\sigma_{i}}=\left(\frac{X_{i}}{\sigma_{i}}\right)^{\prime} \theta+\frac{\varepsilon_{i}}{\sigma_{i}}
$$
or equivalently
$$
Y_{i}^{*}=X_{i}^{* \prime} \theta+\varepsilon_{i}^{*}
$$
where $ \left\{\varepsilon_{i}^{*}\right\}_{i=1}^{n} $ is an IID sequence with zero mean and unit variance. Then the OLS estimator of the transformed linear regression model
$$
\hat{\theta}^{*}=\arg \min _{\theta} \sum_{i=1}^{n}\left(Y_{i}^{*}-X_{i}^{* \prime} \theta\right)^{2}
$$
is called the GLS estimator. In other words, GLS is the OLS estimator after correcting heteroskedasticity. This estimator $ \hat{\theta}^{*} $ discounts noisy observations by dividing them by their standard deviations.

Question: Is an unbiased estimator always better than a biased estimator?

【Example 8.16】Let $ \mathbf{X}^{n} $ be an IID random sample from a $ N\left(\mu, \sigma^{2}\right) $ distribution. The sample variance $ S_{n}^{2}=(n-1)^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2} $ and the MLE estimator $ \hat{\sigma}^{2}=n^{-1} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2} $ are two estimators for $ \sigma^{2} $. Which is more efficient in terms of MSE?

**Solution:**
Because $ \frac{(n-1) S_{n}^{2}}{\sigma^{2}} \sim \chi_{n-1}^{2}, $ we have $ E_{\theta}\left(S_{n}^{2}\right)=\sigma^{2} $ and $ \operatorname{var}_{\theta}\left(S_{n}^{2}\right)=\frac{2 \sigma^{4}}{n-1} . $ It follows that
$$
\begin{aligned}
\operatorname{MSE}_{\theta}\left(S_{n}^{2}\right) &=E_{\theta}\left(S_{n}^{2}-\sigma^{2}\right)^{2} \\
&=\operatorname{var}_{\theta}\left(S_{n}^{2}\right)+\left[\operatorname{Bias}_{\theta}\left(S_{n}^{2}\right)\right]^{2} \\
&=\frac{2 \sigma^{4}}{n-1}
\end{aligned}
$$
Next, observing
$$
\hat{\sigma}^{2}=\frac{n-1}{n} S_{n}^{2}
$$

we have
$$
\begin{aligned}
\operatorname{Bias}_{\theta}\left(\hat{\sigma}^{2}\right) &=E_{\theta}\left(\hat{\sigma}^{2}\right)-\sigma^{2} \\
&=\frac{n-1}{n} \sigma^{2}-\sigma^{2} \\
&=-\frac{\sigma^{2}}{n} \\
\operatorname{var}_{\theta}\left(\hat{\sigma}^{2}\right) &=\left(\frac{n-1}{n}\right)^{2} \operatorname{var}_{\theta}\left(S_{n}^{2}\right) \\
&=\left(\frac{n-1}{n}\right)^{2} \frac{2 \sigma^{4}}{n-1}
\end{aligned}
$$
It follows that
$$
\begin{aligned}
\operatorname{MSE}_{\theta}\left(\hat{\sigma}^{2}\right) &=\left(1-\frac{1}{n}\right)^{2} \frac{2 \sigma^{4}}{n-1}+\frac{\sigma^{4}}{n^{2}} \\
&=\left[\left(1-\frac{1}{n}\right)^{2}+\frac{n-1}{2 n^{2}}\right] \frac{2 \sigma^{4}}{n-1} \\
&=\frac{n-1}{n} \frac{2 n-1}{2 n} \frac{2 \sigma^{4}}{n-1} \\
&<\frac{2 \sigma^{4}}{n-1}=\operatorname{MSE}_{\theta}\left(S_{n}^{2}\right)
\end{aligned}
$$
for all $ n>1 . $ Therefore, the biased estimator $ \hat{\sigma}^{2} $ is better than the unbiased estimator $ S_{n}^{2} $.

**Remarks:**

It is sometimes the case, as in the above example, that **a trade-off occurs between variance and bias** in such a way that a small increase in bias can be traded for a larger decrease in variance, resulting an improvement in MSE.

Statistics and econometrics have perhaps focused too much on biased estimation.

However, the conclusion that $ S_{n}^{2} $ is less efficient than $ \hat{\sigma}_{n}^{2} $ does not mean that $ S_{n}^{2} $ should be abandoned as an estimator for $ \sigma^{2} $. For example, the use of $ S_{n}^{2} $ yield some well-known distribution for some statistic.

变量过多导致多重共线时 Ridge回归

![image-20200531141844030](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531141844030.png)

![image-20200531141829606](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531141829606.png)

![image-20200531141600014](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531141600014.png)

![image-20200531141621287](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531141621287.png)

![image-20200531142013238](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531142013238.png)

![image-20200531142040499](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531142040499.png)

LASSO回归

![image-20200531142138716](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531142138716.png)

![image-20200531142252874](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531142252874.png)

排除了等于零的参数项

![image-20200531142334582](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531142334582.png)



BUE本质是拉格朗日方法，在无偏的约束下最小化方差。

## 8.7 Cramer-Rao Lower Bound

Remarks:

There is an alternative method of evaluating parameter estimators when the population distribution model $ f(x, \theta) $ is available.

For simplicity, we assume that parameter $ \theta $ is a scalar here

【Theorem 8.14】**Cramer-Rao Lower Bound**: Let $ \mathrm{X}^{n} $ be a random sample with joint  PMF/ PDF $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right), $ and let $ \hat{\tau}=\hat{\tau}_{n}\left(\mathbf{X}^{n}\right) $ be any estimator of parameter $ \tau(\theta) $ where $ E_{\theta}(\hat{\tau}) $ is a differentiable function of $ \theta . $ Suppose the joint PMF/ PDF $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ of the random sample $ \mathbf{X}^{n} $ satisfies the condition that
$$
\frac{d}{d \theta} \int_{\mathbb{R}^{n}} h\left(\mathbf{x}^{n}\right) f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n}=\int_{\mathbb{R}^{n}} h\left(\mathbf{x}^{n}\right) \frac{\partial f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta} d \mathbf{x}^{n}
$$
for any measurable function $ h: \mathbb{R}^{n} \rightarrow \mathbb{R} $ with $ E_{\theta}\left|h\left(\mathbf{X}^{n}\right)\right|<\infty $, where $ E_{\theta}(\cdot) $ is taken over the joint PMF/ PDF $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ of $ \mathbf{X}^{n} . $ Then for all $ n>0 $ and all $ \theta \in \Theta $
$$
\operatorname{var}_{\theta}(\hat{\tau}) \geq B_{n}(\theta) \equiv \frac{\left[\frac{d E_{\theta}(\hat{\tau})}{d \theta}\right]^{2}}{E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}} n\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}}
$$
where $ B_{n}(\theta) $ is called the Cramer-Rao lower bound. In particular, when $ \hat{\tau} $ is unbiased for parameter $ \tau(\theta), $ we have
$$
B_{n}(\theta)=\frac{\left[\tau^{\prime}(\theta)\right]^{2}}{E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}}
$$
Unbiased estimator with  $\operatorname{var}_{\theta}(\hat{\tau}) = B_{n}(\theta)$ must be a best unbiased estimator.

**Proof:** 

We consider the case of continuous distributions; the proof for the case of discrete distributions is similar. Suppose we have:

(1) 
$$
\qquad E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}=\operatorname{var}_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]
$$

(2)
$$
\frac{d E_{\theta}(\hat{\tau})}{d \theta}=\operatorname{cov}_{\theta}\left[\hat{\tau}_{n}\left(\mathbf{X}^{n}\right), \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]
$$
Then by the Cauchy-Schwarz inequality, we have

![image-20200531163404618](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200531163404618.png)
$$
\left\{\operatorname{cov}_{\theta}\left[\hat{\tau}_{n}\left(\mathbf{X}^{n}\right), \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]\right\}^{2} \leq \operatorname{var}_{\theta}(\hat{\tau}) \cdot \operatorname{var}_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]
$$

This implies that

$$
\begin{aligned}
\operatorname{var}_{\theta}(\hat{\tau}) & \geq \frac{\left\{\operatorname{cov}_{\theta}\left[\hat{\tau}, \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]\right\}^{2}}{\operatorname{var}_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]} \\
&=\frac{\left[\frac{d E_{\theta}(\hat{\tau})}{d \theta}\right]^{2}}{E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}\left(\mathbf{X}^{n}, \theta\right)}}{\partial \theta}\right]^{2}} \\
&=B_{n}(\theta)
\end{aligned}
$$

given results (1) and (2) above. Therefore, it suffices to show results (1) and (2).

We first prove result (1). We shall show that the mean of the score function $ \frac{\partial \ln f_{\mathbf{x}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta} $ of the random sample $ \mathbf{X}^{n} $ under the joint distribution $ f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right) $ is zero.

This follows because
$$
\begin{aligned}
& E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] \\
=& \int_{\mathbb{R}^{n}}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta}\right] f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n} \\
=& \int_{\mathbb{R}^{n}} \frac{\partial f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta} d \mathbf{x}^{n} \\
=& \frac{d}{d \theta} \int_{\mathbb{R}^{n}} f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n} \\
=& \frac{d(1)}{d \theta} \\
=& 0
\end{aligned}
$$
where the third equality follows by exchanging the orders of integration and differentiation.
Therefore, we obtain the variance of the score function
$$
\begin{aligned}
\operatorname{var}_{\theta}\left[\frac{\partial f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] &=E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}-\left\{E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]\right\}^{2} \\
&=E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}
\end{aligned}
$$

This has proved result (1). 

Next, we prove result (2). Given $ E_{\theta}\left[\frac{\partial f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]=0 $ and $ \hat{\tau}=\hat{\tau}\left(\mathbf{X}^{n}\right), $ and using the formula $ cov(Y, Z)=E(Y Z)-\mu_{Y} \mu_{Z} $, we have
$$
\begin{aligned}
& \operatorname{cov}_{\theta}\left[\hat{\tau}, \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] \\
=& E_{\theta}\left[\hat{\tau} \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]-E_{\theta}\left(\hat{\tau}_{n}\right) E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] \\
=& E_{\theta}\left[\hat{\tau} \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] \\
=& \int_{\mathbb{R}^{n}} \hat{\tau}_{n}\left(\mathbf{x}^{n}\right)\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta}\right] f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n} \\
=& \int_{\mathbb{R}^{n}} \hat{\tau}_{n}\left(\mathbf{x}^{n}\right) \frac{\partial f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta} d \mathbf{x}^{n} \\
=& \frac{d}{d \theta} \int_{\mathbb{R}^{n}} \hat{\tau}_{n}\left(\mathbf{x}^{n}\right) f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n} \\
=& \frac{d E_{\theta}(\hat{\tau})}{d \theta}
\end{aligned}
$$
where the last to second equality follows from the exchange condition between the integration and differentiation. We have proved result (2).

The Cramer-Rao lower bound applies to discrete distributions as well. The only change is to replace the integrals involved by summations, with $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ being a joint PMF rather than a joint PDF of the random sample $ \mathbf{X}^{n} $.

**Remarks:**

It is important to emphasize that a key assumption in the Cramer-Rao theorem is the ability to differentiate under the integral sign, which, of course, is somewhat restrictive.
The condition on the exchange between differentiation and integration is crucial. It can be written as follows:
$$
\frac{d}{d \theta} \int_{\mathbb{R}^{n}} h\left(\mathbf{x}^{n}\right) f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n}=\int_{\mathbb{R}^{n}} h\left(\mathbf{x}^{n}\right) \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right)}{\partial \theta} f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) d \mathbf{x}^{n}
$$
or equivalently,
$$
\frac{d E_{\theta}\left[h\left(\mathbf{X}^{n}\right)\right]}{d \theta}=E_{\theta}\left[h\left(\mathbf{X}^{n}\right) \frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]
$$
Densities in the exponential class will satisfy the assumption but in general, such an assumption needs to be checked; otherwise contradictions may arise. Newey and McFadden (1994, Lemma 3.6) provide sufficient conditions for such an assumption to hold.

Theorem 8.14 implies that $ \operatorname{var}_{\theta}(\hat{\tau}) $ is greater than or at least equal to the Cramer-Rao lower bound

$$
B_{n}(\theta) \equiv \frac{\left[\frac{d E_{\theta}(\tau)}{d \theta}\right]^{2}}{E_{\theta}\left[\frac{\partial \ln f_{\mathrm{x} n}\left(\mathrm{x}^{n}, \theta\right)}{\partial \theta}\right]^{2}}
$$
Suppose the variance of an unbiased estimator $ \hat{\tau} $ of $ \tau(\theta) $ achieves the Cramer-Rao lower bound, that is,
$$
\operatorname{var}_{\theta}(\hat{\tau})=\frac{\left[\tau^{\prime}(\theta)\right]^{2}}{E_{\theta}\left[\frac{\partial \ln f_{\mathrm{x} n}\left(\mathrm{X}^{n}, \theta\right)}{\partial \theta}\right]^{2}}
$$
Then the unbiased estimator $ \hat{\tau} $ must be a most efficient estimator for $ \tau(\theta) $

Question: How to express and show the Cramer-Rao lower bound when $ \theta $ is a parameter vector rather than a scalar parameter?

【Corollary 8.15】**Cramer-Rao Lower Bound Under an IID Random Sample**: Let $ \mathrm{X}^{n} $ be an IID random sample from population PMF/ PDF $ f(x, \theta) $ and let $ \hat{\tau}=\hat{\tau}_{n}\left(\mathrm{X}^{n}\right) $ be any estimator of $ \tau(\theta), $ where $ E_{\theta}\left[\hat{\tau}_{n}\left(\mathbf{X}^{n}\right)\right] $ is a differentiable function of $ \theta \in \Theta . $ Suppose
$$
\frac{d}{d \theta} \int_{-\infty}^{\infty} h(x) f(x, \theta) d x=\int_{-\infty}^{\infty} h(x) \frac{\partial f(x, \theta)}{\partial \theta} d x
$$
for all $ h(x) $ such that $ E_{\theta}\left|h\left(X_{i}\right)\right|<\infty . $ Then for all $ n $
$$
\operatorname{var}_{\theta}(\hat{\tau}) \geq B_{n}(\theta) \equiv \frac{\left[\frac{d E_{\theta}(\hat{\tau})}{d \theta}\right]^{2}}{n I(\theta)}
$$

where
$$
\begin{aligned}
I(\theta) &=E_{\theta}\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right]^{2} \\
&=\int_{-\infty}^{\infty}\left[\frac{\partial \ln f(x, \theta)}{\partial \theta}\right]^{2} f(x, \theta) d x
\end{aligned}
$$
is Fisher's information matrix of the population PMF/ PDF $ f(x, \theta) $ When $ \hat{\tau} $ is unbiased for $ \tau(\theta), $ then
$$
\operatorname{var}_{\theta}(\hat{\tau}) \geq B_{n}(\theta) \equiv \frac{\left[\tau^{\prime}(\theta)\right]^{2}}{n I(\theta)}
$$
**Proof:**

Given the Cramer-Rao lower bound formula, it suffices to show that under the IID assumption for $ \mathbf{X}^{n}, $ the denominator in the Cramer-Rao lower bound becomes $ n I(\theta) $

Because $ \mathbf{X}^{n} $ is an IID sample from population $ f(x, \theta), $ we have $ f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)=\prod_{i=1}^{n} f\left(X_{i}, \theta\right) $. It follows that
$$
\ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)=\sum_{i=1}^{n} \ln f\left(X_{i}, \theta\right)
$$
Hence, the score function of the random sample $ \mathbf{X}^{n} $
$$
\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}=\sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}
$$
By Lemma 8.6, the expectation of the score function $ \frac{\partial}{\partial \theta} \ln f\left(X_{i}, \theta\right) $ under the population distribution $ f(x, \theta) $ is zero:
$$
\begin{aligned}
& E_{\theta}\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right] \\
=& \int_{-\infty}^{\infty} \frac{\partial \ln f(x, \theta)}{\partial \theta} f(x, \theta) d x \\
=& 0
\end{aligned}
$$
It follows from the IID assumption that

$$
\begin{aligned}
& E_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right]^{2} \\
=& \operatorname{var}_{\theta}\left[\frac{\partial \ln f_{\mathbf{X}^{n}}\left(\mathbf{X}^{n}, \theta\right)}{\partial \theta}\right] \\
=& \operatorname{var}_{\theta}\left[\sum_{i=1}^{n} \frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right] \\
=& \sum_{i=1}^{n} \operatorname{var}_{\theta}\left[\frac{\partial \ln f\left(X_{i}, \theta\right)}{\partial \theta}\right] \\
=& n \cdot \operatorname{var}_{\theta}\left[\frac{\partial \ln f(X, \theta)}{\partial \theta}\right] \\
=& n \cdot E_{\theta}\left[\frac{\partial \ln f(X, \theta)}{\partial \theta}\right]^{2} \\
=& n I(\theta)
\end{aligned}
$$
where the third and fourth equalities follows from the IID assumption, the fifth equality follows from the fact that $ E_{\theta}\left[\frac{\partial}{\partial \theta} \ln f\left(X_{i}, \theta\right)\right]=0 $.

**Remarks:**

In this corollary, $ f(x, \theta) $ is the PMF $ / $ PDF of each random variable $ X_{i}, $ while $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ in the previous theorem is the joint $ \mathrm{PMF} / \mathrm{PDF} $ of the random sample $ \mathrm{X}^{n} $.

Under the IID assumption, it is clear that the Cramer-Rao lower bound $ B_{n}(\theta) $ vanishes to zero at a rate $ n $

The Cramer-Rao lower bound is proportional to the inverse of Fisher's information matrix $ I(\theta) . $ The larger $ I(\theta), $ the more information about $ \theta $ is contained in the random variable $ X_{i} . $ As a result, we have a smaller $ B_{n}(\theta) $ The calculation of $ I(\theta) $ sometimes is tedious. By using the information matrix equality $ I(\theta)+H(\theta)=0, $ where
$$
\begin{aligned}
H(\theta) & \equiv E_{\theta}\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial \theta^{2}}\right] \\
&=\int_{-\infty}^{\infty} \frac{\partial^{2} \ln f(x, \theta)}{\partial \theta^{2}} f(x, \theta) d x
\end{aligned}
$$
is called the Hessian matrix, we can write the Cramer-Rao lower bound
$$
B_{n}(\theta)=\frac{\left[\tau^{\prime}(\theta)\right]^{2}}{-n H(\theta)}
$$
The Cramer-Rao lower bound $ B_{n}(\theta) $ depends on the inverse of the curvature of the $ \log $ likelihood function $ \ln f(x, \theta) . $ The larger the curvature in absolute value, the smaller the Cramer-Rao lower bound $ B_{n}(\theta) $.(用hessian matrix 计算会比较简单)

We have shown that the MLE
$$
\sqrt{n}(\hat{\theta}-\theta) \stackrel{d}{\rightarrow} N\left(0,-H(\theta)^{-1}\right) \text {as } n \rightarrow \infty
$$

where $ \theta $ denotes the true parameter value in $ \Theta $. This implies that $\hat{\theta}-\theta $ approximately follows a $ N\left(0,[-n H(\theta)]^{-1}\right) $ distribution for $ n $ sufficiently large. Thus, the variance of the MLE $ \theta $ approximately achieves the Cramer-Rao lower bound when $ n $ is large.

【Example 8.17】Let $ \mathrm{X}^{n} $ be an IID Poison($ \lambda $) random sample. Use the Cramer-Rao lower bound method to show that the sample mean $ \bar{X}_{n} $ is a best unbiased estimator of $ \lambda $.

**Solution:**

In this application we have $ \tau(\theta)=\theta=\lambda, $ and $ \hat{\tau}=\bar{X}_{n} $, $ E_{\lambda}(\hat{\tau})=\lambda $. Therefore, $ \hat{\tau} $ is an unbiased estimator for $ \lambda $.

Because
$$
\operatorname{var}_{\lambda}\left(\bar{X}_{n}\right)=\frac{\sigma^{2}}{n}=\frac{\lambda}{n}
$$
given $ \sigma^{2}=\lambda $ for the Poisson $ (\lambda) $ distribution, it suffices to show that the Cramer-Rao lower bound $ B_{n}(\lambda)=\frac{\lambda}{n} $.

The log-likelihood function
$$
\begin{aligned}
\ln f\left(X_{i}, \lambda\right) &=\ln \left(\frac{e^{-\lambda} \lambda^{X_{i}}}{X_{i} !}\right) \\
&=-\lambda+X_{i} \ln \lambda-\ln X_{i} !
\end{aligned}
$$

Therefore, we have
$$
\begin{aligned}
\frac{\partial^{2} \ln f\left(X_{i}, \lambda\right)}{\partial \lambda^{2}} &=\frac{\partial^{2}\left(-\lambda+X_{i} \ln \lambda-\ln X_{i} !\right)}{\partial \lambda^{2}} \\
&=-\frac{X_{i}}{\lambda^{2}}
\end{aligned}
$$
It follows that
$$
\begin{aligned}
H_{\lambda}(\lambda) &=E_{\lambda}\left[\frac{\partial^{2} \ln f\left(X_{i}, \lambda\right)}{\partial \lambda^{2}}\right] \\
&=E_{\lambda}\left(-\frac{X_{i}}{\lambda^{2}}\right) \\
&=-\frac{E_{\lambda}\left(X_{i}\right)}{\lambda^{2}} \\
&=-\frac{1}{\lambda}
\end{aligned}
$$
Also, because $ \hat{\tau}=\bar{X}_{n}, $ we have $ E_{\lambda}\left(\bar{X}_{n}\right)=\lambda, $ so
$$
\frac{d E_{\lambda}(\hat{\tau})}{d \lambda}=\frac{d \lambda}{d \lambda}=1
$$

$ - $ It follows that
$$
\begin{aligned}
B_{n}(\lambda) &=\frac{\left[\frac{d}{d \lambda} E_{\lambda}(\hat{\tau})\right]^{2}}{-n H_{\lambda}(\lambda)} \\
&=\frac{1^{2}}{-n\left(-\frac{1}{\lambda}\right)} \\
&=\frac{\lambda}{n}
\end{aligned}
$$
Because var $ _{\lambda}\left(\bar{X}_{n}\right)=B_{n}(\lambda), $ i.e., the sample mean estimator $ \bar{X}_{n} $ achieves the Crame-rRao lower bound, it is the best unbiased estimator of $ \lambda $.

**Remarks:**

The Cramer-Rao lower bound approach may not reach a decisive conclusion when $ \operatorname{var}_{\theta}(\hat{\tau}) $ does not attain the Cramer-rao lower bound $ B_{n}(\theta) $.

【Example 8.18】Let $ \mathbf{X}^{n} $ be an IID $ N\left(\mu, \sigma^{2}\right) $ random sample, where $ \mu $ and $ \sigma^{2} $ are unknown. Show that $ S_{n}^{2} $ does not attain the Cramer-Rao lower bound.

**Solution:**

In this application, we have $ \theta=\left(\mu, \sigma^{2}\right), \hat{\tau}=S_{n}^{2} $ and $ \tau(\theta)=\sigma^{2} $

The log-likelihood function of a $ N\left(\mu, \sigma^{2}\right) $ distribution is
$$
\ln f\left(X_{i}, \theta\right)=-\ln \sqrt{2 \pi}-\frac{1}{2} \ln \sigma^{2}-\frac{\left(X_{i}-\mu\right)^{2}}{2 \sigma^{2}}
$$
Hence, we have
$$
\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial\left(\sigma^{2}\right)^{2}}=\frac{1}{2 \sigma^{4}}-\frac{\left(X_{i}-\mu\right)^{2}}{\sigma^{6}}
$$
It follows that the Hessian matrix
$$
\begin{aligned}
E_{\theta}\left[\frac{\partial^{2} \ln f\left(X_{i}, \theta\right)}{\partial\left(\sigma^{2}\right)^{2}}\right] &=\frac{1}{2 \sigma^{4}}-\frac{E_{\theta}\left(X_{i}-\mu\right)^{2}}{\sigma^{6}} \\
&=\frac{1}{2 \sigma^{4}}-\frac{1}{\sigma^{4}} \\
&=-\frac{1}{2 \sigma^{4}}
\end{aligned}
$$
In this example, it is easy to understand why the information matrix $ I(\theta) $ or the Hessian matrix $ H(\theta) $ is a measure of the information contained in the random variable $ X_{i} . $ The smaller the variance $ \sigma^{2}, $ the less noisy the random variable $ X_{i}, $ and so the more precise the estimation of the parameter $ \sigma^{2} $. 

For any unbiased estimator $ \hat{\tau}=\hat{\tau}_{n}\left(\mathbf{X}^{n}\right) $ of $ \sigma^{2}, $ we have $ E_{\theta}\left[\hat{\tau}_{n}\left(\mathbf{X}^{n}\right)\right]=\sigma^{2} $,
$$
\frac{d E_{\theta}\left[\hat{\tau}_{n}\left(\mathbf{X}^{n}\right)\right]}{d \sigma^{2}}=1
$$

It follows that the Cramer-Rao lower bound
$$
\begin{aligned}
B_{n}(\theta) &=\frac{1}{n} \frac{1^{2}}{\frac{1}{2 \sigma^{4}}} \\
&=\frac{2 \sigma^{4}}{n} \\
&<\frac{2 \sigma^{4}}{n-1}=\operatorname{var}_{\theta}\left(S_{n}^{2}\right)
\end{aligned}
$$
Hence, $ S_{n}^{2} $ does not attain the Cramer-Rao Lower Bound $ 2 \sigma^{4} / n $

We cannot say that $ S_{n}^{2} $ is not the best unbiased estimator, because there exist two possibilities:

1. there may be some unbiased estimator that attains $ B_{n}(\theta) ; $ or 
2. $ B_{n}(\theta) $ is unattainable by any unbiased estimator for $ \sigma^{2} $

【Theorem 8.16】Suppose $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ is the joint  PMF/ PDF of the random sample $ \mathbf{X}^{n} $ and $ \hat{\tau}=\hat{\tau}_{n}\left(\mathbf{X}^{n}\right) $ is an unbiased estimator for parameter $ \tau(\theta), $ where $ f_{\mathbf{X}^{n}}\left(\mathbf{x}^{n}, \theta\right) $ and $ \hat{\tau} $ satisfy the conditions in the Cramer-Rao lower bound theorem. Then the estimator $ \hat{\tau} $ attains the Cramer-Rao lower bound if and only if
$$
\hat{\tau}-\tau(\theta)=a(\theta) \frac{\partial \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta}
$$
for some function $ a: \Theta \rightarrow \mathbb{R} $.

**Proof:**

By the Cauchy-Schwarz inequality, we have
$$
\left\{\operatorname{cov}_{\theta}\left[\hat{\tau}, \frac{\partial \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta}\right]\right\}^{2} \leq \operatorname{var}_{\theta}(\hat{\tau}) \operatorname{var}_{\theta}\left[\frac{\partial \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta}\right]
$$
The equality holds if and only if $\left\{\operatorname{corr}_{\theta}\left[\hat{\tau}, \frac{\partial \ln \hat{L}\left(\theta | \mathbf{X}^{n}\right)}{\partial \theta}\right]\right\}^{2}=1$. Then, the centered parameter estimator $ \hat{\tau}-\tau(\theta) $ is proportional to the score function $ \frac{\partial}{\partial \theta} \ln \hat{L}\left(\theta | X^{n}\right) $ of the random sample $ \mathbf{X}^{n} $.

Example 8.19 \text { [Continuation of Example } 8.18]: The likelihood function of an $ 11 D $ $ N\left(\mu, \sigma^{2}\right) $ random sample $ \mathbf{X}^{n} $ is
$$
\hat{L}\left(\theta | \mathbf{X}^{n}\right)=\frac{1}{\left(2 \pi \sigma^{2}\right)^{n / 2}} e^{-\frac{1}{2 \sigma^{2}} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2}}
$$
where $ \theta=\left(\mu, \sigma^{2}\right) . $ Hence, the score function
$$
\frac{\partial \ln \hat{L}\left(\mu, \sigma^{2} | \mathbf{X}^{n}\right)}{\partial \sigma^{2}}=\frac{n}{2 \sigma^{4}}\left[n^{-1} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2}-\sigma^{2}\right]
$$

Thus, taking a $ (\theta)=n /\left(2 \sigma^{4}\right) $ shows that the best unbiased estimator of $ \sigma^{2} $ is $ n^{-1} \sum_{i=1}^{n}\left(X_{i}-\mu\right)^{2} $ if $ \mu $ is known. If $ \mu $ is unknown, the Cramer-Rao lower bound is not attainable.

## 8.8 Conclusion

In this chapter, we first introduce two important estimation methods: MLE and MME, the latter having been extended by econometricians to GMM.

MLE is based on a correctly specified parametric PMF/PDF model for the population distribution, while MME and GMM are based on a set of moment conditions on the population.

Because it utilizes the information on the joint distribution of the random sample, MLE is expected to be more efficient than MME and GMM, unless for the latter, the sample moments used are sufficient statistics for the parameters of interest.

GMM does not require the knowledge of the population distribution of the DGP.

To gain insight into the properties of the MLE and MME / GMM, we develop the asymptotic theory for the proposed two estimators.

In order to evaluate different estimators for the same population parameter, we introduce MSE to measure the closeness between an estimator and the population parameter.

We then develop two important methods to evaluate unbiased parameter estimators.

- **One is the Lagrange multiplier approach, which does not require the knowledge of the population $ \mathrm{PMF} / \mathrm{PDF} $**
- **the other is the Cramer-Rao lower bound approach which requires the knowledgement of the joint likelihood function of the random sample.**
- We have focused on the methods to find the best unbiased estimator(s). It should be emphasized that **the best unbiased estimator may not the most efficient estimator**.
- A biased estimator may outperform an unbiased estimator by substantially reducing the variance with a bit increase in the bias. This is the case with many machine learning algorithms.


