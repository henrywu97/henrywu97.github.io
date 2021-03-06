# 2. Money-in-the-Utility Function


## 2.1 Introduction

The **neoclassical growth model** due to **Ramsey** (1928) and **Solow** (1956) provides the basic framework for much of modern macroeconomics.

When the assumption of a fixed savings rate is replaced by a model of forward looking households choosing savings and labor supply to maximize lifetime utility, the **Solow model** becomes the foundation for **dynamic stochastic general equilibrium(DSGE)** models of the business cycle.

The **neoclassical growth model is a model of a nonmonetary economy**, and although goods are exchanged and transactions must be taking place, there is no medium of exchange—that is, no ‘‘money’’—that is used to facilitate these transactions.

Three general approaches to incorporating money into general equilibrium models have been followed:

- assume that **money yields direct utility** by incorporating money balances into the utility functions of the agents of the model (Sidrauski 1967);
- impose transaction costs of some form that give rise to a demand for money.
- treat money like any other asset used to **transfer resources intertemporally** (Samuelson 1958).

**This chapter develops the first of the three approaches** by incorporating into the basic neoclassical model agents whose utility depends directly on their consumption of goods and their holdings of money.

## 2.2 The Basic MIU Model

To develop the basic MIU approach, we will initially ignore uncertainty and any labor-leisure choice, focusing instead on the implications of the model for money demand, the value of money, and the costs of inflation.

Suppose that the utility function of the representative household takes the form:

$$
U_{t}=u\left(c_{t}, z_{t}\right)
$$
where $z_t $ is the flow of services yielded by money holdings and $ c_t $ is time t per capita consumption. $ \lim _{z \rightarrow 0} u_{z}(c, z)=\infty $ for all $ c, $ where $ u_{z}=\partial u(c, z) / \partial z $.
$$
z_{t}=\frac{M_{t}}{P_{t} N_{t}} \equiv m_{t}
$$
where $M_t$ is total nominal money, $P_t$ is price level, $N_t$ is population.

The representative household is viewed as choosing time paths for consumption and real money balances subject to budget constraints to be specified, with total utility given by:
$$
W=\sum_{t=0}^{\infty} \beta^{t} u\left(c_{t}, m_{t}\right)  \tag{2.1}
$$
where $ \beta $ is a subjective rate of discount($ 0<\beta<1$).

the aggregate economywide budget constraint of the household sector takes the form:
$$
Y_{t}+\tau_{t} N_{t}+(1-\delta) K_{t-1}+\frac{\left(1+i_{t-1}\right) B_{t-1}}{P_{t}}+\frac{M_{t-1}}{P_{t}}=C_{t}+K_{t}+\frac{M_{t}}{P_{t}}+\frac{B_{t}}{P_{t}} \tag{2.2}
$$

where $Y_t$ is aggregate output, $K_t$is the aggregate stock of capital at the start of period t, $\delta$ is the rate of depreciation of physical capital,  $\tau_t N_t$ is the aggregate real value of any lump-sum transfers or taxes, $B_t$ is the amount of bond, $i_t$ is nominal interest rate.

The timing implicit in this specification of the MIU model assumes that it is the household’s real money holdings at the end of the period, $M_t/P_t$, after having purchased consumption goods, that yield utility.

The aggregate production function relates output $ Y_{t} $ to the available capital stock $ K_{t-1} $ and employment $ N_{t}: Y_{t}=F\left(K_{t-1}, N_{t}\right) .^{7} $ Assuming that this production function is linear homogeneous with constant returns to scale, output per capita $ y_{t} $ will be a function of the per capita capital stock $ k_{t-1}: 8 $
$ y_{t}=f\left(\frac{k_{t-1}}{1+n}\right) $

Dividing both sides of the budget constraint (2.2) by population     , the per capita version becomes:

$ \omega_{t} \equiv f\left(\frac{k_{t-1}}{1+n}\right)+\tau_{t}+\left(\frac{1-\delta}{1+n}\right) k_{t-1}+\frac{\left(1+i_{t-1}\right) b_{t-1}+m_{t-1}}{\left(1+\pi_{t}\right)(1+n)}=c_{t}+k_{t}+m_{t}+b_{t} $
where $ \pi_{t} $ is the rate of inflation, $ b_{t}=B_{t} / P_{t} N_{t}, $ and $ m_{t}=M_{t} / P_{t} N_{l} $


The household’s problem is to choose paths for                      to maximize (2.1) subject to (2.4). This is a problem  in dynamic optimization, and it is convenient to formulate the problem in terms of a value function. The value function gives the maximized present discounted value of utility that the household can achieve by optimally choosing consumption, capital holdings, bond holdings, and money balances, given its current state.

The state variable for the problem is the household’s initial level of resources    , and the value function is defined by:

$$
V\left(\omega_{t}\right)=\max _{c_{t}, k_{t}, b_{t}, m_{t}}\left\{u\left(c_{t}, m_{t}\right)+\beta V\left(\omega_{t+1}\right)\right\}
$$

Using (2.4) to express $ k_{t} $ as $ \omega_{t}-c_{t}-m_{t}-b_{t} $ and making use of the definition of
(2.5) can be written as $ \omega_{t+1} $

$$
\begin{aligned}
V\left(\omega_{t}\right)=\max _{c_{t}, b_{t}, m_{t}}\{& u\left(c_{t}, m_{t}\right)+\beta V\left(\frac{f\left(\omega_{t}-c_{t}-m_{t}-b_{t}\right)}{1+n}+\tau_{t+1}\right.\\
&\left.\left.+\left(\frac{1-\delta}{1+n}\right)\left(\omega_{t}-c_{t}-m_{t}-b_{t}\right)+\frac{\left(1+i_{t}\right) b_{t}+m_{t}}{\left(1+\pi_{t+1}\right)(1+n)}\right)\right\}
\end{aligned}
$$

