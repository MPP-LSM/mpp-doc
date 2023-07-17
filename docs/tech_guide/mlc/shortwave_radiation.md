## Governing equations

The downwelling, $I_i^{\downarrow}$ [Wm$^{-2}$], and upwelling, $I_{i+1}^{\uparrow}$ [Wm$^{-2}$], scattered radiation fluxes at $i$-th and
$(i+1)$-th level are given as

\begin{eqnarray}
	I_{i  }^{\downarrow} & = &   I_{i+1  }^{\downarrow} \left[ \mathcal{\tau}_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}\right] 
  	                  + I_{i    }^{\uparrow}                       (1 - \tau_{d,i+1})\rho_{\ell,i+1} \nonumber \\
  \label{eqn_sw_dn}
    	          &  &  + I_{sky,b}^{\downarrow} T_{b,i+1} (1 - \tau_{b,i+1})\tau_{\ell,i+1} \\
	I_{i+1}^{\uparrow} & = &   I_{i    }^{\uparrow} \left[ \tau_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}\right] 
  	                  + I_{i+1  }^{\downarrow}                       (1 - \tau_{d,i+1})\rho_{\ell,i+1} \nonumber \\
    	          &  &  + I_{sky,b}^{\downarrow} T_{b,i+1} (1 - \tau_{b,i+1})\rho_{\ell,i+1}
  \label{eqn_sw_up}
\end{eqnarray}

where
$\tau_{d,i+1}$ [-] and $\tau_{b,i+1}$ [-]  are the diffuse and direct beam transmittances through $(i+1)$-th layer,
$\rho_{\ell,i+1}$ [-]  is the leaf reflectance of $(i+1)$-th layer,
$I_{sky,b}$ [Wm$^{-2}$] is the direct beam radiation incident on the top of the canopy, and
$T_{b,i+1}$ [-]  is the fraction of direct beam radiation that is not intercepted through
the cumulative leaf area above the $(i+1)$-th layer.

## Transmittance

The direct beam transmittance through the $(i+1)$-th layer with leaf area index $\Delta L_{i+1}$ is 

\begin{equation}
	\tau_{d,i+1} = 2 \int_{0}^{\pi/2} \exp \left[ - \frac{G(Z_i)\Omega}{\cos (Z_i)} \Delta L_{i+1} \right] \sin (Z_i) \cos (Z_i) dZ
\end{equation}

where
$Z$ is the sky zenith angle and
$\Omega$ is the leaf clumping factor.
The Ross-Goudriann function, $G(Z)$, is given by

\begin{equation}
	\label{eqn_rg_function}
	G(Z) = \phi_1 + \phi_2 \cos(Z)
\end{equation}
where $\phi_1 = 0.5 -0.633\chi_\ell - 0.33\chi_\ell^2$ and
$\phi_2 = 0.877 (1 - 2\phi_1$). The leaf departure angle from from spherical orientation, $\chi_\ell$,
in restricted to $-0.4 \le \chi_\ell \le 0.6$. The equation \eqref{eqn_rg_function} is numerically approximation
for nine sky zones as

\begin{equation}
\tau_{d,i+1} = 2 \sum_{i=1}^{9} \exp \left[ - \frac{G(Z_i)\Omega}{\cos (Z_i)} \Delta L_{i+1} \right] \sin (Z_i) \cos (Z_i) \Delta Z_i
\end{equation}
with $\Delta Z_i = \pi/18$. 

The diffuse beam transmittance through the $(i+1)$-th layer is

\begin{equation}
	\tau_{b,i+1} = \exp \left( -K_{b,i+1} \Omega \Delta L_{i+1} \right)
\end{equation}
%
where $K_{b,i+1} = G(Z)/\cos(Z)$ is the extinction coefficient for the direct beam.
The fraction of direct been that is not intercepted through the cumulative leaf area above
the $(i+1)$-th layer is computed as

\begin{equation}
	T_{b,i+1} = \prod_{j=i+1}^N \exp \left( -K_{b,j} \Omega_j \Delta L_j \right)
\end{equation}

## Linear system

The equation \eqref{eqn_sw_dn}-\eqref{eqn_sw_up} can be written as a system of linear equations

\begin{eqnarray}
	\label{eqn_sw_linear_system_up}
		-a_i I_i^{\uparrow} + I_i^\downarrow - b_iI_{i+1}^\uparrow &=&  d_i \\
	\label{eqn_sw_linear_system_dn}
                    -e_{i+1}I_i^\downarrow + I_{i+1}^\uparrow - f_{i+1}I_{i+1}^\downarrow &=& c_{i+1}
\end{eqnarray}

where

\begin{eqnarray}
		a_i &=& f_{i+1} = (1-\tau_{d,i+1})\rho_{\ell,i+1} - 
										\frac{[\tau_{d,i+1} + (1 - \tau_{d,i+1}) \tau_{\ell,i+1} ]^2}
												 {(1 - \tau_{d,i+1})/\rho_{\ell,i+1}} \\
		b_i &=& e_{i+1} = \frac{\tau_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}}
													 {(1 - \tau_{d,i+1}) \rho_{\ell,i+1}} \\
		c_i &=& I_{sky,b}^\downarrow T_{b,i  } (1 - \tau_{b,i  }) (\rho_{\ell,i  } - \tau_{\ell,i. } e_i)\\
		d_i &=& I_{sky,b}^\downarrow T_{b,i+1} (1 - \tau_{b,i+1}) (\tau_{\ell,i+1} - \rho_{\ell,i+1} b_i)
