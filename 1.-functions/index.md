# 

# 1. Functions

Math review
o References
o Appendix of MWG
o https://www.coursera.org/learn/mathematics-for-economists/

https://mjo.osborne.economics.utoronto.ca/index.php/tutorial/index/1/toc/c
o How?
read, read, read
o Homework
o submit to: https://workspace.jianguoyun.com/inbox/collect/283420eeee554c158a4cf4bbe8cf97a6/submit

A language without ambiguity

Do NOT be afraid!

Matrix Notation for Derivatives
$ \mathbf{x} \in \mathbb{R}^{\mathrm{N}}: $ column vector
$ \bullet x \cdot y=x^{T} y, x \cdot A_{N \times M}=x^{T} A\left(\because x \cdot " \text { can always be read as } " x^{T \prime \prime}\right) $
o Given a vector valued differentiable function $ \mathrm{f}: \mathbb{R}^{\mathrm{N}} \rightarrow \mathbb{R}^{\mathrm{M}} $
o denote by Df $ (x) $ the $ M \times N $ matrix whose mnth entry is $ \partial f_{m}(x) / \partial x_{n} $
If $ M=1, $ then $ f(x) \in \mathbb{R} $ (real-valued function), and

$$
\operatorname{Df}(\mathrm{x})=\left(\partial \mathrm{f}(\mathrm{x}) / \partial \mathrm{x}_{1}, \partial \mathrm{f}(\mathrm{x}) / \partial \mathrm{x}_{2}, \cdots, \partial \mathrm{f}(\mathrm{x}) / \partial \mathrm{x}_{\mathrm{n}}\right)=[\nabla \mathrm{f}(\mathrm{x})]^{\mathrm{T}}
$$

o and the Hessian matrix $ \mathrm{D}^{2} \mathrm{f}(\mathrm{x})=\mathrm{D}[\nabla \mathrm{f}(\mathrm{x})] $

Matrix Notation for Derivatives
a An exchange economy with $ \mathrm{N} $ goods, and $ \mathrm{M} $ consumers; for each agent i, the utility function $ u_{i}: \mathbb{R}^{N} \rightarrow \mathbb{R} $.
o Demand function $ x: \mathbb{R}^{N+1} \rightarrow \mathbb{R}^{M}, $ where for each $ i \in M $
$ \mathrm{x}_{\mathrm{i}}\left(\mathrm{p}_{1}, \mathrm{p}_{2}, \cdots, \mathrm{p}_{\mathrm{n}}, \mathrm{w}\right), $ is the demand of consumer i.
$ \bullet D_{p} x(p, w)=\left[\begin{array}{cccc}\partial x_{1} / \partial p_{1} & \partial x_{1} / \partial p_{2} & \cdots & \partial x_{1} / \partial p_{n} \\ \partial x_{2} / \partial p_{1} & \partial x_{2} / \partial p_{2} & \cdots & \partial x_{2} / \partial p_{n} \\ \vdots & \vdots & \vdots & \vdots \\ \partial x_{n} / \partial p_{1} & \partial x_{n} / \partial p_{2} & \cdots & \partial x_{n} / \partial p_{n}\end{array}\right] $
$ \bullet \mathrm{M} \times \mathrm{N} $ matrix $ (\text { "Law of demand" }) $

$$
\equiv, \quad \equiv
$$

Matrix Notation for Derivatives
o Concavity of $ u(\cdot): $

