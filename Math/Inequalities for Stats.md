# Inequalities: 
## Axiomatic Inequalities: 
### Boole's Inequality: 
As we previously saw, for a probability function, $P$, an event $A \in \mathcal{B}$, and a  sequence of events, $A_{1},A_{2},\dots,$ Boole's Inequality follows such that: $$P\left( \bigcup_{i=1}^{\infty}A_{i} \right)\leq \sum_{i=1}^{\infty}P(A_{i})\tag{Boole's Ineq.}$$
### Bonferroni's Inequality: 
Bonferroni's Inequality is particularly useful when computing the intersection of events of $\mathcal{B}$ is difficult or even impossible, and takes advantage of the compliment law and the boundedness of $\mathbb{P}(S)$. To define it, we let $A$ and $B$ be two events, such that: $$P(A \cap B) \geq P(A) + P(B) -1 \tag{Bonferroni's Ineq.}$$
- Whenever $P(A)$ and $P(B)$ are arbitrarily large, Bonferroni's Inequality creates a lower bound that is negative, which despite being correct, is not helpful. Regardless, if both events are highly likely, their intersection will also be highly likely. 
## Numerical Inequalities: 
Following the Real Analysis versions of the **Holder and Cauchy-Schwarz inequalities**, we can apply this to any two random variables, $X$ and $Y$. We then begin by recalling these inequalities such that: 
- Holder Inequality for Real Analysis: $$\sum_{i=1}^{\infty}\lvert a_{i}b_{i} \rvert \leq \left( \sum_{i=1}^na_{i}^2 \right)^{\frac{1}{p}} \left(\sum_{i=1}^nb_{i}^2 \right)^{\frac{1}{q}}, \frac{1}{p} + \frac{1}{q}=1, p,q > 1$$
- Since the Cauchy-Schwarz inequality is a special case of the Holder Inequality, where $p=2$ and $q=2$, we recognize: $$\sum_{i=1}^{\infty}\lvert a_{i}b_{i} \rvert \leq \left( \sum_{i=1}^na_{i}^2 \right)^{\frac{1}{2}} \left(\sum_{i=1}^nb_{i}^2 \right)^{\frac{1}{q_{2}}}$$
Then applying these to any two random variables, $X$ and $Y$, we can conclude that the expectation of any two random variables can be bounded such that: 
### Holder's Inequality: 
**Holder's Inequality** for Probability: $$|\mathbb{E}(XY)| \leq \mathbb{E}|XY| \leq (\mathbb{E}|X|^p)^{1/p}(\mathbb{E}|Y|^q)^{1/q} \tag{Holder's Ineq}$$
### Cauchy-Schwarz Inequality: 
**Cauchy-Schwarz Inequality** for Probability: $$|\mathbb{E}(XY)| \leq \mathbb{E}|XY| \leq (\mathbb{E}|X|^2)^{1/2}(\mathbb{E}|Y|^2)^{1/2}\tag{Cauchy-Schwarz}$$
### Lyapunov's Inequality:
We can also recognize another special case of Holder's inequality, called **Lyapunov's Inequality**. 
- Let $Y \equiv 1$ and $s=pr$, where $1<p< \infty$ and $1 < r < p$, then: $$(\mathbb{E}|X|^r)^{1/r} \leq (\mathbb{E}|X|^s)^{1/s}, 1<r<s<\infty \tag{Lyapunovs Ineq.}$$
### Minkowski's Inequality:
There also exists another special case of Holder's inequality called **Minkowski's Inequality**. 
- For $1 \leq p < \infty$:$$(\mathbb{E}|X+Y|^p)^{1/p} \leq (\mathbb{E}|X|^p)^{1/p} + (\mathbb{E}|Y|^p)^{1/p} \tag{Minkowski's}$$
## Functional Inequalities: 
Unlike the numerical inequalities which focus on bounding the expectation of random variables and dealing with uncountable samples spaces, $\mathcal{B}$, we can also bound probability functions, $P$, themselves. These functional inequalities focus on utilizing properties of functions over $\mathbb{R}$, rather than statistical properties and observations. 
### Jensen's Inequality 
- We can begin by recognizing **Jensen's Inequality**, which underscores the behavior of convex and concave functions. Then, we can begin by more rigorously defining a convex map, $g: \mathbb{R} \to \mathbb{R}$. We consider the map $g$ to be **convex** if: $$g(\lambda x+(1-\lambda)y) \leq \lambda g(x)+(1-\lambda)g(y), \forall xy \text{ and } 0 < \lambda< 1$$
	- Following the definition of convex, the map $g(x)$ is **concave** if $-g(x)$ is convex. 
- Then to define **Jensen's Inequality**, for any random variable, $X$, if $g(X=x)$ is a convex function, it follows that: $$\mathbb{E}g(X) \geq g(\mathbb{E}(X))\tag{Jensen's}$$
	- For the case of $\mathbb{E}g(X) = g(\mathbb{E}(X))$, equality holds iff for every line $a+bx$ that is tangent to $g(x)$ at the $x=\mathbb{E}(X)$, $P(g(X) = a + bX)=1$.  
