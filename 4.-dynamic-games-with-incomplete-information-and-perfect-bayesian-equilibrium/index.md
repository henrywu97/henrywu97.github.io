# 

# 4. Dynamic Games with Incomplete Information and Perfect Bayesian Equilibrium

## 4.1 Perfect Bayesian Equilibrium

Beliefs and Sequential Rationality

- MWG Chapter 9:C
- JR Chapter 7.3.7

The notion of PBE will be used later in the following chapters:

- Adverse selection and signalling (MWG 13.B, 13.C, JR 8.1.1, 8.1.2)

When the notion of subgame perfect Nash equilibrium is of no use to refine Nash equilibria.

e.g. MWG (Page 283) Example 9.C.1: 

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200410172830.png)

All Nash equilibria are SPNEs (two pure-strategy N.E./SPNEs are shown in blue).

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200410180549.png)

How to eliminate the unreasonable equilibrium, e.g. (E plays Out; I plays Fight if entry occurs)?

- In the spirt of sequential rationality, we might insist that Firm I’s action be optimal for some belief.
- Viewed in this light, we can conclude that “fight if entry occurs” is not an optimal choice for any belief that Firm I might have.

Roughly speaking, we want to require strategies being optimal given beliefs and beliefs be consistent with strategies.

We need to introduce the notions of a system of beliefs and sequential rationality of strategies.

【Definition】A **system of beliefs** $\mu$ in extensive form game $\Gamma_{E}$ is a specification of a probability $\mu(x) \in[0,1]$ for each decision node $x$ in $\Gamma_{E}$ such that $\sum_{x \in H} \mu(x)=1$ for all information sets $H$.

- A system of beliefs specify, for each information set, a probabilistic assessment by the player who moves there, conditional upon play having reached that information set.
- Let $E\left[u_{i} | H, \mu, \sigma_{i}, \sigma_{-i}\right]$ be Player $i$ 's expected utility starting at $H$ if she has beliefs $\mu$ and follows strategy $\sigma_{i}$ and other players use $\sigma_{-i}$

【Definition】A strategy profile $\sigma$ in extensive form game $\Gamma_{E}$ is **sequentially rational** at information set $H$ given a system of beliefs $\mu$ if, denoting by $\iota(H)$ the player who moves at $H$, we have
$$
E\left[u_{\iota(H)} | H, \mu, \sigma_{\iota(H)}, \sigma_{-\iota(H)}\right] \geq E\left[u_{\iota(H)} | H, \mu, \tilde{\sigma}_{\iota(H)}, \sigma_{-\iota(H)}\right]
$$
for all $\tilde{\sigma}_{\iota(H)} \in \Delta\left(S_{\iota(H)}\right)$.

If strategy profile $\sigma$ satisfies this condition for all information sets $H$, then we say that $\sigma$ is **sequentially rational** given belief system.

Consider **completely mixed strategy**: each player’s strategy assigns a strictly positive probability to each possible action at every one of her information sets. (So every information set in the game is reached with positive probability.)

For each $x$ in a given player's information set $H$, the player should compute the conditional probability of reaching that node given play of strategies $\sigma$ :
$$
\operatorname{Pr}(x | H, \sigma)=\frac{\operatorname{Pr}(x | \sigma)}{\sum_{x^{\prime} \in H} \operatorname{Pr}\left(x^{\prime} | \sigma\right)}
$$
![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200414094935.png)



![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200421090849.png)

【structurally consistent】Also called the “common beliefs” restriction in JR Section 7.3.7: players with identical information have identical beliefs.
$\mu=0.5, \forall \sigma_{1} \in(0,1)$

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200421091436.png)

Extensive-form games with incomplete information: Sequential-move $+$ Bayesian games (players has types)

【PBE】We are going to introduce **Perfect Bayesian Equilibrium** as the solution concept.

- Strategy profile satisfies **sequential rationality**: Each player's strategies specify optimal actions, given the
    strategies of the other players, and given his beliefs.
- Consistency of beliefs: the beliefs are consistent with Bayes‘ rule, whenever possible.

Useful notions: separating (perfect Bayesian) equilibrium, pooling (perfect Bayesian) equilibrium.

【Separating equilibrium】 is a Perfect Bayesian Equilibrium of extensive-form incomplete information game in which different types of player i adopt different strategies.

【Pooling equilibrium】 is a Perfect Bayesian Equilibrium in which different types of player i adopt the same strategy.

## 4.2 5-step to find pure-strategy PBEs 