$$
\begin{aligned}
\mathrm{D}^{2} \mathrm{u}_{\mathrm{i}}(\mathrm{x})=& \mathrm{D}\left[\nabla \mathrm{u}_{\mathrm{i}}(\mathrm{x})\right]=\mathrm{D}\left[\left(\partial \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{1}, \partial \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{2}, \cdots, \partial \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{\mathrm{n}}\right)^{\mathrm{T}}\right] \\
=&\left[\begin{array}{cccc}
\partial^{2} \mathrm{u}_{\mathrm{i}} / \partial^{2} \mathrm{x}_{1} & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{1} \partial \mathrm{x}_{2} & \cdots & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{1} \partial \mathrm{x}_{\mathrm{n}} \\
\partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{2} \partial \mathrm{x}_{1} & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial^{2} \mathrm{x}_{2} & \cdots & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{2} \partial \mathrm{x}_{\mathrm{n}} \\
\vdots & \vdots & \vdots & \vdots \\
\partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{\mathrm{n}} \partial \mathrm{x}_{1} & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial \mathrm{x}_{\mathrm{n}} \partial \mathrm{x}_{2} & \cdots & \partial^{2} \mathrm{u}_{\mathrm{i}} / \partial^{2} \mathrm{x}_{\mathrm{n}}
\end{array}\right]
\end{aligned}
$$

Read by yourself
o The chain rule
- The production rule
Homogeneous Functions

Let $ \mathrm{f}: \mathbb{R}_{+}^{\mathrm{N}} \rightarrow \mathbb{R} $
Definition. A function $ f\left(x_{1}, x_{2}, \cdots, x_{N}\right) $ is homogenous of degree $ r $ (for $ \mathrm{r}=\cdots,-1,0,1, \cdots) $ if for every $ \mathrm{t}>0 $ we have

$$
\mathrm{f}\left(\mathrm{tx}_{1}, \mathrm{tx}_{2}, \cdots, \mathrm{tx}_{\mathrm{N}}\right)=\mathrm{t}^{\mathrm{r}} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}, \cdots, \mathrm{x}_{\mathrm{N}}\right)
$$

example: $ f\left(x_{1}, x_{2}\right)=x_{1} / x_{2}, f\left(x_{1} x_{2}\right)=\left(x_{1} x_{2}\right)^{1 / 2} $

Example: the demand function of object $ j: x_{j}\left(p_{1}, p_{2}, \cdots, p_{n}\right) $ (homogeneous of degree zero)

$$
\mathrm{x}_{\mathrm{i}}\left(\mathrm{p}_{1}, \mathrm{p}_{2}, \cdots, \mathrm{p}_{\mathrm{n}}\right)=\mathrm{x}_{\mathrm{j}}\left(1, \mathrm{p}_{2} / \mathrm{p}_{1}, \cdots, \mathrm{p}_{\mathrm{n}} / \mathrm{p}_{1}\right)
$$

Homogeneous Functions
Theorem. If $ \left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right) $ is homogenous of degree $ \mathrm{r}, $ then for any $ \mathrm{n}=1, \cdots, \mathrm{N} $ the partial derivative function $ \partial \mathrm{f}\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right) / \partial \mathrm{x}_{\mathrm{n}} $ is
homogeneous of degree $ \mathrm{r}-1 . $
Proof. By the definition of homogeneity,

$$
\mathrm{f}\left(\mathrm{tx}_{1}, \cdots, \mathrm{tx}_{\mathrm{N}}\right)-\mathrm{t}^{\mathrm{T}} \mathrm{f}\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right)=0
$$

Differentiating this expression with respect to $ \mathrm{x}_{\mathrm{n}} $
Therefore,

$$
\frac{\partial f\left(t x_{1}, \cdots, t x_{N}\right)}{\partial x_{n}}=t^{r-1} \frac{\partial f\left(x_{1}, \cdots, x_{N}\right)}{\partial x_{n}}
$$

Homogeneous Functions

P Figure M.B.1

$ -\frac{\partial f(t \bar{x}) / \partial x_{1}}{\partial f(t \bar{x}) / \partial x_{2}}=-\frac{t^{r-1} \partial f(\bar{x}) / \partial x_{1}}{t^{r-1} \partial f(\bar{x}) / \partial x_{2}}=-\frac{\partial f(\bar{x}) / \partial x_{1}}{\partial f(\bar{x}) / \partial x_{2}} $
e representative indifferent curve ( "homothetic" preference $ \mathrm{u}(\mathrm{x})=\mathrm{g}(\mathrm{f}(\mathrm{x}))) $

Euler's Formula

