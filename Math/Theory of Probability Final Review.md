# Basics of Counting: 
## Permutations
- Suppose we have a set, $S:= \{1,\dots,n\}$, that contains $n$ numbers. There are $n!$ possible **permutations** of $S$.
## Choosing/Selection:
- Ways to **choose** $k$ numbers out of $n$ numbers: ${n \choose k}$
## Multinomial Coefficients
- **Multinomial coefficients**: Dividing $\{1,\dots,n\}$ into groups containing $n_{1},\dots,n_{r}$ number, such that: $${n \choose {n_{1},\dots ,n_{r}}}=\frac{n!}{n_{1}!,\dots,n_{r}!}$$
## Integer Partitions: 
- Strictly Positive Elements: 
	- Suppose our elements are such that, $x_{1}+\dots+x_{k}\geq{1}=n$. Our solution is such that: $${n-1 \choose k-1}$$
- Strictly Non-Negative Elements: 
	- Suppose our elements are such that, $x_{1}+\dots+x_{k}\geq{1}=n$. Our solution is such that: $${n+k-1 \choose k-1}$$

# Axioms of Probability: 
- For two **disjoint** events $E_{1},\dots,E_{n}$ we can recognize the probability of the union of these events as the sum of the probability of the individual events, such that: $$\mathbb{P}(E_{1} \cup E_{2}\dots)=\mathbb{P}(E_{1})+\mathbb{P}(E_{2})\dots$$
- The **total probability** for the events, $E$ and $F$, are such that: $$\mathbb{P}(E)=\mathbb{P}(E \cap F) + \mathbb{P}(E \cap F^c)=\mathbb{P}(E | F)\mathbb{P}(F)+\mathbb{P}(E|F^c)\mathbb{P}(F^c)$$
- The **inclusion-exclusion principle** for events, $A$, $B$, $C$, is such that:  $$\mathbb{P}(A \cup B \cup C)=\mathbb{P}(A)+\mathbb{P}(B)+\mathbb{P}(C)- \mathbb{P}(A \cap B)- \mathbb{P}(A \cap C)-\mathbb{P}(B \cap C)+\mathbb{P}(A \cap B \cap C)$$
# Conditional Probability and Independence: 
- The **conditional probability** for events, $A$ and $B$, is such that: $$\begin{align}
\mathbb{P}(A|B)&= \frac{\mathbb{P}(A \cap B)}{P(B)} \\ \\
\mathbb{P}(A|B)\mathbb{P}(B)&= {\mathbb{P}(A \cap B)}
\end{align}$$
- Given $A$ and $B$ are independent events if $\mathbb{P}(A|B)=\mathbb{P}(A) \to \mathbb{P}(A \cap B)=\mathbb{P}(A)\mathbb{P}(B)$. 
- Bayes formula: $$\mathbb{P}(B|A)=\frac{\mathbb{P}(A \cap B)}{\mathbb{P}(A)}=\frac{\mathbb{P}(A|B)\mathbb{P}(B)}{\mathbb{P}(A|B)\mathbb{P}(B)+\mathbb{P}(A|B^c)\mathbb{P}(B^c)}$$

# Discrete Random Variables: 
- The **Probability mass function** of the discrete random variable, $X$: $$p_{x}(t)=\mathbb{P}(X=t)$$
- The **expectation/mean** of a discrete random, $X$, is such that: $$\mathbb{E}(X)= \sum_{t}tp_{x}(t)$$
- Suppose we have a function, $g(X)$, which is a function of the discrete random variable $X$. The **expectation** of the function, $g(X)$, is such that: $$\mathbb{E}(g(X))=\sum_{t}g(t)p_{x}(t)$$
- The **variance** of the discrete random variable, $X$, is such that: $$\begin{align}
\text{Var}(X)&=\mathbb{E}(X-\mathbb{E}(X))^2 \\
&= \mathbb{E}(X^2)-(\mathbb{E}(X))^2
\end{align}$$
## Typical Discrete Random Variables: 
### Binomial Random Variables: 
- We would like to represent the binary outcome of $n$ trials, with a probability $p$. 
- For $X\sim \text{Bin}(n,p)$, the **p.m.f.** is such that: $$p_{X}(k)={n \choose k}p^k(1-p)^{n-k}$$
- For a sequence of binomial random variables given by, $X=X_{1}+\dots+X_{n}$, where each $X_{k}$ indicates the result of the $k-$th iteration. Every random variable within the sequence, $X$, is **independent**. 
- **Expectation**: $$\mathbb{E}(X)=np$$
- **Variance**: $$\begin{align}
\text{Var}(X)&=\text{Var}(X_{1})+\dots+\text{Var}(X_{n}) \\
&= np(1-p)
\end{align}$$
- **Additivity under Variance**: $$\text{Var}(X+Y)=\text{Var}(X)+\text{Var}(Y)$$
	- When $X$ and $Y$ are independent 
