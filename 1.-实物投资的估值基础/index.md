# 

# 1. 实物投资的估值基础

【项目(Project)】能够产生未来现金流的实物投资。

【公司(Corporation)】项目的集合。几乎公司的任何决策都可以视为项目。

公司不同的价值取向：股东利益最大化，利益相关者利益最大化，社会价值最大化。

假定公司的目标为：股东利益最大化，等价于股票价值最大化。

问题：公司在投资决策过程中是否需要考虑不同股东的跨期偏好与风险偏好？不同项目是否有统一的决策准则？费雪分离定理解决了该问题。

## 1.1 费雪分离定理

### 1.1.1 简介

**费雪分离定理**(Fisher Separation Theorem)由经济学家欧文·费雪(Irving Fisher, 1867-1947)提出，该定理指出**在完美资本市场(PCM)中，经济主体的投资决策与消费决策可以相互分离，也即投资决策与其消费偏好无关**。

这意味着，公司不用考虑不同股东/投资者的消费偏好，只要投资净现值(NPV)大于0的项目即可。至于消费偏好，股东可以通过运转良好的资本市场予以满足。这从理论上证明了大型现代化公司存在的可能性，因此成为**公司金融的奠基理论**之一。

### 1.1.2 图解

考虑一个仅有两期$t=0, 1$的投资与消费决策问题。

#### Case 1：仅有投资项目没有银行

不投资的部分必须在第0期消费掉，投资收益作为第二期消费

此时产值等价于消费，生产可能性曲线与消费可能性曲线重合。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415083237.png)

#### Case 2：既有投资项目又有银行

此时投资的部分可以储蓄下来作为第二期的消费。投资项目的作用是扩展消费可能性曲线。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415083723.png)

最优的投资决策点是生产可能性曲线与消费可能性曲线(预算约束线)的切点，最优投资额为$I^*$，与股东偏好无关。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415084451.png)

储蓄者(miser)的消费储蓄结构分析

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415084441.png)

过度消费者(spender)的消费储蓄结构分析

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415084700.png)

$NPV$法则：投资$NPV \ge 0$的项目。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415084713.png)

注意到其中三角形横轴产量/消费量即为对应纵轴产量/消费量的现值。

单个项目NPV分析

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415085332.png)

### 1.1.3 证明

考虑一个仅有两期$t=0, 1$的效用最大化问题，假设只有一种消费品，消费者偏好可分离，即效用函数为

$$
u(c_0, c_1) = u(c_0)+\beta u(c_1)
$$

其中$\beta \in [0,1]$代表未来效用的折现因子。

消费者初始的初始禀赋为$y_0$。在第0期可以进行投资$I_0$，投资的产出为$\gamma \Phi (I_0)$，其中$\Phi^\prime>0,\Phi^{\prime\prime}<0,\Phi(0)=0,\Phi^{\prime}(0) = +\infty$。

#### Case 1：仅有投资项目没有银行

效用最大化问题的数学表达如下

$$
\begin{array}{l}
Max & u(C_0)+\beta u(C_1) \\
s.t.& 
C_{0}+I_{0} \leqslant y_{0} \\
&C_{1} \leqslant \gamma \phi\left(I_{0}\right)
\end{array}
$$

将约束条件带入效用函数得到

$$
\operatorname{Max}_{\left\{I_{0}\right\}} u\left(y_{0}-I_{0}\right)+\beta u\left(\gamma \phi\left(I_{0}\right)\right)
$$

一阶条件：

$$
FOC: -u^{\prime}\left(y_{0}-I_{0}\right)+\beta u^{\prime}\left(\phi\left(I_{0}\right)\right) \gamma \phi^{\prime}\left(I_{0}\right)=0
$$

移项后得到

$$
\begin{align}
\frac{1}{\beta} \cdot \frac{u^{\prime}\left(y_{0}-I_{0}\right)}{u^{\prime}\left(\gamma \Phi \left(I_{0}\right)\right)}=\gamma \phi^{\prime}\left(I_{0}\right) \tag{1.1}
\end{align}
$$

等式右边的含义是边际跨期替代率(marginal rate of intertemporal substitution, MRIS)。

进而可以求解得到，$I_0$是$\gamma,y_0, \beta$的函数，且函数$G(\cdot)$与效用函数$u'(\cdot)$有关，此时**由于不存在可以借贷的资本市场，投资决策不独立于消费决策**。

