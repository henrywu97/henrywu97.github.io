# 

# 4. Analysis of Capital Structure I: The MM Benchmark

此前介绍的专题为投资决策，接下来介绍公司的融资决策，融资决策的首要问题是确定债务融资与股权融资的比例，即**资本结构**。

【资本结构(Captial Structure)】公司不同资金来源的组合。

问题：

- 资本结构如何影响公司价值？
- 最优资本结构如何确定？

杠杆的不同计算方法

| 公式                                   | 含义         |
| -------------------------------------- | ------------ |
| $\frac{Debt}{Debt+MVEquity}$           | 长期偿债能力 |
| $\frac{Debt}{\text{Total Book Asset}}$ | 历史融资比例 |
| $\frac{EBITD}{Interest}$               | 利息支付能力 |

公司债由于存在不上市流通的部分，难以估值，通常采用账面价值，用账面价值作为市值(MV)的替代变量。

## 4.1 Modigliani-Miller (M&M)

理论框架

1. M&M Theorem (Proposition I): Irrelevance of capital structure

2. M&M and the Cost of Capital (Proposition II)
3. M&M and the irrelevance of Distribution Policy（1961）

提出者

Franco Modigliani(1918), CMU, MIT（凯恩斯学派）, 1985 Nobel Prize(GE, 生命周期理论).

Merton Miller(1923-2000), CMU,Chicago（芝加哥/自由主义学派）, 1990 Nonbel Prize(M&M), 资本结构之父，现代公司金融之父。

- 学生Eugene Fama, 现代金融之父。

- 学生Myron Scholes, 1997 Nobel Prize, 期权定价之父，衍生品之父。

### 4.1.1 M&M Theorem (Proposition I)

【M&M Theorem Ⅰ】假定：

1. 公司总现金流不受资本结构影响
2. 没有交易成本
3. 没有套利机会

则公司总市值不受资本结构影响。

#### 假设Ⅰ

在没有交易成本和套机机会的情况下，资本结构不影响公司的现金流；

MM定理的另一种表述，在没有交易成本和套机机会的情况下，资本结构影响公司的价值当且仅当，资本结构影响公司的现金流。

该假定排除了以下情况：

1. 税收
2. 破产成本
3. Strategic effects: 竞争对手根据该公司资本结构调整战略
4. 债务人对管理层的压力（战略调整等）

直观理解：将饼看作公司的未来现金流

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/image1.png)

#### 假设Ⅱ

无交易成本（证券发行费用，信息不对称），核心在于保证有一个complete & competitive市场

>  Markets are complete: For each state s, there is an Arrow-Debreu security that costs $P_s$ at date 0 to purchase and pays one unit of the consumption good at date 1 if and only if state s occurs.

公司发行的任何证券(任何现金流)都可以在市场上找到替代品(可以被完全复制)。

No value to “financial marketing”：单纯通过分割现金流(e.g.创造出市场偏好的现金流)是不可能获得收益的。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/image-20200409125709932.png)

#### 假设Ⅲ

无套利，金融估值是理性的。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409193604.png)

Proof:

Suppose that the firm's assets will generate a random cash flow $C$ next period (i.e., $C(s)$ in state $s$). Today the firm issues securities $K_{i}(s)$ against this cash flow $(i=1,2, \dots, N$ is the index for different securities like equity, debt, etc.). 

Denote $C_i(s)$ as cash flow next period for security $i(i=1,2,\ldots,N)$ in state $s$, then the firm's cash flow next period $C(s)=\sum_{i=1}^{N}C_i(s)$ for each state $s$.

Complete Markets: For each future state of the world $s,$ there exists an Arrow-Debreu security (i.e., one that pays $\$ 1$ iff $s$ occurs), trading at a market price of $P(s)$. 

By tracking portfolio using Arrow-Debreu security, the security $i$'s value $K_i=\sum_{s=1}^{S}P(s)C_i(s)$.