## Poisson Random Variables: 
- If $X\sim \text{Poisson}(\lambda)$, then the **p.m.f.** is such that: $$\mathbb{P}(X=n)= \frac{\lambda^n}{n!}e^-\lambda, n \in \mathbb{N}$$
- **Expectation**: $$\mathbb{E}(X)=\text{Var}(X)=\lambda$$
- **Poisson** **approximations** hold for when $X_{n}\sim \text{Bin}(n,p_{n})$ where $n>50$ and $np_{n}=\lambda$, when $\lambda \in (0.1<\lambda<10)$. 
## Geometric Random Variables: 
- Keep repeating trials, until we achieve the desired outcome. We want to find the number of trials necessary to achieve our outcome.  
- For a random variable, $Y$, that follows a geometric distribution such that, $Y\sim \text{Geometric}(p)$, we can define the **p.m.f.** to be such that:  $$p_{y}(n)=(1-p)^{n-1}p, n \in \mathbb{N}$$
- The **expectation** of $Y$ is such that: $$\mathbb{E}(Y)=\frac{1}{p}$$
- The **variance** of $Y$ is such that:$$Var(Y)= \frac{1-p}{p^2}$$
# Continuous Random Variables: 
- If $X$ is a continuous random variable with density function, $f_{X}(t)$, then the **p.m.f.** is such that: $$\begin{align}
&\mathbb{P}(t\leq X\leq t+\Delta t) \approx f_{X}(t)\Delta t \\
\to& \mathbb{P}(a\leq X\leq b)=\int^b_{a}f_{X}(t)dt
\end{align} $$
- The **cumulative distribution function** (CDF) is given, such that: $$F_{X}(x)=\mathbb{P}(X\leq x)=\int^x_{-\infty}f_{X}(x)dx$$
- By the relationship of integration and differentiation, we conclude that the derivative of the CDF is the PMF, such that: $$f_{X}(x)=F_{X}'(x)$$
- The expectation of $X$ is such that: $$\mathbb{E}(X)=\int^\infty_{-\infty}xf_{X}(x)dx$$
- Suppose we have a function, $g(X)$, which is a function of the random variable, $X$. The **expectation** of $g(X)$ is such that: $$\mathbb{E}(g(X))=\int^\infty_{-\infty}g(x)f_{X}(x)dx$$
- The variance of $X$ is given by: $$\text{Var}(X)=\mathbb{E}(X^2)-(\mathbb{E}(X))^2$$
## Typical Continuous Random Variables: 
- **Uniform Distributions**: 
	- If $X\sim \text{Unif}([a,b])$, then the p.m.f. for $a\leq x\leq b$ and 0 else, is such that: $$f_{X}(x)= \frac{1}{b-a}$$
	- The **expectation** of $X$ is such that: $$\mathbb{E}(X)= \frac{a+b}{2}$$
	- The **variance** of $X$ is such that: $$\text{Var}(X)= \frac{(b-a)^2}{12}$$
- **Exponential Distributions**: 
	- If $Y\sim \text{Exp}(\lambda)$, then the p.m.f. for $y>0$ and $0$ otherwise, is such that:   $$f_{Y}(y)=\lambda e^{-\lambda y}$$
	- The **expectation** of $X$ is such that:$$\mathbb{E}(Y)= \frac{1}{\lambda}$$
	- The **variance** of $X$ is such that: $$\text{Var}(Y)= \frac{1}{\lambda^2}$$
- **Normal Distributions**: 
	- If $X\sim N(\mu,\sigma^2)$, then the p.m.f. is such that: $$f_{X}(x)=\frac{1}{\sqrt{ 2\pi \sigma^2 }}e^{-(x-\mu)^2/2\sigma^2}$$
	- The **expectation** of $X$ is such that: $$\mathbb{E}(X)=\mu$$
	- The **variance** of $X$ is such that: $$\text{Var}(X)=\sigma^2$$
	- We can **standardize** any normal distribution by linear transformations. If $X\sim N(\mu,\sigma^2)$ then: $$\frac{X-\mu}{\sigma}\sim N(0,1)$$
	- The cumulative distribution function for standard normal random variables is such that: $$\Phi(x)=\int^x_{-\infty} \frac{1}{\sqrt{ 2\pi }}e^{-\frac{t^2}{2}}dt$$