$$
I_{0}=G\left(y_{0}, \beta, \gamma\right)
$$

##### 比较静态分析

利用式(1.1)结合反证法，可以证明$I_0$是$y_0, \beta$的增函数，这是符合经济直觉的。$I_0$和$\gamma$的关系不能确定，一方面投资回报率更大会更倾向于投资，但同样的投资可以带来更大的回报，因此没有必要投资那么多。

$$
\begin{array}{l}
y_{0} \uparrow \Rightarrow I_{0} \uparrow \\
\beta \uparrow \Rightarrow I_{0} \uparrow \\
\end{array}
$$

#### Case 2：既有投资项目又有银行

效用最大化问题的数学表达式如下

$$
\begin{align}
\operatorname{Max}_{\{C_0,C_1,I_0,S_0\}} \quad &u(C_0)+\beta u(C_{1}) & \\s.t. \quad & C_{0}+I_{0}+S_{0} \leqslant y_{0} \tag{1}\\& C_{1} \leqslant \gamma \phi\left(I_{0}\right)+(1+r) S_{0} \tag{2}
\end{align}
$$

通过$(1)+(2)/(1+r)$，将约束条件转化为

$$
s.t. \quad C_{0}+\frac{C_1}{1+r} \leqslant y_{0}+\frac{\gamma \phi\left(I_{0}\right)}{1+r}-I_{0}
$$

设定拉格朗日函数

$$
L=\mu\left(C_{0}\right)+\beta \mu\left(C_{1}\right)+\mu\left[\left(y_{0}+\frac{\gamma \phi\left(I_{0}\right)}{1+r}-I_{0}\right)-C_0+\frac{C_{1}}{1+r}\right]
$$

根据拉格朗日函数可以将效用最大化问题分解成两个子问题：

1）**投资决策**

投资决策的目标函数如下，

$$
I_{0}^{*}=\operatorname{argmax}_{I_{0}} \frac{\gamma \phi\left(I_{0}\right)}{1+r}-I_{0}
$$

等式右边就是投资的NPV，为了最大化投资的总NPV，只要NPV为正的项目就应该被投资，这也证明了**NPV法则**的正确性。

根据一阶条件，可以发现，最优投资量的**边际收益率=市场利率(机会成本)**。

$$
FOC: \quad \gamma \phi^{\prime}{\left(I_{0}\right)}-1=r
$$

2）**消费决策**

在确定了最优投资$I_{0}^{*}$之后，通过以下最大化问题求出最优消费即可。

$$
\begin{aligned}
\operatorname{Max}_{\{C_0,C_1\}} \quad &\mu\left(C_{0}\right)+\beta \mu\left(C_{1}\right)\\ 
\text {s.t.} \quad & C_0+\frac{C_1}{1+r} \leqslant y_{0}+\left(\frac{\gamma \phi\left(I_{0}^{*}\right)}{1+r}-I_{0}^{*}\right)
\end{aligned}
$$

#### Case 3：考虑风险

Prove Fisher Separation Theorem in the case of one-period uncertainty. Here is the setup:

- There is a single consumption good. There are two dates of consumption, date 0 and date
- There are $N$ states of the world at date $1 .$ The probability that state $s$ hap pens is $\pi s$, where their sum is $1 .$
- Markets are complete: For each state $s$, there is an Arrow-Debreu security that costs $P s$ at date 0 to purchase and pays one unit of the consumption good at date 1 if and only if state $s$ occurs.
- The entrepreneur is an expected utility maximizer: $U(C 0)+\beta E\left[U\left(C_{1}\right)\right]$

- The entrepreneur has an endowment of $y_{0}$ at date $0,$ and no endowment at date $1 .$
- The entrepreneur can invest at date 0 in a technology that pays $\gamma(s) \phi(I o)$ in state s at date 1 . where $I_{0}$ is the amount invested. Notice that $\gamma$ is a function of s. The function satifies$\phi^{\prime}>0, \phi^{\prime \prime}<0, \phi(0)=0, \phi^{\prime}(0)=+\infty$

**Proof:**

Let $c_s$ denote consumption under state s in date 1.

Consider utility maximization problem

