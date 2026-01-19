# Energy Methods: 
- Energy methods specifically exist to help establish the **well-posedness** of a PDE, including hyperbolic, parabolic, and elliptic PDEs. The well-posedness of a PDE establishes the **existence** and uniqueness of a **solution** and also the solution's **continuous dependence** on the specified domain. 
## Stability: 
- We essentially will use the inherent energy contained in the PDE, according to its initial and boundary conditions, to demonstrate the boundedness, which is stability, of the solution. Given the Laplacian PDE with homogenous boundary conditions, such that: $$ 1)\begin{align}
\nabla^2 \cdot u&=0, u \in \Omega \\
u=0 &\text{ on } \partial \Omega \\
\Omega &\subset \mathbb{R}^n
\end{align}$$
- To demonstrate the boundedness of our solution, we assume that our solution $u \in L^2(\Omega)$. We begin by multiplying by our solution, $u$, and integrate along the domain $\Omega$. This essentially is finding the total energy available in the domain of the PDE, which we find to converge to a finite value, aka being bounded, which suggests stability. Essentially, we would then like to demonstrate that: $$2) \int_{\Omega}u \nabla^2udx \leq \int_{\Omega}g^2(x)dx$$
	- This shows that the solution doesn't blow up over time by the fact that it is bounded by another finite-valued function, $g(x)$, defined over the same domain. 
- We can continue simplifying equation $2)$ by first using integration by parts and then using divergence theorem, such that: $$\begin{align}
&\int_{\Omega}u \nabla^2udx \leq \int_{\Omega}g^2(x)dx \\ \\

\to & \int_{\Omega}\nabla \cdot (u\nabla u)dx \\ \\
=&\int_{\Omega}(\nabla u \cdot \nabla v) +(v\nabla u)dx, \text{ by IBP}   \\ \\  
&\text{By the divergence of 1):} \\ \\
&\int_{\partial\Omega}(v\nabla u \cdot \vec{n})dS = \int_{\Omega}(\nabla v \cdot \nabla u) dx + \int_{\Omega}(v\nabla u)dx  \\ \\
\to & \int_{\Omega}(v \nabla u)dx = -\int_{\Omega}(\nabla v \cdot \nabla u)dx + \int_{\partial \Omega}(v\nabla u \cdot \vec{n})dx
\end{align}$$
## Uniqueness of Solutions:
- Assuming $u$ is a solution to an arbitrary elliptic equation, we can create another "placeholder" solution, $v \in \Omega$. Then, by the linearity of elliptic PDEs, we can create another solution by taking a linear combination of solutions. We create another solution, $w \in \Omega$, which is defined such that, $w=u-v$. Since $u$ and $v$ are solutions to our PDE, we will only have a unique solution when $u=v \to w=0$. Then, beginning our proof: $$\begin{align}
\Delta w=0, &w \in \Omega \\
w=0, &w \in \partial \Omega
\end{align}$$
- We continue by multiplying by the solution $w$ and integrating over $\Omega$, such that: $$\int_{\Omega}(w \Delta w)dx=0$$
- Then utilizing integration-by-parts and the divergence theorem result from earlier, we proceed, such that: $$\int_{\Omega}(w \Delta w)dx=-\int_{\Omega}|\nabla w|^2dx +\int_{\partial \Omega}w(\nabla w \cdot \vec{n})dS $$
- By the given Dirichlet boundary condition, $w=0$ on $\partial \Omega$, the second integral on the RHS vanishes. Then we have: $$\int_{\Omega}(w\nabla w)dx=-\int_{\Omega}|\nabla w|^2dx=0$$
- The only way for the integral above to hold is when $\nabla w=0$. Then, since $w$ is constant in $\Omega$ and $w=0$ on $\partial \Omega$, this means that $w=0$, thus $u=v$. Then, we have demonstrated the uniqueness of the solution to an elliptic PDE via energy methods.
- We also recognize that even if we have a Poisson elliptic PDE, meaning it contains a forcing term, the difference of solutions will cause the RHS to be 0. In terms of each solution, their particular components are also equal since they assess the same forcing term. This further validates the use of energy methods for established well-posedness of a PDE. 
## Minimizing Energy Functionals: 
- For a Poisson PDE with Dirichlet boundary conditions on the bounded domain, $\Omega \subset \mathbb{R}^n$, and with forcing term $f$, we have the energy functional: $$E(u)=\frac{1}{2}\int_{\Omega}|\nabla u|^2dx - \int_{\Omega}fudx$$
- Assuming $u$ is a solution to $E$, then let $v$ be another solution, such that, $v:\Omega \to \mathbb{R}$, $v$ is twice-differentiable, and $v=0$ on $\partial \Omega$. Then, we assert: $$E(u)\leq E(v)$$
- We begin by multiplying the Poisson PDE by $v$ and integrating along the domain, $\Omega$, such that: $$\begin{align}
&-\Delta u=f \\
\to & -\int_{\Omega}(\Delta u \cdot v)dx = \int_{\Omega}fvdx
\end{align}$$
- Then using our previous integration-by-parts and divergence theorem result, we proceed such that: $$\begin{align}
-&\int_{\Omega}(\Delta u \cdot v)dx=\int_{\Omega}fvdx \\
\to &\int_{\Omega}(\nabla u \cdot \nabla v)dx - \int_{\partial \Omega}v(\nabla u \cdot \vec{n})dx =\int_{\Omega}fvdx \\
\end{align} $$
- By our Dirichlet boundary conditions, the surface integral of the LHS will vanish, as $v=0$ on $\partial \Omega$, thus we conclude: $$\begin{align}
&\int_{\Omega}(\nabla u \cdot \nabla v)dx - \int_{\partial \Omega}v(\nabla u \cdot \vec{n})dx =\int_{\Omega}fvdx \\ \\
\to & \int_{\Omega}(\nabla u \cdot \nabla v)dx = \int_{\Omega}(fv)dx
\end{align}$$
- Similarly, we apply energy methods for the solution $u$ to our PDE, which then provides: $$\int_{\Omega}|\nabla u|^2dx = \int_{\Omega}(fu)dx$$
- Then, similar to how we demonstrated the uniqueness of the solution to our PDE, we can take the difference of the energy functionals dependent on our solutions, such that: $$\begin{align}
E(v)-E(u)&=\frac{1}{2}\int_{\Omega}|\nabla v|^2 - \int_{\Omega}fv - \frac{1}{2} \int|\nabla u|^2 + \int_{\Omega}fu \\ \\
&= \frac{1}{2}\int_{\Omega} |\nabla v|^2 - \int_{\Omega}(\nabla u \cdot \nabla v)+ \frac{1}{2} \int_{\Omega}|\nabla u|^2 \\ \\
&= \frac{1}{2} \int_{\Omega}(\nabla u - \nabla v) \cdot (\nabla u \cdot \nabla v)\geq{0}
\end{align}$$ 