# Joint Distributions and Independence: 
- **Joint probability mass functions** are such that: $$p_{X,Y}(x,y)=\mathbb{P}(X=x,Y=y)$$
- **Joint probability density functions** for $(X,Y)$ are such that: $$\begin{align}
&\mathbb{P}(x\leq X \leq x +\Delta x, y\leq Y \leq y+ \Delta y) \\
\approx& f_{X,Y}(x,y)\Delta x\Delta y
\end{align}$$
- For jointly continuous random variables, $(X,Y)$, **their probability density function**: $$\mathbb{P}((X,Y)\in A)=\int_{A}f_{X,Y}(x,y)dxdy$$
- For the function, $g(X,Y)$, the **expectation** is such that: $$\begin{align}
&\text{Discrete: }\mathbb{E}g(X,Y)=\sum_{X,Y}g(x,y)p_{X,Y}(x,y) \\
&\text{Continuous: } \mathbb{E}g(X,Y)= \iint g(x,y)f_{X,Y}(x,y)dxdy
\end{align}$$
- The **random variables $X$ and $Y$ are independent**, when $$\begin{align}
&\text{Discrete: }p_{X,Y}(x,y)=p_{X}(x)p_{Y}(y) \\
&\text{Continuous: } f_{X,Y}(x,y)=f_{X}(x)f_{Y}(y)\end{align}$$
- For independent random variables, $X$ and $Y$, if we have the functions of each variable, $f(X)$ and $g(Y)$, the expectation is such that: $$\mathbb{E}(f(X)g(Y))=\mathbb{E}f(X)\mathbb{E}g(Y)$$
# Sums of Independent Random Variables: 
- For a binomial random variable, $X\sim \text{Bin}(n,p)$, we can recognize $X$ as the sum of Bernoulli random variables $X_{k}$ with parameter $p$, such that: $$X=X_{1}+\dots+X_{n}$$ 
- For $X\sim \text{Poisson}(\lambda_{1})$ and $Y \sim \text{Poisson}(\lambda_{2})$, where $X$ and $Y$ are independent, we conclude that: $$X+Y\sim \text{Poisson}(\lambda_{1}+\lambda_{2})$$
# Conditional Distribution and Expectation: 
- **Conditional probability mass functions** can be found such that: $$p_{X|Y}(x|y)=\mathbb{P}(X=x|Y=y)= \frac{p_{X,Y}(x,y)}{p_{Y}(y)}$$
- **Conditional probability density functions** can be found such that: $$f_{X|Y}(x|y)=\frac{f_{X,Y}(x,y)}{f_{Y}(y)}=c(y)f_{X,Y}(x,y)$$
- **Conditional expectation of $X$ given $Y=y$** is such that: $$\begin{align}
&\mathbb{E}[X|Y=y]= \\
&\text{Discrete: }\sum_{X}xp_{X|Y}(x|y) \\
&\text{Continuous: }\int_{-\infty}^\infty xf_{X|Y}(x|y)dx\end{align}$$
- **Tower Property**: $$\mathbb{E}(X)=\mathbb{E}(\mathbb{E}(X|Y))$$
# Covariance and Correlation: 
## Motivation:
- Suppose we have the events $X$ and $Y$ which are independent, and the functions, $g(X)$ and $h(Y)$. The expectation of the product of these functions is such that: $$\begin{align}
\mathbb{E}g(X)h(Y)&=\mathbb{E}(g(X))\mathbb{E}(h(Y)) \\ \\
\mathbb{E}(XY)&=\mathbb{E}(X)\cdot\mathbb{E}(Y)
\end{align}$$
	- The reverse is not true
- We also recognize that $X$ is NOT independent of $X^2$, but they are uncorrelated. 
## Covariance: 
- Suppose we have the random variables, $X$ and $Y$. The **covariance** of these random variables is such that: $$\begin{align}
\text{Cov}(X,Y)&=\mathbb{E}(X-\mathbb{E}(X))(Y-\mathbb{E}(Y)) \\ \\
&= \mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)
\end{align}$$
- We also recognize the specific **reflexive** case of finding the covariance of $X$ and itself, is such that: $$\text{Cov}(X,X)=\text{Var}(X)$$
### Properties of Covariance: 
- **Symmetry** **Property**: $$\text{Cov}(X,Y)=\text{Cov}(Y,X)$$
- **Reflexive Property**: $$\text{Cov}(X,X)=\text{Var}(X)$$
- **Scalar Additivity and Multiplication Properties**: $$\begin{align}
\text{Cov}(X+b,Y)&=\text{Cov}(X,Y) \\ \\
\text{Cov}(aX,Y)&=a\text{Cov}(X,Y)
\end{align}$$
- **Additivity of Random Variables**: $$\text{Cov}(X+Z,Y)=\text{Cov}(X,Y)+\text{Cov}(Z,Y)$$
- **Sum of i.i.d. Random Variables**: $$\text{Cov}\left( \sum_{i=1}^{n}X_{i},\sum_{j=1}^{m}Y_{j} \right)=\sum_{i=1}^n \sum_{j=1}^m\text{Cov}(X_{i},Y_{j})$$
- **Independence of Random Variables**: 
	- When $X$ and $Y$ are independent, then: $$\text{Cov}(X,Y)=0$$
	- Even when $\text{Cov}(X,Y)=0$, this does NOT imply that $X$ and $Y$ are independent. 


## Correlation: 
- For the random variables, $X$ and $Y$, the **correlation** of $X$ and $Y$ is defined such that: $$\begin{align}
\rho(X,Y)&=\frac{\text{Cov}(X,Y)}{\sqrt{ Var(X)Var(Y) }} \\ \\
&= \text{Cov}\left( \frac{X}{\sqrt{ Var(X) }}, \frac{Y}{\sqrt{ Var(Y) }} \right)
\end{align}$$
- For a scalar multiple, $a>0$, and a scalar additive, $b \in \mathbb{R}$, we recognize the **invariance of correlation** such that: $$\rho(X+b,Y)=\rho(aX, Y)=\rho(X,Y)$$
- Similarly, when the **scalar multiple $a<0$ is negative**, we recognize the correlation to be: $$\begin{align}
\rho(aX,Y)&= \frac{a\text{Cov}(X,Y)}{\sqrt{ \text{Var}(aX)\text{Var}(Y) }} \\
&= \frac{a\text{Cov}(X,Y)}{|a|\sqrt{ \text{Var}(aX)\text{Var}(Y) }} \\
&= -\rho(X,Y)
\end{align}$$
- For any random variables, $X$ and $Y$, we recognize that the **correlation is bounded** such that: $$-1\leq \rho(X,Y) \leq{1}$$
	- We can prove this using the Cauchy-Schwarz inequality, such that $$\begin{align}
