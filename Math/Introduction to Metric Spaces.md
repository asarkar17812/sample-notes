# Definitions & Motivation:
## Motivation for Metric Spaces
- As part of the study of mathematical spaces, there exists **Metric Spaces**. Metric spaces are a subset of topological spaces and are specifically important because of their induced metric (aka distance function), which provides the notion of 'distance' between any two points in the space. 
- Then more formally we can define a metric space to be an ordered pair, $(M,d)$, where $M$ is our space and $d$ is a function describing the metric on $M$, such that, $d: M \times M \implies \mathbb{R}$. 
## Properties of Metric Spaces: 
- Given a metric space, $M$, the metric, $d$, and the elements, $x,y,z \in M$, we can define a metric space to be a topological space with the following properties: 
	1) The distance from a point to itself is zero: $$d(x,x)=0$$
	2) **Positive-Definiteness** of the metric, $d$: $$\text{If } x\neq y,\text{ then } d(x,y)>0$$
	3) **Symmetry** of the metric, $d$:$$d(x,y)=d(y,x)$$
	4) Closure under the **Triangle Inequality**: $$d(x,z)\leq d(x,y) + d(y,z)$$
### Triangle Inequality: 
- As specified above, closure under the triangle inequality is a requirement for a topological space to be a metric space. Likewise, we can more rigorously define the inequality, $\forall x,y \in \mathbb{R}$, such that: $$|x+y| \leq |x| + |y|$$
	- The importance of the triangle inequality comes from both its geometric interpretation (nearly the Pythagorean theorem), but also it's usefulness in producing other inequalities, including the reverse triangle inequality, such that: $$\begin{align}
|x-y|&\leq |x-z| + |z-y|, \forall x,y,z\in \mathbb{R} \\ \\
||x| - |y|| &\leq |x-y|, \forall x,y \in \mathbb{R}
\end{align}$$
## Geometric Interpretation by the Absolute Value Map: 
- To form a better intuition for metric spaces, we can begin by recognizing the absolute value map applied to some $x$, such that: $$|x| = \begin{cases}
x&,\text{ if } x>0 \\
-x&, \text{ if } x\leq{0}
\end{cases}$$
	- The absolute value map is an example of a homomorphism, $\{\varphi: \mathbb{R} \to \mathbb{R}^{+}| \forall x \in \mathbb{R}\}$. From this, we can observe certain properties of homomorphisms and the absolute value map, such that: 
		1) Non-Injectivity: $$|-x|=|x|, \forall x\in \mathbb{R}$$
		2) Homomorphic Mapping: $$|xy| = |x||y|, \forall x,y\in \mathbb{R}$$
		3) Absolute Value and Square Root Equivalence: $$|x| = \sqrt{x^2 }, \forall x\in \mathbb{R}$$
		4) Absolute Radius: $$(r>0) \implies ((|x|<r) \iff (-r<x<r))$$
		5) Absolute Convergence: $$-|x|\leq x \leq |x|, \forall x \in \mathbb{R}$$
### Euclidean Distance & Norm, Trivial & Usual Metrics:
- One of the most common metrics that are encountered across mathematics is the notion of **Euclidean Distance**, denoted by $|x|$, which geometrically represents the distance from an element, $x$, to the origin of the space, $0$. More generally, for $x,y \in \mathbb{R}$, $d(x,y)$ can be defined such that: $$d(x,y) = |x-y|$$
	- $d:\mathbb{R} \times \mathbb{R} \to \mathbb{R}$ 
	- The notion of Euclidean Distance is considered the **usual metric** on $\mathbb{R}.$ 
	- While Euclidean Distance may be considered the "usual metric" over $\mathbb{R},$ there exists the **trivial metric** for any non-empty set $X$, which is defined such that: $$d(p,q) = \begin{cases}
1, \text{if } p \neq q \\
0, \text{if } p=q
\end{cases}$$
	- We can denote the **euclidean norm** of a point, $p=(p_{1}, p_{2})$, for $p_{1},p_{2}\in \mathbb{R}^2$, such that: $$||p||_{2} = \sqrt{ p_{1}^2 +p_{2}^2 } $$
		- The norm of a vector spaces induces the notion of distance between any two points. A metric space is sometimes a normed vector space, but a normed vector space is always a metric space.
			- Some examples of metric spaces that do not have a norm include: 
				1) Graph-based metric spaces
				2) Non-Euclidean Geometry (spherical coordinates, etc.)