o Theorem. (Euler's Formula) Suppose that $ \mathrm{f}\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right) $ is homogenous of degree r and differentiable. Then at any $ \left(\overline{\mathrm{x}}_{1}, \cdots, \overline{\mathrm{x}}_{\mathrm{N}}\right) $ we have

$$
\sum_{n=1}^{N} \frac{\partial f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)}{\partial x_{n}} \bar{x}_{n}=r f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)
$$

or, in matrix notation, $ \nabla \mathrm{f}(\overline{\mathrm{x}}) \cdot \overline{\mathrm{x}}=\mathrm{r} \mathrm{f}(\overline{\mathrm{x}}) $
Proof.

$$
\mathrm{f}\left(\mathrm{t} \overline{\mathrm{x}}_{1}, \cdots, \mathrm{t} \overline{\mathrm{x}}_{\mathrm{N}}\right)-\mathrm{t}^{\mathrm{r}} \mathrm{f}\left(\overline{\mathrm{x}}_{1}, \cdots, \overline{\mathrm{x}}_{\mathrm{N}}\right)=0
$$

Differentiating this expression with respect to t,

$$
\sum_{n=1}^{N} \frac{\partial f\left(t \bar{x}_{1}, \cdots, \bar{t} \bar{x}_{N}\right)}{\partial x_{n}} \bar{x}_{n}-r t^{r-1} f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)=0
$$

Evaluating at $ \mathrm{t}=1, $ we obtain Euler's formula.

$$
\equiv
$$

1:
Euler's Formula
o Suppose a production function $ \mathrm{f} $ is homogencous of degree one. Euler's formula says that

$$
\sum_{n-1}^{N} \frac{\partial f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)}{\partial x_{n}} \bar{x}_{n}=f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)
$$

real return: $ w_{n}=\frac{\partial f\left(x_{1}, \cdots, x_{N}\right)}{\partial x_{n}}(\text { marginal product }) $

$$
\sum_{n=1}^{N} w_{n} \bar{x}_{n}=f\left(\bar{x}_{1}, \cdots, \bar{x}_{N}\right)
$$



Concave (and Convex) Functions

**Definition [concave]** The function $ f: A \rightarrow \mathbb{R} $, defined on the convex set $ A \subset \mathbb{R}^{N} $, is concave if
$$
\mathrm{f}\left(\alpha \mathrm{x}^{\prime}+(1-\alpha) \mathrm{x}\right) \geq \alpha \mathrm{f}\left(\mathrm{x}^{\prime}\right)+(1-\alpha) \mathrm{f}(\mathrm{x})
$$

for all x and $ \mathrm{x}^{\prime} \in \mathrm{A} $ and all $ \alpha \in[0,1] . $ If the inequality is strict for all $ \mathrm{x}^{\prime} \neq \mathrm{x} $ and all $ \alpha \in(0,1), $ then we say that the function is **strictly concave**.

Graph: the straight line connecting any two points in the graph of $ f(\cdot) $ lies entirely below the graph.

Concave Functions

**Theorem [A second characterization of concave functions]**: The (continuously differentiable) function $ \mathrm{f}: \mathrm{A} \rightarrow \mathbb{R} $ is concave if and only if
$$
f(x+z) \leq f(x)+\nabla f(x) \cdot z
$$

for all $ \mathrm{x} \in \mathrm{A} $ and $ \mathrm{z} \in \mathbb{R}^{\mathrm{N}}(\text { with } \mathrm{x}+\mathrm{z} \in \mathrm{A}) . $ The function $ \mathrm{f}(\cdot) $ is strictly concave if this inequality holds strictly for all $ \mathrm{x} \in \mathrm{A} $ and all $ \mathrm{z} \neq 0 . $

Graph: any tangent to the graph must lie (weakly) above the graph

**Definition [negative semidefinite]**. The $ \mathrm{N} \times \mathrm{N} $ matrix $ \mathrm{M} $ is negative semidefinite if
$$
z \cdot M z \leq 0
$$

for all $ z \in \mathbb{R}^{N} . $ If the inequality is strict for all $ z \neq 0, $ then the matrix $ M $ is negative definite.

