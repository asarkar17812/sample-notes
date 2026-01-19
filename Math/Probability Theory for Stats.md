# Basic Set Theory Review - Definitions and Motivations
- We can begin to to review set theory foundations to better build the basis of probability. 
## Sample Space: 
- The set, $S$, of all possible outcomes is called the **sample space** of an 'experiment'. We can define $S$ as an interval or a set with specific values depending on how we define the experiment. Some examples include: 
	- Flipping a coin has two outcomes such that: $$S = \{ H,T \}$$
	- SAT scores have outcomes that can be considered such that: $$S = \{ 200,210,220,\dots,780,790,800 \}$$
	- Reaction times of humans have outcomes such that: $$S = (0,\infty)$$
- We recognize the **nuance of countable and uncountable** sample spaces. This distinction is important as it dictates the way that probabilities are assigned which affects the mathematical treatment of these situations. Despite the difference though, in practice probabilistic and statistical methods associated with uncountable samples spaces are generally less cumbersome than those for countable samples spaces and even provide a close approximation to the countable situation. 
	- $S$ is countable iff there exists an injective mapping between $s\in S, \forall s$ and a subset of the integers, $\mathbb{Z}$.
	- $S$ is uncountable if there exists no injective mapping
## Events:
- An event, $A$, is any collection of the possible outcomes of an experiment, such that: $$A \subset S$$
- We also define formally the relationship of **containment and equality** between two events, $A$ and $B$, of a sample space, $S$, such that: $$\begin{align}
&A \subset B \iff x \in A \implies x \in B \tag{containment} \\ \\
&A =B \iff (A \subset B) \wedge (B \subset A) \tag{equality}
\end{align}$$
### Elementary Set Operations on Events: 
We begin by letting $A$ and $B$ be events of the sample space $S$. We can then describe the set operations of these events such that: 
- The **union** of events can be denoted by $A \cup B$ and represents the set of elements that belong either event space or both, such that: $$A \cup B = \{ x|(x\in A) \vee (x\in B)\} \tag{Union}$$
- The **intersection** of events can be denoted by $A \cap B$ and represents the set of elements that belong to both event spaces, such that: $$A \cap B = \{ x | (x\in A)\wedge(x\in B) \} \tag{Intersection}$$
- The **complementation** of an event space can be denoted by $A^c$ and represents the set of all elements that are not contained in $A$, such that: $$A^c = \{ x| x \notin A \} \tag{Complementation}$$
We can also generalize these operations to infinite event spaces, $A_{1},A_{2},\dots,$of a sample space, $S$, such that: 
- The **union of infinite event spaces** follows such that:  $$\bigcup_{i=1}^{\infty}A_{i}= \{ x \in S| x\in A_{i}, \exists i \} \tag{Infinite Union}$$
- The **intersection of infinite event spaces** follows such that: $$\bigcap_{i=1}^{\infty}A_{i} = \{ x \in S | x \in A_{i}, \forall i \} \tag{Infinite Intersection}$$
Alternatively, we can also definite unions and intersections over uncountable collections of sets by letting $\Gamma$ be an index set, such that:
- The **union of uncountable subsets**: $$\bigcup_{a \in \Gamma}A_{a} = \{  x \in S | x \in A_{a}, \exists a \}\tag{Uncountable Union}$$
- The **intersection of uncountable subsets**: $$\bigcap_{a \in \Gamma} A_{a} = \{ x\in S|x\in A_{a}, \forall a \}\tag{Uncountable Intersection}$$
### Properties of Events: 
For any three event spaces, $A,B$ and $C$, of the sample space, $S$, there exist the following properties:
- The **commutativity** of event spaces enables the symmetry of operators such that: $$\begin{align}
A \cup B &= B \cup A \\
A \cap B &= B \cap A
\end{align} \tag{Commutativity}$$
- The **associativity** of event spaces preserves the application of multiple operators by allowing an operation to be segmented without changing the returned set, such that: $$\begin{align}
A \cup (B \cup C) &= (A \cup B) \cup C \\
A \cap (B \cap C) &= (A \cap B) \cap C
\end{align}\tag{Associativity}$$
- The **distributivity** of operators allows the expansion of an operation into separate and more direct binary operations, and also doesn't force operations to be solved from right-to-left, such that: $$\begin{align}
A \cap (B \cup C) &= (A \cap B) \cup (A \cap C) \\
A \cup (B \cap C) &= (A \cup B) \cap (A \cup C)
\end{align}\tag{Distributive Laws}$$
- **DeMorgan's Law** addresses the complementation of an operation by distributing the complement operation of a binary operator to the individual sets themselves, such that: $$\begin{align}
(A \cup B)^c &= A^c \cap B^c \\
(A \cap B)^c &= A^c \cup B^c
\end{align}\tag{DeMorgan's Law}$$

### Disjointness: 
- Two events, $A$ and $B$ of a sample space, $S$, are **disjoint (aka mutually exclusive)** if: $$A \cap B = \emptyset \tag{Disjoint}$$
- The sequence of events, $A_{1},A_{2},\dots$ are **pairwise disjoint** if: $$A_{i} \cap A_{j} = \emptyset, \forall i \neq j \tag{Pairwise Disjoint}$$
### Partitions for Probability: 
- Using the definition of pairwise disjoint on a sequence of events, $A_{1},A_{2},\dots,$ we can conclude that the sequence forms a partition of the sample space, $S$, iff the sequence is pairwise disjoint. 
# Measure Theoretic Foundations for Probability: 
The underlying idea of measure theory is to assign some value, $\mu \in \mathbb{R}, \mu \geq 0$, to every subset of a given set. Then we can let $E$ be a set, such that the set of all subsets of $E$ are denoted by $\mathcal{P}(E)$. It then follows that: 
## Sigma-Fields/Sigma-Algebra: 
- Following the definition of a $\sigma-\text{field},$ a collection of subsets of $S$ is called a **sigma-algebra** (aka **Borel-field**) and is denoted by $\mathcal{B}$, with an event $A$, which must satisfy the following properties: 
  1) $E \in \mathcal{B}$
  2) $A \in \mathcal{B} \implies A^c \in \mathcal{B}$
  3) If $A_{n} \in \mathcal{B}, \forall n \in \mathbb{N}$, then $\bigcup_{n \in \mathbb{N}}A_{n} \in \mathcal{B}$
