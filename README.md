General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# CTL-phase-diagram

Here we aim at calculating a phase diagram for a polymer solution (polymer volume fraction $\phi$, polymerization degree $N$) using an expression by Flory-Huggins [1] for the dimensionless mixing free energy density

$f_m(\phi) = \frac{1}{N} \phi \ln \phi + (1-\phi) \ln (1-\phi) + \chi \phi (1-\phi)$

where $\chi$ is the so-called Flory-Huggins parameter characterizing the effective strength of attraction between solvent molecules and monomers. While $\phi$ varies in the range $[0,1]$, we here assume $\chi$ to be positive and related to temperature $T$ via 

$\chi = \frac{\Theta}{2T}$

where $\Theta$ is known as $\Theta$-temperature, which we use as a parameter characterizing the chemically detailed monomer-solvent interaction. The $\chi$ parameter is usually assumed to be a constant and available in polymer handbooks for various polymer solutions. An extension of this theory, required to describe thermo-responsive polymers, in particular, allows $\chi$ to be $\phi$-dependent, such as $\chi=\chi_0 + \chi_1 \phi + \chi_2 \phi^2$. 

The phase diagram resulting from $f_m$ is the solution to the following two binodal equations that result from minimizing the free energy of the solution, 

$f_m'(\phi_a) = f_m'(\phi_b) = \frac{f_m(\phi_b)-f_m(\phi_a)}{\phi_b-\phi_a}$

for two unknowns $\phi_a$ and $\phi_b\ge \phi_a$. The prime denotes a derivative with respect to $\phi$. To be more specific, for a given $N$, $\Theta$, and temperature $T$, one is seeking for a solution to the binodal equation. If it has two solutions, there are two volume fractions $\phi_a$ and $\phi_b$ that coexist; the system is phase-separated. If the binodal equations have no solution, the system is homogeneous and not phase-separated. At the so-called critical point, it just has one solution. The binodal equations have a graphical ('common tangent') interpretation: Their two solutions, if they exist, can be connected by a line that is tangential to $f_m(\phi)$ at both $\phi=\phi_a$ and $\phi=\phi_b$.

## def fm($N,\chi,\phi$)

This function returns $f_m(\phi)$ for given $N$, $\chi$, and $\phi$.

## def derivfm($N,\chi,\phi$)

This function returns the derivative $f'_m(\phi)$ for given $N$, $\chi$, and $\phi$. Hint: You can choose if you calculate the derivative analytically, or if you approximate it numerically. 

## def plot_mixing_free_energy($N$)

For given $N$, this routine plots the mixing free energy density $f_m(\phi)$ versus $\phi$ for $\chi=\{0,0.1,0.2,0.5\}$ (use different colors for different $\chi$, add axis labels and a legend). Save the graphics file in png, pdf, or jpg format.

## def common_tangent($N,\chi$)

For given $N$ and $\chi$, this routine finds the 0, 1, or 2 volume fractions ($\phi_a$, $\phi_b$) that solve the binodal equations. It returns the number of different solutions and their values. Hint: During developing such algorithm, it is useful to plot $f_m(\phi)$ together with the obtained solution(s) to see, if the line connecting the solution is indeed a common tangent. To obtain a precise estimate, it could also make sense to first scan over volume fractions using a low resolution, and afterwards increase the solution.

## def calculate_phase_diagram($N,\Theta$)

For given $N$ and $\Theta$ (in units of Kelvin), use the common_tangent routine to find the solutions of the binodal equations for temperatures $T$ in the range between $0$ and $2\Theta$ (in 1 K steps or smaller) and save the values in an ascii file (txt or csv-format) with up to four columns: the first column carries $T$, the second column the number of solutions, the following columns the values of these solutions. Hint: It could be convenient to add another column to this file, a number that says how well the binodal equations are fulfilled. 

## def plot_phase_diagram

Read the ascii file created by calculate_phase_diagram, and plot the phase diagram (add axis labels, save figure as graphics png, pdf, or jpg file). If you can, mark the coexistence region enclosed by the binodals using some color or shading.

## Application 1

Plot the mixing free energy and create a graphics file using plot_mixing_free_energy

## Application 2

For $N=100$ and $\Theta=400$ K, plot the phase diagram. Plot temperature versus the solutions of the binodal equations to obtain the so-called phase diagram. The region enclosed by the two solutions is the coexistence region, outside this region the system does not exhibit phase separation and remains homogeneous. 

## Application 3

For $\Theta=400$, plot the phase diagrams for $N=50, 100, 200, 1000$ into a single figure (add axis labels, legend, different colors for different $N$, save figure as graphics file).

## Application 4

For $N=100$ and $\Theta=400$ K, find the critical temperature $T_c$ and corresponding volume fraction $\phi_c$ for which the binodal equations have just one solution at $\phi=\phi_c$. Compare with the theoretical expectations [1]

$\phi_c=\frac{1}{1+\sqrt{N}}$

and $T_c=\Theta/2\chi_c$ with 

$\chi_c=\frac{1}{2} \left(1+\frac{1}{\sqrt{N}}\right)^2$

## Application 5 (advanced)

Thermo-responsive PNIPAM polymers and their brushes (set $N\rightarrow \infty$, i.e., ignore the first term in the mixing free energy density) have been modeled [2] using a $\phi$-and $T$-dependent $\chi$-parameter of the form

$\chi = -12.947 + 0.044959 \ T/{\rm K} + 17.92 \ \phi - 0.056944 \ \phi T/{\rm K} + 14.814 \ \phi^2 - 0.051419 \ \phi^2 T/{\rm K}$

Ignore the first term in the mixing free energy ($N\rightarrow \infty$), and caculate and plot the phase diagram for a PNIPAM brush. Hint: You should find a critical point at $T_c\approx 288.4$ K.




[1] M. Doi, Introduction to Polymer Physics, Clarendon Press Oxford, U.K., 2006. 

[2] http://dx.doi.org/10.1016/j.biomaterials.2012.03.060
 