- Expanding the notion of distance from a point and the origin, we begin by denoting the points, $(p_{1}, p_{2}), (q_{1},q_{2}) \in \mathbb{R}^2$, as $p$. Then, for any points $p$ and $q$, we can determine the distance between these two points, such that: $$d_{2}(p,q)= ||p-q||_{2}=\sqrt{ (p_{1}-q_{1})^2 + (p_{2}-q_{2})^2 }$$
# Boundedness and Supremum/Infimum:
- We begin by letting a sequence, $\{ a_{n} \}$, be over a metric space, $(X,d)$.
	- We consider the sequence to be **bounded above** if, $\exists M$, such that $a_{n}\leq M$ for every $n \in \mathbb{Z}^+$, such that $M$ is considered the **upper-bound.** 
	- Similarly, we consider the sequence to be **bounded below** if, $\exists M$, such that $a_{n}\geq M$, for every $n \in \mathbb{Z}^+$, such that $M$ is considered the **lower-bound.** 
- Then it follows that the sequence, $\{ a_{n} \}$, is bounded iff, $\lvert a_{n} \rvert \leq M$. 
## Supremum: 
- Following the definition of an upper bound, we can define the **least upper bound**, aka the **supremum**, $\alpha$ of a set, $A$, such that: $$\alpha=\text{sup}A \iff \begin{cases}
\forall a \in A, a \leq \alpha \\
\forall \epsilon>0, \exists a\in A \text{ s.t. } (a> \alpha-\epsilon)
\end{cases}$$
### Existence and Uniqueness of Supremums:
- It then follows that for every non-empty subset, $A \subset \mathbb{R}$, that is bounded above also has a unique supremum. 
	- $\mathit{Proof:}$
		- Suppose $A$ has two supremums, $\alpha$ and $\beta$, such that $\alpha< \beta$
		- If $\alpha$ is the supremum, then $\beta$ cannot be the supremum as well, thus we have a contradiction that makes $\alpha$ the only supremum of a set. 
### Supremums of Functions and Sequences:
 - For a function, $f: A \to \mathbb{R}$, the supremum can be denoted such that $\text{sup}f(A)$. 
	 - By this definition, the supremum of $f$ is the supremum of the post-image of $f$, such that $\alpha=\text{sup}f(A) \implies \alpha \in \mathbb{R}$ 
- It then follows that: $$\alpha=\text{sup}f(A) \iff \begin{cases}
f(x) \leq a, \forall a\in A \\ \\
\text{For any } \epsilon>0, \exists a \in A, \text{ s.t. } f(a)> \alpha - \epsilon
\end{cases}$$
- If we define a function as a sequence such that, $f: \mathbb{N} \to \mathbb{R}$, then we have $a_{n}=f(n)$, we can ascertain the supremum such that $\alpha = \text{sup}a_{n}$
# Open and Closed Sets:
## Epsilon Neighborhoods and Interior Points
- We return to more rigorously defining the boundaries of sets along $\mathbb{R}$, but also for any arbitrary metric space written as $(X,d)$ for $X \in \mathbb{R}$. To do this, we begin by an $\epsilon-$neighborhood around some point $p$, such that: $$N_{\epsilon}(p)= \{ x \in X: d(p,x)< \epsilon \}$$
	- Intuitively, $\epsilon$ represents an infinitesimally small, positive nudge around some point $p$. 
	- Under the usual metric in $\mathbb{R}$, we can define an $\epsilon-$neighborhood with $p \in \mathbb{R}$ and $\epsilon>0$, to be such that: $$N_{\epsilon}(p)= \{ x: p-\epsilon < x <p +\epsilon \}$$
		- In this case, $N_{\epsilon}(p)$ represents an open interval $(p- \epsilon, p + \epsilon)$ which is centered at a point, $p$, with radius $\epsilon$. This intuitively can be expanded to $n-\text{dim}$, with the notion of the unit ball and hypersphere.
