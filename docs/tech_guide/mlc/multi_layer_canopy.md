## Governing equations

The equations for the time evolution of
air temperature, $\theta$, and 
water vapor, $q$, 
sunlit leaf temperature, $T_{\ell sun}$, and
shaded leaf temperature, $T_{\ell shd}$, 
in a MLCM is given by

\begin{eqnarray}
\rho_mc_p
\left(\frac{\partial\theta}{\partial t}\right) &=&
	c_p \nabla \cdot \left( g_{a} \nabla \theta \right)
 + \frac{Q_{\theta sun,i} \Delta L_{sun,i}}{\Delta z_i}
 + \frac{Q_{\theta shd,i} \Delta L_{shd,i}}{\Delta z_i} \label{eqn_mlc_tair} 
 + S_\theta \\
\rho_m
\left( \frac{\partial q}{\partial t} \right) &=&
	\nabla \cdot \left( g_{a} \nabla q \right) 
	+ \frac{Q_{qsun,i} \Delta L_{sun,i}}{\Delta z_i}
  + \frac{Q_{qshd,i} \Delta L_{shd,i}}{\Delta z_i} \label{eqn_mlc_qair}
  + S_q \\
c_{\ell}
\left( \frac{\partial T_{\ell sun}}{\partial t} \right) &=&
\text{R}_{n,sun} - Q_{\theta sun} - \lambda Q_{qsun} + S_{\ell sun} \label{eqn_mlc_tsun} \\
c_{\ell}
\left( \frac{\partial T_{\ell shd}}{\partial t} \right) &=&
\text{R}_{n,shd} - Q_{\theta shd} - \lambda Q_{qshd} + S_{\ell shd}  \label{eqn_mlc_tshd}
\end{eqnarray}

where
$\rho_m$ is density of air,
$\lambda$ is latent heat of vaporization for water,
$c_p$ is specific heat capacity of air,
$c_{\ell}$ is specific heat capacity of leaf,
$g_{a}$ is atmospheric conductance,
$\Delta L_{sun}$ is the leaf area index of the sunlit leaf,
$\Delta L_{shd}$ is the leaf area index of the shaded leaf,
$Q_{\theta sun}$ is the heat source from the sunlit leaf to the canopy air,
$Q_{\theta shd}$ is the heat source from the shaded leaf to the canopy air,
$Q_{qsun}$ is the water vapor source from the sunlit leaf the canopy air,
$Q_{qsun}$ is the water vapor source from the shaded leaf the canopy air,
$\text{Rn}_{sun}$ is the net shortwave and longwave radiation absorbed by the sunlit leaf, and
$\text{Rn}_{shd}$ is the net shortwave and longwave radiation absorbed by the shaded leaf.

The source of heat and water vapor for sunlit and shaded leaves at the $i$-th layer are given by

\begin{eqnarray}
		Q_{\theta sun} &=& 2c_p(T_{\ell sun} - \theta_i)g_{bh} \\
		Q_{\theta shd} &=& 2c_p(T_{\ell shd} - \theta_i)g_{bh}\\
		Q_{qsun}   &=& (q_{sat}(T_{\ell sun}) - q_i) g_{\ell sun} \\
		Q_{qshd}   &=& (q_{sat}(T_{\ell shd}) - q_i) g_{\ell shd}
\end{eqnarray}

where
$g_{bh,i}$ is the boundary layer conductance for heat,
$g_{bw,i}$ is the boundary layer conductance for water vapor,
$g_{\ell sun,i}$ is the total leaf conductance for the sunlit leaf, and
$g_{\ell shd,i}$ is the total leaf conductance for the shaded leaf.
The leaf conductances are given as

\begin{eqnarray}
		g_{\ell sun}   &=& \left(\frac{1}{g_{bw}^{-1} + g_{sw,sun}^{-1}}\right) f_{dry} + g_{bw} f_{wet}\\
		g_{\ell shd}   &=& \left(\frac{1}{g_{bw}^{-1} + g_{sw,shd}^{-1}}\right) f_{dry} + g_{bw} f_{wet}
\end{eqnarray}

where
$g_{sw,sun}$ is the stomatal conductance for the sunlit leaf, and
$g_{sw,shd}$ is the stomatal conductance for the shaded leaf.

The net radiation absorbed by sunlit and shaded leaf are given by

\begin{eqnarray}
\label{eqn_rn}
\text{Rn}_{sun}   &=& \vec{I}^{d}_{sun} + \vec{I}^{b}_{sun} + \vec{L}_{sun}\\
\text{Rn}_{shd}   &=& \vec{I}^{d}_{shd} + \vec{L}_{shd} \label{eqn:net_}
\end{eqnarray}

