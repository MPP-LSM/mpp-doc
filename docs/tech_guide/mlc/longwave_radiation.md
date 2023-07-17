## Governing equations

The downwelling, $L_{i}^\downarrow$ [Wm$^{-2}$], and upwelling $L_{i+1}^\uparrow$ [Wm$^{-2}$], longwave radiation can
be similarly described as the shortwave radiation model by replacing the direct beam
scattering term with a thermal radiation source term as

\begin{eqnarray}
	L_{i  }^{\downarrow} & = &   L_{i+1  }^{\downarrow} \left[ \mathcal{\tau}_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}\right] 
  	                  + L_{i    }^{\uparrow}                       (1 - \tau_{d,i+1})\rho_{\ell,i+1} \nonumber \\
    	          &  &  + \varepsilon_\ell \sigma T_{\ell,i+1}^4 (1 - \tau_{d,i+1}) \\
	L_{i+1}^{\uparrow} & = &  L_{i    }^{\uparrow} \left[ \tau_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}\right] 
  	                  + L_{i+1  }^{\downarrow}                       (1 - \tau_{d,i+1})\rho_{\ell,i+1} \nonumber \\
    	          &  &  + \varepsilon_\ell \sigma T_{\ell,i+1}^4 (1 - \tau_{d,i+1})
\end{eqnarray}

where $\varepsilon_{\ell}$ [-] is the leaf emissivity and
$T_\ell$ [K] is the leaf temperature.
If sunlit and shaded leaves are modeled explicitly,
an effective leaf temperature is defined based on the
sunlit and shaded leaf fraction.

## Linear system

The linear system of equations for the longwave model can be written as

\begin{align}
	\begin{bmatrix}
		1    & -(1-\varepsilon_{g}) &       &        &        &        &        &      \\[.6em]
		-a_0 & 1                    & -b_0  &        &        &        &        &      \\[.6em]
		     & -e_1                 & 1     & -f_1   &        &        &        &      \\[.6em]
		     &                      & -a_1  &  1     & -b_1   &        &        &      \\[.6em]
		     &                      &       & \ddots & \ddots & \ddots &        &      \\[.6em]
		     &                      &       &        & \ddots & \ddots & \ddots &      \\[.6em]
		     &                      &       &        &        & -e_N   & 1      & -f_N \\[.6em]
		     &                      &       &        &        &        & 0      & 1    
	\end{bmatrix}
	\begin{bmatrix}
		L_0^\uparrow   \hspace{5pt} \\[.5em]
		L_0^\downarrow    \\[.5em]
		L_1^\uparrow    \\[.5em]
		L_1^\downarrow    \\[.5em]
		\vdots     \\[.5em]
		\vdots     \\[.5em]
		L_N^\uparrow    \\[.5em]
		L_N^\downarrow    
	\end{bmatrix}
	=
	\begin{bmatrix}
	    c_0 \hspace{5pt}   \\[.6em]
		d_0    \\[.6em]
		c_1    \\[.6em]
		d_1    \\[.6em]
		\vdots     \\[.6em]
		\vdots     \\[.6em]
		c_N    \\[.6em]
		d_N    
	\end{bmatrix}
\end{align}

where

\begin{eqnarray}
		a_i &=& f_{i+1} = (1-\tau_{d,i+1})\rho_{\ell,i+1} - 
										\frac{[\tau_{d,i+1} + (1 - \tau_{d,i+1}) \tau_{\ell,i+1} ]^2}
												 {(1 - \tau_{d,i+1})/\rho_{\ell,i+1}} \\[1em]
		b_i &=& e_{i+1} = \frac{\tau_{d,i+1} + (1 - \tau_{d,i+1})\tau_{\ell,i+1}}
													 {(1 - \tau_{d,i+1}) \rho_{\ell,i+1}} \\[1em]
		c_i &=& (1 - e_i)(1 - \tau_{d,i  }) \varepsilon_\ell \sigma T_{\ell,i  }^4 \\[1em]
		d_i &=& (1 - b_i)(1 - \tau_{d,i+1}) \varepsilon_\ell \sigma T_{\ell,i+1}^4
\end{eqnarray}

The boundary conditions for the downwelling radiation at the bottom layer, $i=0$, and
the upwelling radiation at the top layer, $i=N$, are given as

\begin{eqnarray}
		c_0 &=& \varepsilon_{g} \sigma T_g^4 \\
		d_N &=& L_{sky}^\downarrow
\end{eqnarray}

where 
$\varepsilon_g$ [-] is ground surface emissivity,
$T_g$ [K] is the ground surface temperature, and
$L_{sky}^\downarrow$ [Wm$^{-2}$] is incident longwave radiation at the top of the canopy.

## Absorbed fluxes

The net longwave flux absorbed per unit ground area, $\overrightarrow{L}_i$ [Wm$_{ground}^{-2}$], and
per unit leaf area, $\overrightarrow{L}_{\ell,i}$ [Wm$_{leaf}^{-2}$], by the $i$-th layer are

\begin{eqnarray}
		\overrightarrow{L}_i &=& \varepsilon_{\ell} \left( L_i^\downarrow + L_{i-1}^\uparrow \right) (1 - \tau_{d,i})
			- 2 \varepsilon_\ell \sigma T_{\ell,i}^4 (1 - \tau_{d,i}) \\[.2em]
		\overrightarrow{L}_{\ell,i} &=& \frac{\overrightarrow{L}_i}{\Delta L_i}
\end{eqnarray}

The radiation absorbed by the canopy, $\overrightarrow{L}_{c}$ [Wm$_{ground}^{-2}$], and
the ground, $\overrightarrow{L}_{g}$ [Wm$_{ground}^{-2}$], is given by

\begin{eqnarray}
		\overrightarrow{L}_c &=& \sum_{i=1}^{N} \overrightarrow{L}_c  \\[.2em]
		\overrightarrow{L}_{g} &=& \varepsilon_g L_0^\downarrow - \varepsilon_g \sigma T_g^4
\end{eqnarray}