- Given a non-empty set $X\in \mathbb{R}$ with a metric $d$, let $E \subseteq X$. Then let a point $p \in E$. We consider $p$ to be an **interior point** if $\exists\epsilon>0$ such that $N_{\epsilon} \subset E$. Then, we can denote the set of interior points of $E$ with $\text{Int}(E)$, which is called the interior of $E$. 
## Open Sets: 
Intuitively, an open set can be recognized through an $\epsilon-$ball. The volume of the ball contains the interior points of the "set", and if this set only contains the interior points, we call the set open. Alternatively, if the "set" also includes the points along the surface of the $\epsilon-\text{ball}$, we call the set closed, as the set contains the union of the volume and the closure of the ball. 
- Now that we have a notion of interior points in metric spaces, we can more accurately define open and closed sets, such that: 
	- Let $O \subset \mathbb{R}$. We consider $O$ to be **open** if:$$\forall o \in O, o \in \text{Int}(O)$$
	- Then using this notion over an arbitrary metric space, $(X,d)$, such that: $$B_{\epsilon}(p)= \{ y \in X| d(x,y)<\epsilon \}$$
		- In other words, a set $O \subseteq \mathbb{R}$ is considered open if, $\forall a \in O$, $\exists N_{\epsilon} \subseteq O$. 
Furthermore, we can define certain properties of open sets under the typical set operations, such that: 
1) The union of an arbitrary collection of open sets is open. 
	- Proof: 
		- Let $\{ O_{\lambda} : \lambda \in \Lambda \}$ be a collection of open sets and $O = \bigcup_{\lambda\in \Lambda}O_{\lambda}$. 
		- For an arbitrary element, $a$, $a \in O \implies a \in O_{\lambda'}$. 
		-  $O_{\lambda'} \text{ is open} \implies \exists N_{\epsilon}(a) \subseteq O_{\lambda'}$. 
		- 
2) The intersection of a finite collection of open sets is open. 

## Limit & Isolated Points: 
To rigorously define a closed set, we must first define both limit and isolated points. 
1) A point $x$ is a **limit point** of a set $A$ if: $$\forall N_{\epsilon}(x) \cap A \neq \{ y\in A| x\neq y \}$$
	- Furthermore, a point $x$ is a limit point of a set $A$ $\iff$ $x = \lim_{ n \to \infty }\{ a_{n} \}$ where $\{ a_{n} \} \subseteq A$ and $a_{n} \neq x, \forall n \in \mathbb{N}$. 
2) A point $a \in A$ is an **isolated point** of $A$, if, it is not a limit point of $A$. 
	- Isolated points are always an element of the set $A$, whereas, the limit points of $A$ may or may not be necessarily contained in $A$. 
## Closed Sets: 
1) Let $F \subset \mathbb{R}$. We consider $F$ to be **closed** if:$$F^c=\frac{\mathbb{R}}{F}, \forall f \in F^c, f \in \text{Int}(F^c)$$
- When applying these notions of open and closed to intervals, we can form a geometric intuition. 
	-  Let the points $a,b,c \in \mathbb{R}$, where the point $c$ represents the center of our interval. Using the notion of distance that is induced by the metric and the triangle inequality, we can define an open interval to be such that: $$(a,b)= \{  x\in \mathbb{R}| d(x,c)=|x-c|< \epsilon \}$$
- These definitions allow us to derive the following facts: 
	1) Every open interval in $\mathbb{R}$ is an open subset of $\mathbb{R}$
	2) 
### Properties of Closed Sets: 
- We let $(M,d)$ be a metric space. Let there be a point $x \in M$, such that $M, \emptyset, \{ x \}$ are closed subsets of $M$. 
	- If $x$ is a limit point of $M$, then $x \in M$ by the definition of a limit point, which then implies $M$ is closed. 
	- To show that $\emptyset$ is closed, we can use the method of contradiction, which then means that we suppose $\emptyset$ is not closed. $\implies \exists x \in M$, such that $x$ is a limit point of $\emptyset$, but since $\emptyset$ is not closed, $x \not\in \emptyset$, which $\implies$ that $\exists \{ x_{n} \} \in \emptyset$ such that $\lim_{ n \to \infty }\{ x_{n} \}=x, \forall n \in \mathbb{N}$, which contradicts our supposition, and thus $\emptyset$ is closed. 
	- For a limit point $y$ of $\{ x \}$, such that $\exists \{ x_{n} \} \in \{ x \}$, where $\lim_{ n \to \infty }\{ x_{n} \} =y$. Since $\{ x_{n} \} \in \{ x \}, \forall n \in \mathbb{N} \implies $