1. Specify a strategy profile for the privately informed player, either separating or pooling.
- In our above example, there are only four possible strategy profiles for the privately informed monetary authority: two separating strategy profiles, High $^{S}$ Low $^{W}$ and Low $^{S}$ High $^{W}$ and two pooling strategy profiles, High $^{S}$ High $^{W}$ and Low $^{S}$ Low $^{W}$.
    - (For future reference, it might be helpful to shade the branches corresponding to the strategy profile we test.)
2. Update the uninformed player's beliefs using Bayes' rule, whenever possible.
  - In our above example, we need to specify beliefs $\mu$ and $\gamma$ which arise after the labor union observes a high or a low inflation announcement, respectively.
3. Given the uninformed player's updated beliefs, find his optimal response.
  - In our above example, we first determine the optimal response of the labor union $(\mathrm{H} \text { or } \mathrm{L}$ ) upon observing a high-inflation announcement (given its updated belief $\mu$ ),
  - we then determine its optimal response (H or L) after observing a low-inflation announcement (given its updated belief $\gamma$ ).
      - (Also for future reference, it might be helpful to shade the branches corresponding to the optimal responses we ust found
4. Given the optimal response of the uninformed player, find the optimal action (message) for the informed player.
  - In our previous example, we first check if the Strong monetary authority prefers to make a high or low inflation announcement (given the labor union's responses determined in step 3 ).
  - We then operate similarly for the Weak type of monetary authority.
5. Then check if this strategy profile for the informed player coincides with the profile suggested in step 1
  - If it coincides, then this strategy profile, updated beliefs and optimal responses can be supported as a PBE of the incomplete information game.
  - Otherwise, we say that this strategy profile cannot be sustained as a PBE of the game.

### 4.2.1 Example

Let us consider the following sequential game with incomplete information:

- A monetary authority (such as the Federal Reserve Bank) privately observes its real degree of commitment with
    maintaining low information levels.
- After knowing its type (either Strong or Weak), the monetary authority decides whether to announce that the expectation for information is either High or Low.
- A labor union, observing the message sent by the monetary authority, decides whether to ask for high or low salary raises(denoted as H or L, respectively)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200414113942.png)

Let us next separately apply this procedure to test each of the four candidate strategy profiles:

- two separating strategy profiles:
    - $\text { High }^{S} \text { Low }^{W} $
    - $\text { Low }^{S} \text { High}^{W}$

- And two pooling strategy profiles:
    - $\text { High }^{S} \text { High }^{W} $
    - $\text { Low }^{S} \text { Low}^{W}$

#### Separating equilibrium

Let us first check separating strategy profile: $\text { Low }^{S} \text { High}^{W}$

Step 1: Specifying strategy profile $\text { Low }^{S} \text { High}^{W}$ that we will test. (See shaded branches in the figure.)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502160440.png)

Step 2: Updating beliefs

(a) After high inflation announcement (left-hand side)
$$
\mu=\frac{0.6 \alpha^{\text {Strong}}}{0.6 \alpha^{\text {Strong}}+0.4 \alpha^{\text {Weak}}}=\frac{0.6 \times 0}{0.6 \times 0+0.4 \times 1}=0
$$
where $\alpha^{\text{Strong}}$ is the probability that monetary authority choose high inflation given type is strong.

This implies that after high inflation, the labor union restricts its belief to the lower left-hand corner (see box), since $\mu=0$ and $1-\mu=1$

(b) After low inflation announcement (right-hand side)
$$
\gamma=\frac{0.6\left(1-\alpha^{\text {Strong}}\right)}{0.6\left(1-\alpha^{\text {Strong}}\right)+0.4\left(1-\alpha^{\text {Weak}}\right)}=\frac{0.6 \times 1}{0.6 \times 1+0.4 \times 0}=1
$$
This implies that, after low inflation, the labor union restricts its belief to the upper right-hand corner (see box), since $\gamma=1$ and $1-\gamma=0$.

Step 3: Optimal response
(a) After high inflation announcement, respond with $\mathrm{H}$ since
$$
0>-100
$$
in the lower left-hand corner of the figure.

(b) After low inflation announcement, respond with $\mathrm{L}$ since
$$
0 >-100
$$
in the upper right-hand corner of the figure.

We can hence summarize the optimal responses we just found, by shading them in the figure:

- $\mathrm{H}$ after high inflation, but $\mathrm{L}$ after low inflation.

Step 4: Optimal messages by the informed player

(a) When the monetary authority is Strong, if it chooses Low (as prescribed), its payoff is $\$ 300$. while if it deviates, its payoff decreases to $\$ 0$. No incentives to deviate.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502161648.png)

