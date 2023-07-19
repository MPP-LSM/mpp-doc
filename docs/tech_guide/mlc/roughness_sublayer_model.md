## Wind profile above canopy

The wind profile, $u$, above canopy the is given as

\begin{equation}
		\label{eqn_du_dz_above}
		\frac{\kappa (z-d)}{u_*     }\frac{\partial u     }{\partial z} = \Phi_m\left( z \right)
\end{equation}

where $\Phi_m$ [-] is an effective similarity function that is given by

\begin{equation}
		\label{eqn_phi_m}
		\Phi_m(z) = \phi_m \left( \frac{z-d}{L_{MO}}\right) \hat{\phi}_m \left( \frac{z-d}{l_m /\beta }\right)
\end{equation}

\begin{equation}
		u(z) = \frac{u_*}{\kappa} 
									\left[ 
										\ln \left( \frac{z - d}{z_{0m}} \right) 
										- \psi_m\left( \frac{z - d}{L_{MO}} \right)
										+ \psi_m\left( \frac{z_{0m}}{L_{MO}} \right)
										+ \hat{\psi}_m(z)
									\right] 
\end{equation}

where

\begin{equation}
	\label{eqn:wind_profile_rsl_above}
	\hat{\psi}_m = \int_z^\infty \phi_m \left( \frac{z' - d}{L_{MO}} \right)
								\left[ 1 - \hat{\phi}_m \left(\frac{z' -d }{l_m/\beta} \right) \right] 
								\frac{dz'}{z' - d}
\end{equation}

Given equation \eqref{eqn:wind_profile_rsl_above}, the wind at canopy height is given by

\begin{equation}
	\label{eqn:wind_at_hc}
	u_{hc} = \frac{u_*}{\beta}
\end{equation}

\begin{eqnarray}
		u(z)           &=& \frac{u_*}{\kappa} 
									\left[ 
										\ln \left( \frac{z - d}{h_c - d} \right) 
										- \psi_m\left( \frac{z - d}{L_{MO}} \right)
										+ \psi_m\left( \frac{h_c - d}{L_{MO}} \right) \right. \nonumber \\
									 & &
	\label{eqn_u_with_hc}
									 \left.
										+ \hat{\psi_m}(z)
										- \hat{\psi_m}(h_c)
							 		  + \frac{\kappa}{\beta}
									\right] 
\end{eqnarray}


## Wind profile within canopy


HF-2007[@harman2007simple] assumed an exponential wind profile within the canopy that is given as

\begin{equation}
	\label{eqn_du_dz_within}
	u(z) = u(h_c)\exp\left( \frac{z - h_c}{l_m/\beta} \right)
\end{equation}

and the derivative of the wind profile is

\begin{eqnarray}
	\frac{\partial u(z)}{\partial z} &=& \frac{u(h_c)}{l_m/\beta} \exp\left( \frac{z - h_c}{l_m/\beta} \right) \nonumber \\
	                                 &=& \frac{u(z)}{l_m/\beta} 
\end{eqnarray}

\begin{equation}
h_c - d = \frac{l_m}{2\beta} = \beta^2 L_c
\end{equation}

Enforcing the continuity of derivative of wind at canopy height ($h_c$) from
equation \eqref{eqn_du_dz_above} and \eqref{eqn_du_dz_within} leads to

\begin{eqnarray}
	\frac{u_*}{\kappa (h_c - d)} \Phi_m(h_c) &=& \frac{u(h_c)}{l_m/\beta} \nonumber \\
	\Phi_m(h_c) &=& \frac{u(h_c)}{u_*} \times \frac{\kappa (h_c - d)}{l_m/\beta} \nonumber \\
	\Phi_m(h_c) &=& \frac{1}{\beta} \times \frac{\kappa l_m/(2\beta) }{l_m/\beta} \nonumber \\
	\label{eqn_phi_m_at_hc}
	\Phi_m(h_c) &=& \frac{\kappa l_m}{2\beta} 
\end{eqnarray}


## Wind similarity function

For the above canopy wind profile, HF-2007[@harman2007simple] assumed the similarity function for momentum to be

\begin{equation}
 \hat{\phi}_m \left( \frac{z-d}{l_m /\beta} \right) =
 		1 - c_1 \exp \left[ -c_2 \left( \frac{z-d}{l_m/\beta} \right)\right]
\end{equation}

where
$c_1$ and $c_2 (= 0.5)$ are parameters. The parameter $c_1$ is found by evaluating $\hat{\phi}_m$ at $z=h_c$
that gives

\begin{eqnarray}
 \hat{\phi}_m \left( \frac{h_c - d}{l_m /\beta} \right) &=&			1 - c_1 \exp \left[ -c_2 \left( \frac{h_c-d}{l_m/\beta} \right)\right] \nonumber \\
 &=& 1 - c_1 \exp \left[ -c_2 \left( \frac{l_m/(2\beta)}{l_m/\beta} \right)\right] \nonumber \\
 &=& 1 - c_1 \exp \left( -0.5c_2\right) \nonumber \\
 c_1		&=& \left[ 1 - \hat{\phi}_m \left( \frac{h_c - d}{l_m /\beta} \right)\right] \exp (0.5c_2)
\end{eqnarray}

In order to compute $c_1$ from the above equation, an expression of $\hat{\phi}_m$ at $z = h_c$ is needed,
which is obtained using equation \eqref{eqn_phi_m} at $z = h_c$ and equation \eqref{eqn_phi_m_at_hc} as

\begin{equation}
	\hat{\phi}_m \left( \frac{h_c-d}{l_m/\beta}\right) = \frac{\kappa}{2\beta} \phi_m^{-1} \left( \frac{h_c-d}{L_{MO}}\right)
\end{equation}

## Wind beta term

The critical unknown in the roughness sublayer parameterization is $\beta$. 
HF-2007[@harman2007simple] derived an expression for $\beta$ as

\begin{equation}
	\beta \phi_m \left( \frac{h_c - d}{L_{MO}} \right) = \beta_N
\end{equation}

or

\begin{equation}
	\label{eqn_beta}
	\beta \phi_m \left( \frac{\beta^3 L_c}{L_{MO}} \right) = \beta_N
\end{equation}

The solution of equation \eqref{eqn_beta} depends on if $\phi$ is evaluated for unstable or stable condition
and leads to following equations

\begin{eqnarray}
	(\beta^2)^2 + 16 \frac{L_c}{L_{MO}}\beta^4\beta^2 - \beta_N^4 &=& 0  L_{MO} < 0 \\
	5 \frac{L_c}{L_{MO}} \beta^3 + \beta - \beta_N &=& 0  L_{MO} \geq 0
\end{eqnarray}

The correct solution is the larger root for the sable condition, while the
unstable case has only one real root.

## Temperature profile

Similar to the equations for wind profiles, the equations describing profiles
of heat (or scalar) above and within the canopy are given below.

\begin{eqnarray}
		\label{eqn_theta_du_dz_1}
		\frac{\kappa (z-d)}{\theta_*}\frac{\partial \theta}{\partial z} &=& \Phi_c\left( z \right) \\		
		\Phi_c(z) &=& \phi_c \left( \frac{z-d}{L_{MO}}\right) \hat{\phi}_c \left( \frac{z-d}{l_m /\beta }\right) \\
		\theta(z) - \theta_s &=& \frac{\theta_*}{\kappa} 
									\left[ 
										\ln \left( \frac{z - d}{z_{0c}} \right) 
										- \psi_m\left( \frac{z - d}{L_{MO}} \right)
										+ \psi_m\left( \frac{z_{0c}}{L_{MO}} \right)
										+ \hat{\psi}_c(z)
									\right] 
\end{eqnarray}

where

\begin{equation}
	\hat{\psi}_c = \int_z^\infty \phi_c \left( \frac{z' - d}{L_{MO}} \right)
								\left[ 1 - \hat{\phi}_c \left(\frac{z' -d }{l_m/\beta} \right) \right] 
								\frac{dz'}{z' - d}
\end{equation}

An exponential profile of air temperature is assumed within the canopy that is given by
\begin{equation}
	\theta(z) - \theta_s = (\theta(h_c) - \theta_s) \exp\left[ \frac{f(z - h_c)}{l_m/\beta} \right]
\end{equation}

where parameter $f$ relates the length scale of heat (scalar) to that of momentum and is given by

\begin{equation}
	f = \frac{1}{2} (1 + 4r_c\text{Pr})^{1/2} - \frac{1}{2}
\end{equation}

and

\begin{equation}
	\text{Pr} = 0.5 + 0.3\tanh(2L_c/L_{MO})
\end{equation}

The derivatives of the profile within the canopy is

\begin{equation}
	\label{eqn_theta_du_dz_2}
	\frac{\partial \theta (z)}{\partial z} = \frac{(\theta(h_c) - \theta_s) f}{l_m/\beta}\exp\left[ \frac{f(z - h_c)}{l_m/\beta} \right]
\end{equation}

Enforcing continuity of derivative at $z = h_c$ using equation \eqref{eqn_theta_du_dz_1} and \eqref{eqn_theta_du_dz_2}

\begin{equation}
	\left. \frac{\partial \theta}{\partial z}\right|_{z=h_c} = \frac{\theta_*}{\kappa (h_c - d)}\Phi_c(h_c) = \frac{f[\theta(h_c) -\theta_s]}{l_m/\beta}
\end{equation}

so that

\begin{equation}
	\frac{\theta(h_c) - \theta_s}{\theta_*} = \frac{\text{Pr}}{f\beta}
\end{equation}

An equation similar to equation \eqref{eqn_u_with_hc} can be written for $\theta$

\begin{eqnarray}
		\theta(z) - \theta_s        &=& \frac{\theta_*}{\kappa} 
									\left[ 
										\ln \left( \frac{z - d}{h_c - d} \right) 
										- \psi_c\left( \frac{z - d}{L_{MO}} \right)
										+ \psi_c\left( \frac{h_c - d}{L_{MO}} \right)
										\right. \nonumber \\
	\label{eqn_q_with_hc}
										& & \left.
										+ \hat{\psi_c}(z)
										- \hat{\psi_c}(h_c)
							 		  + \frac{\kappa\text{Pr}}{f\beta}
									\right] 
\end{eqnarray}

For the above canopy wind profile, HF-2007[@harman2007simple] assumed the similarity function for momentum to be

\begin{equation}
 \hat{\phi}_c \left( \frac{z-d}{l_m /\beta} \right) =
 		1 - c_1 \exp \left[ -c_2 \left( \frac{z-d}{l_m/\beta} \right)\right]
\end{equation}

\begin{eqnarray}
 c_1 &=& 
 				\left[ 1 - \hat{\phi}_c \left( \frac{h_c - d}{l_m /\beta} \right)\right] \exp (0.5c_2) \\
\hat{\phi}_c \left( \frac{z-d}{l_m/\beta}\right) &=& 
		\frac{\kappa \text{Pr}}{2\beta} \phi_c^{-1} \left( \frac{z-d}{L_{MO}}\right)
\end{eqnarray}


## Aerodynamic conductance

The aerodynamic conductances for scalar, $g_{ac}$, is given as

\begin{equation}
	\frac{1}{g_{ac}} = \int_{z_1}^{z_2} \frac{dz}{\rho_m K_c}
\end{equation}

where $K_c$ is the eddy diffusivity for scalar based on K-theory. 
The aerodynamic conductance above canopy is

\begin{equation}
	g_{am,i+1/2} = \rho_m \kappa^2 u_*
							\left[
										\ln \left( \frac{z_{i+1} - d}{z_i - d} \right) +
										\psi_{i+1} - \psi_i
							\right]^{-1}
\end{equation}
where

\begin{equation}
	\psi_i = 
											- \psi_c\left( \frac{z_i - d}{L_{MO}} \right)
										+ \psi_c\left( \frac{h_c - d}{L_{MO}} \right)
										+ \hat{\psi_c}(z_i)
										- \hat{\psi_c}(h_c)
\end{equation}

The aerodynamic conductance within canopy is

\begin{equation}
	g_{ac,i+1/2} = \frac{\rho \beta u_*}{\text{Pr}}
								\left[ 
									\exp
										\left( 
											\frac{-(z_{i+1}-h_c)}{l_m/\beta} 
										\right) 
										-
										\left( 
											\frac{-(z_i-h_c)}{l_m/\beta} 
										\right) 
								\right]^{-1}
\end{equation}