(\mathbb{E}(XY))^2 &\leq \mathbb{E}(X^2)\mathbb{E}(Y^2) \\
&\iff  \\
\mathbb{P}(tX=Y&)=1, t \in \mathbb{R}
\end{align} $$
- We can also recognize the case of **squaring the correlation, which then changes our bounds**, such that: $$\begin{align}
0 \leq\rho(X,Y)^2 \leq{1}
\end{align}$$
- Some **visual motivation** for the appearances of correlation: ![[Pasted image 20250508173136.png]]

# Moment Generating Functions: 
- Suppose we have a random variable $X$. For $n\geq{1}$, the $n-$th moment of $X$ is defined as $\mathbb{E}(X^n)$. 
- We begin by considering the moment-generating-function (MGF), as: $$M_{X}(t)=\sum_{n=0}^\infty \frac{t^n}{n!}\mathbb{E}X^n$$
	- We can recognize this as the Taylor approximation of the function, such that: $$\begin{align}
e^{tX}&=\sum^\infty_{n=0} 
       \frac{(tX)^n}{n!} \\
\therefore M_{X}(t)&=\mathbb{E}(e^{tX})
\end{align}$$
- Thus it then follows that: $$\mathbb{E}(X^n)= \frac{d^n}{dt}M_{X}(t)|_{t=0}$$
## MGF for Binomial Random Variables: 
- Suppose we have a random variable, $X \sim \text{Bin}(n,p)$. Our **MGF** then follows: $$\begin{align}
M_{X}(t)&=\mathbb{E}e^{tX} \\
&= (pe^t + (1-p))^n
\end{align}$$
- We can then define the **expectation** for $X$ to be such that: $$\mathbb{E}(X)= M'_{X}(0)=np$$
- We can also define the **variance** of $X$ to be such that: $$\text{Var}(X)=np-np^2 = np(1-p)$$
## MGF for Poisson Random Variables: 
- Suppose we have a random variable, $X \sim \text{Pois}(\lambda)$. Our **MGF** then follows: $$\begin{align}
M_{X}(t)&=\mathbb{E}e^{tX}  \\
&= \sum_{k=0}^\infty \frac{{\lambda^k e^{-\lambda}}}{k!}e^{tk} \\
&= e^{\lambda(e^t -1)}
\end{align}$$
- We define the **expectation** for $X$ to be such that: $$\mathbb{E}(X)=M'_{X}(0)=\lambda$$
- We can also further define the **variance** of $X$ to be such that: $$\text{Var}(X)=\lambda$$
## MGF for Uniform Random Variables: 
- Suppose we have a random variable, $X \sim \text{Unif}([a,b])$. We can define our **MGF** to be such that: $$\begin{align}
M_{X}(t)&= \mathbb{E}(e^{tX}) \\
&= \int_{a}^{b} \frac{1}{b-a}e^{tx}dx \\
&= \frac{e^{tb}-e^{ta}}{t(b-a)}
\end{align}$$
## MGF for Normal Random Variables: 
- Let $X \sim N(\mu,\sigma^2)$, then our MGF follows such that: $$\begin{align}
M_{X}(t)&= \mathbb{E}e^{t\mu +t \sigma \xi} \\ 
&= \int^\infty_{-\infty} \frac{1}{\sqrt{ 2\pi }}e^{tx - x^2/2}dx \\
&= e^{t\mu + (\sigma^2t^2)/2}
\end{align}$$
- The **expectation** of $X$ and $X^2$ is given by: $$\begin{align}
\mathbb{E}(X)&=\mu \\
\mathbb{E}(X^2)&=\sigma^2 + \mu^2
\end{align}$$
## Properties of Moment Generating Functions: 
- **Additivity of Random Variables:** If the random variables $X$ and $Y$ are independent,  $Z=X+Y$, then the MFG of $Z$ is such that: $$M_{Z}(t)=M_{X}(t)M_{Y}(t)$$
	- Suppose $X \sim N(\mu_{1},\sigma^2_{1})$ and $Y \sim N(\mu_{2},\sigma^2_{2})$. Then $Z\sim N(\mu_{1} + \mu_{2}, \sigma^2_{1} + \sigma^2_{2})$, by the properties of exponentials. 
- **Uniqueness of Distribution**: If $M_{X}(t)$ is finite for some interval containing 0 and $M_{Y}(t)=M_{X}(t)$, then we assert that $X$ and $Y$ have the same distribution. 
	- #### Example: 
		- If a random variable $X$ has a MGF of $e^{\mu t + (\sigma^2 t^2)/2}$, then $X$ must be a normal random variable with expectation $\mu$ and variance $\sigma^2$
## Characteristic Functions: 
- Moment generating functions have the downside that they can go to $\infty$ for $t\neq{0}$
	- To solve this, we can replace the parameter $t$, with $it$ in our MGF. 