- The elements of $\mathcal{B}$ are called measurable sets. We can denote the measure space of the set $E$, with $(S,\mathcal{B})$. Following the definition of a $\sigma-\text{field}$, we can also conclude that: 
	1) $\emptyset \in \mathcal{B}$, by the definition of the power-set, $\mathcal{P}(S)$
		- $\implies S= \emptyset^c$
	2) If $A_{n} \in \mathcal{B}, \forall n \in \mathbb{N}$, it also then follows that $\bigcap_{n\in \mathbb{N}}A_{n} \in \mathcal{B}$
- There exists many different $\sigma-$algebras over a sample space $S$.
	- $\{ \emptyset,S \}$ is considered the trivial $\sigma-$algebra
- Following the properties of a power-set, $\mathcal{P}(S)$, if $S$ is countable and contains $n$ elements, the order of $\mathcal{B}$ is $2^n$. 
### Examples of Countable and Uncountable Sigma Algebras:
- Suppose $S= \{ 1,2,3 \}$, such that $S$ is a countable sample space. Then its $\sigma-$algebra follows such that: $$\mathcal{B} = \begin{matrix}
\{ 1 \} & \{ 1,2 \} & \{ 1,2,3 \} \\
\{ 2 \} & \{ 1,3 \} & \emptyset \\
\{ 3 \} & \{ 2,3 \}
\end{matrix}$$
	- We can recognize that the order of $\mathcal{B}$ follows, $\lvert S \rvert = 3 \implies \lvert \mathcal{B} \rvert = 2^3 = 8$ 