**Theorem**: The (twice continuously differentiable) function $ \mathrm{f}: \mathrm{A} \rightarrow \mathbb{R} $ is concave if and only if $ \mathrm{D}^{2} \mathrm{f}(\mathrm{x}) $ is negative semidefinite for every $ \mathrm{x} \in \mathrm{A} . $ If $ \mathrm{D}^{2} \mathrm{f}(\mathrm{x}) $ is negative definite for every $ \mathrm{x} \in \mathrm{A}, $ then the function is strictly concave.

Concave Functions

Let $ f: \mathbb{R} \rightarrow \mathbb{R} $ be a twice continuously differentiable function. Then $ f $ is concave if

1. $ f\left(\alpha x^{\prime}+(1-\alpha) x\right) \geq \alpha f\left(x^{\prime}\right)+(1-\alpha) f(x), $ or
2. $ \mathrm{f}(\mathrm{x}+\mathrm{z}) \leq \mathrm{f}(\mathrm{x})+\mathrm{f}^{\prime}(\mathrm{x}) \mathrm{z}, $ or
3. $ \mathrm{f}^{\prime \prime}(\mathrm{x}) \leq 0\left(\Leftarrow \mathrm{z}^{2} \mathrm{f}^{\prime \prime}(\mathrm{x}) \leq 0 \text { for all } \mathrm{z} \in \mathbb{R}^{\mathrm{N}}\right) $

Matrices: Negative (Semi) Definiteness

Theorem. Suppose that $ \mathrm{M} $ is an $ \mathrm{N} \times \mathrm{N} $ matrix.

1. The matrix M is negative definite if and only if the symmetric matrix $ \mathrm{M}+\mathrm{M}^{\mathrm{T}} $ is negative definite.
2. If $ \mathrm{M} $ is symmetric, then $ \mathrm{M} $ is negative definite if and only if all of the characteristic values of M are negative.
3. If $ \mathrm{M} $ is symmetric, then $ \mathrm{M} $ is negative definite if and only if $ \left.(-1)^{\mathrm{r}}\right|_{\mathrm{r}} \mathrm{M}_{\mathrm{r}} \mid>0 $ for every $ \mathrm{r}=1, \cdots, \mathrm{N} $
4. If $ \mathrm{M} $ is symmetric, then $ \mathrm{M} $ is negative semidefinite if and only if $ \left.(-1)^{\mathrm{r}}\right|_{\mathrm{r}} \mathrm{M}_{\mathrm{r}}^{\pi} \mid \geq 0 $ for every $ \mathrm{r}=1, \cdots, \mathrm{N} $ and for every permutation $ \pi $ of the indices $ \{1, \cdots, N\} . $ (Note that $ M^{\pi} $ is the matrix in which rows and columns are correspondingly permuted.)

Matrices: Negative (Semi) Definiteness

Example: a real valued function of two variables, $ f\left(x_{1}, x_{2}\right) $
$$
\mathrm{D}^{2} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right)=\mathrm{D}\left(\left(\mathrm{f}_{1}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right), \mathrm{f}_{2}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right)^{\mathrm{T}}\right)=\left[\begin{array}{ll}
\mathrm{f}_{11} & \mathrm{f}_{12} \\
\mathrm{f}_{21} & \mathrm{f}_{22}
\end{array}\right]\right.
$$

$ \mathrm{f}(\cdot) $ is strictly concave if $ \mathrm{D}^{2} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right) $ is negative definite for all $ \left(\mathrm{x}_{1}, \mathrm{x}_{2}\right) $. This is true if and only if
$$
\left|f_{11}\right|<0 \quad \text { and }\left|\begin{array}{cc}
f_{11} & f_{12} \\
f_{21} & f_{22}
\end{array}\right|>0
$$

or equivalently, if and only if

$$
\mathrm{f}_{11}<0 \text { and } \mathrm{f}_{11} \mathrm{f}_{22}-\mathrm{f}_{12}^{2}>0
$$

