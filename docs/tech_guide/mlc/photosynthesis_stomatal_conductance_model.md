## Governing equations

The photosynthesis model has two equations ([first](photosynthesis_biological_demand.md#mjx-eqn%3Aeqn_an_bio_demand) and [second](photosynthesis_diffusion.md#mjx-eqn%3Aeqn_ci_diff)) that
involves three unknowns ($c_i$, $A_n$, and $g_{sw}$). Thus, an additional equation is needed for stomatal 
conductance to close the system of equations.
In the literature, multiple stomatal conductance models (SCMs) have been developed that are
based on empirical, semi-empirical, or optimization approach. Furthermore,
SMCs can exclude or include plant hydraulics.

## Semi-empirical models without accounting for plant hydraulics

### **Ball-Berry model**

The semi-empirical Ball-Berry (BB) SCM[@ball1987model] is given as

\begin{equation}
\label{eqn_bb}
g_{sw} = g_0 + g_1\frac{A_n}{c_s}h_s
\end{equation}

where 
$g_0$ [mol H$_2$O m$^{-2}$ s$^{-1}$] is the minimum stomatal conductance,
$g_1$ [mol H$_2$O m$^{-2}$ s$^{-1}$] is the slope of the relationship, and
$h_s $ [-] is the fractional humidity at the leaf surface.
The fractional humidity at the leaf surface is $h_s = e_s/e_{sat}(T_\ell)$
where $e_s$ and $e_{sat}(T_\ell)$ are the vapor pressure at the leaf surface
and saturated vapor pressure at leaf temperature, $T_\ell$, respectively.
The vapor pressure at leaf surface can be given as

\begin{equation}
\label{eqn_vp_leaf}
e_s = \frac{g_{bw}e_a + g_{sw} e_{sat}(T_\ell) }{g_{bw} + g_{sw}}
\end{equation}

Substituting equation \eqref{eqn_vp_leaf} in equation \eqref{eqn_bb} leads the
following quadratic equation in which $g_{sw}$ is the larger root of
the equation.

\begin{equation}
\alpha g_{sw}^2 + \beta  g_{sw}  + \gamma = 0
\end{equation}

where

\begin{eqnarray}
\alpha &=&  1 \\
\beta  &=&  g_{gw} - g_0 - \frac{g_1 A_n}{c_s} \\
\gamma &=& - g_{bw} \left[ g_0 + \frac{g_1 A_n e_a}{c_s e_{sat}(T_\ell)} \right]
\end{eqnarray}


### **Medlyn model**
The semi-empirical Medlyn SCM[@medlyn2011reconciling] is given as

\begin{equation}
\label{eqn_medlyn}
g_{sw} = g_0 + 1.6\frac{A_n}{c_s} \left( 1 + \frac{g_1}{\sqrt D_s}\right)
\end{equation}

where 
$g_0$ [mol H$_2$O m$^{-2}$ s$^{-1}$] is the minimum stomatal conductance,
$g_1$ [mol H$_2$O m$^{-2}$ s$^{-1}$] is the slope of the relationship, and
$D_s = (e_{sat}(T_\ell) - e_s)$ [KPa] is the vapor pressure deficit.
Similar to BB model, substituting equation \eqref{eqn_vp_leaf} in equation \eqref{eqn_medlyn}
leads to following quadratic equations, whose larger root is $g_{sw}$.

\begin{equation}
\alpha g_{sw}^2 + \beta  g_{sw}  + \gamma = 0
\end{equation}

where

\begin{eqnarray}
\alpha &=&  1 \\
\beta  &=&  - 2 \left( g_{0} - 1.6\frac{g_1 A_n}{c_s}\right)  
						- \left( \frac{1.6 A_n g_1}{c_s} \right)^2 \frac{1}{g_{bw} D_\ell} \\
\gamma &=& - \left[ 2g_0 + \frac{1.6A_n}{c_s} \left( 1 - \frac{g_\ell^2}{D_\ell} \right) \right] \frac{1.6 A_n g_1}{c_s}
\end{eqnarray}

with $D_\ell = e_{sat}(T_\ell) - e_a$.


## Optimization-based models

Optimization-based SCMs maximize carbon update, $A_n$, while
minimizing the cost associated with carbon update, $\Theta$,
related a measure of stomatal opening, $\chi$[@wang2020theoretical].
Such models can be formulated as

\begin{equation}
\label{eqn_opt_obj_fn}
\begin{aligned}
\max_{\chi} \quad & (A_n - \Theta)
\end{aligned}
\end{equation}

and the solution of equation \eqref{eqn_opt_obj_fn} is obtained by finding
$\chi$ that satisfies the following equation

\begin{equation}
\label{eqn_opt_soln}
\frac{\partial A_n}{\partial \chi} - \frac{\partial \Theta}{\partial \chi} = 0
\end{equation}



### **Marginal water-use efficiency (WUE) model without accounting for plant hydraulics**

In this model, $\chi = E$ and $\Theta = \xi E$, where
$\xi$ is a constant model parameter. Thus, equation \eqref{eqn_opt_soln} reduces to

\begin{equation}
\label{eqn_wue}
\frac{\partial A_n}{\partial E} = \xi
\end{equation}

The LHS term of equation \eqref{eqn_wue} can be derived[@buckley2017optimal] as

\begin{equation}
\frac{\partial A_n}{\partial E} =
  		\left( \frac{c_a - c_i}{w_l} \right) 
		  \left( \frac{ \partial A_n/\partial c_i}{\partial A_n/\partial c_i + g_{lc}} \right) 
		  1.6 \frac{g_{lc}^2}{g_{\ell w}^2}
\end{equation}
where $w_\ell = \left[ e_{sat}(T_\ell) - e_a \right]/P_{ref}$ [mol mol$^{-1}$] is the vapor pressure
deficit.


### **Intrinsic WUE (iWUE) model without accounting for plant hydraulics**

In this model, $\chi = g_{sw}$ and the cost function is similar to that
of the WUE model (i.e. $\Theta = \xi E$). The equation \eqref{eqn_opt_soln} then reduces to

\begin{equation}
\label{eqn_iwue}
\begin{split}
\frac{\partial A_n}{\partial g_{sw}} &= \xi \frac{\partial E}{\partial g_{sw}} \\
&= \xi \frac{\partial}{\partial g_{sw}} \left( \frac{(e_{sat}(T_\ell) - e_s ) g_{sw} }{P_{ref}} \right) \\
&\approx \xi w_s
\end{split}
\end{equation}
where
$w_s (= [e_{sat}(T_\ell) - e_s]/P_{ref})$ [mol mol$^{-1}$] is the water vapor deficit
at the leaf surface. In equation \eqref{eqn_iwue}, the term $\partial e_s/\partial g_{sw}$ is neglected.

### **WUE model including plant hydraulics**

The marginal WUE model can be modified to account for
loss of xylem conductivity by including dependence of $\xi$
in equation \eqref{eqn_wue} on leaf water potential[@manzoni2011optimizing] as

\begin{equation}
\xi(\psi_\ell) = \exp(\beta \psi_\ell)
\end{equation}

where $\beta$ is a model parameter.

### **Co-optimization model of Bonan2014**

Bonan2014[@bonan2014modeling] is a SCM that maximizes $g_{sw}$ while satisfying
two constraints: 
(1) WUE or iWUE is greater than a threshold (i.e. $\partial A_n/\partial E \ge \xi$ or $(\partial A_n/\partial g_{sw})/w_s \ge \xi$, and
(2) leaf water potential is greater than a threshold (i.e. $\psi_\ell \ge \psi_{\ell, min})$.
The plant hydraulics model assumes leaves (sunlit or shaded) at any height
are directly connected to multiple soil layers via a root system. The leaf water storage is
given by

\begin{equation}
\label{eqn_bonan14_phm}
\frac{d\psi_\ell}{dt} = \frac{K_L (\psi_s - \psi_\ell - \rho_wgh) - 10^3 \times E}{C_p}
\end{equation}

where
$\psi_\ell$ [MPa] is the leaf water potential,
$\psi_s$ [MPa] is the soil water potential,
$\rho_wgh$ [MPa] is the gravitational head,
$C_p$ [$\mu$mol H$_2$O { }m$^{-2}_\ell$ MPa$^{-1}$] is the leaf capacitance, and
$K_L$ [$\mu$mol H$_2$O { }m$^{-2}_\ell$ s$^{-1}$ MPa$^{-1}$] is the whole plant hydraulic conductance, and
$E$ [mmol H$_2$O { }m$^{-2}_\ell$ s$^{-1}$] is the transpiration flux.
The $K_L$ is independent of $\psi_l$ and thus integrating equation \ref{eqn_bonan14_phm} 
provides an analytical expression for the change of leaf water potential, $\Delta \psi_\ell^{t+\Delta t}$,
for time step, $\Delta t$, as

\begin{equation}
\Delta\psi_\ell^{t+\Delta t} = \left[ \psi_s - \psi_\ell^{t} - \rho_w g h - \frac{10^3 \times E}{K_L}\right]
	\left( 1 - e^{-K_L\Delta t/C_p}\right)
\end{equation}

The second constraint of the co-optimization approach leads to

\begin{equation}
	\psi_{\ell}^t + \Delta\psi_\ell^{t+\Delta t} \ge \psi_{\ell, min}
\end{equation}

The whole plant hydraulic conductance depends on
soil-to-stem conductance, $K_{L,s2s}$ [$\mu$mol H$_2$O { }m$^{-2}_\ell$ s$^{-1}$ MPa$^{-1}$], and
stem-to-leave conductance, $K_{L,s2\ell}$ [$\mu$mol H$_2$O { }m$^{-2}_\ell$ s$^{-1}$ MPa$^{-1}$] as

\begin{equation}
\frac{1}{K_L} = \frac{1}{K_{L,s2s}} + \frac{1}{K_{L,s2\ell}}
\end{equation}

### **Modified Bonan2014 model**

In this study, we have developed a modified plant hydraulic model of Bonan2014 by including dependence 
of leaf water potential on stem-to-soil conductance, which is modeled by a Weibull function as

\begin{equation}
	K_{L,s2\ell}(\psi_\ell) = \psi_{L,s2\ell}^{max} \exp \left[ \left(\frac{-\psi_{\ell}}{b}\right)^c \right]
\end{equation}
where 
$b$ [MPa] and $c$ [-] are parameters.
The modified equation \eqref{eqn_bonan14_phm} is solved using the forward
Euler time-integration scheme.

### **Wang2020 model**

In Wang2020 model[@wang2020theoretical], $\chi = E$ and the cost function is given as

\begin{equation}
\Theta = A_n\frac{E_{\ell}}{E_{critical}}
\end{equation}


## Semi-empirical model with downregulation due to plant hydraulics

Empirical models have been proposed for reducing $g_{sw}$ to account for loss
of xylem hydraulic conductivity with water potential. Examples of such 
empirical stomatal downregulation models include equation \eqref{eqn_chris}[@christoffersen2016linking]
and equation \eqref{eqn_bohrer}[@bohrer2005finite].

\begin{eqnarray}
g_{sw} &=& g_{sw,max} \left[ 1 + \left(\frac{-\psi_{\ell}}{\psi_{50}}\right)^a \right]^{-1} \label{eqn_chris}\\
g_{sw} &=& g_{sw,max} \exp \left[ -\left( \frac{\psi_{\ell}}{\psi_{50}}\right)^a \right] \label{eqn_bohrer}
\end{eqnarray}

where $a$ [-] and $\psi_{50}$ [KPa] are model parameters.
In these empirical stomatal downregulation models, $g_{sw,max}$ is
obtained from equation 
\ref{eqn_bb} or
\ref{eqn_medlyn} or
\ref{eqn_wue} or
\ref{eqn_iwue}.