- Then suppose $S = (-\infty,\infty) = \mathbb{R}$, such that $S$ is an uncountable sample space. Its $\sigma-$algebra then follows such that: $$\mathcal{B} = \begin{matrix}
[a,b] & (a,b] & (a,b) & [a,b)
\end{matrix}$$
	- We can recognize that the order of $\mathcal{B}$ cannot necessarily be determined by the order of the sample space, $S$, but that it does contain the open, closed, and clopen intervals of some $a,b \in \mathbb{R}$.
## Probability Functions and Kolmogorov Axioms: 
- Given a sample space, $S$, with an associated $\sigma-$algebra, $\mathcal{B}$, there exists a function $P$, with the pre-image, $\mathcal{B}$, and an event, $A$, that satisfies:
	1) $0 \leq \mathbb{P}(A) \leq 1, \forall A \in \mathcal{B}$
		- The probability of any specific event in $S$ is bounded
	2) $\mathbb{P}(S)=1$
		- The probability of the entire sample space, $S$, must sum to 1
	3) If the sequence of events, $A_{1}, A_{2},\dots \in \mathcal{B}$ are pairwise disjoint, it then follows that: $$\begin{align}
&\mathbb{P}\left( \bigcup_{i=1}^{\infty}A_{i} \right) = \sum_{i=1}^{\infty}\mathbb{P}(A_{i}) \tag{Countable Additivity}
\end{align}$$
### Axiom of Finite Additivity: 
- For the events $A$ and $B$, where $A,B \in \mathcal{B}$, whenever $A$ and $B$ are disjoint, it then follows that their union is such that: $$\mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B) \tag{Finite Additivity}$$
## Calculus of Probabilities, Properties of Probability Functions, and Inequalities: 
### Properties of Probability Functions:
Following the Kolmogorov Axioms, we can construct properties of probability functions which are important in calculating closed-form, analytic solutions of more complicated probability functions, such that: 
- Let $P$ be a probability function and the event $A \in \mathcal{B}$. It then follows that: 
	1) $P(\emptyset)=0$
	2) $P(A) \leq 1$
	3) $P(A^c) = 1 - P(A)$
		- This result follows from the boundedness of a probability, such that, $$\begin{align}
P(A \cup A^c)&= P(A) + P(A^c)\\
&=P(S) \\
&=1
\end{align}\tag{Complement Law}$$
		- Likewise, we can work backwards such that: $$\begin{align}
1 &= P(S) \\
&= P(S \cup \emptyset) \\
&= P(S) + P(\emptyset) \\ \\
\implies& P(\emptyset) = 0
\end{align}$$
- Similarly, if $P$ is a probability function and $A$ and $B$ are events, such that $A,B \in \mathcal{B}$, then: 
	1) $P(B \cap A^c)= P(B) - P(A \cap B)$
	2) The inclusion-exclusion principle: $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
	3) $A \subset B \implies P(A) \leq P(B)$
- We also note that the inclusion-exclusion property can be generalized for any $A,B,C \in \mathcal{B}$, such that: $$\mathbb{P}(A \cup B \cup C)=\mathbb{P}(A)+\mathbb{P}(B)+\mathbb{P}(C)- \mathbb{P}(A \cap B)- \mathbb{P}(A \cap C)-\mathbb{P}(B \cap C)+\mathbb{P}(A \cap B \cap C)$$
- If $P$ is a probability function, then for an event $A \in \mathcal{B}$ and for a finite sequence of partitions, $C_{1},C_{2},\dots,$ it then follows that:
	1) $P(A)= \sum_{i=1}^{\infty}P(A \cap C_{i})$ for any partition, $C_{1}, C_{2},\dots$
	2) $P\left( \bigcup_{i=1}^{\infty}A_{i} \right) \leq \sum_{i=1}^{\infty}P(A_{i})$ for any events, $A_{1},A_{2},\dots$
		- This is also called Boole's Inequality 