- Then for a random variable $X$, its **characteristic function** is defined such that: $$\phi_{X}(t)=\mathbb{E}(e^{itX})$$
	- #### Example: 
		- Let the random variable $X$ follow a normal distribution, such that: $X \sim N(\mu, \sigma^2)$. Then the characteristic function of $X$ is given by: $$\begin{align}
\phi_{X}(t)&=\mathbb{E}(e^{itX}) \\
&= e^{i\mu t - (\sigma^2t)/2}
\end{align}$$
		- Then our characteristic function will **converge** such that: $$|\phi_{X}(t)|\leq 1, t \in \mathbb{R}$$
- **Additivity of Random Variables**: Suppose we have random variables $X$ and $Y$, which are independent of each other. Then let another random variable $Z$ represent the sum of $X$ and $Y$, such that $Z=X+Y$. Then it follows that the characteristic function of $Z$ is the product of the characteristic functions of $X$ and $Y$, such that: $$\phi_{Z}(t)=\phi_{X}(t)\phi_{Y}(t)$$
- **Relation MGFs and CFs**: We also recognize that characteristic functions and moment generating functions determine each other as well. 

# Inequalities about Expectation: 
## Markov's Inequality (Law of Large Numbers): 
- Suppose we have random variables $X$ and $Y$:
	- We can recall that if, $X\geq 0$, then $\mathbb{E}(X)\geq 0$. This equality only holds if $\mathbb{P}(X=0)=1$. 
	- Similarly, if $X\geq Y$, it then follows that: $$\mathbb{E}(X)\geq \mathbb{E}(Y)$$
	- Since $-|X| \leq X \leq |X|$, it also follows that $$|\mathbb{E}(X)|\leq \mathbb{E}|X|$$
### Proof of Markov's Inequality: 
- Let $X$ is a random variable that takes on ONLY non-negative values; then for any value $a>0$, it follows that: $$\mathbb{P}\{X\geq a\}\leq \frac{\mathbb{E}(X)}{a}$$
- For $a>0$, let $$I = \begin{cases}
1, X\geq a \\
0, \text{else}
\end{cases}$$
- We then also recognize that $X\geq 0$, which allows us to conclude: $$I \leq \frac{X}{a}$$
- Then taking the expectation of the preceding inequality yields, $$\mathbb{E}(I)\leq \frac{\mathbb{E}(X)}{a}$$
- Which, because $\mathbb{E}(I)=\mathbb{P}(X\geq a)$, then proves Markov's Inequality. 

## Chebyshev's Inequality: 
- Suppose $X$ is a  random variable with expectation $\mu$ and variance $\sigma^2$. Then for any $k>0$, we can proceed such that: $$|X-\mu|\geq k \iff (X-\mu)^2 \geq k^2$$
- Then, by Markov's inequality, where $a=k^2$, we can further conclude that: $$\begin{align}
&\mathbb{P}(|X-\mu|\geq k) = \mathbb{P}((X-\mu)^2\geq k^2)\leq \frac{\mathbb{E}(X-\mu)^2}{k^2}=\frac{\sigma^2}{k^2} \\
\to & \mathbb{P}(|X-\mu| \geq k)\leq \frac{\sigma^2}{k^2}
\end{align}$$
- Thus, Chebyshev's inequality: $$\begin{align}
&\mathbb{P}(|X-\mu|\geq k) \leq \frac{\sigma^2}{k^2} \\
\to & \mathbb{P}\{(X-\mu)^2 \geq k^2\} \leq \frac{\mathbb{E}[(X-\mu)^2]}{k^2}
\end{align}$$
### One-Sided Chebyshev's Inequality: 
- Suppose $X$ is a random variable with expectation $\mu$ and variance $\sigma^2$, we have: $$\mathbb{P}(X\geq \mu +k)\leq \frac{\sigma^2}{\sigma^2 + k^2}$$
- For any $a> -\mu-k$, we can minimize over $a$, such that: $$\mathbb{P}(X\geq \mu +k)= \mathbb{P}(X+a \geq \mu +k +a )\leq \frac{\mathbb{E}(X+a)^2}{(\mu+k+a)^2}$$
## Chernoff Bounds: 
- Let $X$ be a random variable with a moment generating function: $$M_{X}(t)=\mathbb{E}e^{tX}$$
- For $k>0$ and $t>0$, we can apply Markov's inequality such that: $$\mathbb{P}(X\geq k)= \mathbb{P}(e^{tX}\geq e^{tk})\leq e^{-tk}\mathbb{E}(e^{tX})= e^{-tk}M_{X}(t)$$
- If the random variables, $X_{1},\dots,X_{n}$, are independent then $$\mathbb{P}(X_{1},\dots,X_{n}\geq k)\leq e^{-tk}M_{X_{1}+\dots+X_{n}}(t)=e^{-tk}M_{X_{1}}(t)+\dots+M_{X_{n}}(t)$$
	- We can choose an optimal $t$ or fix a specific $t$. 

# Convergence of Random Variables: 
- We begin by supposing that $X_{n}$ and $X$ are random variables. We can recognize three distinct cases identifying the convergence of random variables, such that: 
	1) $X_{n}$ converges to $X$ **almost surely** if: $$\mathbb{P}(\lim_{ n \to \infty } X_{n}=X)=1$$
	2) $X_{n}$ converges to $X$ **in probability**, if for any $\delta>0$: $$\lim_{ n \to \infty }\mathbb{P}(|X_{n}-X|\geq \delta)=0$$
	3) $X_{n}$ converges to $X$ **in distribution** if for any number, $x$, $F(x)=\mathbb{P}(X\leq x)$ is continuous at $x$, such that: $$\begin{align}