$$
\begin{align}
\operatorname{Max} \quad & U(C_0)+E[U(C_{1})]&\\
s.t. \quad & C_{0}+I_{0}+\sum_{s=1}^{N} \tau(s)P_s \leqslant y_{0} \quad &(1) \\
& c_{s} \leqslant \gamma(s) \phi\left(I_{0}\right)+ \tau(s), \text{ for } s=1,2,\dots,N \quad &(2) 
\end{align}
$$

Take a summation of bugdet constrait (2), we have

$$
\sum_{s=1}^{N} P_s c_s \leq   \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}\right) +   \sum_{s=1}^{N}\tau(s)P_s \quad (3)
$$

By (2) + (3), we have

$$
C_0 + \sum_{s=1}^{N} P_s c_s \leq  y_0 + \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}\right)- I_0
$$

Rewrite utility maximization problem,

$$
\begin{align}
\operatorname{Max} \quad &U(C_0)+E[U(C_{1})]\\
s.t. \quad & C_0 + \sum_{s=1}^{N} P_s c_s \leq  y_0 + \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}\right)- I_0
\end{align}
$$

Set Lagrange function,

$$
\mathcal {L} = U(C_0)+E[U(C_{1})] + \lambda \left[y_0 + \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}\right)- I_0 - C_0 - \sum_{s=1}^{N} P_s c_s \right]
$$

Then we can separate utility maximization problem into two steps:

1）Optimal Investment

$$
I_{0}^{*}=\operatorname{argmax}_{I_{0}} \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}\right)- I_0
$$

FOC

$$
\frac{\partial \mathcal{L}}{\partial I_0} = \sum_{s=1}^{N}P_s\gamma(s) \phi^{\prime}\left(I_{0}\right)- 1 = 0
$$

2）Optimal Saving and Consumption

$$
\begin{aligned}
\operatorname{Max} \quad &U(C_0)+E[U(C_{1})]\\
s.t. \quad & C_0 + \sum_{s=1}^{N} P_s c_s \leq  y_0 + \sum_{s=1}^{N}P_s\gamma(s) \phi\left(I_{0}^*\right)- I_0^*
\end{aligned}
$$

### 1.1.4 评价

**费雪分离定理**：完美资本市场（借贷）的存在使得投资可以从消费问题中抽离出来（先做出投资决策，再根据投资结果决定消费）

**理解**：结合之前的图像，投资具有扩大财富与财富跨期转移的功能，当资本市场不完善时，投资需要承担一定的财富跨期转移功能，由于不同个体拥有不同的跨期偏好，可能导致不同的投资决策（无差异曲线与生产可能性曲线的交点）；当资本市场完善时，投资仅承担扩大财富的功能，财富转移的功能由资本市场承担，即使偏好不同，最终投资决策的均衡点也相同（$NPV \geq 0$ 或者 $r_i = r$）。

**关键假设**：PCM（完美资本市场）

- No fraction：无交易成本，存贷利率相等。
  - 存贷利率不相等时，对于存款者与贷款者存在不同的投资均衡点。

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415161141.png)

- 信息对称：例如投资项目信息等
- 完全竞争：利率的接受者

虽然PCM在现实中并不存在，但该定理仍然具有**极其重要的理论意义**：

- 公司只负责扩大财富，其唯一的标准即$NPV \geq 0$；
- 公司价值等于投资项目的未来现金流的折现的加总；
- 将公司的股利政策视为公司给投资者带来的消费，那么股利政策与投融资决策相互独立；
- 发达的资本市场可以统一不同个体的投资决策，使更多人参与到投资中来。

### 1.1.5 费雪

最后值得一提的是，费雪分离定理的提出者欧文·费雪(Irving Fisher, 1867-1947)。

**费雪是20c初经济学界的“顶级流量”，是经济学领域的集大成者**。费雪最著名的经济学贡献包括费雪效应(名义利率=实际利率+通胀率)，货币数量论($MV=PQ$)，他还对一般均衡理论、计量经济学也作出了很大的贡献。他是货币主义学派的先驱，被弗里德曼、托宾等称为**“20世纪美国最伟大的经济学家”**。

然而他错误地判断了20c30s年代的大萧条，导致其资产大幅缩水，名声和学术地位也受到了很大影响，但其仍在经济学史上留下了浓墨重彩的一笔。

## 1.2 NPV法则