with the maximization problem now an unconstrained one over $ c_{t}, b_{t}, $ and $ m_{t} . $ The first-order necessary conditions for this problem are
$ u_{c}\left(c_{t}, m_{t}\right)-\frac{\beta}{1+n}\left[f_{k}\left(k_{t}\right)+1-\delta\right] V_{\omega}\left(\omega_{t+1}\right)=0 $
$ \frac{1+i_{t}}{\left(1+\pi_{t+1}\right)(1+n)}-\left[\frac{f_{k}\left(k_{t}\right)+1-\delta}{1+n}\right]=0 $
$ u_{m}\left(c_{t}, m_{t}\right)-\beta\left[\frac{f_{k}\left(k_{t}\right)+1-\delta}{1+n}\right] V_{\omega}\left(\omega_{t+1}\right)+\frac{\beta V_{\omega}\left(\omega_{t+1}\right)}{\left(1+\pi_{t+1}\right)(1+n)}=0 $

$ f_{k}(k)-\delta=r $
$ f_{k}(k)-\delta+1=? $
$ f_{k}(k)-\delta+1=1+r $
$ f_{k}(k)-\delta+1=1+r=\frac{1+i}{1+\pi} $

together with the transversality conditions
$ \lim _{t \rightarrow \infty} \beta^{t} \lambda_{t} x_{t}=0 \quad $ for $ x=k, b, m $
where $ \lambda_{t} $ is the marginal utility of period $ t $ consumption. The envelope theorem implies
$ V_{\omega}\left(\omega_{t}\right)=\frac{\beta}{1+n}\left[f_{k}\left(k_{t}\right)+1-\delta\right] V_{\omega}\left(\omega_{t+1}\right) $
which together with (2.6) yields
$ \lambda_{t}=u_{c}\left(c_{t}, m_{t}\right)=V_{\omega}\left(\omega_{t}\right) $

Using (2.6) and (2.10),(2.8) can be written as
$ u_{m}\left(c_{t}, m_{t}\right)+\frac{\beta u_{c}\left(c_{t+1}, m_{t+1}\right)}{\left(1+\pi_{t+1}\right)(1+n)}=u_{c}\left(c_{t}, m_{t}\right) $
which states that the marginal benefit of adding to money holdings at time $ t $ must equal the marginal utility of consumption at time $ t $. The marginal benefit of additional money holdings has two components. First, money directly yields utility $ u_{m} $. Second, real money balances at time $ t $ add $ 1 /\left(1+\pi_{t+1}\right)(1+n) $ to real per capita resources at time $ t+1 ; $ this addition to $ \omega_{t+1} $ is worth $ V_{\omega}\left(\omega_{t+1}\right) $ at $ t+1, $ or $ \beta V_{\omega}\left(\omega_{t+1}\right) $ at time $ t $. Thus, the total marginal benefit of money at time $ t $ is $ u_{m}\left(c_{t}, m_{t}\right)+ $ $ \beta V_{\omega}\left(\omega_{t+1}\right) /\left(1+\pi_{t+1}\right)(1+n) $. Equation (2.11) is then obtained by noting that $ V_{\omega}\left(\omega_{t+1}\right)=u_{c}\left(c_{t+1}, m_{t+1}\right) $

From $ (2.6),(2.7), $ and (2.11)
$ \frac{u_{m}\left(c_{t}, m_{t}\right)}{u_{c}\left(c_{t}, m_{t}\right)}=1-\left[\frac{1}{\left(1+\pi_{t+1}\right)(1+n)}\right] \frac{\beta u_{c}\left(c_{t+1}, m_{t+1}\right)}{u_{c}\left(c_{t}, m_{t}\right)} $
$ \quad=1-\frac{1}{\left(1+r_{t}\right)\left(1+\pi_{t+1}\right)} $
$ \quad=\frac{i_{t}}{1+i_{t}} \equiv \Upsilon_{t} $

where $ 1+r_{t} \equiv f_{k}\left(k_{t}\right)+1-\delta $ is the real return on capital, and (2.6) implies $ \beta u_{c}\left(c_{t+1}, m_{t+1}\right) / u_{c}\left(c_{t}, m_{t}\right)=(1+n) /\left(1+r_{t}\right) $. Equation (2.12) also makes use of (2.7)
which links the nominal return on bonds, inflation, and the real return on capital. This latter equation can be written as
$ 1+i_{t}=\left[f_{k}\left(k_{t}\right)+1-\delta\right]\left(1+\pi_{t+1}\right)=\left(1+r_{t}\right)\left(1+\pi_{t+1}\right) $
If one notes that $ (1+x)(1+y) \approx 1+x+y $ when $ x $ and $ y $ are small, (2.13) is often written as
$ i_{t}=r_{t}+\pi_{t+1} $

To interpret (2.12) , consider a very simple choice problem in which the agent must pick $ x $ and $ z $ to maximize $ u(x, z) $ subject to a budget constraint of the form $ x+p z= $ $ y $, where $ p $ is the relative price of $ z $. The first-order conditions imply $ u_{z} / u_{x}=p $; in words, the marginal rate of substitution between $ z $ and $ x $ equals the relative price of
$ z $ in terms of $ x $

### 2.2.1 Steady-State Equilibrium

Consider the properties of this economy when it is in a steady-state equilibrium with         and the nominal supply of money growing at the rate   . Let the superscript    denote values evaluated at the steady state.

Note that with real money balances constant in the steady state, it must be that the prices are growing at the same rate as the nominal stock of money, or        .           Using (2.10) to eliminate           , the equilibrium conditions can be written as:

$ u_{c}\left(c^{s s}, m^{s s}\right)-\beta\left[f_{k}\left(k^{s s}\right)+1-\delta\right] u_{c}\left(c^{s s}, m^{s s}\right)=0 $
$ \frac{1+i^{s s}}{1+\theta}-\left[f_{k}\left(k^{s s}\right)+1-\delta\right]=0 $
$ u_{m}\left(c^{s s}, m^{s s}\right)-\beta\left[f_{k}\left(k^{s s}\right)+1-\delta\right] u_{c}\left(c^{s s}, m^{s s}\right)+\frac{\beta u_{c}\left(c^{s s}, m^{s s}\right)}{1+\theta}=0 $
$ f\left(k^{s s}\right)+\tau^{s s}+(1-\delta) k^{s s}+\frac{m^{s s}}{1+\theta}=c^{s s}+k^{s s}+m^{s s} $