&F_{n}(x)=\mathbb{P}(X_{n}\leq x) \\
\to& \mathbb{P}(X\leq x)=F(x)
\end{align}$$
- We then recognize that convergence almost surely $\implies$ convergence in probability $\implies$ convergence in distribution. 
	- Suppose $X_{n}$ converges to $X$ almost surely. Let $A$ be the event where $\lim_{ n \to \infty }X_{n}=X$, which also has probability $1$. Then for any $\delta>0$, there exists some random $N(w)< \infty, w\in A$, such that for any $n>N(w)$, $|X_{n}(w)-X(w)|<\delta$. Since $\mathbb{P}(N<\infty)=1$, it holds that for $\lim_{ n \to \infty }\mathbb{P}(N>m)=0$, which then further implies that $\lim_{ n \to \infty }\mathbb{P}(|X_{n}-X|\geq \delta)=0$
	- Suppose $X_{n}$ converges to $X$ in probability and $F$ is continuous at the point $x$. Then $|F_{n}(x)-F(x+\epsilon)|\leq \mathbb{P}(|X_{n}-X|>\epsilon)$. 
### Weak Law of Large Numbers: 
- Let $X_{1},X_{2},\dots$ be a sequence of i.i.d. random variables with finite expectation, $\mu$. Then $\frac{X_{1}+\dots+X_{n}}{n}=\bar{X}$ converges to $\mu=\mathbb{E}(X_{1})$ in probability. That is, for any $\delta>0$: $$\lim_{ n \to \infty }\mathbb{P}\left( |\frac{(X_{1}+\dots+X_{n})}{n}-\mu|> \delta \right)=0 $$
### Strong Law of Large Numbers: 
- Let $X_{1},X_{2},\dots$ be a sequence of i.i.d. random variables, again with a finite expectation, $\mu$. Then $\bar{X}$ converges to $\mu=\mathbb{E}(X_{1})$ almost surely. That is, on an event with probability 1: $$\lim_{ n \to \infty } \frac{\bar{X}}{n}=\mu $$
# Central Limit Theorem: 
- For a sequence, $S$, of i.i.d. random variables $X_{1},\dots,X_{n}$, we can conclude, by the Strong Law of Large Numbers (SLLN), that our sequence converges to $\mathbb{E}(X_{1})$.
- Then, we begin by supposing that the random variables of $S$ have an expectation of $\mu$ and variance $\sigma^2$. Then we conclude that $S$ converges in distribution to a standard normal variable, such that: $$\frac{X_{1}+\dots+{X_{n}}-n\mu}{\sqrt{ n\sigma^2 }} \to N(0,1)$$
## Skorokhod's Representation Theorem for CID: 
- If $X_{n}$ converges to $X$ in distribution, then one can find random variables, $Y_{n}$ and $Y$, such that $Y_{n}$ converges to $X_{n}$, $Y$ converges to $X$ in distribution, while $Y_{n}$ converges to $Y$ almost surely. 
	- It then follows that for any bounded continuous function $f$, $f(Y_{n})$ converges to $f(Y)$ almost surely. 
	- Thus, the convergence of expectation, further implies that: $$\mathbb{E}f(X_{n})=\mathbb{E}f(Y_{n}) \to \mathbb{E}f(Y)=\mathbb{E}f(X)$$
	- We also can conclude that the characteristic function converges such that: $$\phi_{X_{n}}(t)=\mathbb{E}e^{itX_{n}} \to \mathbb{E}e^{itX}=\phi_{X}(t)$$
		- The reverse of this statement is also true, meaning that if the characteristic function of $X_{n}$ converges to the characteristic function of $X$, then $X_{n}$ converges in distribution to $X$, such that: $$\phi_{X_{n}}(t) \to \phi_{X}(t) \implies \lim_{ n \to \infty }X_{n}=^dX $$
# Introduction to Markov Chains: 
- We begin by supposing that we have a set of states, $S$. We then consider a sequence of random variables, $(X_{n})_{n\geq{0}}$, such that $X_{n}$ represents the state on the $n-$th iteration. 
- **Memorylessness**: The next state ONLY depends on the current state AND NONE of the states from previous iterations. 
- $(X_{n})_{n\geq{0}}$ is called a Markov chain IF obeys the Markov property AND $\mathbb{P}(X_{n+1}=j|X_{n}=i)=p_{ij}$ does NOT depend on $n$. 
	- The probability $p_{ij}$ is called a transition probability. 