(b) When the monetary authority is Weak, if it chooses High (as prescribed), its payoff is $\$ 100$. While if it deviates, its payoff decreases to $\$ 50$. No incentives to deviate either.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502161733.png)

Since no type of privately informed player (monetary authority) has incentives to deviate, The separating strategy profile $\text{Low}^{S} \text{High}^W$ can be sustained as a PBE.

Redo the 5-step, we can check that $\text { High }^{S} \text { Low }^{W} $ cannot be sustained as a PBE.

#### Pooling equilibrium

Let us now test the pooling strategy profile $\text { High }^{S} \text { High }^{W} $

Step 1: Specifying strategy profile High' High W that we will test. (See shaded branches in the figure.)

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502162945.png)

Step 2: Updating beliefs 

(a) After high inflation announcement
$$
\mu=\frac{0.6 \alpha^{\text {Strong}}}{0.6 \alpha^{\text {Strong}}+0.4 \alpha \text {Weak}}=\frac{0.6 \times 1}{0.6 \times 1+0.4 
\times 1}=0.6
$$
so the high inflation announcement is uninformative.

(b) After low inflation announcement (off-the-equilibrium path)
$$
\gamma=\frac{0.6\left(1-\alpha^{\text {Strong}}\right)}{0.6\left(1-\alpha^{\text {Strong}}\right)+0.4\left(1-\alpha^{\text {Weak}}\right)}=\frac{0.6 \times 0}{0.6 \times 0+0.4 \times 0}=\frac{0}{0} \\
$$
Hence, $\gamma \in[0,1]$.

Step 3: Optimal response

(a) After high inflation announcement (along the equil. path), respond with $L$ since
$$
\begin{aligned}
E U_{\text {Labor}}(H | \text {High}) &=0.6 \times(-100)+0.4 \times 0=-60 \\
E U_{\text {Labor}}(L | \text {High}) &=0.6 \times 0+0.4 \times(-100)=-40
\end{aligned}
$$
(a) After low this from and announcement (off-the equil.)
$$
\begin{aligned}
E U_{\text {Labor}}(H | \text {Low}) &=\gamma \times(-100)+(1-\gamma ) \times 0=-100\gamma  \\
E U_{\text {Labor}}(L | \text {Low}) &=\gamma  \times 0+(1-\gamma ) \times(-100)=-100+100\gamma 
\end{aligned}
$$
i.e., respond with H if $\gamma < 1$.

Summarizing the optimal responses we found. Note that we need to divide our analysis into two cases:

- Case 1: where $\gamma < 1/2$, implying that the labor union responds with H after observing low inflation (right-hand side).
- Case 2: where $\gamma \geq 1/2$, implying that the labor union responds with L after observing low inflation (right-hand side).

Step 4: Optimal messages

- Case 1, where $\gamma<\frac{1}{2}$

(a) When the monetary authority is Strong, if it chooses High
(as prescribed), its payoff is $\$ 200$. While if it deviates, its payoff decreases to $\$ 100$. No incentives to deviate.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502164646.png)

(b) When the monetary authority is Weak, if it chooses High
(as prescribed), its payoff is $\$ 150$. While if it deviates, its payoff drops to $\$ 0$. No incentives to deviate either.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502164925.png)

No type of monetary authority has incentives to deviate.

Hence, the pooling strategy profile $\text{High}^S \text{High}^W$ can be sustained as a PBE when off-the-equilibrium beliefs satisfy $\gamma < 1/2$

- Case 2, where $\gamma \geq\frac{1}{2}$, $\text{High}^S \text{High}^W$ can't be sustained as a PBE

Remark: 

- In case 2 we include both $\gamma>1 / 2$ and $\gamma=1 / 2$. Observe that the labor union is in fact indifferent between $\mathrm{H}$ and $\mathrm{L}$ off the equilibrium path when $\gamma=1 / 2$

- If we consider mixed strategy, then the union could choose $H$ with any $\sigma_{H} \in[0,1]$ and $L$ with probability $1-\sigma_{H}$

- As stated at the beginning, we focus on pure strategy PBE.

- In addition, we only consider the case in which the union would choose $L$ with probability 1 when $\gamma=1 / 2$ (so that this case can be combined with the case $\gamma>1 / 2$ and to be excluded from being a PBE).
- More rigorously, we should also consider a case in which the union chooses H with probability 1 when $\gamma=1 / 2 .$ In this case, no type of the monetary authority has incentive to deviate, and the corresponding strategy profile and belief can be sustained as a pure strategy PBE, which leads us back to case 1 with $\gamma<1 / 2$

