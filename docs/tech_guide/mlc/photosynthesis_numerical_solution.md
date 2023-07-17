
The set of nonlinear equations for photosynthesis model include:

 1. biological demand,
 2. diffusion, and
 3. [stomatal conductance model](photosynthesis_stomatal_conductance_model.md##Governing equations).

The set of nonlinear equations are numerically solved when the residual equation, $R(x)$,
where $x$ is the unknown variable. The solution, $x^*$, of the nonlinear is obtained when
$R(x^*) = 0$. The residual equation for photosynthesis model with various SCMs is
provided below.

### **BB and Medlyn model**
The unknown variable is $c_i$ and the residual equation is

\begin{equation}
	\label{eqn_residual_semiempirical}
	R(c_i) \equiv A_n - g_{\ell c} (c_a - c_i) = 0
\end{equation}

### **Marginal WUE**
The unknown variable is $g_\ell$ and with the residual equation
for model without plant hydraulics (i.e. $\xi$ is independent of 
$\psi_\ell$) is

\begin{equation}
	\label{eqn_residual_wue}
	R(g_\ell) \equiv \frac{\partial A_n}{\partial g_{sw}} - \xi = 0
\end{equation}

For models that include plant hydraulics, equation \eqref{eqn_residual_wue}
is modified by making $\xi$ depend on $\psi_\ell$.


### **iWUE**
The unknown variable is $g_\ell$ and with the residual equation
for model without plant hydraulics (i.e. $\xi$ is independent of 
$\psi_\ell$) is

\begin{equation}
\label{eqn_residual_iwue}
R(g_\ell) \equiv \frac{\partial A_n}{\partial g_{sw}} - \xi w_s = 0
\end{equation}

For models that include plant hydraulics, equation \eqref{eqn_residual_iwue}
is modified by make $\xi$ depend on $\psi_\ell$.

### **SCM with stomatal dowregulation**
Depending on the choice of $g_{sw,max}$ ([described here](photosynthesis_stomatal_conductance_model.md##Semi-empirical model with downregulation due to plant hydraulics)),
the residual equation is given by equation \eqref{eqn_residual_semiempirical} or \eqref{eqn_residual_wue} or \eqref{eqn_residual_iwue}.


### **Original and modified Bonan2014 co-optimization model**
The unknown variable is $g_\ell$ and the residual equation for the first
constraint is given by equation \eqref{eqn_residual_wue} or \eqref{eqn_residual_iwue}.
The residual equation for the second constraint is given as

\begin{equation}
	R(g_\ell) \equiv \psi_{\ell}^t + \Delta\psi_\ell^{t+\Delta t} - \psi_{\ell, min} = 0
\end{equation}


### **Wang2020**
The unknown variable is $g_\ell$ and the residual equation is

\begin{equation}
R(g_\ell) \equiv \left( 1 - \frac{E_\ell}{E_{critical}} \right) \frac{\partial \Theta}{\partial E} - \frac{A_n}{E_{critical}} \frac{\partial E_\ell}{E} = 0
\end{equation}

<!---
\begin{comment}
The model implementation in the code is:

\begin{equation}
\frac{\partial g_{sw}}{\partial t} = \left( \frac{\partial A_n}{\partial E} - \frac{\partial \Theta}{\partial E} \right) \tau_{osm}
\end{equation}
\end{comment}
--->