\end{eqnarray}

The boundary conditions 
for the downwelling radiation at the bottom layer, $i=0$, 
and the upwelling radiation at the top layer, $i=N$, are given by

\begin{eqnarray}
		c_0 &=& \rho_{gb} I_{sky,b}^\downarrow T_{b,0} \\
		f_0 &=& \rho_{gd} \\
		d_N &=& I_{sky,d}^\downarrow
\end{eqnarray}

where 
$\rho_{gb}$ [-] is the surface albedo for beam radiation,
$\rho_{gd}$ [-] is the surface albedo for diffuse radiation, and
$I_{sky,d}$ [Wm$^{-2}$] is the diffuse radiation incident on the top of the canopy.

The linear system of equations given in equation \eqref{eqn_sw_linear_system_up}-\eqref{eqn_sw_linear_system_dn}
can be written as

\begin{align}
	\begin{bmatrix}
		1    & -\rho_{gd} &       &        &        &        &        &      \\[.6em]
		-a_0 & 1          & -b_0  &        &        &        &        &      \\[.6em]
		     & -e_1       & 1     & -f_1   &        &        &        &      \\[.6em]
		     &            & -a_1  &  1     & -b_1   &        &        &      \\[.6em]
		     &            &       & \ddots & \ddots & \ddots &        &      \\[.6em]
		     &            &       &        & \ddots & \ddots & \ddots &      \\[.6em]
		     &            &       &        &        & -e_N   & 1      & -f_N \\[.6em]
		     &            &       &        &        &        & 0      & 1    
	\end{bmatrix}
	\begin{bmatrix}
\hspace{5pt}		I_0^\uparrow   \hspace{5pt} \\[.5em]
		I_0^\downarrow    \\[.5em]
		I_1^\uparrow    \\[.5em]
		I_1^\downarrow    \\[.5em]
		\vdots     \\[.5em]
		\vdots     \\[.5em]
		I_N^\uparrow    \\[.5em]
		I_N^\downarrow    
	\end{bmatrix}
	=
	\begin{bmatrix}
	\hspace{5pt}	c_0 \hspace{5pt}   \\[.6em]
		d_0    \\[.6em]
		c_1    \\[.6em]
		d_1    \\[.6em]
		\vdots     \\[.6em]
		\vdots     \\[.6em]
		c_N    \\[.6em]
		d_N    
	\end{bmatrix}
\end{align}

## Absorbed radiative fluxes

The diffuse, $\overrightarrow{I}_{cd,i}$ [Wm$_{ground}^{-2}$], and 
direct beam, $\overrightarrow{I}_{cb,i}$ [Wm$_{ground}^{-2}$], radiation absorbed by the
$i$-th canopy layer is

\begin{eqnarray}
		\overrightarrow{I}_{cd,i} &=& \left( I_i^\downarrow + I_{i-1}^\uparrow \right) (1 - \tau_{d,i})(1 - \omega_{\ell,i}) \\
		\overrightarrow{I}_{cb,i} &=& I_{sky,b}^\downarrow T_{b,i}(1 - \tau_{b,i})(1 - \omega_{\ell,i})
\end{eqnarray}

The radiation absorbed at the ground, $\overrightarrow{I}_{g}$ [Wm$_{ground}^{-2}$], is

\begin{equation}
	\overrightarrow{I}_g = \left( 1 - \rho_{gd} \right) I_0^\downarrow + \left( 1 - \rho_{gb} \right) I_{sky,b}^\downarrow T_{b,0}
\end{equation}

It is assumed that the shaded leaves only absorb diffuse radiation, while sunlit
leaves receive direct and diffuse radiations. The absorbed radiation fluxes by
shaded, $\overrightarrow{I}_{\ell sha, i}$ [Wm$_{leaf}^{-2}$], and 
sunlit, $\overrightarrow{I}_{\ell sun, i}$ [Wm$_{leaf}^{-2}$], is given as


\begin{eqnarray}
		\overrightarrow{I}_{\ell sha, i} &=& \frac{I_{cd,i}}{\Delta L_i} \\[0.5em]
		\overrightarrow{I}_{\ell sun, i} &=& \overrightarrow{I}_{\ell sha, i} 
			+ \frac{\overrightarrow{I}_{cb,i}}{f_{sun,i} \Delta L_i}
\end{eqnarray}

where $f_{sun}$ [-] is the fraction of sunlit leaves at $i$-th layer.

The absorbed canopy fluxes for 
shaded, $\overrightarrow{I}_{cSha}$ [Wm$_{ground}^{-2}$], and
sunlit, $\overrightarrow{I}_{cSun}$ [Wm$_{ground}^{-2}$], are

\begin{eqnarray}
		\overrightarrow{I}_{cSha} &=& \sum_{i=1}^N \overrightarrow{I}_{\ell sha, i} ( 1 - f_{sun}) \Delta L_i 
		= \sum_{i=1}^N I_{cd,i} (1 - f_{sun})\\
		\overrightarrow{I}_{cSun} &=& \sum_{i=1}^N \overrightarrow{I}_{\ell sun, i}       f_{sun}  \Delta L_i
		= \sum_{i=1}^N \left( \overrightarrow{I}_{cd, i} f_{sun} + \overrightarrow{I}_{cb,i}\right)
\end{eqnarray}