Redo the 5-step, we can check that $\text { Low }^{S} \text { Low }^{W} $ can't be sustained as a PBE for any off-the-equilibrium beliefs $\mu$.

## 4.3 The Intuitive Criterion

The Intuitive Criterion (Cho and Kreps 1987) is to refine the set of PBEs.

It is mostly useful in the signalling games (with both discrete and continuous message space).

- One player is privately informed. e.g. he knows information about the market demand, his own production cost, etc.
- He uses his actions (e.g. his production decision, investment in capacity, etc.) to communicate/conceal this information to the other uninformed player.

In particular, let us precisely describe the time structure of the signalling game: (用观测到的动作更新nature的信息)

1. Nature reveals to player $i$ some piece of private information, $\theta_{i} \in \Theta_{i}$
2. Then, player $i,$ who privately observes $\theta_{i},$ chooses an action (or message $m$ ) which is observed by the other player $j$
3. Player j observes message $m,$ but does not know player i's type. He knows the prior probability distribution that nature selects a give type $\theta_{i}$ from $\Theta_{i}$ e.g. the prior probability for $\Theta_{i}=\{\text { Strong, Weak }\}$ is 0.6 and 0.4
4. After observing player i's message $m,$ player $j$ updates his beliefs about player i's type. Let $\mu\left(\theta_{i} | m\right)$ denote $j$ 's belief about i's type being $\theta_{i}$
5. Given the beliefs, player $j$ selects an optimal action, $a,$ as a best response to the message $m$

The Intuitive Criterion is an equilibrium selection for PBE. So we start with an already-established PBE.

Consider a PBE with its corresponding equilibrium payoff for player $i$ as $u_{i}^{*}\left(\theta_{i}\right) .$ **Apply the Intuitive Criterion in two steps**:

### 4.3.1 Step 1

Figure out which type of the informed player $i$ (the monetary authority in the previous example) could benefit by deviating from the equilibrium message?

Let us focus on those types of informed player i who can obtain a higher payoff by deviating form equilibrium than by keeping their equilibrium message unaltered.
$$
\Theta_{i}^{* *}(m)=\{\theta_{i} \in \Theta_{i} | \underbrace{u_{i}^{*}\left(\theta_{i}\right)}_{\text {Equil. Payoff }} \leq \underbrace{\max _{a \in A^{*}\left(\Theta_{i}, m\right)} u_{i}\left(m, a, \theta_{i}\right)}_{\text {Highest Payoff from Deviating to message } m}\}
$$
where $A^{*}\left(\Theta_{i}, m\right)$ denotes the set of best responses of the uninformed player $j,$ who has a belief over the entire type space $\Theta_{i}$

We restrict out attention to those types of informed player for which sending the off-the-equilibrium message $m$ could give them a higher payoff than that in equilibrium. If $m$ does not satisfy this inequality, we say that $m$ is "equilibrium donimated."

### 4.3.2 Step 2

If deviations can only come from the type of player $i$ identified in the First Step, is the lowest payoff from deviating higher than the original equilibrium payoff?

- If the answer is yes, then the equilibrium violates the Intuitive Criterion. (And we can safely refine it out.)
- If the answer is no, then the equilibrium survives the Intuitive Criterion.

Take the subset of types of player $i$ for which the off-the-equilibrium message $m$ is not equilibrium dominated, $\Theta_{i}^{* *}(m),$ and check if the original equilibrium strategy profile $\left(m^{*}, a^{*}\right),$ with associated equilibrium payoff for the informed player $u_{i}^{*}\left(\theta_{i}\right),$ satisfies:
$$
\underbrace{\min _{a \in A^{*}\left(\theta_{i}^{*}(m), m\right)} u_{i}\left(m, a, \theta_{i}\right)}_{\text {Lowest Payoff from Deviating to } m}>\underbrace{U_{i}^{*}\left(\theta_{i}\right)}_{\text {Equil. Payott }}
$$
where $A^{*}\left(\Theta_{i}^{* *}(m), m\right)$ denotes the set of best responses of the uninformed player $j,$ who is now focusing on the subset of types $\Theta_{i}^{* *}(m)$ after applying Step 1.

If there is a type for which this condition holds, then the equilibrium strategy profile $\left(m^{*}, a^{*}\right)$ violates the Intuitive Criterion.

Imagine the possible speech to the uninformed player from the informed player who has incentives to deviate:

> "It is clear that my type is in $\Theta_{i}^{* *}(m)$. If my type was outside $\Theta_{i}^{* *}(m)$ । would have no chance of improving my payoff over what I can obtain at the equilibrium (condition (1)). We can therefore agree that $m$ y type is in $\Theta_{i}^{* *}(m) .$ Hence, update your beliefs as you wish, but restricting my type to be in $\Theta_{i}^{* *}(m)$. Given these beliefs, any of your best responses to my message improves my payoff over what 1 would obtain with my equilibrium strategy (condition (2)). For this reason, 1 am sending you such off-the-equilibrium message."

### 4.3.3 Example: Binary Types + Binary Actions

Let us come back to the signally game between a monetary authority and a labor union:

The only two strategy profiles that can be support as a PBE are

- A pooling PBE with both types choosing (High, High) with $\gamma<1 / 2 ;$ and

- A separating PBE with $\left(L o w^{S}, H i g h^{W}\right)$

Let us check if (High, High) survives the Intuitive Criterion.

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502204728.png)

First Step: which types of monetary authority have incentives to deviate towards Low inflation?

Low inflation is an off-the-equilibrium message.

Let us first apply condition (1) to the Strong type

$$
\begin{aligned}
\underbrace{u_{i}^{*}(\text { High } | \text { Strong })}_{\text {Equil. Payoff }}&<\underbrace{\max _{a_{j}} u_{i}(\text { Low } | \text { Strong })}_{\text {Highest payoff from deviating to Low inflation }} ?\\
200&<300
\end{aligned}
$$
Hence, the Strong type of monetary authority has incentives to deviate towards Low inflation.

Graphically, we can represent the incentives of the Strong monetary authority to deviate towards Low inflation as follows:

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502205937.png)

Let us now check if the Weak type also has incentives to deviate towards Low inflation:
$$
\begin{aligned}
\underbrace{u_{i}^{*}(\text { High } | \text { Weak })}_{\text {Equil. Payoff }}&<\underbrace{\max _{a_{j}} u_{i}(\text { Low } | \text { Weak })}_{\text {Highest payoff from deviating to Low inflation }} ?\\
150&>50
\end{aligned}
$$
Thus, the Weak type of monetary authority does not have incentives to deviate towards Low inflation.

Hence, the only type of monetary authority with incentives to deviate is the Strong type, $\Theta_{i}^{* *}(\mathrm{Low})=\{\text { Strong }\}$ 

Thus, the labor union believes that after observing a "Low-inflation" deviation it must be from the Strong type.

Intuition. Imagine the possible speech to the uninformed player from the informed player with incentives to deviate (the Strong type):

> "It is now clear that my type is in $\Theta_{i}^{* *}(L O W)=\{\text { Strong }\}$. Given this new belief, your best response to my message improves my payoff over what I would obtain with my original equilibrium strategy (condition (2)). For this reason, 1 am sending you such off-the-equilibrium message of Low inflation."

Second Step: to check if there is a type of monetary authority and a message it could use such that condition (2) is satisfied:
$$
\begin{aligned}
\min _{a \in A^{-}\left(\Theta ;^{*}(m), m\right)} u_{i}\left(m, a, \theta_{i}\right) &>u_{i}^{*}\left(\theta_{i}\right) ? \\
300 &>200
\end{aligned}
$$
![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200502210847.png)

Therefore, the pooling PBE of (High, High) with $\gamma<1 / 2$ violates the Intuitive Criterion: There exists a type of informed player (Strong type) and a message (Low inflation announcement) which gives to this informed player a higher payoff than in the original equilibrium.

In the binary example, there is only one equilibrium of this signalling game that survives the Intuitive Criterion,: the separating PBE with (Low, High):

- Why don’t we need to apply the Intuitive Criterion to the separating PBE to check if this equilibrium survives?

- This is because in the separating PBE there is no off-the-equilibrium message, since both messages are used by either type of the informed player.

- So the two-step checking is already included in the process when we establish this separating PBE.

- Recall that in the Intuitive Criterion we start by checking if an informed player has incentives to deviate towards an off-the-equilibrium message, then we restrict the uninformed player’s off-the-equilibrium beliefs.

Our previous result implies that, in signalling games with the binary structure (two types of the informed player and two available messages for each type), the separating PBE always survives the Intuitive Criterion.

Question and exercise: what if two types of the informed player can choose among three or more possible messages?

- e.g. Type t1 uses message m1, type t2 uses message m2, and nobody uses message m3.
- Then m3 is an off-the-equilibrium message. In this case, we need to check if this separating PBE survives the Intuitive Criterion.