where $ \omega^{s s}=f\left(k^{s s}\right)+\tau^{s s}+(1-\delta) k^{s s}+m^{s s} /(1+\pi) . $ In $ (2.14)-(2.17), $ use has been
made of the fact that in the equilibrium of this representative agent model, $ b=0 $. Equation (2.15) is the steady-state form of the Fisher relationship linking real and nominal interest rates. This can be seen by noting that the real return on capital (net of depreciation) is $ r^{s s} \equiv f_{k}\left(k^{s s}\right)-\delta, $ so (2.15) can be written as
$ 1+i^{s s}=\left(1+r^{s^{s}}\right)(1+\theta)=\left(1+r^{s s}\right)\left(1+\pi^{s s}\right) $

neutrality of money
Notice that in (2.14)–(2.17) money appears only in the form of real money balances. Thus, any change in the nominal quantity of money that is matched by a proportional change in the price level, leaving  unchanged, has no effect on the economy’s real equilibrium.

Dividing (2.14) by $ u_{c}\left(c^{s s}, m^{s s}\right) $ yields $ 1-\beta\left[f_{k}\left(k^{s s}\right)+1-\delta\right]=0,0 r $
$ f_{k}\left(k^{s S}\right)=\frac{1}{\beta}-1+\delta $
This equation defines the steady-state capital-labor ratio $ k^{s s} $ as a function of $ \beta $ and
$ \delta $. If the production function is Cobb-Douglas, say $ f(k)=k^{\alpha} $ for $ 0<\alpha \leq 1, $ then $ f_{k}(k)=\alpha k^{\alpha-1} $ and
$ k^{s s}=\left[\frac{\alpha \beta}{1+\beta(\delta-1)}\right]^{1 /(1-\alpha)} $

Because changes in the nominal quantity of money are engineered in this model by making lump-sum transfers to the public, the real value of these transfers must equal $ \left(M_{t}-M_{t-1}\right) / P_{t}=\theta M_{t-1} / P_{t}=\theta m_{t-1} /\left(1+\pi_{t}\right) . $ Hence, steady-state transfers are given by $ \tau^{s s}=\theta m^{s s} /\left(1+\pi^{s s}\right)=\theta m^{s s} /(1+\theta), $ and the budget constraint (2.17) reduces to the economy's resource constraint
$ c^{s s}=f\left(k^{s s}\right)-\delta k^{s s} $
Assuming that $ f(k)=k^{\alpha}, $ then $ k^{s s} $ is given by (2.20) and

$$
c^{s s}=\left[\frac{\alpha \beta}{1+\beta(\delta-1)}\right]^{\alpha /(1-\alpha)}-\delta\left[\frac{\alpha \beta}{1+\beta(\delta-1)}\right]^{1 /(1-\alpha)}
$$

superneutrality of money
the steady-state values of the capital stock, consumption, and output are all independent of the rate of growth of the nominal money stock. 
Since the real rate of interest is equal to the marginal product of capital, it also is invariant across steady states that differ only in their rates of money growth. 
the Sidrauski MIU model possesses the properties of both neutrality and superneutrality.

To understand why superneutrality holds, note that from $ (2.10), u_{c}=V_{\omega}\left(\omega_{t}\right), $ so using (2.6)
$ u_{c}\left(c_{t}, m_{t}\right)=\beta\left[f_{k}\left(k_{t}\right)+1-\delta\right] u_{c}\left(c_{t+1}, m_{t+1}\right) $
or
$ \frac{u_{c}\left(c_{t+1}, m_{t+1}\right)}{u_{c}\left(c_{t}, m_{t}\right)}=\frac{1 / \beta}{f_{k}\left(k_{t}\right)+1-\delta} $

Recall from (2.19) that the right side of this expression is equal to 1 in the steady state.
Discussion:               and 

Recall from (2.19) that the right side of this expression is equal to 1 in the steady state. If $ k<k^{s s} $ so that $ f_{k}(k)>f_{k}\left(k^{s s}\right), $ then the right side is smaller than $ 1, $ and the marginal utility of consumption will be declining over time. It will be optimal to postpone consumption to accumulate capital and have consumption grow over time (so $ u_{c} $ declines over time). As long as $ f_{k}+1-\delta>1 / \beta, $ this process continues, but as the capital stock grows, the marginal product of capital declines until eventually $ f_{k}(k)+1-\delta=1 / \beta . $ The converse holds if $ k>k^{s s} $. Consumption remains constant only when $ f_{k}+1-\delta=1 / \beta . $ If an increase in the rate of money growth (and therefore an increase in the rate of inflation) were to induce households to accumulate more capital, this would lower the marginal product of capital, leading to a situation in which $ f_{k}+1-\delta<1 / \beta . $ Households would then want their consumption path to decline over time, so they would immediately attempt to increase current consumption and reduce their holdings of capital. The value of $ k^{s s} $ consistent with a steady state is independent of the rate of inflation.


What is affected by the rate of inflation?
One thing to expect is that the interest rate on any asset that pays off in units of money at some future date will be affected; the real value of those future units of money will be affected by inflation, and this will be reflected in the interest rate required to induce individuals to hold the asset, as shown by (2.13).

Existence of the Steady State
To ensure that a steady-state monetary equilibrium exists, there must exist a positive but finite level of real money balances      that satisfies (2.12), evaluated at the steady-state level of consumption.

When $ u(c, m)=v(c)+\phi(m), $ the dynamics of real balances around the steady state can be described easily by multiplying both sides of (2.12) by $ M_{t} $ and noting that $ M_{t+1}=(1+\theta) M_{i} $
$ B\left(m_{t+1}\right) \equiv \frac{\beta}{1+\theta} v_{c}\left(c_{s s}\right) m_{t+1}=\left[v_{c}\left(c^{s s}\right)-\phi_{m}\left(m_{t}\right)\right] m_{t} \equiv A\left(m_{t}\right) $

