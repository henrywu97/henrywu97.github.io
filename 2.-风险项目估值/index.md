# 

## 2. 风险项目估值

 思想：tracking portfolio

Almost any real world project has risky future cash flows:
$$
\underbrace{C_{0}}_{\text {cost }} \underbrace{\widetilde{C}_{1} \tilde{C}_{3} \ldots \widetilde{C}_{\text {T }}}_{\text {Risky future cash flows }} 
$$

### 2.1 利用远期估值

Main Insight: The forward price of, say, a commodity, represents the certainty equivalent of the future risky price
- Certainty Equivalent of a risky cash flow: Future risk-free cash flow that has the same present value as the risky cash flow

远期价格代表未来风险价格的确定性等价

$$
F_t = S_0(e^{rt})
$$
If

- "The risk in project cash flows stems from future price uncertainty of a particular good (e.g., an input or an output)
- There is a forward market for that good
then the forward price can be used to find the PV of the CF

Procedure:

1. Calculate $C E(\tilde{C}),$ the certainty equivalent of the risky cash flow
2. Discount at the risk-free rate to find the PV:

其本质在于调整分资至无风险

$$
\mathrm{PV}=\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{1}\right)}{1+\bar{r}_{1}}+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{2}\right)}{\left(1+\overline{\mathrm{r}}_{2}\right)^{2}}+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{3}\right)}{\left(1+\overline{\mathrm{r}}_{\mathrm{j}}\right)^{3}}+\ldots \ldots+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{\mathrm{T}}\right)}{\left(1+\overline{\mathrm{r}}_{\mathrm{r}}\right)^{T}}
$$

![](https://upload-images.jianshu.io/upload_images/20447423-673059df766f1183.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/20447423-fb4fddd12b0312c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/20447423-ab0d7b2a9332e8ad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/20447423-426b8ec59911703f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

但现实中往往难以完全复制，即使复制后也可能难以计算。

### 2.2 风险调整的DCF

$$
\mathrm{PV}=\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{1}\right)}{1+\bar{r}_{1}}+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{2}\right)}{\left(1+\overline{\mathrm{r}}_{2}\right)^{2}}+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{3}\right)}{\left(1+\overline{\mathrm{r}}_{\mathrm{j}}\right)^{3}}+\ldots \ldots+\frac{\mathrm{E}\left(\tilde{\mathrm{C}}_{\mathrm{T}}\right)}{\left(1+\overline{\mathrm{r}}_{\mathrm{r}}\right)^{T}}
$$

For now, consider only one future risky cash flow. Our objective is to find its PV:

$$
\frac{t=0}{P V} \frac{t=1}{\widetilde{C}}
$$

Suppose CAPM is the model pricing financial assets. If the project was a traded asset, we would have

$$
\frac{\widetilde{\mathbf{C}}}{\mathrm{PV}}-1=r_{f}+\beta\left(\widetilde{r}_{M}-r_{f}\right)+\varepsilon
$$

where

$$
\beta=\frac{\operatorname{cov}\left(\frac{\widetilde{C}}{P V}, \tilde{r}_{M}\right)}{\operatorname{var}\left(\widetilde{r}_{M}\right)}
$$

Measures the systematic risk of the project

$\cdot$ The CAPM pricing equation is:

$$
\frac{\mathrm{E}(\widetilde{\mathrm{C}})}{\mathrm{PV}}-1=r_{f}+\beta\left(\bar{r}_{M}-r_{f}\right)
$$

Solving for PV, we get

Risk-adjusted discounting using CAPM:

$$
\mathrm{PV}=\underbrace{\frac{\mathrm{E}(\widetilde{\mathrm{C}})}{1+r_{f}+\beta\left(\bar{r}_{M}-r_{f}\right)}}_{\text {Project's cost of capital }}
$$

Risk-adjusted discounting using APT:

$$
\mathrm{PV}=\frac{\mathrm{E}(\widetilde{\mathrm{C}})}{1+r_{f}+\lambda_{1} \beta_{1}+\lambda_{2} \beta_{2}+\ldots+\lambda_{k} \beta_{k}}
$$

Inputs necessary to implement DCF 

- Expected cash flow (i.e., the average free cash flow) 
- If CAPM is used: expected return on the market, and the return beta of the project 
- If APT is used: factor premium for each factor, and the return sensitivity of the project to each factor 
- The risk-free rate

#### $\beta$的估计

In practice “The Comparison Method” is commonly used to implement risk-adjusted discounting: 

–Use public financial information to estimate risk of the business. 

Procedure 

1. Identify a set of companies in the same business (i.e. in the same risk class) 
2. Use regression of companies’ traded equity returns on market (or factor) returns to obtain betas 
3. Adjust for taxes (we will examine tax adjustments later) 
4. Adjust for leverage

Why do we adjust for leverage? 

• We want the beta of comparable businesses (i.e., project, or asset beta) 

• We observe the beta of one of the claims to those assets (the equity beta) 

• The amount of debt financing (leverage) affects the equity beta 

Hence: • We need to adjust the beta of the equity in order to recover the beta of the assets.

Moderate leverage (risk-free debt):

$$
\boldsymbol{\beta}_{A}=\frac{D}{D+E} 0+\frac{E}{D+E} \boldsymbol{\beta}_{E} \Rightarrow \boldsymbol{\beta}_{E}=\left(1+\frac{D}{E}\right) \boldsymbol{\beta}_{A}
$$

High leverage (risky debt):

$$
\begin{aligned}
\beta_{A}=\frac{D}{D+E} \beta_{D}+\frac{E}{D+E} \beta_{E} \Rightarrow \beta_{E} &=\left(1+\frac{D}{E}\right) \beta_{A}-\left(\frac{D}{E}\right) \beta_{D}\\
&=\beta_{A}+(\beta_{A}-\beta_{D}) \cdot L \\
\end{aligned}
$$

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415185409.png)

注意$\beta_D$是L的增函数

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415185542.png)

