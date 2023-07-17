
The boundary conductance controls the transfer of heat and mass (both, H$_2$O and CO$_2$)
from the leaf surface to the surrounding air. The Nusslet number, $Nu$ [-], is the ratio of
convective to conductive heat transfer, while the Sherwood number, $Sh$ [-], is the
ratio of convective to conductive mass transfer that are given by

\begin{eqnarray}
	\label{eqn_definitation_of_numbers}
		\text{Nu}   &=& \frac{g_{bh}d_\ell}{\rho_m D_h} \\[0.2em]
		\text{Sh}_w &=& \frac{g_{bw}d_\ell}{\rho_m D_w} \\[0.2em]
		\text{Sh}_c &=& \frac{g_{bc}d_\ell}{\rho_m D_c}
\end{eqnarray}

where
$g_{bh}$ [mol m$^{-2}_{leaf}$ s$^{-1}$] is boundary conductance for heat ,
$g_{bv}$ [mol m$^{-2}_{leaf}$ s$^{-1}$] is boundary conductance for H$_2$O,
$g_{bc}$ [mol m$^{-2}_{leaf}$ s$^{-1}$] is boundary conductance for CO$_2$,
$D_h$ [m$^2$ s$^{-1}$] is the molecular diffusivity for heat,
$D_w$ [m$^2$ s$^{-1}$] is the molecular diffusivity for H$_2$O,
$D_c$ [m$^2$ s$^{-1}$] is the molecular diffusivity for CO$_2$,
$\rho_m$ [mol m$^{-3}$] is molar density, 
$d_\ell$ [m] is the representative leaf dimension, and
$\text{Sh}_w$ and $\text{Sh}_c$ are Sherwood number for water vapor and CO$_2$, respectively.

Empirical studies have developed relationship for $\text{Nu}$, $\text{Sh}_w$,
and $\text{Sh}_c$ for laminar flow:

\begin{eqnarray}
		\text{Nu}^{Laminar}   &=& b_1 0.66 \text{Pr}  ^{0.33}Re^{0.5} \\[0.4em]
		\text{Sh}_w^{Laminar} &=& b_1 0.66 \text{Sc}_w^{0.33}Re^{0.5} \\[0.4em]
		\text{Sh}_c^{Laminar} &=& b_1 0.66 \text{Sc}_c^{0.33}Re^{0.5}
\end{eqnarray}

and turbulent flow:

\begin{eqnarray}
		\text{Nu}^{Turbulent}   &=& b_1 0.036\text{Pr}  ^{0.33}Re^{0.8} \\[0.4em]
		\text{Sh}_w^{Turbulent} &=& b_1 0.036\text{Sc}_w^{0.33}Re^{0.8} \\[0.4em]
		\text{Sh}_c^{Turbulent} &=& b_1 0.036\text{Sc}_c^{0.33}Re^{0.8}
\end{eqnarray}

where 
$\text{Re}$ [-] is the Reynolds number that is a ratio of inertial forces to viscous forces, 
$\text{Pr}$ [-] is the Prandtl number that is a ratio of diffusivity of momentum to diffusivity of heat in fluid,
$\text{Sc}_w$ [-] and $\text{Sc}_c$ [-] are the Schmidt numbers that are ratio of diffusivity of momentum to diffusivity of mass for H$_2$O and CO$_2$) in fluid, respectively,
and
$b_1 = 1.5$ is a typical value that converts the empirical relationship developed
for a flat rectangular plate to for leaves. 

The Prandtl, Reynolds, and Schmidt numbers are

\begin{eqnarray}
		\text{Re} &=& \frac{u d_\ell}{\nu} \\[0.4em]
		\text{Pr} &=& \frac{\nu}{D_h}\\[0.4em]
		\text{Sc}_w &=& \frac{\nu}{D_w} \\[0.4em]
		\text{Sc}_c &=& \frac{\nu}{D_c}
\end{eqnarray}

where $\nu$ [m$^2$ s$^{-1}$] is the kinematic viscosity.
The forced flow due to laminar and turbulent flow is given as

\begin{eqnarray}
		\text{Nu}  ^{forced}  &=& \max(\text{Nu}^{Laminar}, \text{Nu}  ^{Turbulen}) \\[0.4em]
		\text{Sh}_w^{forced} &=& \max(Shv^{Laminar}, \text{Sh}_w^{Turbulent}) \\[0.4em]
		\text{Sh}_c^{forced} &=& \max(Shc^{Laminar}, \text{Sh}_c^{Turbulent}) 
\end{eqnarray}

In free convection, The Nusselt and Scherwood number are described in terms
of Grashof number, $\text{Gr}$ [-], as

\begin{eqnarray}
		\text{Nu}^{Free}   &=& 0.54\text{Pr}  ^{0.25}\text{Gr}^{0.25} \\[0.4em]
		\text{Sh}_w^{Free} &=& 0.54\text{Sc}_c^{0.25}\text{Gr}^{0.25} \\[0.4em]
		\text{Sh}_c^{Free} &=& 0.54\text{Sc}_c^{0.25}\text{Gr}^{0.25} \\[0.4em]
\end{eqnarray}

The Grashof number is given as

\begin{equation}
		\text{Gr} = \frac{gd_\ell^3 (T_\ell - T_a)}{\nu^2 T_a}
\end{equation}

where
$g$ [m s$^{-2}$] is the gravitational acceleration,
$T_\ell$ [K] is the leaf temperature,
and
$T_a$ [K] is the air temperature.
Lastly, the combined Nusselt and Scherwood number for forced
and free flow are given as

\begin{eqnarray}
	\label{eqn_combined_numbers}
		\text{Nu}   &=& \text{Nu}  ^{Forced} + \text{Nu}  ^{free} \\[0.4em]
		\text{Sh}_w &=& \text{Sh}_w^{Forced} + \text{Sh}_w^{free} \\[0.4em]
		\text{Sh}_c &=& \text{Sh}_c^{Forced} + \text{Sh}_c^{free} 
\end{eqnarray}

The leaf boundary conductances for heat, H$_2$O, and CO$_2$ are given by
combining equations \eqref{eqn_definitation_of_numbers} and \eqref{eqn_combined_numbers}

\begin{eqnarray}
		g_{bh} &=& \frac{D_h \times \text{Nu}}{d_\ell} \rho_m\\[0.4em]
		g_{bw} &=& \frac{D_w \times Sh_v}{d_\ell} \rho_m\\[0.4em]
		g_{bc} &=& \frac{D_c \times Sh_c}{d_\ell} \rho_m
\end{eqnarray}

The kinematic viscosity and molecular diffusivities are adjusted to account
for air temperature and air pressure, $P_a$ [Pa], as

\begin{eqnarray}
		\nu &=& f \times \nu_0 \\
		D_h &=& f \times Dh_0 \\
		D_w &=& f \times Dv_0 \\
		D_c &=& f \times Dc_0 \\
      f &=& \frac{10325}{P_{a}}\times \left(\frac{T_a}{272.15}\right)^{1.81}
\end{eqnarray}

where
$\nu_0$ is kinematic viscosity at 0$^0$ C,
and
$Dh_0$, $Dv_0$, $Dc_0$ are molecular diffusivity for
heat, H$_2$O, and CO$_2$ at 0$^0$ C.