### QM-AM-GM-HM Inequality:
Then, by utilizing Jensen's and Holder's Inequality, we can derive the $\text{QM-AM-GM-HM}$ inequality **(arithmetic, geometric, harmonic, and quadratic means inequality)**. To do this, we let the sequence $a_{1},a_{2},\dots,a_{n}=\{ a_{n} \} \subset\mathbb{R}^+$ and recognize the expectations, such that: $$\begin{align}
a_{A} &= \frac{1}{n}\sum_{i=1}^na_{i} \tag{Arithmetic Mean} \\
a_{G} &= \left( \prod_{i=1}^n a_{i} \right)^{1/n} \tag{Geometric Mean} \\
a_{H} &= \left( \frac{n}{\sum_{i=1}^na_{i}} \right) \tag{Harmonic Mean} \\
a_{Q} &= \sqrt{ \frac{\sum_{i=1}^na_{i}^2}{n} } \tag{Quadratic Mean}
\end{align}$$
- It then follows that we can bound the expectation of the sequence $\{ a_{n} \}$, such that: $$\begin{align}
&a_{H} \leq a_{G} \leq a_{A} \leq a_{Q}  \\ \\

\implies & \left( \frac{n}{\sum_{i=1}^na_{i}} \right) \leq  \\
&\left( \prod_{i=1}^n a_{i} \right)^{1/n} \leq  \\
&\frac{1}{n}\sum_{i=1}^na_{i} \leq  \\
&\sqrt{ \frac{\sum_{i=1}^na_{i}^2}{n} }
\end{align}\tag{QM-AM-GM-HM} $$
### Covariance Inequalities: 
- We begin by letting $X$ be any random variable. We also define the functions, $g(x)$ and $h(x)$, to be any functions such that $\mathbb{E}(g(X)), \mathbb{E}(h(X))$ and $\mathbb{E}(g(X)h(X))$ exist. Then we can recognize the following cases: 
	1) If $g(x)$ is a monotonically increasing function and $h(x)$ to be monotonically decreasing function, then we can bound the expectation of the products of these functions such that: $$\mathbb{E}(g(X)h(X)) \leq (\mathbb{E}(g(X))\mathbb{E}(h(X)))$$
	2) Alternatively, if $g(x)$ and $h(x)$ are either both monotonically increase or decreasing, then: $$\mathbb{E}(g(X)h(X)) \geq (\mathbb{E}(g(X))\mathbb{E}(h(X)))$$
