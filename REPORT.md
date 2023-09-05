General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# CTL-phase-diagram

Here we aim at calculating a phase diagram for a polymer solution (polymer volume fraction $\phi$, polymerization degree $N$) using an expression by Flory-Huggins for the dimensionless mixing free energy density

$f_m(\phi) = \frac{1}{N} \phi \ln \phi + (1-\phi) \ln (1-\phi) + \chi \phi (1-\phi)$

where $\chi$ is the so-called Flory-Huggins parameter characterizing the effective strength of attraction between solvent molecules and monomers. While $\phi$ varies in the range $[0,1]$, we here assume $\chi$ to be positive and related to temperature $T$ via 

$\chi = \frac{\Theta}{2T}$

where $\Theta$ is known as $\Theta$-temperature, which we use as a parameter characterizing the chemically detailed monomer-solvent interaction. The $\chi$ parameter is usually assumed to be a constant and available in polymer handbooks for various polymer solutions. An extension of this theory, required to describe thermo-responsive polymers, in particular, allows $\chi$ to be $\phi$-dependent, such as $\chi=\chi_0 + \chi_1 \phi + \chi_2 \phi^2$. 

The phase diagram resulting from $f_m$ is the solution to the following two binodal equations that result from minimizing the free energy of the solution, 

$f_m'(\phi_a) = f_m'(\phi_b) = \frac{f_m(\phi_b)-f_m(\phi_a)}{\phi_b-\phi_a}$

for two unknowns $\phi_a$ and $\phi_b$. To be more specific, for a given $N$, $\Theta$, and temperature $T$, one is seeking for a solution to the binodal equation. If it has a solution, there are two volume fractions $\phi_a$ and $\phi_b$ that coexist; the system is phase-separated. If the binodal equations have no solution, the system is homogeneous and not phase-separated.  

## Task

Design an algorithm that finds the solutions of the binodal equations for $N=100$, $\Theta=300$, and vary $T$ in the range between $0$ and $600$. Plot temperature versus the solutions of the binodal equations to obtain the so-called phase diagram. The region enclosed by the two solutions is the coexistence region, outside this region the system does not exhibit phase separation and remains homogeneous. 

## Critical temperature and critical volume fraction
 