- Then, it follows that the sum of all transition probabilities goes to one, such that: $$\sum_{j}p_{ij}=1$$
## Transition Matrix: 
- To represent the transition probabilities, we can recognize the stochastic transition matrix, $P$ which is an $n \times n$ matrix with the states represented along each edge. The entry at $P_{ij}$ represents the transition probability from state $i$ to state $j$. 
- If we write $v$ as a vector, $\vec{v}=(v_{1},\dots,v_{n})$, then we can describe the distribution of $X_{n+1}$ given that $X_{n}$ has a distribution $v$, described by $\vec{v}P$. In order to find the state on the $n-$th iteration, we proceed such that: $$v^n=v^{n-1}P=\dots=v^0P^n$$
## Stationary Distributions: 
- If $v^0$ has the property $v^0P=v^0$, then for any $n$, $v^n=v^0$. We recognize this as a **stationary distribution**, such that: $$\pi P=\pi$$
- Stationary distributions do not need to be unique. If $P$ is the identity matrix, we do not change state at all. 
- If the state space, $S$, is finite, then stationary distribution always exists. This is a consequence of the fact that when $\det(I-P)=0$, where $(1,\dots,1)^T$ is an eigenvector with eigenvalue, $\lambda=1$. 
- If the state space is infinite, then the stationary distribution does not necessarily exist. 
	- For example, for a random walk on $\mathbb{Z}$, there is no stationary distribution. 
## Ergodic Markov Chains: 
- **Periodic**: A Markov chain is periodic if: the state $i$ has a period $d$, and all $n$ iterations with $p^n_{ii}=\mathbb{P}(X_{n}=i|X_{0}=i)>0$ are divisible by $d$. 
- **Aperiodic**: A Markov chain is aperiodic if its period is one, and a Markov chain is aperiodic if all it states have period of $1$.
- **Strongly Connected**: For any $i$ and $j$, it is possible to reach the state $j$ from $i$. Thus, there exists an $n>0$ such that $p^n_{ij}=\mathbb{P}(X_{n}=j|X_{0}=i)>0$. 
- **Ergodic**: A Markov chain is ergodic if it is both **aperiodic** AND **strongly connected** 
	- There exists a common $n$,  such that: $p^n_{ij}=\mathbb{P}(X_{n}=j|X_{0}=i)>0$, **jointly** for any states $i$ and $j$.
## Limiting Behavior: 
- Suppose $(X_{n})_{n\geq{0}}$ is an **ergodic** Markov chain with finite state space, $S$. Then the stationary distribution, $\pi$, is unique. Then, for any state $i$, we can recognize the stationary distribution of the state $j$, such that: $$\pi_{j}=\lim_{ n \to \infty }p_{ij}^n=\lim_{ n \to \infty }\mathbb{P}(X_{n}=j|X_{0}=i)$$
- In other words, given any distribution of $X_{0}$, the limiting distribution of $X_{n}$ equals the stationary distribution. Essentially, the **limiting distribution represents the steady state of an ergodic Markov chain**. 
# Poisson Processes: 
## Motivation by the Discrete Case: 
- We begin by recalling that a random variable $X\sim\text{Bin}(n,p)$ with large $n$ and a fixed expectation, $np=\lambda$, can be approximated using $\text{Pois}(\lambda)$. 
- Then, we can divide the **time interval**, such that: $$L_{n,k}=\left[\frac{k}{n}, \frac{k+1}{n}\right)$$
- We assume that independently during each time interval, $L_{n,k}$, the event $A$ occurs with probability, such that: $$\mathbb{P}(A)=\frac{\lambda}{n}$$
- Let $T_{1}$ be the first time event $A$ occurs. For $a>0$ and $a=\frac{k}{n}$, we can recognize that the probability of $T_{1}>a$ is approximately $\text{Exp}(\lambda)$ : $$\begin{align}
\mathbb{P}(T_{1}>a)&=\left( 1-\frac{\lambda}{n} \right)^k \\
&= \left(1-\frac{\lambda}{n} \right)^{an} \\
&= e^{-\lambda a}
\end{align}$$
## Axioms of Poisson Processes: 
- The collection of random variables, $\{N(t): t>0\}$, which "counts the number of events that have occurred" within the time interval, $[0,t]$, with parameter $\lambda>0$, is considered a Poisson process if: 
	1) $N(0)=0$
	2) The numbers of events that occur in disjoint time intervals are independent. 
	3) $N(t')-N(t)$ depends ONLY on $t'-t$.
	4) For small $h$: $\mathbb{P}(N(h)=1)=\lambda h +o(h)$ AND $\mathbb{P}(N(h)\geq 2)=o(h)$
## Properties of Poisson Processes: 
- **Markov Property**: From the independence property, a Poisson process satisfies the Markov property, for $t_{1}<t_{2}<\dots<t_{n+1}$.
- **Additivity Property**: If the Poisson processes, $\{N_{1}(t)\}_{t\geq 0}$ and $\{N_{2}(t)\}_{t>0}$, are independent Poisson processes with parameters, $\lambda_{1}$ and $\lambda_{2}$ respectively, then their sum is another Poisson process, with parameters $\lambda_{1}+\lambda_{2}$, such that: $$\{N_{1}(t)+N_{2}(t)\}_{t\geq 0}$$
- **Division Property**: Let  $\{N_{1}(t)\}_{t\geq 0}$ be a Poisson process with parameter, $\lambda$. For $p>0$, let $\zeta_{1}\dots$ be independent $\text{Ber}(p)$ random variables. Let $N_{1}(t)=\sum^{N(t)}_{n=1}\mathbb{1}_{\zeta_{n}=1}$ and $N_{2}(t)=\sum^{N(t)}_{n=1}\mathbb{1}_{\zeta_{n}=0}$. Then it follows that $\{N_{1}(t)\}_{t\geq 0}$ and $\{N_{1}(t)\}_{t\geq 0}$ are independent Poisson processes with parameters $\lambda p$ and $\lambda(1-p)$. 
## Poisson Point Processes: 
- Let $\Theta$ be a random collection of points on $S$, where $S \subset \mathbb{R}^n$. 
- $\Theta$ is a Poisson point process on $S$, with parameter $\lambda$, if: 
	1) For any $A \subset S$, $\#(A \cap \Theta)$ is a Poisson random variable with parameter $\lambda \cdot \text{Area}(A)$. 
	2) If $A,B \subset S$ are disjoint, then $\#(A \cap \Theta)$ and $\#(B \cap \Theta)$ are independent. 