A steady-state value for m satisfies                    . The functions                     are illustrated in figure 2.1.

![](https://cdn.jsdelivr.net/gh/henrywu97/FigBed/Figs/20210305205112.png)

Discussion:

a. $ \lim _{m \rightarrow 0} \phi_{m} m=0 $
b. $ \lim _{m \rightarrow 0} \phi_{m} m=\tilde{m}>0 $         

### 2.2.2 Steady States with a Time-Varying Money Stock

when the focus is on the relationship between money and prices, one might be more interested in a steady state in which real quantities such as consumption and the capital stock are constant but the growth rate of money varies over time.

Assume that                       all t. Setting population growth n to zero and using (2.10), the equilibrium conditions (2.6) and (2.7) can be written as:

$ u_{c}\left(c^{*}, m_{t}\right)=\beta\left[f_{k}\left(k^{*}\right)+1-\delta\right] u_{c}\left(c^{*}, m_{t+1}\right) $
$ \frac{1+i_{t}}{\left(1+\pi_{t+1}\right)}=\left[f_{k}\left(k^{*}\right)+1-\delta\right] $
and (2.12) implies
$ \frac{u_{m}\left(c^{*}, m_{t}\right)}{u_{c}\left(c^{*}, m_{t}\right)}=\frac{i_{t}}{1+i_{t}} $
The budget constraint becomes
$ c^{*}=f\left(k^{*}\right)-\delta k^{*} $

and the evolution of the real stock of money is given by
$ m_{t}=\left(\frac{1+\theta_{t}}{1+\pi_{t}}\right) m_{t-1} $
If $ \theta $ is constant, one has the situation previously studied. There is a steady state with inflation equal to the rate of growth of money $ (\pi=\theta) $, and real money balances are constant. With $ m $ constant, (2.24) uniquely determines the capital stock such that $ \beta\left[f_{k}\left(k^{s s}\right)+1-\delta\right]=1 $. The economy's resource constraint then determines $ c^{*} $.

There may also be steady-state equilibria in which    is changing over time. Reis (2007) investigated how monetary policies that allow the monetary stock to be time-varying can alter the steady-state values of consumption and capital.
consider (2.24) for, then:

$ \frac{u_{c}\left(c^{*}, m_{t+1}\right)}{u_{c}\left(c^{*}, m_{t}\right)}=\frac{1}{\beta\left[f_{k}\left(k^{*}\right)+1-\delta\right]}>1 $


   a steady state that satisfies (2.28) may not be feasible.

If, following Fischer $ (1979 \mathrm{~b}) $, the utility function takes the form
$ u(c, m)=\frac{\left(c^{1-\gamma} m^{\prime}\right)^{1-\eta}}{1-\eta} $
with $ \eta<1 $ and $ \gamma \in(0,1) $, then (2.28) requires that real money balances evolve according to
$ \left(\frac{m_{t+1}}{m_{t}}\right)=\left\{\frac{1}{\beta\left[f_{k}\left(k^{*}\right)+1-\delta\right]}\right\}^{1 /(1-\gamma(1-\eta))} . $

Rather than characterize the steady state in terms of the growth rate of the nominal stock of money, Reis (2007) examined the behavior of the nominal interest rate directly, since central banks today generally employ a nominal interest rate and not a nominal quantity as their policy instrument. The equilibrium condition (2.26) implicitly defines a money demand function of the form
$ m_{t}=\phi\left(i_{t}, c^{*}\right) $
so (2.29) implies the path of the nominal rate must satisfy
$ \frac{\phi\left(i_{t+1}, c^{*}\right)}{\phi\left(i_{t}, c^{*}\right)}=\left\{\frac{1}{\beta\left[f_{k}\left(k^{*}\right)+1-\delta\right]}\right\}^{1 /(1-\gamma(1-\eta))} $

Returning to $ (2.12), $ this equation characterizes the demand for real money balances as a function of the nominal rate of interest and real consumption. For example, suppose that the utility function in consumption and real balances is of the constant elasticity of substitution (CES) form:
$ u\left(c_{t}, m_{t}\right)=\left[a c_{t}^{1-b}+(1-a) m_{t}^{1-b}\right]^{1 /(1-b)} $
with $ 0<a<1 $ and $ b>0, b \neq 1 $. Then
$ \frac{u_{m}}{u_{c}}=\left(\frac{1-a}{a}\right)\left(\frac{c_{t}}{m_{t}}\right)^{b} $
and (2.12) can be written $ \mathrm{as}^{21} $
$ m_{t}=\left(\frac{1-a}{a}\right)^{1 / b}\left(\frac{i}{1+i}\right)^{-1 / b} c_{t} $

In terms of the more common log specification used to model empirical money demand equations,
$ \log \frac{M_{t}}{P_{t} N_{t}}=\frac{1}{b} \log \left(\frac{1-a}{a}\right)+\log c-\frac{1}{b} \log \frac{i}{1+i}, $

The interest elasticity of money demand
The elasticity of money demand with respect to the opportunity cost variable                         . For simplicity, this will often be referred to as the interest elasticity of money demand.

While the parameter b governs the interest elasticity of demand, the steady-state level of money holdings depends on the value of a. From (2.31), the ratio of real money balances to consumption in the steady state will be:

$ \frac{m^{s s}}{c^{s s}}=\left(\frac{1-a}{a}\right)^{1 / b}\left(\frac{1+\pi^{s s}-\beta}{1+\pi^{s s}}\right)^{-1 / b} $


Empirical Evidence on the Interest Elasticity of Money Demand
The empirical literature on money demand is vast.

### 2.2.4 Limitations

In the MIU model, there is a clearly defined reason for individuals to hold money—it provides utility. However, this essentially solves the problem of generating a positive demand for money by assumption; it doesn’t address the reasons that money, particularly money in the form of unbacked pieces of paper, might yield utility.

## 2.3 The Welfare Cost of Inflation

Because money holdings yield direct utility and higher inflation reduces real money balances, inflation generates a welfare loss. This raises two questions: How large is the welfare cost of inflation? Is there an optimal rate of inflation that maximizes the steady-state welfare of the representative household?

The second question—the optimal rate of inflation—was originally addressed by Bailey (1956) and M. Friedman (1969).The optimal rate of inflation is a rate of deflation approximately equal to the real return on capital.
The major criticism of this result is due to Phelps (1973), who pointed out that money growth generates revenue for the government—the inflation tax.

Now let’s return to the first question—what is the welfare cost of inflation?
Beginning with Bailey (1956), this welfare cost has been calculated from the area under the money demand curve (showing money demand as a function of the nominal rate of interest) because this provides a measure of the consumer surplus lost as a result of having a positive nominal rate of interest.

Figure 2.2  real money balances

![](https://cdn.jsdelivr.net/gh/henrywu97/FigBed/Figs/20210305205026.png)

Welfare costs of inflation as measured by the area under the demanded curve.

Nominal interest rates reflect expected inflation, so calculating the area under the money demand curve provides a measure of the costs of anticipated inflation and is therefore appropriate for evaluating the costs of alternative constant rates of inflation. There are other costs of inflation associated with tax distortions and with
variability in the rate of inflation; these are discussed in the survey on the costs of inflation by Driffill, Mizon, and Ulph (1990); relative price distortions generated by inflation when prices are sticky are discussed in chapter 8 .

Lucas (1994) provided estimates of the welfare costs of inflation by starting with the following specification of the instantaneous utility function:
$ u(c, m)=\frac{1}{1-\sigma}\left\{\left[c \varphi\left(\frac{m}{c}\right)\right]^{1-\sigma}-1\right\} $
With this utility function, (2.12) becomes
$ \frac{u_{m}}{u_{c}}=\frac{\varphi^{\prime}(x)}{\varphi(x)-x \varphi^{\prime}(x)}=\frac{i}{1+i}=\Upsilon $

Lucas proposed to measure the costs of inflation by the percentage increase in steady-state consumption necessary to make the household indifferent between a nominal interest rate of i and a nominal rate of 0. If this cost is denoted       , it is defined by:

$ u(1+w(\Upsilon), m(\Upsilon)) \equiv u\left(1, m^{*}\right) $

where       denotes the solution of (2.34) for real money balances evaluated at steady-state consumption       .

Lucas (2000) calculated the welfare costs of inflation for two alternative specifications of money demand. The first takes the form
$ \ln (m)=\ln (A)-\eta \ln (i) $
the second takes the form
$ \ln (m)=\ln (B)-\xi i $

## 2.4 Extensions

### 2.4.1 Interest on Money

If the welfare costs of inflation are related to the positive private opportunity costs of holding money, paying explicit interest on money would be an alternative to deflation as a means of eliminating these costs. There are obvious technical difficulties in paying interest on cash, but ignoring these, assume that the government pays a nominal interest rate of $ i^{m} $ on money balances. Assume further that these interest payments are financed by lump-sum taxes $ s $. The household's budget constraint, (2.4) , now becomes (setting $ n=0) $

$$
f\left(k_{t-1}\right)-s_{t}+\tau_{t}+(1-\delta) k_{t-1}+\left(1+r_{t-1}\right) b_{t-1}+\frac{1+i_{t}^{m}}{1+\pi_{t}} m_{t-1}=c_{t}+k_{t}+m_{t}+b_{t}
$$

and the first-order condition (2.8) becomes
$ -u_{c}\left(c_{t}, m_{t}\right)+u_{m}\left(c_{t}, m_{t}\right)+\frac{\beta\left(1+i_{t}^{m}\right) V_{\omega}\left(\omega_{t+1}\right)}{\left(1+\pi_{t+1}\right)}=0 $
whereas (2.12) is now
$ \frac{u_{m}\left(c_{t}, m_{t}\right)}{u_{c}\left(c_{t}, m_{t}\right)}=\frac{i_{t}-i_{t}^{m}}{1+i_{t}} $


the optimal quantity of money can be achieved as long as              , regardless of the rate of inflation. If          , so that the rate of inflation in the steady state is also zero, the optimal quantity of money is obtained with a positive nominal interest rate as long as                     .

2.4.2 Nonsuperneutrality
suppose utility depends on consumption, real money holdings, and leisure:

The economy’s production function becomes

where n is employment. If the total supply of time is normalized to equal 1, then n=1-l. The additional first-order condition implied by the optimal choice of leisure is:

$ \frac{u_{l}(c, m, l)}{u_{c}(c, m, l)}=f_{n}(k, 1-l) $

Now, both steady-state labor supply and consumption may be affected by variations in the rate of inflation. Specifically, an increase in the rate of inflation reduces holdings of real money balances. If this affects the marginal utility of leisure, then (2.43) implies the supply of labor will be affected, leading to a change in the steady-state per capita stock of capital, output, and consumption.

Equation (2.43) suggests that if $ u_{l} / u_{c} $ were independent of $ m, $ then superneutrality would hold. This is the case because the steady-state values of $ k, c, $ and $ l $ could then be found from
$ \frac{u_{l}}{u_{c}}=f_{n}\left(k^{s s}, 1-l^{s s}\right), $
$ f_{k}\left(k^{s s}, 1-l^{s s}\right)=\frac{1}{\beta}-1+\delta $
and
$ c^{s s}=f\left(k^{s s}, 1-l^{s s}\right)+\delta k^{s s} . $

## 2.5 Dynamics in an MIU Model

The analysis of the MIU approach has, up to this point, focused on steady-state properties. It is also important to understand the model’s implications for the dynamic behavior of the economy as it adjusts to exogenous disturbances.
One way to study the model’s dynamics is to employ numerical methods to carry out simulations using the model.

### 2.5.1 The Decision Problem

When the household chooses how much labor to supply, current income is no longer predetermined from the perspective of the household’s choices of money, bonds, and capital investment. Consequently, income (output)    cannot be part of the state vector for period t. Instead, let

$ a_{t}=\tau_{t}+\left[\left(1+i_{t-1}\right) /\left(1+\pi_{t}\right)\right] b_{t-1}+\left[1 /\left(1+\pi_{t}\right)\right] m_{t-1} $


be the household’s real financial wealth plus transfer at the start of period t.

output per household     is given by:

$$
y_{t}=f\left(k_{t-1}, n_{t}, z_{t}\right)
$$

The household's decision problem is defined by

$$
V\left(a_{t}, k_{t-1}\right)=\max \left\{u\left(c_{t}, m_{t}, 1-n_{t}\right)+\beta \mathrm{E}_{t} V\left(a_{t+1}, k_{t}\right)\right\},
$$

where the maximization is over $ \left(c_{t}, m_{t}, b_{t}, k_{t}, n_{t}\right) $ and is subject to

$$
\begin{array}{l}
f\left(k_{t-1}, n_{t}, z_{t}\right)+(1-\delta) k_{t-1}+a_{t} \geq c_{t}+k_{t}+b_{t}+m_{t} \\
a_{t+1}=\tau_{t+1}+\left(\frac{1+i_{t}}{1+\pi_{t+1}}\right) b_{t}+\frac{m_{t}}{1+\pi_{t+1}}
\end{array}
$$

Equation (2.45) will always hold with equality (as long as $ \left.u_{c}>0\right) $; it can be used to eliminate $ k_{t} $, and (2.46) can be used to substitute for $ a_{t+1} $, allowing the value function
to be rewritten as

$$
\begin{array}{c}
V\left(a_{t}, k_{t-1}\right)=\max _{c_{t}, n_{t}, b_{t}, m_{t}}\left\{u\left(c_{t}, m_{t}, 1-n_{t}\right)+\beta \mathrm{E}_{t} V\left(\tau_{t+1}+\left(\frac{1+i_{t}}{1+\pi_{t+1}}\right) b_{t}+\frac{m_{t}}{1+\pi_{t+1}}\right.\right. \\
\left.\left.f\left(k_{t-1}, n_{t}, z_{t}\right)+(1-\delta) k_{t-1}+a_{t}-c_{t}-b_{t}-m_{t}\right)\right\}
\end{array}
$$

where this is now an unconstrained maximization problem. The first-order necessary conditions with respect to $ c_{t}, n_{t}, b_{t}, $ and $ m_{t} $ are
$ u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)-\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right)=0 $
$ -u_{l}\left(c_{t}, m_{t}, 1-n_{t}\right)+\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right) f_{n}\left(k_{t-1}, n_{t}, z_{t}\right)=0 $
$ \beta \mathrm{E}_{t}\left(\frac{1+i_{t}}{1+\pi_{t+1}}\right) V_{a}\left(a_{t+1}, k_{t}\right)-\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right)=0 $
$ u_{m}\left(c_{t}, m_{t}, 1-n_{t}\right)+\beta \mathrm{E}_{t}\left[\frac{V_{a}\left(a_{t+1}, k_{t}\right)}{1+\pi_{t+1}}\right]-\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right)=0 $
and the envelope theorem yields
$ V_{a}\left(a_{t}, k_{t-1}\right)=\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right) $
$ V_{k}\left(a_{t}, k_{t-1}\right)=\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right)\left[1-\delta+f_{k}\left(k_{t-1}, n_{t}, z_{t}\right)\right] $

