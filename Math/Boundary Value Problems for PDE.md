# Dirichlet Conditions: 
- We begin by considering the homogenous wave equation with **Dirichlet** conditions, such that: $$\begin{align}
DE) &\ u_{tt}=c^2u_{x x},  \ 0<x<l, t>0\\ \\
DBC) &\ u(0,t)= c_{1}, \ u(l,t)= c_{2}\\ \\
IC) &\ u(x,0)=\phi(x), u_{t}(x,0)=\psi(x)
\end{align}$$
- Through seperation of variables, we can write our solution, $u(x,t)$, as the product of independent variables, $X(x)$ and $T(t)$. Treating the proceeding system of ODEs like an eigenvalue problem, we set them equal to a constant, $\lambda$. By considering the values of $\lambda$ and using the boundary conditions, we can find the form of our solutions to the independent ODEs, which then can be used to find the solution to our PDE. 
- Dirichlet boundaries can be generalized to be when we are given a specific value of the dependent variable on the boundary of the given interval. Our dependent variable in this case involves the spatial dimension, $x$.
- In the case of the heat equation, we can imagine Dirichlet conditions as the temperatures at the end of either side of our "bar" (which is the real line)
- Dirichlet conditions can exist for Elliptic, Hyperbolic, and Parabolic forms of PDEs. 
# Neumann Conditions: 
- We begin by considering the homogenous wave equation with **Neumann** conditions, such that: $$\begin{align}
DE) \ &u_{tt}=c^2u_{x x}, \ x \in (0,l), t>0\\ \\
NBC) \ &u_{x}(0,t)= c_{1}, \ u_{x}(l,t)=c_{2}\\ \\
IC) \ &u(x,0)=\phi(x), u_{t}(x,0)=\psi(x)
\end{align}
$$
- Neumann boundary conditions can generalized to be when we are given a specific value for the normal derivative of the dependent variable on the boundary. Our dependent variable is the spatial dimension, $x$. 
- We can imagine Neumann conditions for the diffusion equation to be the heat flow/flux at the ends of the "bar". 
- Neumann conditions can exist for Elliptic, Hyperbolic, and Parabolic PDEs. 
# Cauchy Boundary Conditions: 
- Cauchy boundary conditions are the combination of Neumann and Dirichlet boundary conditions, such that we have a specified value and specified normal derivative for the dependent variable along the boundary. 
- Cauchy conditions only hold for Hyperbolic PDEs defined over an open "spatial" surface, as other boundary conditions are too restrictive for a solution to exist or are too weak to determine a unique solution. 
- We consider the homogenous wave equation wtih Cauchy conditions, such that: $$\begin{align}
DE) \ &u_{tt}=c^2u_{x x}, \ x \in (0,l), t>0\\ \\
CBC) \ &u_{x}(0,t)= c_{1}, \ u_{x}(l,t)=c_{2} \\
\\ & u(0,t) = c_{3}, \ u(l,t)=c_{4} \\ \\
IC) \ &u(x,0)=\phi(x), u_{t}(x,0)=\psi(x)
\end{align}
$$
# Periodic Boundary Conditions: 
- We can use periodic boundary conditions to define periodic spatial surfaces, such as rings, toruses/tori, or repeating lattices. The pattern of occurrences of our PDE allow us to reduce the PDE to the domain of exactly one occurrence  with periodic boundary conditions to represent the geometric sequence of our problem.  
- Periodic boundary conditions hold for Hyperbolic, Parabolic, and Elliptic PDEs. 
- We cannot have periodic boundary conditions if we have a non-periodic forcing term in our PDE. 
- We consider the homogenous heat equation with periodic boundary conditions, such that: $$\begin{align}
DE) \ &u_{tt}=c^2u_{x x}, \ x \in (0,l), t>0\\ \\
PBC) \ &u_{x}(0,t)= u_{x}(l,t)=c_{1} \\
\\ & u(0,t) = u(l,t)=c_{2} \\ \\
IC) \ &u(x,0)=\phi(x), u_{t}(x,0)=\psi(x)
\end{align}
$$
# Robin Boundary Conditions:
- Continuing the usage of the method of seperation of variables, can consider the case of robin conditions. Considering the simplified ODE:$$\begin{align}
&-X'' = \lambda X \\ \\
\to& X' -a_{0}X=0, x=0 \\
& X' + a_{l}X = 0, x=l \\
\end{align}$$
	- We recognize the mixed signs of the scalar constant in the solution to the ODE at the boundaries at the ends of the domain. This describes the flux about the ends of the domain and whether its entering, leaving, or is conserved over time. 
	- The reason that we recognize the case of Robin Boundary Conditions is motivated by  physical means, such that: 
		1) Radiation of Energy:
			- When $a_{0}$ and $a_{l}$ are both positive
		2) Absorption of Energy: 
			- When $a_{0}$ and $a_{l}$ are both negative 
		3) Insulation of Energy: 
			- When $a_{0}=0$ and $a_{l}=0$
			- When we do seperation of variables, we also would like to specifically exclude complex eigenvalues. 
	- The mathematical motivation for writing the constants this way specifically is that we are considering the unit normal or "outward". At $x=0$ we recognize the unit normal to point to the left. At $x=l$, the unit normal points to the right. Because of that, we expect the nature of the eigenfunctions of $X(x)$ to depend on the signs of two constants to opposite ways. 
	- Recognizing the physical manifestations, we now consider the signs of the eigenvalue for the eigenfunction $X(x)$. Using the method of judicious guessing to find our solution, we then continue such that: $$\begin{align} 
\text{Case 1)} \ \lambda&=\beta^2>0: \\ 
X(x)&= C\left( \cos(\beta x)+\frac{a_{0}}{\beta}\sin(\beta x) \right) \\ \\
\text{Case 2)} \ \ \lambda&=\beta^2=0 \\
X(x)&=0 \\
\iff \\
&a_{0}+a_{l}=-a_{0}a_{l}l,\  a_{0}=a_{l}=0 \\ \\
\text{Case 3)} \ \lambda&=-\gamma^2<0:  \\
X(x)&= A\cosh(\gamma x) + B\sinh(\gamma x) \\
\to&\tanh(\gamma l)=-\frac{(a_{0}+a_{l})\gamma}{\gamma^2 + a_{0}a_{l}} \\
\to X(x)&= \cosh(\gamma x)+\frac{a_{0}}{\gamma}\sinh(\gamma x)
\end{align} $$