where
$\vec{I}^{d}$ is absorbed diffuse radiation,
$\vec{I}^{b}$ is absorbed beam radiation, and
$\vec{L}$ is absorbed longwave radiation.
The finite volume and implicit time discretization of equation \eqref{eqn_mlc_tair}-\eqref{eqn_mlc_tshd} leads to the following equations
for the $i$-th layer can be written as

\begin{eqnarray}
     \begin{bmatrix}
           \alpha_{1,1} & {\alpha_{1,2}} & {\alpha_{1,3}} & \alpha_{1,4} & \alpha_{1,5} & \alpha_{0,6} & {\alpha_{1,7}} & {\alpha_{1,8}}\\
            0 & 0 & 0 & {\alpha_{2,4}} & {\alpha_{2,5}} & {\alpha_{2,6}} & {\alpha_{2,7}} & {\alpha_{2,8}}\\
           0 & {\alpha_{3,2}} & 0 & 0 & {\alpha_{3,5}} & 0 & {\alpha_{3,7}} & 0 \\
           0 & {\alpha_{4,2}} & 0 & 0 & {\alpha_{4,5}} & 0 & 0 & {\alpha_{4,8}}\\
         \end{bmatrix}
     \begin{bmatrix}
           \theta_{i-1}^{t+1}   \\
           \theta_{i  }^{t+1}   \\
           \theta_{i+1}^{t+1}   \\
           q_{i-1}^{t+1}   \\
           q_{i  }^{t+1}   \\
           q_{i+1}^{t+1}   \\
           T_{lsun,i}^{t+1} \\
           T_{lshd,i}^{t+1} 
         \end{bmatrix}
  =
     \begin{bmatrix}
           \beta_{1}   \\
           \beta_{2}   \\
           \beta_{3}   \\
           \beta_{4}
         \end{bmatrix}
  \label{eqn_mlc_matrix}
\end{eqnarray}


## Air temperature equation

The discretized equation \ref{eqn_mlc_tair} at an internal vertical layer (i.e. $0<i<N$)

\begin{eqnarray}
\frac{\rho_m }{\Delta t}
\left(\theta_i^{t+1} - \theta_i^{t}\right) &=&  
	+ g_{a,i+\frac{1}{2}} \left(\frac{ {\theta_{i+1}^{t+1} - \theta_{i  }^{t+1}} } {z^c_{i+1} - z^c_{i  }}\right)
	- g_{a,i-\frac{1}{2}}\left(\frac{ {\theta_{i  }^{t+1} - \theta_{i-1}^{t+1}}}{ z^c_{i } - z^c_{i-1}} \right) \nonumber \\
	& & + 2 \left(T_{\ell sun,i}^{t+1} - \theta_i^{t+1}\right) \left( \frac{g_{bh,i}\Delta L_{sun,i}}{\Delta z_i} \right)  \nonumber \\
	& & + 2 \left(T_{\ell shd,i}^{t+1} - \theta_i^{t+1}\right) \left( \frac{g_{bh,i}\Delta L_{shd,i}}{\Delta z_i} \right)
\end{eqnarray}

The non-zero coefficients $\alpha_{i=1,*}$ of equation \eqref{eqn_mlc_matrix} for $0<i<N$ are thus given as

\begin{eqnarray}
\label{eqn_atemp_terms}
	\alpha_{1,1} &=& -\left(\dfrac{g_{a,i-\frac{1}{2}}^{t+1}}{\Delta z^c_{i,i-1}} \right) \\
	\alpha_{1,2} &=& \left(\dfrac{\rho_m}{\Delta t}\right)
       + \left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1} }{\Delta z^c_{i+1,i}} \right)
       + \left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1} }{\Delta z^c_{i+1,i}} \right) \nonumber \\
			 & &
       + \frac{2 g_{bh,i}^{t+1} \left(\Delta L_{sun,i} + \Delta L_{shd,i}\right)}{\Delta z_i} \\
	\alpha_{1,3} &=& -\left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1}}{\Delta z^c_{i+1,i}} \right)\\
	\alpha_{1,7} &=& - \frac{2 g_{bh,i}^{t+1} \Delta L_{sun,i}}{\Delta z_i}\\
	\alpha_{1,8} &=& - \frac{2 g_{bh,i}^{t+1} \Delta L_{shd,i}}{\Delta z_i} \\
	\beta_{1} &=& \left(\dfrac{\rho_m}{\Delta t}\right) \theta_i^{t+1}