Updating (2.52) one period and using $ (2.51), $ one obtains
$ V_{k}\left(a_{t+1}, k_{t}\right)=\mathrm{E}_{t}\left\{\left[1-\delta+f_{k}\left(k_{t}, n_{t+1}, z_{t+1}\right)\right] V_{a}\left(a_{t+1}, k_{t}\right)\right\} $
Now substituting this for $ V_{k}\left(a_{t+1}, k_{t}\right) $ in (2.47) yields
$ u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)-\beta \mathrm{E}_{t}\left\{\left[1-\delta+f_{k}\left(k_{t}, n_{t+1}, z_{t+1}\right)\right] V_{a}\left(a_{t+1}, k_{t}\right)\right\}=0 $
When it is recognized that $ u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)=\beta \mathrm{E}_{t} V_{k}\left(a_{t+1}, k_{t}\right),(2.50),(2.53), $ and
(2.51) take the same form as (2.8),(2.6) , and $ (2.10), $ the first-order conditions for the basic Sidrauski model, which did not include a labor-leisure choice. The only new condition is (2.48) , which can be written, using (2.47) , as
$ \frac{u_{l}\left(c_{t}, m_{t}, 1-n_{t}\right)}{u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)}=f_{n}\left(k_{t-1}, n_{t}, z_{t}\right) $