## Bolzano-Weierstrass Theorem:
For any convergent sequence, $\{ a_{n} \}$, we can conclude that the sequence is also bounded. To prove this, let $\lim_{ n \to \infty }a_{r}=L$. If for some $\epsilon>0$, $\exists N>0$ such that if $n\geq N$, by the definition of convergence: $$|a_{n}-L|< \epsilon$$
- Thus, if $n \geq N$, we can proceed to add $|L|$ and bound both sides of the inequality, such that: $$|a_{n}| \leq |a_{n} -L| + |L| \leq \epsilon + |L|$$
- Analyzing the other case where $n<N$, we can conclude that: $$|a_{n}| \leq \text{max}\{ |a_{1}|, \dots,|a_{N-1}| \}$$
- Thus we have demonstrated that any convergent sequence is also bounded. 
Using the result from above, we can begin to derive the Bolzano-Weierstrass theorem, which states that **every** bounded sequence has a convergent subsequence. This result is a fundamental property of $\mathbb{R}$ and is equivalent to the least-upper-bound axiom, which is also known as the supremum property of sequences in $\mathbb{R}$. Then we can begin:
- $\mathit{Proof:}$
	- We begin by letting $\{ a_{n} \}$ be a bounded sequence in $\mathbb{R}$. 
	- Then, we suppose that there is a closed interval, $\Omega=[c,d]$, such that $a_{n} \in \Omega$ for every $n \in \mathbb{Z}^+$. 
	- We consider the two closed intervals, such that: $$\left[c, \frac{c+d}{2}\right], \left[\frac{c+d}{2}, d\right]$$
	- Then, one of these intervals must contain $a_{n}$ for infinitely many positive integers $n$. We can denote this smaller interval with $[c_{k}, d_{k}]$, as we can continue to slowly shrink the interval until it most definitely contains $a_{n}$. This continuous shrinking leads to the sequence of intervals, such that: $$[c_{1}, d_{1}], \dots, [c_{k}, d_{k}]$$
		- This sequence of closed intervals maintains a specific structure where the $i+1 < k$ interval is a subset of the $i$th interval. 
	- We then can proceed to rewrite the interval, $[c_{k}, d_{k}]$, as: $$d_{k} - c_{k} = \frac{d-c}{2^k}, \text{ for } k \in \mathbb{Z}^+$$
	- Thus, $\{ a_{n_{k}} \}_{k=1}^{\infty}$ is a subsequence of $\{ a_{n} \}$. We can also demonstrate that $a_{n_{k}}$ is convergent by recognizing that the subsequences $\{ c_{k} \}$ and $\{ d_{k} \}$ are monotone and bounded. 
	- Then, these subsequences converge to the finite values, $L$ and $M$ respectively, which allows us to proceed such that: $$\begin{align}
M-L&= \lim_{ k \to \infty }d_{k} - \lim_{ k \to \infty } c_{k}  \\ \\
&= \lim_{ k \to \infty }(d_{k} -c_{k})  \\ \\
&= \lim_{ k \to \infty }\frac{(d-c)}{2^k} \\ \\
&= 0  \\ \\
\therefore M - L &= 0 \\ \\
\therefore c_{k} \leq &a_{n_{k}} \leq d_{k}
\end{align} $$
	- Then, by the squeeze theorem, $\{ a_{n_{k}} \}$ converges to $L=M$. 
# Cauchy Sequences: 
- We can define a sequence, $\{ a_{n} \}$ over a metric space $(X,d)$, to be **Cauchy** if, for every $\epsilon>0$, $\exists N \in \mathbb{N}$ such that $d(a_{n},a_{m})<\epsilon$ for $n,m \geq N$. 
	- Then, the Cauchy criteria is stating that the distance between two elements of the sequence, $\{ a_{n} \}$, must converge to the same $\alpha \in \mathbb{R}$.
	- If $\{ a_{n} \}$ is convergent, it then follows that $\{ a_{n} \}$ is also Cauchy. 
		- $\mathit{Proof:}$
			- Let $\{ x_{n} \}$ be a convergent sequence in $(X,d)$. 
			- Then suppose that $\lim_{ n \to \infty }x_{n}=x$. 
			- Let $\epsilon>0$. It then follows that $\exists N>0, n \in \mathbb{Z}^+$, such that if $n \geq N$, then $d(x_{n},x) < \frac{\epsilon}{2}$. 
			- If $m,n \geq N$, then: $$d(x_{m}, x_{n}) \leq d(x_{n},x) + d(x_{m},x) < \frac{\epsilon}{2} + \frac{\epsilon}{2} = \epsilon$$
				- The line above states that the distance between any two elements in the sequence is less than or equal to the distance from the element and the limit of the sequence, which is then less than some $\epsilon$. This then proves that a subsequence of the sequence $\{ x_{n} \}$ is also convergent, iff, $\{ x_{n} \}$ is also convergent.