\end{eqnarray}

For the top vertical layer $i = N$, the coefficients $\alpha_{i=1,*}$ remain same as terms in equation \eqref{eqn_atemp_terms} same except

\begin{eqnarray}
\label{eqn_atemp_terms_top}
	\beta_{1} &=& \left(\dfrac{\rho_m}{\Delta t}\right) \theta_i^{t+1} + \left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1}}{\Delta z^c_{i+1,i}} \right) \theta_{ref}^{t+1}
\end{eqnarray}

where $\theta_{ref}^{n+1}$ is prescribed atmospheric temperature.

For $i = 0$, the energy balance for the soil surface, $\text{Rn}_0$, is given by

\begin{eqnarray}
\label{eqn_soil_bc_air_heat}
\text{Rn}_0 &=& c_p(T_0^{n+1} - \theta_1^{n+1})g_{a,0} 
	 \nonumber \\
	& & + \lambda \left\{ 
		h_{s0} q_{sat}(T_0^{n+1}) - q_1^{n+1} 
	\right\}g_{s0} \nonumber \\
	& & + \frac{\kappa_{1}}{\Delta z_{1/2}} \left( T_0^{n+1} - T_{-1}^n\right) \nonumber \\
 &=& c_p(T_0^{n+1} - \theta_{1}^{n+1})g_{a,0} \nonumber \\
 & & + 
	\lambda 
	\left\{ 
		h_{s0} \left[ q_{sat}(T_0^{n}) + s_0\left( T_0^{n+1} - T_0^n\right)\right] - q_1^{n+1} 
	\right\}g_{s0}\nonumber \\
	& & + \frac{\kappa_{1}}{\Delta z_{1/2}} \left( T_0^{n+1} - T_{-1}^n\right)
\end{eqnarray}

where 
$\theta_0^{n+1} = T_0^{n+1}$ is the soil surface temperature,
$T_{-1}^{n}$ is the soil temperature of the first soil layer, 
and
$z_{1/2}$ is the distance between the soil surface and centroid of first soil layer.
The non-zero coefficients $\alpha_{1,*}$ for $i = 0$ are thus given as

\begin{eqnarray}
\label{eqn_atemp_terms_soil}
	\alpha_{1,2} &=& \left( c_p g_{a,0} + \lambda h_{s0} g_{s0} s_{0} + \frac{\kappa_{1}}{\Delta z_{1/2}} \right)   \\
	\alpha_{1,3} &=& - c_p g_{a,0}  \\
	\alpha_{1,6} &=& - \lambda g_{s,0} \\
	\beta_{1} &=& \text{Rn}_0 - \lambda h_{s0} \left[ q_{sat}(T_0^{n}) - s_0T_0^n\right] g_{s0} + \frac{\kappa_{1}}{\Delta z_{1/2}} T_{-1}^n
\end{eqnarray}


## Air vapor pressure equation

The discretized equation \ref{eqn_mlc_qair} at an internal vertical layer (i.e. $0<i<N$)

\begin{eqnarray}
\frac{\rho_m}{\Delta t}
\left(q_i^{t+1} - q_i^t \right) &=&
	+ g_{a,i+\frac{1}{2}} \left(\frac{ {q_{i+1}^{t+1} - q_{i  }^{t+1}} } {z^c_{i+1} - z^c_{i  }}\right)
	- g_{a,i-\frac{1}{2}}\left(\frac{ {q_{i  }^{t+1} - q_{i-1}^{t+1}}}{ z^c_{i } - z^c_{i+1}} \right) \nonumber \\
  & & + \left[q_{sat, \ell sun,i}^{t+1} - q_i^{t+1}\right] \left( \frac{ g_{\ell sun,i}\Delta L_{sun,i}} {\Delta z_i} \right)\nonumber \\
  & & + \left[q_{sat, \ell sha,i}^{t+1} - q_i^{t+1}\right] \left( \frac{ g_{\ell sun,i}\Delta L_{sun,i}} {\Delta z_i} \right) \nonumber \\
