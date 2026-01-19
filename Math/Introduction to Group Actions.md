# Definitions and Motivations: 
- Despite defining group and developing theory about maps acting on these structures, quotient and product spaces, and so on, but we have yet to consider the case of where a group acts on a set or another algebraic structure. 
- Despite being able to define a group action on another set or any algebraic structure, the more structure and properties that are induced on the underlying set, the more we can learn about the group that is performing the action itself. 
- Groups actions are one of the most important applications of group theory and abstract algebra as a whole. It appears in the proof of Sylow's Theorem and classifications of it, modules, vector spaces and fields, canonical forms for matrices, and Galois theory. 
- We begin by recognizing the symmetric group, $S_{n},$ and any subgroups of it, $K_{i}\leq S_{n},$ may act on the set, $\{ 1,2,\dots,n \}=\mathbb{N}$. We can say that the symmetric group $S_{n}$ acts on the set $\mathbb{N}$ and that each elements of the symmetric group, $s \in S_{n},$ follows an **action** which is an underlying rule/function/mapping of that group, which in this case is the permutation of the ordering of elements, $n_{i} \in \mathbb{N}$.
- For a group $G$ acting on another set, $S$, group actions are sometimes denoted such that: $$G \curvearrowright S \equiv \mathcal{A}: G \to \text{Aut}(S)$$

# Properties of Group Actions : 
- Let $G$ be a group that actions on some nonempty set $A$. A **group action** is a map from $G \times A \to A$ and is defined such that: $$\begin{align}
&\sigma_{g}: \begin{cases}
G \times A \to A \tag{Mapping}\\
A\mapsto g \cdot a |\forall a\in A, \forall g\in G  \\
\end{cases} \\ \\
& \sigma_{g}(a) = g \cdot a \tag{Element-Wise Definition}
\end{align}
$$
- From this definition, group actions have an inherent structural imposition that leads to the properties: 
	1) For each fixed element, $g \in G$, the group action $\sigma_{g}$ is a permutation of the ordering of the elements of the set $A$.
	2) The specific map,  $\varphi:G \to S_{A}$, which is defined by $\{ g\mapsto \sigma_{g}  \iff \varphi(g) = \sigma_{g}| g \in G\}$ and is a homomorphism, such that: $$\begin{align}
\varphi(g_{1}g_{2})(a) &= \sigma_{g_{1}}\sigma_{g_{2}}  \\
&= (g_{1}g_{2}) \cdot a \tag{Map Def.}\\
&= g_{1}(g_{2}\cdot a) \tag{Group Action Def.}\\
&= \sigma_{g_{1}}(\sigma_{g_{2}}(a)) \tag{Group Action Def}\\
&= (\varphi(g_{1}) \circ \varphi(g_{2}))(a) 
\end{align}$$
## Distinctiveness, Faithfulness, and Kernels of Group Actions: 
- We recall that the kernel of a homomorphism is the set of elements in the pre-image that get mapped to the identity in the post-image. Then, the **kernel of the action** of $G_{a}$, is the set of elements in $G$ that act trivially on every element, $a \in A$, such that: $$\{ g \in G | gb=b, \forall b \in B \}\tag{kernel of group actions}$$
	- We recognize the special case of the trivial action, whose kernel is the entire set of the acting group $G$. This action is considered unfaithful for whenever $\lvert G \rvert>1.$
- If acts on a set $B$ and distinct elements of induce distinct permutations of $B$, the action is considered to be **faithful**, such that associated permutation representation is injective. Axiomatically, it follows that an action is faithful if its kernel is the identity element of the group, $G$.
# Simple Examples of Group Actions: 
We begin by letting $G$ be a group and $A$ be a non-empty set for the following examples. 
### The Trivial Action:
1) Let $ga=a, \forall a \in A, g \in G$. This action is called the **trivial action** and the group $G$ is considered to **act trivially** on the set $A$.The associated permutation representation, $G \to S_{A}$ is called the trivial homomorphism which maps every element of $G$ to the identity. More intuitively, the distinct elements of $G$ induce the same permutation on $A$.
### Vectors and Fields and Group Actions: 
The axioms for a vector space $V$ over a field $F$ include two axioms that the multiplicative group $F^{\times}$ acts on $V$. More particularly, $V$ must be an abelian group...
# Permutation Representations: 
- Let $G$ be a group that acts on a nonempty set $A$. Then, for each element of the group, $g \in G$, we recognize it as a map $\sigma_{g}:A \to A$, which is more rigorously defined as a permutation of $A$, such that: $$\sigma_{g}:A \mapsto g \cdot a|a\in A$$
	- This is called the **permutation representation** associated to the given action, $g\in G$. 
- We can recognize the **permutation representation**, $\sigma_{g}$, as the set of actions on a group $G$ on the set $A$ that are homomorphisms from $G$ to the symmetric group $S_{A}$ that are bijective. We should note the definition of an action might have been named a **left action** since the group elements are left-composed and a **right action** when the group elements are right-composed. 
- To demonstrate that the specific map, $\sigma_{g}$ is a permutation of the set $A$, we must show that for any set map, which in this case is $\sigma_{g}$, there exists a $2-$sided inverse, $\sigma_{g^-1}$ associated with the original map. Then: $$\begin{align}
\forall a \in A, (\sigma_{g^-1} \circ \sigma_{g} ) &= (\sigma_{g}=\sigma_{g^-1}) \tag{Supposition} \\ \\