- The converse of the Cauchy sequence is not necessarily true. If a subsequence is Cauchy and thus convergent, we can conclude the sequence itself is convergent iff the sequence is **complete**. 
	- If every Cauchy sequence in $(X,d)$ is convergent, then we call the metric space, $X$ to be a **complete metric space**. 
- $\mathbb{R}$ is a complete metric space, and thus for any convergent subsequence that is Cauchy in $\mathbb{R}$, the sequence itself is convergent. 
	- $\mathit{Proof:}$
		- Let $\{ a^{(k)} \}$ be a Cauchy sequence in $\mathbb{R}^n$. Then let $\epsilon>0$. 
		- Then, $\exists N \in \mathbb{Z}^+$, such that if, $k,m \geq N$, then by the Euclidean norm, it follows that: $$\sqrt{ \sum_{i=1}^{n}(a_{i}^{(k)} - a_{i}^{(m)})^2 } = d(a^{k},a^{m})< \epsilon$$
		- Then to bound the statement from below, let $j \in \mathbb{Z}^+$, such that: $$\lvert a_{j}^{k}-a_{j}^m \rvert \leq \sqrt{ \sum_{i=1}^{n}(a_{i}^{(k)} - a_{i}^{(m)})^2 } = d(a^{k},a^{m})< \epsilon$$
## Nested-Interval Theorem:
- The nested interval theorem states that the continuous intersection of increasingly smaller closed intervals over a metric space leads to the production of a non-empty set.
- More rigorously, we can define the nested-interval theorem such that for each $n \in \mathbb{N}$, we assume that we have a closed interval: $$I_{n}= [a_{n},b_{n}]=\{ x\in\mathbb{R} | a_{n} \leq x \leq b_{n}\}$$
	- We then assume that each interval, $I_{n}$, contains the $I_{n+1}$ interval. 
	- Then, the resulting nested sequence of closed intervals leads to: $$\dots I_{3} \subset I_{2} \subset I_{1} \implies \bigcap_{n=1}^{\infty}I_{n} \neq \emptyset$$
	- Because the intervals are nested, we can see that every $b_{n}$ serves as an upper bound for the set $A$, such that $x= \text{sup}A$.
## Monotone Sequences and Monotone-Bounded Theorem: 
- Let $\{ a_{n} \}$ be a sequence over a metric space, $(X,d)$. 
	- We consider $\{ a_{n} \}$ to be **monotonically increasing**, if $a_{n} \leq a_{n+1}, \forall n \in \mathbb{N}$. 
		- If $a_{n} < a_{n+1}, \forall n \in \mathbb{N}$, we consider $\{ a_{n} \}$ to be **strictly monotonically increasing** 
	- Likewise, we consider $\{ a_{n} \}$ to be **monotonically decreasing**, if $a_{n} \geq a_{n+1}, \forall n \in \mathbb{N}$ 
		- If $a_{n} > a_{n+1}, \forall n \in \mathbb{N}$, we consider $\{ a_{n} \}$ to be **strictly monotonically decreasing**
- We consider a monotone sequence, $\{ a_{n} \}$, to be convergent iff $\{ a_{n} \}$ is bounded. 
	- $\mathit{Proof:}$
		- 
# Commutative Diagram of Topological Theorems of Metric Spaces: 
$$
\begin{array}{ccc}
\text{Existence of Supremum} & \to  &\text{Monotone-Bounded Theorem} & \\ \uparrow & & \downarrow\\
 \uparrow & & \text{Nested-Interval Theorem} \\
\uparrow & & \downarrow \\
\text{Cauchy Convergence Theorem}& \leftarrow & \text{Bolzano-Weierstrass Theorem}
\end{array}
$$
- Important Series: 
	- $p-$series
		- For $L^p$ spaces and infinite-dimensional linear algebra
	- Geometric series
		- For fractal dimensions
	- Harmonic Series 
		- For harmonic analysis for solving Laplace/Poisson PDEs