### Hoeffding's Inequality: 
Hoeffding's Inequality is a special case of the Azuma-Hoeffding Inequality on Martingales. It's particularly useful as it allows us to provide an upper-bound on the amount that a sum of bounded and independent random variables deviates from its expected value. 
- To begin defining Hoeffding's Inequality we recognize the sequence of  bounded and independent random variables by $X_{1},\dots,X_{n}$ where each random variable, $X_{i},$ is confined in a bounded interval such that, $a_{i} \leq X_{i} \leq b_{i}, i \in \mathbb{N}$. Then, for any $\lambda > 0$, we can denote the sum of these random variables with $S_{n},$ such that: $S_{n} = \sum_{i=1}^nX_{i}$. We can then define Hoeffding's Inequality such that: $$\begin{align}
&P(S_{n} - \mathbb{E}(S_{n}) \geq \lambda) \leq e^{-\frac{2\lambda^2}{\sum_{i=1}^n(b_{i}-a_{i})^2}} \\
\implies &P(|S_{n} - \mathbb{E}(S_{n})| \geq \lambda) \leq 2e^{-\frac{2\lambda^2}{\sum_{i=1}^n(b_{i}-a_{i})^2}}
\end{align}\tag{Hoeffding's}$$

### Dvoretzky–Kiefer–Wolfowitz (DKW) Inequality:
Following the definition of Hoeffding's Inequality, we can recognize DKW's Inequality, which is a special case of Hoeffding's Inequality, where $a_{i}=0$ and $b_{i}=1$, $\forall i \in \mathbb{N}$. This is particularly in the case where the sequence of independent and bounded random variables, $X_{1},\dots,X_{n},$ are Bernoulli random variables that are either successful or not. Despite $X_{i}$ being independent of each other, they are not necessarily iid. 
- Recognizing that $a_{i}=0$ and $b_{i}=1,$ $\forall i \in \mathbb{N}$, we can denote DKW's Inequality such that: $$P(|S_{n}- \mathbb{E}(S_{n})| \geq \lambda) \leq 2e^{-\frac{2\lambda^2}{n}}\tag{DKW's Ineq.}$$
#### DKW for Estimators 
Then utilizing this result, we can apply it to the empirical distribution function, $\hat{F}_{n},$ which is an estimator for $X \sim F$ where the sequence of bounded and independent random variables, $X_{1},\dots,X_{n} \sim X$, is considered to be iid. 
- Recognizing $\text{DKW's Ineq.}$ and the empirically derived distribution function, $\hat{F}_{n},$ we can first find an equality for $\hat{F}_{n}$ based on $S_{n}$, and then proceed to bound the estimator such that: $$\begin{align}
S_{n} &= Y_{1} + \dots + Y_{n} = \sum_{i=1}^nY_{i} \\
Y_{i} &= I(X_{i}\leq x), i \in \mathbb{N}  \\
\hat{F}_{n}(x) &= \frac{S_{n}}{n}
\end{align}$$
- Then if we set $\lambda=\delta n$ for any $\delta>0$ and make the substitution $X_{i}=Y_{i},$ by $\text{DKW's Ineq.},$ we can obtain the bound: $$P(\lvert  \hat{F}_{n} - F(x) \rvert \geq \delta ) \leq 2e^{-2\delta^2n}\tag{DKW Estimator}$$
### Bennett's Inequality: 
Bennett's Inequality is an extension of Hoeffding's Inequality and finds its practical uses in situations where a sequence of independent random variables, $X_{1},\dots,X_{n}$, are bounded from one-side. 
It can be considered 'more refined' than Hoeffding's Inequality, in the sense that it considers the variance of each individual random variable and also because it does not assume two-sided boundedness of the random variables. 
- Thus, we can denote Bennett's Inequality in the case that the sequence of independent random variables that are bounded from above or below, such that: $$\begin{align}
&(X_{i}-\mathbb{E}(X_{i}) \leq b), i \in \mathbb{N}, b>0 \tag{Bounded Above} \\
&(X_{i} - \mathbb{E}(X_{i} \geq -b), i \in \mathbb{N}, b>0 \tag{Bounded Below}
\end{align}$$
- For the sake of simplicity, we first consider the case of the sequence of independent random variables being bounded from above. It then follows that for $S_{n}=\sum_{i=1}^nX_{i}$, we can define: $$\begin{align}
&\Sigma^2 := V(S_{n})=\sum_{i=1}^nV(X_{i})=\sum_{i=1}^n\mathbb{E}((X_{i}-\mathbb{E}(X_{i}))^2) \\
\implies& P(S_{n}- \mathbb{E}(S_{n}) \geq \lambda) \leq \exp\left( -\frac{2\lambda^2}{\sum_{i=1}^n(b_{i}-a_{i})^2} \right), \lambda>0
\end{align}$$
- Alternatively, when the sequence of independent random variables are bounded from below, it follow that: $$P(S_{n}-\mathbb{E}(S_{n}) \leq -\lambda) \leq \exp\left( -\frac{2\lambda^2}{\sum_{i=1}^n(b_{i}-a_{i})^2} \right), \lambda>0$$
Since Bennett's inequality assumes that the sequence of independent random variables is only bounded from one-side, we can take the case where the random variables are bounded from both above and below, such that we assume: $$(\lvert X_{i} - \mathbb{E}(X_{i}) \rvert \leq b), i \in \mathbb{N}, b>0$$
- Combining what we previously found in the cases where $X_{i}$ was either bounded from above or below, we can proceed such that: $$P(\lvert S_{n} - \mathbb{E}(S_{n}) \rvert \geq \lambda) \leq 2\exp\left( -\frac{2\lambda^2}{\sum_{i=1}^n(b_{i}-a_{i})^2} \right), \lambda>0$$
	- This effectively extends Hoeffding's Inequality by considering the variance of the individual random variables in the sequence. 
## Estimating Expectation of Bounded Random Variables: 
Recognizing that we can bound the expectation of a sequence of bounded and independent random variables, we can also derive inequalities that effectively bound the variance of a sequence of random variables. 
Then, we let $X$ be a bounded random variable where $\mathbb{E}(X)=\mu$ and $X \in [a,b].$ We then let a sequence of random variables, $X_{1},\dots,X_{n} \sim X$, be iid copies of the bounded random variable, each with an expected value of $\mu.$
- Then, we let $Y_{n}=n\overline{X}_{n}$ and $\lambda=n\delta \ \ (\delta>0)$, and by using Hoeffding's Inequality, we can proceed such that: $$P(\lvert \overline{X}_{n} - \mu \rvert \geq \delta) \leq2\exp\left( -\frac{2n\delta^2}{(b-a)^2}\right)\tag{Mean Estimator}$$
#### Bhatia-David and Popoviciu's Inequalities: 
Following the iid sequence of independent and bounded random variables, $X_{1},\dots,X_{n} \sim X$, where $\mathbb{E}(X)=\mu$ and $X \in [a,b]$, we can begin with the following: $$\begin{align}
&0 \leq \mathbb{E}(X^2)- \mu^2 \leq (a+b)\mu -ab - \mu^2 \\
\implies =& (a-b)\mu -ab-\mathbb{E}(X^2)
\end{align}$$
- Then, we can derive the Bhatia-David Inequality, such that: $$\begin{align}
&\sigma^2 = \mathbb{E}(X^2)-\mu^2 \leq (a+b)\mu_{0}-ab-\mu^2 \\
\implies & \sigma^2 \leq (b-\mu)(\mu-a)\tag{Bhatia-David}
\end{align}$$

If we optimize the Bhatia-David inequality by maximizing the RHS where $\mu \in [a,b]$, then we get, $\mu = \frac{a+b}{2}$, which by substitution into the Bhatia-David inequality gives us the Popoviciu's Inequality, such that: $$\sigma^2 \leq \frac{(b-a)^2}{4}\tag{Popoviciu}$$
- We can also recognize that if we take the upper-bound of the variance, $\sigma^2 \approx \frac{(b-a)^2}{4},$ when we substitute the optimized expectation, $\mu = \frac{a+b}{2}$, we can derive the Central Limit Theorem, such that: $$2\exp\left( -\frac{2n\delta^2}{(b-a)^2}\right) \approx 2\exp\left( -\frac{\delta^2}{\frac{2\sigma^2}{n}} \right) = 2\exp\left( -\frac{\delta^2}{2V(X_{n})} \right)$$
