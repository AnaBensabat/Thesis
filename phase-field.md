# The Phase Field Model

## Background knowledge

The phase field model was developed out of a necessity of modelling systems with complex boundaries that cannot be described by simple mathematical functions or parametrisations. E.g.: mixtures of immiscible components, phase diagrams and other stuff.

The way to go about this is to represent the domains as order parameters that have different values depending on the phase present at each point in space and time. The domains are separated by diffuse interfaces that change themselves over time. We model the system by defining an energy functional that encapsulates all the relevant physical processes that take place. The diffusive interface prevents the problem of having boundary conditions between the interfaces. 

The basic energy functional has the following shape:

$$
F[\phi(\mathbf{r})] = \int \left[V(\phi)+\frac{\varepsilon^2}{2}(\nabla \phi)^2\right]\text{d}\mathbf{r}
$$
The choice of the potential depends on how we want to label the different phases of the system. It gives us the stable values for the order parameter. As an example, we can consider the following potential:

$$
\begin{align*}
V(\phi) = -\frac{\phi^2}{2}+\frac{\phi^4}{4} && \quad && V'(\phi) = -\phi + \phi^3
\end{align*}
$$
Where its easy to see that the minima in this case are at $\phi=-1$ and 1 (and a maximum at $\phi=0$.

The second term in the phase field is responsible for the creation of a smooth interface since it penalizes abrupt changes in the order parameter.

There are different branch models, the application of which depends on the physical system of interest.

### Model A

In this model, the evolution of the system is given by:

$$
\frac{\partial \phi}{\partial t} + \nabla \cdot (\phi \mathbf{v})=-M\frac{\delta F}{\delta \phi},
$$
where $\mathbf{v}$ is some advective velocity. $M$ is the motility coefficient and the current is given by $\frac{\delta F}{\delta \phi}$. This was first defined by Allen and Cahn.

### Model B
Now, a conservation law is imposed. We begin from the continuity equation:

$$
\frac{\delta \phi }{\delta t} + \nabla \cdot \mathbf{J} = 0
$$
Which when can relate to Fick's law of diffusion:

$$
J = -M\nabla \frac{\delta F}{\delta \phi}
$$
where we can see that the current is in the direction that minimizes the free energy with respect to changes in the order parameter.

We can now plug this into the conservation law and get:

$$
\frac{\delta \phi}{\delta t} = \nabla \cdot \left(M\nabla \frac{\delta F}{\delta \phi}\right)
$$
Since this is based on a conservation law, the total phase:

$$
\phi_\text{tot} = \int_V \phi \text{d}\mathbf{r}
$$
when we integrate over that whole system, is constant in time.

 @allenMicroscopicTheoryAntiphase1979

## Cell + Nucleus Model

The energy functional is given by:

$$
\begin{align*}
F[\phi,\nu, \psi]= &\int \kappa_C \left(\frac{1}{4}\phi^2(1-\phi)^2+\frac{\varepsilon^2}{2}(\nabla \phi)^2\right) \text{d} \mathbf{r} +\int \kappa_N \left(\frac{1}{4}\nu^2(1-\nu)^2-\frac{\varepsilon^2}{2}(\nabla \nu)^2\right) \text{d}\mathbf{r} + \\ 
		+&\int \left(\eta \nabla h(\phi) \cdot \nabla h(\psi)\right) \text{d}\mathbf{r} +\int \left(\gamma h(\phi)h(\psi) + \gamma h(1-\phi)h(\nu)\right)\text{d}\mathbf{r} + \\
		+&\alpha_V(V_\text{target, C}-V[\phi])^2 + \alpha_V(V_\text{target, N}-V[\nu])^2,
\end{align*}
$$

where $h(\phi)=\phi^2(3-2\phi)$ and $\phi$, $\nu$ and $\psi$ are the phase fields of the cell, the nucleus and the substrate respectively.

The dynamics of the system is given by the partial differential equation:
$$\frac{\partial \phi}{\partial t} = -M \frac{\delta F}{\delta \phi},$$where $M$ is the mobility. The time scale for the dynamics of this system is given by $\tau$ that relates to the mobility $M$ and the surface tension of the cell membrane $\kappa_0$ as:

$$
\begin{align*}
	[M] = L^3T^{-1}E^{-1} && [\kappa_0] = EL^{-3	} && M\kappa_0 = \frac{1}{\tau},
\end{align*}
$$
The equations of the dynamics for each of the domains will be thus given by the following equations:

$$
\begin{align*}
		\frac{\partial \phi}{\partial t} = -M\frac{\delta F}{\delta \phi} =\\
=&
-M \big[\kappa_C\left(\phi(\phi-1)(\phi-1/2)-\varepsilon^2\nabla^2\phi\right)- 6\eta \phi(1-\phi)\nabla^2h(\psi)+ \\
		&+6\gamma \phi(1-\phi)(h(\psi)-h(\nu))-12\alpha_V\phi(1-\phi)(V_\text{target,C}-V[\phi])\big],
	\end{align*}
    $$
$$
\begin{align*}
			\frac{\partial \nu}{\partial t} = &-M\frac{\delta F}{\delta \nu}  \\
			= &-M \big[\kappa_N\left(\nu(\nu-1)(\nu-1/2)-\varepsilon^2\nabla^2\nu\right)+6\gamma \nu(1-\nu)h(1-\phi)- \\
			&-12\alpha_V\nu(1-\nu)(V_\text{target,C}-V[\nu])\big],
	\end{align*}
$$
and similarly for the substrate.

### Domain integrity term

To prevent a domain in the phase field from breaking apart, the following term can be added to the equation of the dynamics:

$$
-\chi\int_S \Theta\big(-e^{|\mathbf{r}-\mathbf{r}'|/\phi(1-\phi)\nabla \phi(\mathbf{r})\nabla \phi(\mathbf{r}')\delta}\big)\text{d}\mathbf{r}'
$$
## Equilibrium Solution

