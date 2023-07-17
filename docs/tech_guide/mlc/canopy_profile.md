The leaf area density (LAD), $a(z)$ [m$^2$ m$^{-3}$], at height $z$ are given by a beta distribution as

\begin{equation}
	a(z) = \left(\frac{L}{h_c}\right) \left( \frac{ (z/h_c)^{p-1} (1 - (z/h_c)^{q-1})}{B(p,q)}\right)
\end{equation}

where
$p$ and $q$ are the shape function of the beta distribution,
$B(p,q)$ is a normalization constant,
$h_c$ is the canopy height.
The total leaf area index (LAI),$L$ [m$^2$ m$^{-2}$] and
the cumulative leaf area index, $L(z)$ [m$^2$ m$^{-2}$], from the top of the canopy
is given as

\begin{align}
	L &=& \int_0^{h_c} a(z) dz \\
	L(z) &=& \int_z^{h_c} a(z) dz
\end{align}

The stem area density (SAD) is also similarly modeled by a beta distribution.
The plant area density (PAD) is the sum of LAD and SAD.