$ \mathrm{f}(\cdot) $ is concave if $ \mathrm{D}^{2} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right) $ is negative semidefinite for all $ \left(\mathrm{x}_{1}, \mathrm{x}_{2}\right) $. This is true if and only if
$$
\left|f_{11}\right| \leq 0 \quad \text { and } \quad\left|\begin{array}{cc}
f_{11} & f_{12} \\
f_{21} & f_{22}
\end{array}\right| \geq 0
$$

and, permuting the rows and columns of $ \mathrm{D}^{2} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right) $,

$$
\left|f_{22}\right| \leq 0 \quad \text { and } \quad\left|\begin{array}{cc}
f_{22} & f_{21} \\
f_{12} & f_{11}
\end{array}\right| \geq 0
$$

Thus, $ f(\cdot) $ is concave if and only if

$$
\mathrm{f}_{11} \leq 0, \quad \mathrm{f}_{22} \leq 0, \quad \text { and } \quad \mathrm{f}_{11} \mathrm{f}_{22}-\mathrm{f}_{12}^{2} \geq 0
$$

## Quasi-concave Functions

Convex preferences: "averages are better than extremes."

Formally, a preference relation $ \succeq $ on the consumption set $ X $ is called (strictly) convex if for any $ \mathrm{x}, \mathrm{y}, \mathrm{z} \in \mathrm{X} $ where $ \mathrm{y} \succeq \mathrm{x} $ and $ \mathrm{z} \succeq \mathrm{x}(\text { and } \mathrm{y} \neq \mathrm{z}) $ and for every $ \left.\theta \in[0,1],(\theta \in(0,1)) \theta_{\mathrm{y}}+(1-\theta) z \succeq \mathrm{x} \text { (hold with } \succ\right) $

A concave utility function represents a convex preference:

$$
\mathrm{u}(\theta \mathrm{y}+(1-\theta) \mathrm{z}) \geq \theta \mathrm{u}(\mathrm{y})+(1-\theta) \mathrm{u}(\mathrm{z}) \geq[\theta+(1-\theta)] \mathrm{u}(\mathrm{x})=\mathrm{u}(\mathrm{x})
$$

However, concavity is a **"cardinal"** property in that it will not generally be preserved under an increasing transformation of $ \mathrm{f}(\cdot) $.

E.g. $ \mathbf{u}(\mathbf{x})=\mathbf{x}^{1 / 2}, \mathbf{f}(\mathbf{y})=\mathbf{y}^{4} $, then $ \mathbf{f}(\mathbf{u}(\mathbf{x}))=\mathbf{x}^{2} $

That is, **there are utility functions that are not concave but represent convex preferences**, such as quasi-concave functions.

Definition The function $ \mathrm{f}: \mathrm{A} \rightarrow \mathbb{R} $, defined on the convex set $ \mathrm{A} \subset \mathbb{R}^{\mathrm{N}} $, is quasi-concave if its upper contour sets $ \{\mathrm{s} \in \mathrm{A}: \mathrm{f}(\mathrm{s}) \geq \mathrm{t}\} $ are convex sets; that is, if 

$ \mathrm{f}(\mathrm{x}) \geq \mathrm{t} $ and $ \mathrm{f}\left(\mathrm{x}^{\prime}\right) \geq \mathrm{t} $ implies that $ \mathrm{f}\left(\alpha \mathrm{x}+(1-\alpha) \mathrm{x}^{\prime}\right) \geq \mathrm{t} $

for any $ \mathrm{t} \in \mathbb{R}, \mathrm{x}, \mathrm{x}^{\prime} \in \mathrm{A}, $ and $ \alpha \in[0,1] . $ If the inequality is strict
whenever $ \mathrm{x} \neq \mathrm{x}^{\prime} $ and $ \alpha \in(0,1), $ then we say that $ \mathrm{f}(\cdot) $ is strictly quasi-concave.

Theorem. The (continuously differentiable) function $ f: A \rightarrow \mathbb{R} $ is quasi-concave if and only if
$$
\nabla f(x) \cdot\left(x^{\prime}-x\right) \geq 0 \quad \text { whenever } \quad f\left(x^{\prime}\right) \geq f(x)
$$