项目的现金流：

$$
\underbrace{C_{0}}_{\text {cost}} \quad \underbrace{C_{1} \quad  C_{2} \quad  C_{3} \ldots  C_{T}}_{\text {cash flows}}
$$

$$
\mathrm{NPV}=\underbrace{\mathrm{PV}(\text { future cash flows })}_{\text{Present (market) value of future cash flows}
}-\mathrm{C}_{0}
$$

### Step 1. 计算自由现金流

计算时仅考虑项目带来的增量现金流

假定是一个全部以股权融资的公司，因此不考虑利息以及利息带来的税盾效应

**计算公式**：

- 公司自由现金流＝息税前利润－税金 + 折旧与摊销－资本支出－营运资本追加

- 股东自由现金流＝净利润 + 折旧与摊销－资本支出－营运资本追加

- 其中，净利润＝息税前利润－税金－利息

注意到上述税金中的税基是没有扣除利息的EBIT

更精确的公式如下

$$
\mathrm{FCF}=\mathrm{EBIT}^{*}(1-\mathrm{t})+\text { Depreciation }-\mathrm{CAPX}-\text { Change in NWC }
$$
![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415132013.png)

公式的理解

- 现金流入有两个来源：主要来源是企业通过**生产经营活动产生的利润**；另一个来源是企业的**折旧与摊销**，这部分是作为企业的经营费用在利润中扣除的，但并没有实际的支付现金出去，所以在计算现金流时需要加回去。

- 现金流出：**税金**，**资本支出**（包括购置固定资产，无形资产及其他营业性资产的支出）和营运资本（存货、应收款项的增加而占用的资金等），最后剩余就是股东和债权人理论上能从企业提取的最大现金。

### Step 2. 计算未来现金流的PV

思想(“Tracking Portfolio” Approach): 在金融市场找到与项目未来现金流相同的资产组合，该资产组合的市场价值等于项目的现值(Present Value, PV)。

本章仅考虑无风险项目，此时折现率(discount rate)为零息债券的到期收益率(yield to maturity, YTM)，项目的PV为

$$
P V=\frac{C_{1}}{1+Y T M_{1}}+\frac{C_{2}}{\left(1+Y T M_{2}\right)^{2}}+\ldots \ldots+\frac{C_{T}}{\left(1+Y T M_{T}\right)^{T}}
$$

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415161240.png)

## 1.3 IRR法则

内部收益率(Internal Rate of Return, IRR) ，使项目NPV为0的折现率。IRR可以类比为项目的投资回报率，便于理解，因此比NPV法则更加流行。

折现现金流是折现率$i$的函数

$$
DCF(i) = C_0 +\frac{C_1}{1+i}+\frac{C_2}{(1+i)^2}+ \dots+ \frac{C_T}{(1+i)^T}
$$

### 1.3.1 IRR使用方法

- 首先计算现金机会成本(opportunity cost of cash, OCC)：
    - 如果利率期限结构是水平线，即无风险利率不随时间变化，则直接将无风险利率作为OCC；项目有风险时需要加上风险溢价。	
    - 如果利率期限结构不是水平的，则需要计算**hurdle rate**：首先计算项目NPV，使折现现金流等于NPV的折现率即为hurdle rate，并将其作为OCC。

$$
\begin{array}{c}
DCF(i)=0 \Rightarrow i = IRR \\
DCF(i)=N P V \Rightarrow i=h \\
D C F(i)-C_{0}=PV \Rightarrow i=h
\end{array}
$$

- 对于Late Cash-Flow stream (investing): 前期负现金流，后期正现金流。$DCF(i)$关于i递减，IRR大于OCC时接受该项目

- 对于Early Cash-Flow stream (financing): 前期正现金流，后期负现金流。$DCF(i)$关于i递增，IRR小于OCC时接受该项目(类比借钱，利率越低越好)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415154837.png)

### 1.3.2 局限性

- IRR本身作为折现率并不符合现实

- 非传统项目现金流(e.g. 正负号多次变化)可能存在多个或者不存在IRR

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415160432.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415155821.png)

- 互斥项目不能直接比较IRR

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415160710.png)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200415160730.png)

**总结**：IRR在实际中是常用的方法，但在非传统现金流中常常无法给出判断。$NPV>0$才是衡量是否投资一个项目的最终准则。
