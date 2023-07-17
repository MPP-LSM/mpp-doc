## Governing equations

The net CO$_2$ assimilation due to biological demand
must match the diffusion of CO$_2$ from the
surrounding air to the leaf surface and into the leaf, and is given by

\begin{equation}
	\label{eqn_an_diffusion}
	A_n = g_{bc} (c_a - c_s) = g_{sc} (c_s - c_i) = g_{\ell c} (c_a - c_i)
\end{equation}

where
$c_a$ [$\mu$mol {CO$_2$} mol$^{-1}$] is the atmospheric CO$_2$,
$c_s$ [$\mu$mol CO$_2$ mol$^{-1}$] is the leaf surface CO$_2$,
$c_i$ [$\mu$mol CO$_2$ mol$^{-1}$] is the intercellular CO$_2$,
$g_{bc}$ [mol m$^{-1}$ s$^{-2}$o] is the boundary conductance of CO$_2$, 
$g_{sc}$ [mol m$^{-1}$ s$^{-2}$o] is the stomatal conductance of CO$_2$,
and
$g_{\ell c}$ [mol m$^{-1}$ s$^{-2}$o] is the leaf conductance of CO$_2$.

Similarly, the transpiration of flux, $E$ [mol H$_2$O m$^{-2}$o s$^{-1}$], is given as
\begin{equation}
	E = g_{bw} (q_a - q_s) = g_{sw} (q_s - q_i) = g_{\ell w} (q_a - q_i)
\end{equation}

where
$q_a$ [$\mu$mol H$_2$O mol$^{-1}$] is the atmospheric H$_2$O,
$q_s$ [$\mu$mol H$_2$O mol$^{-1}$] is the leaf surface H$_2$O,
$q_i$ [$\mu$mol H$_2$O mol$^{-1}$] is the intercellular H$_2$O,
$g_{bc}$ [mol m$^{-1}$ s$^{-2}$o] is the boundary conductance of H$_2$O, 
$g_{sc}$ [mol m$^{-1}$ s$^{-2}$o] is the stomatal conductance of H$_2$O, 
and
$g_{\ell c}$ [mol m$^{-1}$ s$^{-2}$o] is the leaf conductance of H$_2$O.
The leaf conductances can be written in terms of boundary and stomatal 
conductances as


\begin{eqnarray}
	\label{eqn_glc}
	g_{\ell c}  &=  \frac{1}{g_{bc}^{-1} + g_{sc}^{-1}} \\[0.4em]
	g_{\ell w}  &=  \frac{1}{g_{bw}^{-1} + g_{sw}^{-1}}
\end{eqnarray}

It is assumed that $g_{sc} = g_{sw}/1.6$. Using equations \eqref{eqn_an_diffusion}
and \eqref{eqn_glc}, $c_i$ can be given as

\begin{equation}
	\label{eqn_ci_diff}
	c_i = c_a - \frac{A_n}{g_{\ell c}}
\end{equation}