&=& 
	+ g_{a,i+\frac{1}{2}} \left(\frac{ {q_{i+1}^{t+1} - q_{i  }^{t+1}} } {z^c_{i+1} - z^c_{i  }}\right)
	- g_{a,i-\frac{1}{2}}\left(\frac{ {q_{i  }^{t+1} - q_{i-1}^{t+1}}}{ z^c_{i } - z^c_{i+1}} \right) \nonumber \\
  & & + \left[ q_{sat, \ell sun,i}^{t} + s_{sun,i} \left( T_{\ell,sun}^{n+1} - T_{\ell, sun}^n \right) - q_i^{t+1}\right] \left( \frac{ g_{\ell sun,i}\Delta L_{sun,i}} {\Delta z_i} \right)\nonumber \\
  & & + \left[ q_{sat, \ell sha,i}^{t} + s_{sha,i} \left( T_{\ell,sha}^{n+1} - T_{\ell, sha}^n \right) - q_i^{t+1}\right] \left( \frac{ g_{\ell sun,i}\Delta L_{sun,i}} {\Delta z_i} \right)
\end{eqnarray}

The non-zero coefficients $\alpha_{i=2,*}$ of equation \eqref{eqn_mlc_matrix} for $0<i<N$ are thus given as

\begin{eqnarray}
\label{eqn_avapor_terms}
	\alpha_{2,4} &=& -\left(\dfrac{g_{a,i-\frac{1}{2}}^{t+1}}{\Delta z^c_{i,i-1}} \right) \\
	\alpha_{2,5} &=& \left(\dfrac{\rho_m}{\Delta t}\right)
       + \left(\dfrac{g_{a,i-\frac{1}{2}}^{t+1} }{\Delta z^c_{i,i-1}} \right)
       + \left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1} }{\Delta z^c_{i+1,i}} \right) \nonumber \\
			 & & + \frac{g_{lsun,i}^{t+1} \Delta L_{sun,i} +  g_{lshd,i}^{t+1} \Delta L_{shd,i}}{\Delta z_i} \\
	\alpha_{2,6} &=& -\left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1}}{\Delta z^c_{i+1,i}} \right) \\
	\alpha_{2,7} &=& - \frac{s_{sun,i} g_{lsun,i}^{t+1} \Delta L_{sun,i}}{\Delta z_i} \\
	\alpha_{2,8} &=& - \frac{s_{shd,i} g_{lshd,i}^{t+1} \Delta L_{shd,i}}{\Delta z_i} \\
	\beta_{2} &=& \left(\dfrac{\rho_m}{\Delta t}\right) q_i^{t+1} \nonumber \\
						& & + \frac{\left(q_{sat}(T_{lsun,i}^{t+1}) - s_{sun,i} T_{lsun}^{t+1} \right)
	                g_{lsun,i}^{t+1}\Delta L_{sun,i}}{\Delta z_i}  \nonumber \\
            & & + \frac{\left(q_{sat}(T_{lshd,i}^{t+1}) - s_{shd,i} T_{lshd}^{t+1} \right) 
	              g_{lshd,i}^{t+1}  \Delta L_{shd,i}}{\Delta z_i}
\end{eqnarray}

For the top vertical layer $i = N$, the coefficients $\alpha_{i=2,*}$ remain same as terms in equation \eqref{eqn_avapor_terms} same except

\begin{eqnarray}
	\alpha_{2,6} &=& 0\\
	\beta_{2} &=& \left(\dfrac{\rho_m}{\Delta t}\right) q_i^{t+1} \nonumber \\
						& & + \frac{\left(q_{sat}(T_{lsun,i}^{t+1}) - s_i T_{lsun}^{t+1} \right) 
	                g_{lsun,i}^{t+1}\Delta L_{sun,i}}{\Delta z_i}  \nonumber \\
            & & + \frac{\left(q_{sat}(T_{lshd,i}^{t+1}) - s_i T_{lshd}^{t+1} \right) 
	              g_{lshd,i}^{t+1}  \Delta L_{shd,i}}{\Delta z_i} \nonumber \\
	          & & + \left(\dfrac{g_{a,i+\frac{1}{2}}^{t+1}}{\Delta z_{i+1,i}} \right) q_{ref}^{n+1}
\end{eqnarray}

where $q_{ref}^{n+1}$ is prescribed atmospheric water vapor pressure.

For soil surface layer $i=0$, the water vapor balance is given by

\begin{eqnarray}
q_0^{n+1} &=& 
		h_{s0} \left[ q_{sat}(T_0^{n}) + s_0\left( T_0^{n+1} - T_0^n\right)\right] \nonumber \\
-h_{s0} s_0 T_0^{n+1} + q_0^{n+1} &=& h_{s0} \left[ q_{sat}(T_0^{n}) - s_0T_0^n\right] 
\end{eqnarray}

The non-zero coefficients $\alpha_{1,*}$ for $i = 0$ are thus given as