- If $\{N(t)\}_{t\geq 0}$ is a Poisson process with parameter, $\lambda$, then $\{T_{k}\}_{k\geq 1}$, would be a Poisson point process on the interval, $(0, \infty)$, with parameter $\lambda$.
# Entropy and Coding: 
- We ONLY consider the entropy for **discrete random variables**. 
- Then, we begin by supposing that a random variable, $X$, has a p.m.f., $p_{i}=\mathbb{P}(X=a_{i})$ where $\{a_{i}\}$ are different numbers. 
- The **entropy** of $X$ is defined as: $$H(X)=\sum_{i}-p_{i}\log_{2}(p_{i})$$
	- Examples: 
	1) Suppose we flip $n$ coins. For each outcome, the probability is equal to $2^{-n}$. The entropy would then be, $2^n(-2^{-n}\log_{2}(2^{-n}))=n$. 
	2) If $X\sim \text{Geom}\left( \frac{1}{2} \right)$, then $\mathbb{P}(X=n)=2^{-n}$ and $$\begin{align}
H(X)&=\sum_{n=1}^\infty-2^{-n}\log_{2}(2^{-n}) \\
&= \sum_{n=1}^\infty n 2^{-n} \\
&= 2
\end{align}$$
## Joint Entropy: 
- Suppose $X$ and $Y$ are discrete random variables with joint probability mass function, $p_{x_{i},y_{j}}=\mathbb{P}(X=x_{i},Y=y_{j})$. 
- The **joint entropy** of $(X,Y)$ is defined as: $$H(X,Y)=\sum_{i,j}=-p_{x_{i},y_{j}}\log_{2}(p_{x_{i},y_{j}})$$
	- This is the same as the entropy for a single random variable, $Z=(X,Y)$. 
- If $X$ and $Y$ are independent, then $H(X,Y)=H(X)+H(Y)$. 
## Conditional Entropy: 
- Suppose the conditional p.m.f. of $X$ given $Y=y_{j}$ is such that: $$p(x_{i}|y_{j})=\mathbb{P}(X=x_{i}|Y=y_{j})$$
- The **conditional entropy** of $X$ and $Y$ follow such that: $$\begin{align}
H_{Y=y_{j}}(X)&=\sum_{i}-p(x_{i}|y_{j})\log_{2}(p(x_{i}|y_{j})) \\
&= \sum_{j}H_{Y=y_{j}}(X)p_{Y}(y_{j})
\end{align}$$
	- We recognize that $\mathbb{E}(X|Y)$ is a random variable and a function of $Y$ whereas $H_{Y}(X)$ is a number. 
## Properties of Entropy: 
- For any discrete, independent, random variables, $X$ and $Y$, we can conclude $H_{Y}(X)\leq H(X)$. 
	- The more information you have, the less entropy you have
- The entropy of $X$, $H(X)$, is maximized when $X$ is uniform, such that $H(X)=\log_{2}(n)$
## Coding: 
- We begin with the motivation of the "twenty question game", where we can ask 20 yes/no (binary state) questions  to figure out something. 
- Let $X$ be a discrete random variable. We will attempt to find the value of $X$ by using these binary questions.
### Shannon's Noisy Coding Theorem: 
- The expected number of questions/bits to conclude the value of $X$ is AT LEAST the entropy, $H(X)$. 
- For each possible outcome $x_{k}$, we encode the result using either 0 or 1.
- Each code for $x_{k}$ should be different. 
- The numbers of bits required, $n_{k}$, is the length of the 0/1 sequence for $x_{k}$. 
- Then, by **Shannon's Noisy Coding Theorem**, we know: $$H(X)\leq\mathbb{P}(X=x_{1})n_{1}+\dots+\mathbb{P}(X=x_{m})n_{m}$$
	- There always exists coding such that the expected number of bits is at most $H(X)+1$. 
### Huffman Code: 
- We begin by constructing a binary tree and build from the bottom up, towards the root. 
- Starting with $m$ nodes for $x_{1},\dots,x_{m}$ and for node $x_{k}$, we assign frequency $p_{k}$. 
- We would like to find the two nodes $x_{k_{1}},x_{k_{2}}$ with the smallest frequency. 
	- We accomplish this by creating a new node and joining $x_{k_{1}},x_{k_{2}}$ into the created node. The frequency of this new node is $p_{k_{1}}+p_{k_{2}}$. 
- We continue to iterate until we get a connected tree. 
- The expected number of bits would be less than $H(X)+1$. 