(\sigma_{g_{^{-1}}} \circ \sigma_{g}) &= \sigma_{g^{-1}}({\sigma_{g}}(a)) \tag{Function Composition} \\
&=g^{-1} \cdot (g \cdot a) \tag{Def of Inverses} \\
&= (g^{-1}g) \cdot a \tag{Group Action Prop 1} \\
&= 1 \cdot a \tag{Group Action Prop 2} \\
&= a
\end{align}$$

- The kernel of an action is a normal subgroup of $G$, such that $ker(\varphi) \trianglelefteq G$ and $G/ker(\varphi) \cong \varphi(G)= \mathrm{Im}(G \curvearrowright A)$. 
	- It then follows that for any two elements, $g_{1},g_{2} \in G$, induce the same permutation of $A$ iff they are in the same coset of $ker(G)$. 
		- This condition is technically equivalent to if $g_{1}, g_{2}$ are in the same fiber of the permutation representation of $\varphi$. 
### The Orbit-Stabilizer Theorem:
#### Stabilizers:
- We begin by defining the **stabilizer** of a group action as: the set of elements in the acting group $G$ that fix the element $a \in A$, and is often denoted by $G_{a}$. Axiomatically, this appears as: $$G_{a}\equiv \text{Stab}_{G}(A)=\{ g \in G | g \cdot a =a,  a\in A \} \tag{Stabilizer Def}$$
	- The stabilizer in $G$ of an element $a \in A$ is a subgroup of $G$. 
	- Since $a$ is a fixed element, it follows that the kernel of the group action, is contained in the stabilizer $G_{a}$, as the kernel is the set of elements of $G$ that stabilizer every point, such that $\cap_{a \in A}G_{a}$. 
#### Orbits: 
- An other words, if $G \curvearrowright A$ and $g \in G$, $a \in A$, then the **orbit** of $a$ under the action of $G$ is the subset of $A$ that contains all the elements that can be reached $a$ by applying actions of the elements of $G$, such that: $$G \cdot a = \{ g \cdot a | g\in G \} \tag{Orbit Def}$$
	- The action of $G$ on $A$ is called **transitive** if there exists only one orbit. Given any two elements, $a,b \in A$, there is some $g \in G$ such that $a = g \cdot b.$ 
	- If the order of $G$ is finite, then the number of elements in the orbit of $a$ is at most equal to $\lvert G \rvert$, but may be less. 
##### Properties of Orbits: 
1) For every $a\in A$, we have $a\in G \cdot a$, since $a = e_{g} \cdot a$
2) If $y \in G \cdot a$ for some $a \in A$, then $G \cdot y = G \cdot a$
3) If an element $z \in A$ belongs to the orbits of both $x,y\in A$, then $G \cdot z = G \cdot x = G \cdot y$. 
4) The action of $G \curvearrowright A$ partitions $A$ into a collection of disjoint subsets, which are orbits. 
5) An action with only one orbit is called transitive. Then, if $G \curvearrowright A$, for any elements $x,y \in A$, there is an element $g \in G$, for which $g \cdot x = y$. 
#### The Orbit-Stabilizer and Cayley's Theorem: 
- Then we can define the **Orbit-Stabilizer theorem** by first letting $G$ be a finite group acting an element, $\chi \in S$, of the set $S$.
	- Then the number of elements in the orbit $G \cdot \chi_{i}$ is the number of elements in the orbit, such that:$$G \cdot \chi = [G: \text{Stab}_{G}(\chi)] \tag{Orbit-Stabilizer}$$
- We also must recognize **Cayley's Theorem**, which stats that any finite group, and specifically its action on itself by let multiplication, can be considered to be a group of permutations of $n$ objects and thus may be considered to be a subgroup of the symmetric group, $S_{n}$. 
	- As a result of Cayley's Theorem it follows that, for a group $G$, the permutation representation of $G$ is any homomorphism of $G$ into the symmetric group $S_{A}$, for some non-empty set $A$. Then, for a given action of $G$ on $A$, we can say that this action **afford/induces** an associated permutation representation of $G$, which is an equivalence relation. 
### Group Actions and Equivalence Classes:
- Following the previous statement that, a given action of the group $G$ on the non-empty set $A$ induces an associated equivalence relation, the relation on $A$ is defined by: $$a \sim b \iff a=g \cdot b, \text{ for some } g \in G \tag{Equiv. Relat.}$$
	- For each $a \in A$, the order of the induced equivalence class,$[G]_{A}$, that contains $a$ is $\lvert G:G_{a} \rvert$, which is the index of the stabilizer of $a$.
# Cycle Decompositions: 
Using the tool of group actions, and specifically its definition and properties, we can now prove that every element $\sigma \in S_{n}$ has a unique cycle decomposition. A **cycle** is a string of integers which represents the element of $S_{n}$ which cyclically permutes a list of integers, $L$, which contains $n$ elements. 
- To begin, let $L= \{ 1,2,\dots,n \}$, $\sigma \in S_{n}$, and let $G=\langle \sigma\rangle$. Then let $\langle \sigma\rangle \curvearrowright L$, such that it partitions $L$ into a unique set of disjoint orbits. Then let $\mathcal{O}$ be one of the orbits and $x\in \mathcal{O}$. 
	- As a result, when applying the action $A = \mathcal{O}$, we can see there is a bijection between the left cosets of $\text{Stab}_{G}(x) \in G$, which gives us: $$\sigma^ix \mapsto \sigma^iG_{x}$$
	- Since $G$ is a cyclic group, $\text{Stab}_{G}(x) \trianglelefteq G$, and ${G}/{G_{x}}$ is cyclic of order $d$, where $d$ is the smallest positive integer for which $\sigma^d \in \text{Stab}_{G}(x)$. 