\begin{eqnarray}
	\alpha_{2,2} &=& -h_{s0} s_0 \\
	\alpha_{2,5} &=& 1\\
	\beta_{2} &=& h_{s0} \left[ q_{sat}(T_0^{n}) - s_0T_0^n\right] 
\end{eqnarray}


## Sunlit leave temperature

The discretized equation \ref{eqn_mlc_tsun} at an internal vertical layer (i.e. $0<i<N$) is
given by

\begin{eqnarray}
 \frac{c_{\ell,i}}{\Delta t} \left( T_{\ell sun,i}^{t+1} - T_{\ell sun,i}^{t} \right)&=& 
\text{Rn}_{sun} 
- 2 \left(T_{\ell sun,i}^{t+1} - \theta_i^{t+1}\right) g_{bh,i} \nonumber \\
& & - \lambda \left[ q_{sat, \ell sun,i}^{t+1} - q_i^{t+1}\right] g_{\ell sun,i} \nonumber \\
&=& 
\text{Rn}_{sun} 
- 2 \left(T_{\ell sun,i}^{t+1} - \theta_i^{t+1}\right) g_{bh,i} \nonumber \\
& &- \lambda  \left[ q_{sat, \ell sun,i}^{t} + s_{sun,i} \left( T_{\ell,sun}^{n+1} - T_{\ell, sun}^n \right) - q_i^{t+1}\right] g_{\ell sun,i}
\end{eqnarray}

The non-zero coefficients $\alpha_{i=3,*}$ of equation \eqref{eqn_mlc_matrix} for $0<i<N$ are thus given as

\begin{eqnarray}
	\alpha_{3,2} &=& -2 c_p g_{bh,i}^{t+1}  \\
	\alpha_{3,5} &=& - \lambda g_{lsun,i}^{t+1}   \\
	\alpha_{3,7} &=& \left( \frac{c_{L,i}}{\Delta t} \right) + 2 c_p g_{bh,i}^{t+1} + \lambda s_i g_{lsun,i}^{t+1} \\
	\beta_{3} &=& \text{Rn}_{sun}^{t+1,0} + \left(\dfrac{c_{L,i}}{\Delta t}\right) T_{lsun,i}^{t+1} 
	           - \lambda \left(q_{sat}(T_{lsun,i}^{t+1}) - s_i T_{lsun}^{t+1} \right) g_{lsun,i}^{t+1}
\end{eqnarray}

## Shaded leave temperature

The discretized equation \ref{eqn_mlc_tshd} at an internal vertical layer (i.e. $0<i<N$) is
given by

\begin{eqnarray}
 \frac{c_{\ell,i}}{\Delta t} \left( T_{\ell shd,i}^{t+1} - T_{\ell shd,i}^{t} \right)&=& 
\text{Rn}_{shd} 
- 2 \left(T_{\ell shd,i}^{t+1} - \theta_i^{t+1}\right) g_{bh,i} \nonumber \\
& & - \lambda \left[ q_{sat, \ell shd,i}^{t+1} - q_i^{t+1}\right] g_{\ell shd,i} \nonumber \\
&=& 
\text{Rn}_{shd} 
- 2 \left(T_{\ell shd,i}^{t+1} - \theta_i^{t+1}\right) g_{bh,i} \nonumber \\
& & - \lambda  \left[ q_{sat, \ell shd,i}^{t} + s_{shd,i} \left( T_{\ell,shd}^{n+1} - T_{\ell, shd}^n \right) - q_i^{t+1}\right] g_{\ell shd,i}
\end{eqnarray}

The non-zero coefficients $\alpha_{i=4,*}$ of equation \eqref{eqn_mlc_matrix} for $0<i<N$ are thus given as

\begin{eqnarray}
	\alpha_{4,2} &=& -2 c_p g_{bh,i}^{t+1}  \\
	\alpha_{4,5} &=& - \lambda g_{lshd,i}^{t+1}   \\
	\alpha_{4,8} &=& \left( \frac{c_{L,i}}{\Delta t} \right) + 2 c_p g_{bh,i}^{t+1} + \lambda s_i g_{lshd,i}^{t+1} \\
	\beta_{4} &=& \text{Rn}_{shd}^{t+1,0} + \left(\dfrac{c_{L,i}}{\Delta t}\right) T_{lshd,i}^{t+1} 
	          - \lambda \left(q_{sat}(T_{lshd,i}^{t+1}) - s_i T_{lshd}^{t+1} \right)  g_{lshd,i}^{t+1}
\end{eqnarray}