for all $ \mathrm{x}, \mathrm{x}^{\prime} \in \mathrm{A} . $ If $ \nabla \mathrm{f}(\mathrm{x}) \cdot\left(\mathrm{x}^{\prime}-\mathrm{x}\right)>0 $ whenever $ \mathrm{f}\left(\mathrm{x}^{\prime}\right) \geq \mathrm{f}(\mathrm{x}) $ and
$ \mathrm{x}^{\prime} \neq \mathrm{x}, $ then $ \mathrm{f}(\cdot) $ is strictly quasi-concave.
Graph. The gradient vector $ \nabla f(x) $ and the vector $ \left(x^{\prime}-x\right) $ must form an acute angle(??????).

![image-20200806162133262](C:\Users\Wuhao\AppData\Roaming\Typora\typora-user-images\image-20200806162133262.png)

$ \mathbf{o} \mathrm{f}\left(\mathrm{x}_{1}, \mathrm{x}_{2}\right)=\mathrm{t} \Rightarrow \mathrm{f}_{1} \cdot \mathrm{dx}_{1}+\mathrm{f}_{2} \cdot \mathrm{dx}_{2}=0 $ (direction of gradient vector.)

Comparative Statics and the Implicit Function Theorem
We have a system of N equations depending on $ \mathrm{N} $ endogenous variables $ \mathrm{x}=\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right) $ and $ \mathrm{M} $ parameters $ \mathrm{q}=\left(\mathrm{q}_{1}, \cdots, \mathrm{q}_{\mathrm{M}}\right) $
$$
\begin{array}{l}
\mathrm{f}_{1}\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}} ; \mathrm{q}_{1}, \cdots, \mathrm{q}_{\mathrm{M}}\right)=0 \\
\vdots \\
\mathrm{f}_{\mathrm{N}}\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}} ; \mathrm{q}_{1}, \cdots, \mathrm{q}_{\mathrm{M}}\right)=0
\end{array}
$$

The domain of the endogenous variables is $ \mathrm{A} \subset \mathbb{R}^{\mathrm{N}} $ and the domain of the parameters is $ \mathrm{B} \subset \mathbb{R}^{\mathrm{M}} $

$$
=
$$

Comparative Statics and the Implicit Function Theorem
Suppose that $ \overline{\mathrm{x}}=\left(\overline{\mathrm{x}}_{1}, \cdots, \overline{\mathrm{x}}_{\mathrm{N}}\right) \in \mathrm{A} $ and $ \overline{\mathrm{q}}=\left(\overline{\mathrm{q}}_{1}, \cdots, \overline{\mathrm{q}}_{\mathrm{M}}\right) \in \mathrm{B} $ satisfy
the above system of equations.
We are interested in the possibility of solving for $ \mathrm{x}=\left(\mathrm{x}_{1}, \cdots, \mathrm{x}_{\mathrm{N}}\right) $ as a function of $ \mathrm{q}=\left(\mathrm{q}_{1}, \cdots, \mathrm{q}_{\mathrm{N}}\right) $ locally around $ \overline{\mathrm{q}} $ and $ \overline{\mathrm{x}} . $ That is,
$ \mathrm{f}_{\mathrm{n}}\left(\eta_{1}(\mathrm{q}), \cdots, \eta_{\mathrm{N}}(\mathrm{q}) ; \mathrm{q}\right)=0 \quad $ for every $ \mathrm{q} \in \mathrm{B}^{\prime} \subset \mathrm{B} $ and every $ \mathrm{n} $
and
$$
\eta_{\mathrm{n}}(\overline{\mathrm{q}})=\overline{\mathrm{x}}_{\mathrm{n}} \quad \text { for every } \mathrm{n}
$$

So that we can carry out "comparative statics" analysis -test the effects of parameters.

Comparative Statics and the Implicit Function Theorem
o Figure M.E.1