The equilibrium values of consumption, capital, money holdings, and labor supply must satisfy the conditions given in $ (2.47)-(2.51) . $ These conditions can be simplified, however. Note that $ (2.47),(2.49), $ and (2.51) imply that

$$
u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)=\beta\left(1+i_{t}\right) \mathrm{E}_{t}\left[\frac{u_{c}\left(c_{t+1}, m_{t+1}, 1-n_{t+1}\right)}{1+\pi_{t+1}}\right]
$$

Using this relationship and $ (2.47), $ one can now write $ (2.50),(2.48), $ and (2.53) as

$$
\begin{array}{l}
u_{m}\left(c_{t}, m_{t}, 1-n_{t}\right)=u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)\left(\frac{i_{t}}{1+i_{t}}\right) \\
u_{l}\left(c_{t}, m_{t}, 1-n_{t}\right)=u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right) f_{n}\left(k_{t-1}, n_{t}, z_{t}\right) \\
u_{c}\left(c_{t}, m_{t}, 1-n_{t}\right)=\beta \mathrm{E}_{t}\left(1+r_{t}\right) u_{c}\left(c_{t+1}, m_{t+1}, 1-n_{t+1}\right)
\end{array}
$$

where, in (2.56)
$ r_{t}=f_{k}\left(k_{t}, n_{t+1}, z_{t+1}\right)-\delta $
is the marginal product of capital net of depreciation. In addition, the economy's aggregate resource constraint, expressed in per capita terms, requires that
$ k_{t}=(1-\delta) k_{t-1}+y_{t}-c_{t} $
and the production function is
$ y_{t}=f\left(k_{t-1}, n_{t}, z_{t}\right) $