The Cahn Hilliard equation is given by:

$$
V'(\phi) -\varepsilon^2 \frac{\text{d}^2\phi}{\text{d}x^2}=0,
$$
where, in our case, $V(\phi)=\frac{1}{4}\phi^2(1-\phi)^2$ and hence $V'(\phi) = \frac{\phi}{2}-\frac{3\phi^2}{2}+\phi^3$. Hence, our Cahn-Hilliard equation reads:

$$
\frac{\phi}{2}-\frac{3\phi^2}{2}+\phi^3 - \varepsilon^2\frac{\text{d}^2\phi}{\text{d}x^2}=0
$$
Multiplying both sides by $\frac{\text{d}\phi}{\text{d}x}$ we get:

$$
\begin{align*}
\frac{\text{d}\phi}{\text{d}x}\frac{\text{d}V}{\text{d}\phi} - \varepsilon^2\frac{\text{d}\phi}{\text{d} x}\frac{\text{d}^2\phi}{\text{d}x^2}&=0\\
\frac{\text{d}}{\text{d}x}\left[V(\phi) - \frac{\varepsilon^2}{2}\left(\frac{\text{d}\phi}{\text{d}x}\right)^2\right]&=0
\end{align*}
$$
Integrating, we get:

$$
\int_{-\infty}^x dx' \frac{\text{d}}{\text{d} x}\left[\frac{1}{4}\phi^2(1-\phi)^2-\frac{\varepsilon^2}{2}\left(\frac{\text{d} \phi}{\text{d} x}\right)^2\right] = 0
$$
and since both $\phi$ and $\frac{\text{d} \phi}{\text{d} x}$ are zero at $-\infty$ we get:

$$
\begin{align*}
\frac{1}{4}\phi^2(1-\phi)^2-\frac{\varepsilon^2}{2}\left(\frac{\text{d} \phi}{\text{d} x}\right)^2 &= 0 \\
2\varepsilon^2 \left(\frac{\text{d} \phi}{\text{d} x}\right)^2= \phi^2(1-\phi)^2 \\
\frac{\text{d} \phi}{\text{d} x} = \pm \frac{1}{\sqrt{2}\varepsilon}\phi(1-\phi)
\end{align*}
$$
We pick the positive branch (_I'm still not entirely sure why_).  Integrating, we can solve for $\phi$ since we have a separable differential equation:

$$
\phi(x) = \frac{1}{e^{-x/\sqrt{2}\varepsilon}}
$$
For other potentials, when $\phi \in [-1,-1]$ the procedure is similar but we get a hyperbolic tangent. For instant, Marcos used the potential $V(\phi) = -\frac{\phi^2}{2}+\frac{\phi^4}{4}$ and got $\tanh\left(\frac{x}{\sqrt{2}\varepsilon}\right)$.

## Energies

The membrane energy per unit area is given by:

$$
\int \left(\frac{1}{4}\phi^2(1-\phi)^2+\varepsilon^2(\nabla \phi)^2\right)\text{d}\mathbf{r}
$$
Which in our case [^1] gives $S_C = \frac{\kappa_C\varepsilon}{6\sqrt{2}}$.
The energy of adhesion per unit area is simply the adhesion term as well:

$$
\int \eta \nabla h(\phi)\cdot \nabla h(\psi) \text{d}\mathbf{r}
$$
Which in our case gives $H_{C,S} = \frac{9}{35\sqrt{2}}\eta$.

[^1]: with the amazing help of Mathematica
