## Governing equations

The net photosynthetic uptake of CO$_2$, $A_n$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$],
is given as

\begin{eqnarray}
	\label{eqn_an_bio_demand}
	A_n &=& \min(A_c, A_j, A_p) - R_d \nonumber \\
  	  &=& A_g - R_d
\end{eqnarray}

where 
$A_c$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] is the Rubisco-limited CO$_2$ assimilation,
$A_j$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] is the light-limited CO$_2$ assimilation, 
$A_p$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] is the PEP carboxylase-limited CO$_2$ assimilation,
$A_g$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] is the co-limited gross CO$_2$ assimilation,
and
$R_d$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] is mitochondrial respiration.
$A_g$ is given as the smaller of two quadratic roots

\begin{eqnarray}
	0.98A^2_i - (A_c + A_j) + A_c A_j &=& 0 \\
	0.98A^2_g - (A_i + A_p) + A_i A_p &=& 0
\end{eqnarray}

The assimilation fluxes ($A_c$, $A_j$, and $A_p$) for C3 and C4 photosynthesis pathway
are described next.

## C3 Photosynthesis

The CO$_2$ assimilation fluxes for C3 photosynthesis are 

\begin{eqnarray}
	A_c &=& \frac{V_{cmax} (c_i - \Gamma^*)}{c_i + K_c(1 - o_i/K_o)}\\[0.4em]
	A_j &=& \frac{J}{4}\left( \frac{c_i - \Gamma^*}{c_i + 2 \Gamma^*}\right) \\[0.4em]
	A_p &=& 0
\end{eqnarray}

where
$V_{cmax}$ [$\mu$mol CO$_2$ m$^{-2}$ s$^{-1}$] maximum rate of carboxylation,
$c_i$ [$\mu$mol CO$_2$ mol$^{-1}$] is the intercellular CO$_2$,
$o_i$ [$\mu$mol O$_2$  mol$^{-1}$] is the intercellular O$_2$,
$K_c$ [$\mu$mol CO$_2$ mol$^{-1}$] is the Michaelist-Mention constant for CO$_2$,
$K_o$ [$\mu$mol O$_2$  mol$^{-1}$] is the Michaelist-Mention constant for O$_2$,
$J$   [$\mu$mol CO$_2$ mol$^{-1}$] is the electron transport rate, and
$\Gamma^*$ [$\mu$mol CO$_2$ mol$^{-1}$] is the compensation point defined as the 
$c_i$ at which no net CO$_2$ update occurs.

The rate of electron transport is related to photosynthetically active
radiation and is given as the smaller root of the following quadratic equation.

\begin{equation}
	\Theta_j J^2 - (I_{PSII} + J_{max}) + I_{PSII} J_{max} = 0
\end{equation}

where
$I_{PSII}$ [$\mu$mol CO$_2$ mol$^{-1}$] is the amount of light utilized in photosynthesis II,
$J_{max}$  [$\mu$mol CO$_2$ mol$^{-1}$] is the maximum transport rate, and
$\Theta_j = 0.9$ is the curvature parameter.
The amount of light utilized in photosynthesis II is

\begin{equation}
	I_{PSII} = \frac{\Phi_{PSII}}{2} \alpha_\ell \overrightarrow{I}_{PAR}
\end{equation}

where 
$\Phi_{PSII} = 0.7$ [mol mol$^{-1}$] is the quantum yield of photosystem II,
$\alpha_\ell = 1$ is the leaf absorptance,
$\overrightarrow{I}_{PAR}$ [$\mu$mol photon m$^{-2}$ s$^{-1}$] is the absorbed 
photosynthetically active radiation.

The parameters $K_c$, $K_o$, $\Gamma^*$, $V_{cmax}$, $J_{max}$, and $R_d$ vary from their
values at 25$^0$C as function of leaf temperature, $T_\ell$, that are given as

\begin{eqnarray}
	K_{c} &=& K_{c25} f(T_\ell) \\[0.4em]
	K_{o} &=& K_{o25} f(T_\ell) \\[0.4em]
	\Gamma^* &=& \Gamma^* f(T_\ell) \\[0.4em]
	V_{cmax} &=& V_{cmax25} f(T_\ell) f_H(T_\ell)\\[0.4em]
	J_{max}  &=& J_{cmax25} f(T_\ell) f_H(T_\ell)\\[0.4em]
	R_{d}    &=& R_{d25}    f(T_\ell) f_H(T_\ell)
\end{eqnarray}

where

\begin{eqnarray}
	f(T_\ell) &=& \exp \left[ 
													\frac{\Delta H_a}{298.15 \mathcal{R}} 
													\left( 1 - \frac{298.15}{T_\ell} \right) 											
											\right] \\[0.4em]
	f_H(T_\ell)    &=& \left[1 + \exp \left( \frac{298.15\Delta S - \Delta H_d}{298.15\mathcal{R}} \right)  \right]
										 \left[1 + \exp \left( \frac{\Delta S T_\ell - \Delta H_d}{\mathcal{R} T_\ell} \right)\right]^{-1}
\end{eqnarray}

Lastly, the $J_{max}$ and $R_{d}$ at 25$^0$C are given as

\begin{eqnarray}
	J_{max25}  &=& 1.67  V_{cmax25} \\
	R_{d25}    &=& 0.015 V_{cmax25} 
\end{eqnarray}


## C4 Photosynthesis

The CO$_2$ assimilation fluxes for C4 photosynthesis are

\begin{eqnarray}
	A_c &=& V_{cmax} \\
	A_j &=& \alpha_\ell \overrightarrow{I}_{PAR} E\\
	A_p &=& k_p c_i
\end{eqnarray}

where 
$E = 0.05$ [mol mol$^{-2}$] is the quantum yield and
$k_p$ [mol m$^{-2}$ s$^{-1}$] is the initial slope of the CO$_2$ response curve.
The temperature dependence of $V_{cmax}$, $R_d$, and $k_p$ are given as

\begin{eqnarray}
	V_{cmax} &=& V_{cmax25} 
							 Q_{10}^{(T_\ell - 298.16)/10} 
							 \left( 1 + \exp[s_1(T_\ell - s_2)] \right)^{-1}
							 \left( 1 + \exp[s_3(s_4 - T_\ell)] \right)^{-1} 
							 \\[0.4em]
	R_d &=& R_{d25}
					Q_{10}^{(T_\ell - 298.16)/10} 
					\left( 1 + \exp[s_5(s_6 - T_\ell)] \right)^{-1} 
					\\[0.4em]
	k_p &=& k_{p25} Q_{10}^{(T_\ell - 298.16)/10}
\end{eqnarray}

where
$Q_{10} = 2$,
$s_1 = 0.3$ [K$^{-1}$],
$s_2 = 313.15$ [K],
$s_3 = 0.2$ [K$^{-1}$],
$s_4 = 288.15$ [K],
$s_5 = 1.3$ [K$^{-1}$], and
$s_6 = 328.15$ [K]. 

The max $R_{d}$ and $k_{p}$ at 25$^0$C are given as

\begin{eqnarray}
	R_{d25} &=& 0.025 V_{cmax25} \\
	k_{p25} &=& 0.02  V_{cmax25} 
\end{eqnarray}