Then the total value of this firm is 
$$
\begin{aligned}

  V &= \sum_{i=1}^{N}K_i \\

   &= \sum_{i=1}^{N} \sum_{s=1}^{S}\left[P(s)C_i(s)\right] \\

   &= \sum_{s=1}^{S}\sum_{i=1}^{N}\left[P(s)C_i(s)\right] \\

   &= \sum_{s=1}^{S}\left[P(s)\sum_{i=1}^{N}C_i(s)\right] \\

   &= \sum_{s=1}^{S}\left[P(s)C(s)\right]

\end{aligned}
$$
It means that the firm's value is determined by it's cash flow, independent of how it issues securities (M\&M 1).

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409193615.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409193623.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409193655.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409193702.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409204236.png)

### 4.1.2 M&M and the cost of capital

【M&M Theorem Ⅱ】在M&MⅠ的假设下，WACC独立于资本结构。

证明：


$$
\begin{equation}P V=\frac{E(C F)}{1+WACC}\end{equation}
$$
由M&MⅠ，$PV$不随资本结构变化；由假设Ⅰ，$CF$不随资本结构变化。因此$WACC$与资本结构无关。

#### 1. 杠杆增加股权收益率

假设Ⅰ表明无税收，因此
$$
WACC = \bar{r}^*=\frac{D}{V}\bar{r}_{D}+\frac{E}{V}\bar{r}_{E}
$$

从而股权收益率将随杠杆增大而增加(与上一章相符合)
$$
\begin{equation}\bar{r}_{E}=\bar{r}^{*}+\left(\bar{r}^{*}-\bar{r}_{D}\right) \frac{D}{E}\end{equation}
$$


![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409210559.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409211417.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409212035.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409211815.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409211759.png)

#### 2. 杠杆增加股权风险

The "asset beta" of firm
$$
\beta^{*}=\frac{D}{V} \beta_{D}+\frac{E}{V} \beta_{E}
$$
Solve for $\beta_{E}$
$$
\beta_{E}=\beta^{*}+\left(\beta^{*}-\beta_{D}\right) \frac{D}{E}
$$
从而杠杆将增加股权的系统性风险(即使债务无风险)。

进一步通过CAPM模型可以将股权收益分解为business risk premium和financial risk premium
$$
\begin{aligned}
\bar{r}_{E}&=r_{f}+\left[\boldsymbol{\beta}^{*}+\left(\boldsymbol{\beta}^{*}-\boldsymbol{\beta}_{D}\right) \frac{D}{E}\right]\left(\bar{r}_{m}-r_{f}\right)\\
&=r_{f}+\underbrace{\boldsymbol{\beta}^{*}\left(\bar{r}_{m}-r_{f}\right)}_{\text{business risk premium}}
+\underbrace{\left(\boldsymbol{\beta}^{*}-\boldsymbol{\beta}_{D}\right) \frac{D}{E}\left(\bar{r}_{m}-r_{f}\right)}_{\text{financial risk premium}}
\end{aligned}
$$

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409215329.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409215311.png)

不同融资结构对于投资者而言仅仅改变现金流的跨期结构，不改其现值/价值。这种改变可以通过资本市场实现，因此两种资本结构对投资者无差异。

#### 3. 风险债务

M&MⅡ对于有风险债务仍然成立。e.g.有可能破产的情况下M&MⅡ仍成立，前提是无破产成本(假设Ⅱ)。

公司增发债务也不改变公司的价值，但是可能改变公司价值的分配：新债的风险大于旧债，如果新债和旧债有一样的优先级，股东获利，旧债权人吃亏(此种情况下旧债发行人事实上不完全理性)；如果新债低于旧债的优先级，则股东价值仍不变。(例题)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409221344.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409221353.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409221330.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200409222113.png)

### 4.1.3 M&M dividend irrelevance theorem(不要求掌握)

【定理】假定无税收，无交易成本，公司的投融资决策、经营策略固定，那么发放股利与股票回购对股权人无差异。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200410114411.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200410114411.png)

## 4.2 理论意义

M&M定理表明，若融资决策不影响投资决策，则融资不改变企业价值。同时指出，WACC与资本结构无关；EPS具有杠杆效应，并非越高越好。

>  If we know what does not matter, we may infer what does.

但现实中，由于税盾、破产成本等存在，融资决策仍然会影响公司价值。
