# Basics of Hyperbolic Equations
- We begin by defining a linear operator, $\mathcal{L}$, on our solution $u$, to be such that: $$\mathcal{L}(u):=a\partial_{x}^2u + 2b\partial_{x}\partial_{y}u+c\partial_{y}^2u = f$$
- We recognize the second-order linear PDE above, in three distinct cases. Since our PDE is strongly related to quadratic forms, we consider the forms of our PDE depending on the sign of their discriminant. These cases relate to the shape of the level curves with the associated quadratic form, such that: 
1)  Hyperbolic Equations: $$b^2-ac>0$$
	- The linear operator, $\mathcal{L}$, has two distinct real factors, which allows us to factorize the differentials such that: $$\begin{align}
\mathcal{L}u&=(\alpha \partial_{x}+\beta \partial_{y})(\gamma \partial_{x}+\delta \partial_{y}) \\ \\
\frac{\beta}{\alpha}&\neq \frac{\delta}{\gamma}
\end{align}$$
	- The conclusion above implies that a second-order hyperbolic PDE operator has two distinct characteristic speeds, $\frac{\beta}{\alpha}$ and $\frac{\delta}{\gamma}$. 
- We also recognize that hyperbolic PDEs **require** **having both initial conditions**, $u(x,0)=\phi(x)$ which represents initial displacement, and $u_{t}(x,0)=\psi(x)$, which represents initial velocity.
# D'Alembert's Solution: 
- Revisiting the factorization of $\mathcal{L}$, we can recognize that the two characteristic curves in terms of the parameters, $s$ and $t$, are such that: $$s = \delta x - \gamma y; \ t=\beta x - \alpha y$$
- Using change of variables and chain rule, we can rewrite the partials that appear in our factorization in terms of our parameters, $s$ and $t$, such that: $$\begin{align}
&\frac{\partial u}{\partial x}= \frac{\partial u}{\partial s} \frac{\partial s}{\partial x} + \frac{\partial u}{\partial t} \frac{\partial t}{\partial x}=\delta 
 \frac{\partial u}{\partial s}+ \beta 
 \frac{\partial u}{\partial t} \\
 \\
&\frac{\partial u}{\partial y}= \frac{\partial u}{\partial s} \frac{\partial s}{\partial y} + \frac{\partial u}{\partial t} \frac{\partial t}{\partial y}= - \gamma 
 \frac{\partial u}{\partial s}-\alpha 
 \frac{\partial u}{\partial t}
\end{align}$$
- Solving our system of partials, we can recover our partials with respect to the parameters $s$ and $t$, such that: $$\alpha \partial_{x}+\beta \partial_{y} = \sigma \partial_{s}, \gamma \partial_{x}+\delta \partial_{y}=-\sigma \partial_{t}$$
	- Where $\sigma = \alpha \delta - \beta \gamma$ and $\sigma\neq{0}$
- Then we conclude that when our linear operator is applied to a solution $u$ with hyperbolic characteristics ($b^2 - ac>0$), it can be rewritten such that: $$\mathcal{L}u= -\sigma^2 \partial_{s} \partial_{t}u$$
- Then, the PDE represented by $\mathcal{L}u=f$ can be integrated, such that: $$\begin{align}
&u(s,t)=F(s) + G(t) - \Phi(s,t) \\ \\
&\Phi(s,t)=\frac{1}{\sigma^2}\iint f(x(s,t),y(s,t))dsdt
\end{align}$$
	- Where $F(s)$ and $G(t)$ are arbitrary functions of integration
- Rewriting our solution above in terms of the original variables $x$ and $y$, we can recognize the homogeneous and particular components, such that: $$u(x,y)=F(\delta x - \gamma y)+G(\beta x - \alpha y) - \Phi(s(x,y),t(x,y))$$
	- $\Phi(s,t)$ represents the contributions of the source term 
	- $F(\delta x - \gamma y)$ is constant along the characteristic curves of $s$
	- $G(\beta x - \alpha y)$ is constant along the characteristic curves of $t$

- Applying our methodology to the standard, homogeneous wave equation, we proceed to factorize, such that: $$\begin{align}
&u_{tt}-c^2u_{x x}=0 \\ \\
\to &=(\partial_{t}+c\partial_{x})(\partial_{t}-c\partial_{x})u
\end{align}$$
	- This suggests that our change of variables to represent the parameters $s$ and $t$ in terms of $x$ and $y$, such that: $$\begin{align}
y=x-ct, s=x+ct
\end{align}$$
	- Applying this conclusion to our solution, $u(x,t)$, we can further conclude that we travel along our characteristic curves at speeds of $\pm c$. We then proceed, such that: $$u(x,t)=F(x-ct)+G(x+ct)$$
	- This leads to the formulation of D'Alembert's Solution to the wave equation, such that: $$u(x,t)=\frac{1}{2}(g_{0}(x-ct)+g_{0}(x+ct))+\frac{1}{2c}\int_{x-ct}^{x+ct}g_{1}(z)dz$$
		- $F(x)+G(x)=g_{0}(x)$
		- $G'(x)-F'(x)=\frac{g_{1}(x)}{c}$
		- The integral in the solution recognizes the contributions of the forcing term in the inhomogeneous case 
# Conservation of Energy for Hyperbolic PDEs:
- Similar to how we used the energy method to establish well-posedness of elliptic PDEs, we can demonstrate the well-posedness of hyperbolic PDEs. For the standard, homogeneous hyperbolic PDE, we consider: $$u_{tt}=c^2u_{x x}$$
- We proceed by multiplying both sides of the given PDE by $u_{t}$ and integrating across the spatial domain. This will allow us to rewrite the LHS in terms of an integral and differential by Leibniz's rule, such that: $$\int u_{tt}u_{t}dx=\frac{1}{2} \frac{d}{dt}\int(u_{t})^2dx$$
- To simplify the RHS, we can use integration by parts and our boundary conditions, such that: $$\int u_{x x}u_{t}dx=u_{x}u_{t}|_{0}^L-\int u_{x}u_{xt}dx$$
	- Assuming we have homogenous Dirichlet boundary conditions, then the boundary terms resulting from integration by parts will also go to 0. Similar to how we simplified the LHS, we can also use Leibniz's rule such that: $$\begin{align}
\int u_{x x}u_{t}dx&= - \int u_{x}u_{xt}dx \\
&= -\frac{1}{2} \frac{d}{dt}\int(u_{x})^2
dx\end{align}$$
- Then, rewriting our PDE in terms of our simplified RHS and LHS, we have: $$\begin{align}
&\frac{1}{2} \frac{d}{dt}\int(u_{t})^2dx=-\frac{c^2}{2}\int(u_{x})^2dx \\ \\
\to& \frac{1}{2} \left( \frac{d}{dt} \int (u_{t})^2+c^2(u_{x})^2  \right)dx = 0 
\end{align}$$
- Finally, we conclude that the LHS of our PDE represents the global potential energy of the wave, while the RHS represents the global kinetic energy of the wave. Then, we finally recognize that our most recent conclusion provides the total global energy of the wave, such that: $$E(t)= \frac{1}{2} \left(\int (u_{t})^2+c^2(u_{x})^2  \right)dx$$
- When $E(t)=0$, we recognize that energy is conserved across the domain. 