Finally, real money balances evolve according to
$ m_{t}=\left(\frac{1+\theta_{t}}{1+\pi_{t}}\right) m_{t-1} $
where $ \theta_{t} $ is the stochastic growth rate of the nominal stock of money. Once processes for the exogenous disturbances $ z_{t} $ and $ \theta_{t} $ have been specified, equations $ (2.54)-(2.60) $ constitute a nonlinear system of equations to determine the equilibrium values of the model's seven endogenous variables: $ y_{t}, c_{t}, k_{t}, m_{t}, n_{t} $,
$ r_{t}, \pi_{t} $

Consider a steady-state equilibrium of this model in which all real variables (including $ m $ ) are constant and shocks are set to zero. It follows immediately from (2.56) that $ 1+r^{s s}=\beta^{-1} $ and from (2.57) that
$ f_{k}\left(k^{s s}, n^{s s}, 0\right)=\beta^{-1}-1+\delta $

With constant returns to scale, $ \phi(k / n)=f / n $ can be defined as the intensive production function. Then, from the economy's resource constraint,
$ c^{s s}=f\left(k^{s s}, n^{s s}, 0\right)-\delta k^{s s}=\left[\phi\left(\frac{k^{s s}}{n^{s s}}\right)-\delta\left(\frac{k^{s s}}{n^{s s}}\right)\right] n^{s s}=\bar{\phi} n^{s s}, $
where $ \bar{\phi} \equiv \phi\left(k^{s s} / n^{s s}\right)-\delta\left(k^{s s} / n^{s s}\right) $ does not depend on anything related to money. Now, (2.55) implies that
$ \frac{u_{l}\left(c^{s s}, m^{s s}, 1-n^{s s}\right)}{u_{c}\left(c^{s s}, m^{s s}, 1-n^{s s}\right)}=f_{n}\left(k^{s s}, n^{s s}, 0\right) $
In the case of constant returns to scale, $ f_{n} $ depends only on $ k^{s s} / n^{s s}, $ which is a function of $ \beta $ and $ \delta $, so using the definition of $ \bar{\phi}, $ one can rewrite this last equation as
$ \frac{u_{l}\left(\bar{\phi} n^{s s}, m^{s s}, 1-n^{s s}\right)}{u_{c}\left(\bar{\phi} n^{s s}, m^{s s}, 1-n^{s s}\right)}=\phi\left(\frac{k^{s s}}{n^{s s}}\right)-\left(\frac{k^{s s}}{n^{s S}}\right) \phi^{\prime}\left(\frac{k^{s s}}{n^{s S}}\right) . $

### 2.5.2 The Steady State

Suppose the utility function is separable in money so that neither the marginal utility of leisure nor the marginal utility of consumption depend on the household’s holdings of real money balances. Then (2.62) becomes:

$ \frac{u_{l}\left(\bar{\phi} n^{s s}, 1-n^{s s}\right)}{u_{c}\left(\bar{\phi} n^{s s}, 1-n^{s s}\right)}=\phi\left(\frac{k^{s s}}{n^{s s}}\right)-\left(\frac{k^{s s}}{n^{s s}}\right) \phi^{\prime}\left(\frac{k^{s s}}{n^{s s}}\right) $

If utility is nonseparable, so that either $ u_{l} $ or $ u_{c} $ (or both) depend on $ m^{s s} $, then
money is not superneutral. Variations in average inflation that affect the opportunity cost of holding money will affect $ m^{s s} $. Different levels of $ m^{s s} $ will change the value of $ n^{s s} $ that satisfies (2.62) . Since $ 1+i^{\$ s}=\left(1+r^{s s}\right)\left(1+\pi^{s s}\right)=\beta^{-1}\left(1+\theta^{s s}\right) $, equation (2.54) can be rewritten as
$ \frac{u_{m}\left(\bar{\phi} n^{s s}, m^{s s}, 1-n^{s s}\right)}{u_{c}\left(\bar{\phi} n^{s s}, m^{s s}, 1-n^{s s}\right)}=\left(\frac{i^{s s}}{1+i^{s S}}\right)=\frac{1+\theta^{s s}-\beta}{1+\theta^{s s}} . $

### 2.5.3 The Linear Approximation

To further explore the effects of money outside the steady state, it is useful to approximate the model’s equilibrium conditions around the steady state.
Percentage deviations of a variable qt around its steady-state value will be denoted by     ,where           
                        .

$ q_{t} \equiv q^{s s}\left(1+\hat{q}_{t}\right) $

As is standard, the production function is taken to be Cobb-Douglas with constant returns to scale, so
$ y_{t}=e^{z_{t}} k_{t-1}^{\alpha} n_{t}^{1-\alpha} $
with $ 0<\alpha<1 $. For the utility function, it is assumed that
$ u\left(c_{t}, m_{t}, 1-n_{t}\right)=\frac{\left[a c_{t}^{1-b}+(1-a) m_{t}^{1-b}\right]^{(1-\Phi) /(1-b)}}{1-\Phi}+\Psi \frac{\left(1-n_{t}\right)^{1-\eta}}{1-\eta} . $