![](https://cdn.jsdelivr.net/gh/Henrry-Wu/FigBed/Figs/20200806163110.png)

Theorem. (Implicit Function Theorem) Suppose that every equation $ \mathrm{f}_{\mathrm{n}}(\cdot) $ is continuously differentiable with respect to its $ \mathrm{N}+\mathrm{M} $ variables and that we consider a solution $ \bar{x} $ at parameter values $ \bar{q}, $ that is, $ \mathrm{f}_{\mathrm{n}}(\overline{\mathrm{x}} ; \overline{\mathrm{q}})=0 $ for every n. If
$$
\left|\mathrm{D}_{\mathrm{x}} \mathrm{f}(\overline{\mathrm{x}} ; \overline{\mathrm{q}})\right|=\left|\begin{array}{ccc}
\frac{\partial \mathrm{f}_{1}(\overline{\mathrm{x}}, \overline{\mathrm{q}})}{\partial \mathrm{x}_{1}} & \cdots & \frac{\partial \mathrm{f}_{1}(\overline{\mathrm{x}}, \overline{\mathrm{q}})}{\partial \mathrm{x}_{\mathrm{N}}} \\
\frac{\partial \mathrm{f}(\overline{\mathrm{x}}, \overline{\mathrm{q}})}{\partial \mathrm{x}_{1}} & \ddots & \\
& \cdots & \frac{\partial \mathrm{f}_{1}(\overline{\mathrm{x}}, \overline{\mathrm{q}})}{\partial \mathrm{x}_{\mathrm{N}}}
\end{array}\right| \neq 0
$$

then the system can be locally solved at $ (\overline{\mathrm{x}}, \overline{\mathrm{q}}) $ by implicitly defined functions $ \eta_{\mathrm{n}}: \mathrm{B}^{\prime} \rightarrow \mathrm{A}^{\prime} $ that are continuously differentiable. Moreover, the first-order effects of $ \mathrm{q} $ on $ \mathrm{x} $ at $ (\overline{\mathrm{x}}, \overline{\mathrm{q}}) $ are given by

$$
\mathrm{D}_{\mathrm{q}} \eta(\overline{\mathrm{q}})=-\left[\mathrm{D}_{\mathrm{x}} \mathrm{f}(\overline{\mathrm{x}} ; \overline{\mathrm{q}})\right]^{-1} \mathrm{D}_{\mathrm{q}} \mathrm{f}(\overline{\mathrm{x}} ; \overline{\mathrm{q}})
$$

Example Consider the competitive firm that uses a single input to produce a single output with the differentiable production function $ f $ facing the price $ w $ for the input and the price $ p $ for output. Profit maximization: $ \mathrm{pf}(\mathrm{z})-\mathrm{wz} $ First order condition: $ \mathrm{pf}^{\prime}(\mathrm{z}(\mathrm{w}, \mathrm{p}))-\mathrm{w}=0 $ for all $ (\mathrm{w}, \mathrm{p}) $

How does z depend on w and p?

Differentiating with respect to w the equation that z $ (w, p) $ satisfies we get
$$
\mathrm{pf}^{\prime \prime}(\mathrm{z}(\mathrm{w}, \mathrm{p})) \mathrm{z}_{\mathrm{w}}^{\prime}(\mathrm{w}, \mathrm{p})-1=0
$$

If $ \mathrm{f}^{\prime \prime}(\mathrm{z}(\mathrm{w}, \mathrm{p})) \neq 0, $ then

$$
z_{w}^{\prime}(w, p)=\frac{1}{p f^{\prime \prime}(z(w, p)}
$$

since $ z(w, p) $ is a maximizer, $ f^{\prime \prime}(z(w, p)) \leq 0 . $ Hence if $ f^{\prime \prime}(z(w, p)) \neq 0 $ then $ z_{w}^{\prime}(w, p)<0 $
Similar argument for the effect of p.
omparative Statics and the Implicit Function Theorem

Figure M.E.2: what might happen if the condition fails?
(
o Note that $ f_{x}^{\prime}(\bar{x} ; \bar{q})=0 $