![](https://upload-images.jianshu.io/upload_images/20447423-28dfe9696b4dac7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/20447423-68847b1c88e9f5cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

d) Leverage does not change the cost of capital of figures

 Levering-up an investment makes it riskier, consequently its return should also increase

![](https://upload-images.jianshu.io/upload_images/20447423-ef692c0c6308ad85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Project Betas vs. Firm Betas 

• It is the risk of project cash flows (and hence project beta) that matters for valuation 

• In practice, most firms use their own (overall) cost of capital in evaluating projects

• No formal method to adjust for project risk

A different discount rate for each maturity? 

• Typically, the beta of a future cash flow will depend on its maturity 

• However, most firms use the same beta for discounting cash flows of all maturities 

• The resulting misvaluation may be severe, especially when the late cash flow pattern is pronounced

Could use long- or short-term risk-free rate, and a corresponding long- or short-term beta

### 2.3 Ratio Comparison Method (Valuation by Multiples)

Commonly used in real estate valuation and by investment banks (M&As, IPOs) 

– Basic Insight: An asset should sell for \$20 if it has twice the annual cash flow of a similar asset that recently sold for \$10 

– Implicit assumptions: 

• Project and comparison cash flows will grow at the same rate 

• Comparison prices are accurate

– Relative valuation
• Do not need to specify how actual prices are determined
• Future expected cash flows and risk are implicit in the comparison price

Procedure 

1. Choose comparable firms 

- Use a large enough sample to average out firms’ idiosyncrasies and eliminate firms that have suffered “abnormal”events (i.e., takeovers) 

2. Choose bases for multiples 

- Generic: Sales, Gross Profits, Operating Profits, Net Income, Book Values 

- Industry Specific: Paid Miles Flown, # of restaurants, # of subscribers, circulation of a newspaper etc. 

3. Average across industry 

- Calculate multiple for each comparable firm and then take the average 

4. Project bases for the valued firm 

5. Value the project (or the firm)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415200514.png)

The most popular version of ratio comparison approach
Procedure:
1. For a comparable business calculate $\frac{P}{E}=k$
2. Estimate project's first year expected earnings $E_{f}$
3. Compute the present value of future cash flows as

$$
P V=E_{f} \cdot k
$$

Future earnings growth rates must be similar

• What if current project earnings are negative?

​	– Start from the first year in which earnings are projected to be positive and discount the resulting price back
​	– Use other multiples

• What if some comparison firms have negative earnings?

​	– May sum the values and the earnings separately and compute the average based on the aggregate value and aggregate earnings

**Leverage effects** 

Leverage may increase P/E (growth firms) or reduce P/E (cash cows with declining earnings) 

**For comparisons, we need to use unlevered** $\mathbf{P} / \mathbf{E}:$ P/E ratio that would obtain if the comparison firm were all-equity financed

$$
\text { Observed (levered) } P / E=\frac{\text { Price }}{\text { Earnings }}=\frac{A-D}{X-r_{D} D}
$$

$A=$ market value of the firm (i.e., debt + equity) 

$X=$ pre-interest earnings 

$D=$ debt value

$r_{D}=\operatorname{cost} \text { of debt }$

Therefore, the unlevered P/E ratio is $\boldsymbol{A} / \boldsymbol{X}$

![ ](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415201517.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415201652.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200726175705.png)

![](https://upload-images.jianshu.io/upload_images/20447423-6e6a1a340bae5bf2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Pros
1. Incorporates a lot of information in a simple way
2. Incorporates market consensus about discount rates and growth rates
3. Provides discipline in valuation process by ensuring that your valuation is
in line with other valuations

Cons

1. Implicitly assumes all companies are alike in growth rates, cost of capital,
  and business composition. Hard to find true comps
2. Difficult to incorporate firm specific information. Particularly problematic
  if operating changes are going to be implemented
3. Accounting differences, particularly with earnings and equity-based
  measures. Multiples of FCF and EBITD may be preferable
4. Provides little intuition on what the sources of value are
  – Why are prices high or low?

In sum, when you have more than five minutes to value a project… DCF is a must!

### 2.4 Terminal Value Calculations

In valuing long-lived projects or ongoing businesses, we cannot forecast every year of cash flows. 

Instead, forecast FCF until it is reasonable to think that the project or company is in “steady state” and estimate a “terminal value”.

$$
\begin{equation}
\text { Project Value }=\sum_{t=0}^{N} \frac{F C F_{t}}{(1+r)^{t}}+\frac{\text { Terminal Value }_{N}}{(1+r)^{N}}
\end{equation}
$$

Typically, terminal value is calculated in one of three ways:

#### 1. Terminal Value as Liquidation Value

Unless liquidation is likely, this method tends to underestimate TV (useful as a lower bound) 

• Liquidation Value depends on Salvage Value and Net Working Capital recovered 

a) Salvage Value (SV): CF that the firm receives from liquidating its assets 

SV = Liquidation price – Liquidation costs 

b) Net Working Capital 

Does firm recoup NWC at project end? 

• If so, last $\Delta $NWC = last NWC 

NWC’s actual value can differ from its book value 

• cannot recoup the A/R fully 

• inventory may sell above or below book value

![](https://upload-images.jianshu.io/upload_images/20447423-4ca86796814005a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. Using Multiples to get Terminal Value

TV = k × MULTIPLE

![](https://upload-images.jianshu.io/upload_images/20447423-84d0955506e33f17.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