To this system of eight endogenous variables, it will be convenient to add investment, $ x_{t}, $ given by $ x_{t}=k_{t}-(1-\delta) k_{t-1}, $ and to define $ \lambda_{t} $ as the marginal utility of consumption. The linearized expression for $ \hat{\lambda}_{t} $ is $ \hat{\lambda}_{t}=\Omega_{1} \hat{c}_{t}+\Omega_{2} \hat{m}_{t} $
where $ \Omega_{1}=[(b-\Phi) \gamma-b], \Omega_{2}=(b-\Phi)(1-\gamma), $ and the parameter $ \gamma $ is equal to $ a\left(c^{s s}\right)^{1-b} /\left[a\left(c^{s s}\right)^{1-b}+(1-a)\left(m^{s s}\right)^{1-b}\right] $
Then, in linearized form, the equilibrium conditions include (2.65) and (see the chapter appendix):
$ \left(\frac{x^{s s}}{k^{s s}}\right) \hat{x}_{t}=\hat{k}_{t}-(1-\delta) \hat{k}_{t-1} $
$ \hat{y}_{t}=\alpha \hat{k}_{t-1}+(1-\alpha) \hat{n}_{t}+z_{t} $
$ \left(\frac{y^{s s}}{k^{s s}}\right) \hat{y}_{t}=\left(\frac{c^{s s}}{k^{s s}}\right) \hat{c}_{t}+\delta \hat{x}_{t} $

$ \hat{r}_{t}=\alpha\left(\frac{y^{s s}}{k^{s s}}\right)\left(\mathrm{E}_{t} \hat{y}_{t+1}-\hat{k}_{t}\right) $
$ \hat{\lambda}_{t}=\mathrm{E}_{t} \hat{\lambda}_{t+1}+\hat{r}_{t} $
$ -\hat{\lambda}_{t}+\eta\left(\frac{n^{s s}}{1-n^{s s}}\right) \hat{n}_{t}=\hat{y}_{t}-\hat{n}_{t} $
$ \hat{\imath}_{t}=\hat{r}_{t}+\mathrm{E}_{t} \hat{\pi}_{t+1} $
$ \hat{m}_{t}-\hat{c}_{t}=-\left(\frac{1}{b}\right)\left(\frac{1}{i^{s s}}\right) \hat{\imath}_{t} $
$ \hat{m}_{t}=\hat{m}_{t-1}-\hat{\pi}_{t}+u_{t} $
Consistent with the real-business-cycle literature, a stochastic disturbance to total factor productivity is incorporated that follows an AR(1) process:
$ z_{t}=\rho_{z} z_{t-1}+e_{t} $
Assume that $ e_{t} $ is a serially uncorrelated mean zero process and $ \left|\rho_{z}\right|<1 . $ Note the timing convention in (2.67): the capital carried over from period $ t-1, K_{t-1}, $ is available for use in producing output during period $ t $.

It is also necessary to specify the process followed by the nominal stock of money. In previous sections, $ \theta $ denoted the growth rate of the nominal money supply. Assume then that the average growth rate is $ \theta^{s s}, $ and let $ u_{t} \equiv \theta_{t}-\theta^{s s} $ be the deviation in period $ t $ of the growth rate from its unconditional average value. This deviation will be treated as a stochastic process given by
$ u_{t}=\rho_{u} u_{t-1}+\phi z_{t-1}+\varphi_{t}, \quad 0 \leq \gamma<1 $
where $ \varphi_{t} $ is a white noise process and $ \left|\rho_{u}\right|<1 $. This formulation allows the growth rate of the money stock to display persistence $ \left(\right. $ if $ \left.\rho_{u}>0\right) $, respond to the real productivity shock $ z, $ and be subject to random disturbances through the realizations of $ \varphi_{l} $

Separability allows the real equilibrium to be solved independent of money and inflation, but it has more commonly been used in monetary economics to allow the study of inflation and money growth to be conducted independent of the real equilibrium. When $ \Phi=b,(2.73) $ and (2.74) constitute a two-equations system in inflation and real money balances, with $ u $ representing an exogenous random disturbance and $ \hat{c} $ and $ \hat{r} $ determined by $ (2.67)-(2.71) $ and exogenous to the determination of inflation and real money balances. Equation (2.73) can then be written as
$ \mathrm{E}_{t} \pi_{t+1} \equiv \mathrm{E}_{t} \hat{p}_{t+1}-\hat{p}_{t}=-\left(b i^{i s}\right) \hat{m}_{t}+\chi_{t}=-\left(b i^{s s}\right)\left(\hat{M}_{t}-\hat{p}_{t}\right)+\chi_{t} $
This is an expectational difference equation that can be solved for the equilibrium path of $ \hat{p} $ for a given process for the nominal money supply and the exogenous variable $ \chi_{t} \equiv\left[\left(b i^{s s}\right) \hat{c}_{t}-\hat{r}_{t}\right] $

To actually determine how the equilibrium responds to money growth rate shocks and how the response depends quantitatively on             , one must calibrate the parameters of the model and numerically solve for the rational-expectations equilibrium.

### 2.5.4 Calibration

### 2.5.5 Simulation Results

![](https://cdn.jsdelivr.net/gh/henrywu97/FigBed/Figs/20210305220947.png)

![](https://cdn.jsdelivr.net/gh/henrywu97/FigBed/Figs/20210305221031.png)

![](https://cdn.jsdelivr.net/gh/henrywu97/FigBed/Figs/20210305221058.png)

## 2.6 Summary

Assuming that holdings of real money balances yield direct utility is a means of ensuring a positive demand for money so that, in equilibrium, money is held and has value. This assumption is clearly a shortcut; it does not address the issue of why money yields utility or why certain pieces of paper that we call money yield utility but other pieces of paper presumably do not.

The Sidrauski model, because it assumes that agents act systematically to maximize utility, allows welfare comparisons to be made. The model can be used to assess the welfare costs of inflation and to determine the optimal rate of inflation. Friedman’s conclusion that the optimal inflation rate is the rate that produces a zero nominal rate of interest is quite robust (see chapter 4).

Finally, by developing a linear approximation to the basic money-in-the-utility function model (augmented to include a labor supply choice), it was shown how the effects of variations in the growth rate of the money supply on the short-run dynamic adjustment of the economy depended on the effect of money holdings on the marginal utility of consumption and leisure.
