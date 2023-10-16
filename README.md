General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# CTL-phase-diagram

Here we aim at calculating a phase diagram for a polymer solution (polymer volume fraction $\phi$, polymerization degree $N$) using an expression by Flory-Huggins [1] for the dimensionless mixing free energy density

$f_m(\phi) = \frac{1}{N} \phi \ln \phi + (1-\phi) \ln (1-\phi) + \chi \phi (1-\phi)$

where $\chi$ is the so-called Flory-Huggins parameter characterizing the effective strength of attraction between solvent molecules and monomers. While $\phi$ varies in the range $[0,1]$, we here assume $\chi$ to be positive and related to temperature $T$ via 

$\chi = \frac{\Theta}{2T}$

where $\Theta$ is known as $\Theta$-temperature, which we use as a parameter characterizing the chemically detailed monomer-solvent interaction. The $\chi$ parameter is usually assumed to be a constant and available in polymer handbooks for various polymer solutions. An extension of this theory, required to describe thermo-responsive polymers, in particular, allows $\chi$ to be $\phi$-dependent, such as $\chi=\chi_0 + \chi_1 \phi + \chi_2 \phi^2$. 

The phase diagram resulting from $f_m$ is the solution to the following two binodal equations that result from minimizing the free energy of the solution, 

$f_m'(\phi_a) = f_m'(\phi_b) = \frac{f_m(\phi_b)-f_m(\phi_a)}{\phi_b-\phi_a}$

for two unknowns $\phi_a$ and $\phi_b\ge \phi_a$. The prime denotes a derivative with respect to $\phi$. To be more specific, for a given $N$, $\Theta$, and temperature $T$, one is seeking for solutions to the binodal equations. If they have two (different) solutions, there are two volume fractions $\phi_a$ and $\phi_b$ that coexist; the system is phase-separated. If the binodal equations have no solution, the system is homogeneous and not phase-separated. At the so-called critical point, it just has one solution. The binodal equations have a graphical ('common tangent') interpretation: Their two solutions, if they exist, can be connected by a line that is tangential to $f_m(\phi)$ at both $\phi=\phi_a$ and $\phi=\phi_b$. With $\phi_a$ and $\phi_b$ at hand, one can tell how much volume within a polymer solution that has been prepared using a polymer volume fraction $\phi$ is occupied by the polymer-richer phase. Within this polymer-rich phase, the polymer volume fraction is $\phi_b$, and the corresponding volume is $(\phi_b-\phi)/(\phi_b-\phi_a)$ times the total volume of the polymer solution.

Another property of relevance for applications is the location of the spinodal. It is enclosed by the binodal and meets it at the critical point. The equation determining the spinocal volume fractions $\phi_a^{(s)}$ and $\phi_b^{(s)}$ reads

$f_m''(\phi_a^{(s)}) = f_m''(\phi_b^{(s)}) = 0$

Solving these equations is usually much simpler than solving the binodal equations. The idea of this project is to determine both spinodals and binodals using the above expression for $f_m(\phi)$, which is parameterized by polymerization degree $N$ and interaction parameter $\chi$, but make sure that the code also works if the expression for $f_m(\phi)$ is replaced by another function, so that it can be used in practise. 

Please use the following functions to structure your code. The functions are followed by tasks.  

## def fm(*N,chi,phi*)

This function returns $f_m(\phi)$ for given $N$, $\chi$ (chi), and $\phi$ (phi).

## def derivfm(*N,chi,phi*)

This function returns the derivative $f'_m(\phi)$ for given $N$, $\chi$, and $\phi$. Hint: You can choose if you calculate the derivative analytically (symbolically), or if you approximate it numerically. 

## def plot_mixing_free_energy(*N*)

For given $N$, this routine plots the mixing free energy density $f_m(\phi)$ versus $\phi$ for $\chi=\{0,0.1,0.2,0.5\}$ (use different colors for different $\chi$, add axis labels and a legend). Save the graphics file in png, pdf, or jpg format.

## def find_spinodal(*N,chi*)

For given $N$ and $\chi$, this routine finds the 0, 1, or 2 volume fractions ($\phi_a^{(s)}$, $\phi_b^{(s)}$) that solve the spinodal equations. It returns the number of different solutions and their values. Hint: During developing such algorithm, it is useful to plot $f'_m(\phi)$ together with the obtained solution(s) to see, if the solutions are indeed extrema of this function. The goal is to obtain volume fractions whose error is below 0.001. 

## def find_binodal(*N,chi*)

For given $N$ and $\chi$, this routine finds the 0, 1, or 2 volume fractions ($\phi_a$, $\phi_b$) that solve the binodal equations. It returns the number of different solutions and their values. Hint: During developing such algorithm, it is useful to plot $f_m(\phi)$ together with the obtained solution(s) to see, if the line connecting the solution is indeed a common tangent. To obtain a precise estimate, it could also make sense to first scan over volume fractions using a low resolution, and afterwards increase the solution.

## def calculate_phase_diagram(*N,Theta*)

For given $N$ and $\Theta$ (Theta) (in units of Kelvin), use the find_binodal routine to find the solutions of the binodal equations for temperatures $T$ in the range between $0$ and $2\Theta$ (in 1 K steps or smaller) and save the values in an ascii file (txt or csv-format) with up to four columns: the first column carries $T$, the second column the number of solutions, the following columns the values of these solutions. Hint: It could be convenient to add another column to this file, a number that says how well the binodal equations are fulfilled. An analogous routine should be added for the spinodal.  

## def plot_phase_diagram

Read the ascii file created by calculate_phase_diagram, and plot the phase diagram (add axis labels, save figure as graphics png, pdf, or jpg file). If you can, mark the coexistence region enclosed by the binodals using some color or shading.

## Application 1

Plot the mixing free energy and create a graphics file using plot_mixing_free_energy

## Application 2

For $N=100$ and $\Theta=400$ K, plot the phase diagram. Plot temperature versus the solutions of the binodal equations (solid lines) and spinodal equations (dashed lines) to obtain the so-called phase diagram. The region enclosed by the two binodal $\phi_a$ and $\phi_b$ is the coexistence region, outside this region the system does not exhibit phase separation and remains homogeneous. 

## Application 3 

For $\Theta=400$, plot the phase diagrams for different polymerization degrees $N=50, 100, 200, 1000$ into a single figure (add axis labels, legend, different colors for different $N$, save figure as graphics file).

## Application 4

For $N=100$ and $\Theta=400$ K, find the critical temperature $T_c$ and corresponding volume fraction $\phi_c$ for which the binodal equations have just one solution at $\phi=\phi_c$. Compare with the theoretical expectations [1]

$\phi_c=\frac{1}{1+\sqrt{N}}$

and $T_c=\Theta/2\chi_c$ with 

$\chi_c=\frac{1}{2} \left(1+\frac{1}{\sqrt{N}}\right)^2$

This application may be best implemented by first creating a new def obtain_critical_point($N,\chi$). You are free to invent a method to find the critical volume fraction $\phi_c$ and the corresponding critical $\chi_c$, but note, that $\phi_c$ and $\chi_c$ are the solutions to the two equations $f_m''(\phi_c)=f_m'''(\phi_c)=0$. 

## Application 5

Thermo-responsive PNIPAM polymers and their brushes (set $N\rightarrow \infty$, i.e., ignore the first term in the mixing free energy density) have been modeled [2] using a $\phi$-and $T$-dependent $\chi$-parameter of the form

$\chi(\phi,T) = -12.947 + 0.044959 \ T/{\rm K} + 17.92 \ \phi - 0.056944 \ \phi T/{\rm K} + 14.814 \ \phi^2 - 0.051419 \ \phi^2 T/{\rm K}$

which is very different from the above $\chi=\Theta/2T$ form.

Ignore the first term in the mixing free energy ($N\rightarrow \infty$), and calculate and plot the phase diagram for a PNIPAM brush. Hint: You should find a critical point at $T_c\approx 288.4$ K. Discuss the result and compare with the result for a polymer solution described by the unmodified Flory-Huggins theory. 


# Theoretical background information

The binodal equations and the expression for $f_m(\phi)$ can actually be derived for a polymer solution using basic concepts of statistical physics that I am going to review here, based on [1]. First of all, for a system contained in fixed total volume *V*, at fixed temperature *T*, and fixed material amount, a system tends to minimize its total Helmholtz free energy *F*. The total free energy *F=E-TS* is the difference between total internal energy *E* (arising from interactions between particles) and entropy *S=k<sub>B</sub> ln(W)* (arising from the number of configurations *W* a system can explore at this *E*), where *T* denotes temperature. If the system has one state (*W<sub>0</sub>=1*) with very low internal energy *E<sub>0</sub>*, *S<sub>0</sub>=k<sub>B</sub> ln(W<sub>0</sub>)=0*, and ten (*W<sub>1</sub>=10*) other states with a higher internal energy *E<sub>1</sub> > E<sub>0</sub>*, *S<sub>1</sub>=k<sub>B</sub> ln(W<sub>1</sub>)* &gg; *0*, the system might tend to prefer in the states with *E<sub>1</sub>*, when *F<sub>1</sub>=E<sub>1</sub>-T S<sub>1</sub> < F<sub>2</sub>*. Flory and Huggins imagined a polymer solution to be represented by a regular lattice where each cell can be either occupied by a monomer or occupied by a solvent particle, assuming that monomers have the size of a solvent particle (water molecule, for example). Further assuming that the energy cost &epsilon;<sub>pp</sub> for a monomer-monomer pair of cells is different from the energy cost &epsilon;<sub>ps</sub> for a monomer-solvent pair, and that energy cost for a solvent-solvent pair is &epsilon;<sub>ss</sub>, and moreover assuming that the probability to find a monomer cell next to a solvent cell is the volume fraction &phi; of monomers, they wrote down an expression for the internal energy of a system 

$E = -6V \left[\frac{\epsilon_{\rm pp}}{2}\phi^2 + \epsilon_{\rm ps} \phi(1-\phi) + \frac{\epsilon_{\rm ss}}{2} (1-\phi)^2\right]$

To calculate *W* they counted the number of polymer configurations one can generate on a lattice (volume *V*) for a given &phi; and a given polymerization degree *N*. The result is a lengthy expression for *W* as function of &phi; and *N*. With this expression at hand one can write down *F=E-k<sub>B</sub>T ln(W)* which can be regarded as a function of two quantities: *V* and &phi; and one writes *F(V,&varphi;)*. Coming back to the polymer solution, there are now two possibilities: either the polymer likes the solvent, and they tend to mix (the whole volume *V* then carries a homogeneous polymer solution at the user-supplied polymer volume fraction &varphi;), or (ii) they do not like each other and tend to separate into different regions of the system. If one denotes the volumes of the two regions by *V<sub>1</sub>* and *V<sub>2</sub>=V-V<sub>1</sub>*, and the polymer volume fractions in these different regions by &varphi;<sub>1</sub> and &varphi;<sub>2</sub>, the goal is to minimize the total free energy *F<sub>1</sub>+F<sub>2</sub>* with respect to &varphi;<sub>1</sub> and &varphi;<sub>2</sub>. To this end Flory and Huggins wrote *F(V,&varphi;)* as a sum of free energies of the pure phases and a mixing term *F<sub>m</sub>*, i.e., 

$F(V,\phi) = F(V\phi,1)-F((1-\phi)V,0)+F_m(V,\phi)$

where this equation actually defines *F<sub>m</sub>(V,&varphi;)*. The result is *F<sub>m</sub>(V,&varphi;)=Vk<sub>B</sub>Tf<sub>m</sub>(&varphi;)* with the above *f<sub>m</sub>(&varphi;)*. It contains only a combination of the pair-energies, giving rise to the Flory-Huggins parameter *&chi;=3[&epsilon;<sub>pp</sub>+&epsilon;<sub>ss</sub>-2&epsilon;<sub>ss</sub>]/k<sub>B</sub>T*. Now requiring that $\partial F/\partial \phi_1 = 0$ and $\partial F/\partial \phi_2=0$ as required for a minimum of *F* a straightforward calculation [1] yields the two binodal equations stated above for the two unknowns &varphi;<sub>1</sub> and &varphi;<sub>2</sub>. Because *f<sub>m</sub>* contains the parameter &chi; inversely proportional to temperature *T*, there is either no solution to the binodal equations, or two solutions (or one solution at the critical point). The phase diagram usually shows the binodal solutions (horizontal axis) versus the temperature (vertical axis). For a given temperature, if one adds a certain volume fraction &varphi; of polymer to the solution which is is within the interval [*&varphi;<sub>1</sub>,&varphi;<sub>2</sub>*], the system will phase-separate and achieve the two different volume fractions in two disjunct regions of the system. If *&varphi;* is beyond this region, the components will mix. 

The spinodal volume fractions *&varphi;<sub>1</sub>* and *&varphi;<sub>2</sub>* solving $\partial f_m/\partial^2 \phi=0$ can be regarded as an approximation to the binodal. At the critical point the spinodal meets the binodal. The solution to the binodal equations can be graphically obtained from *f<sub>m</sub>(&varphi;)* via a common tangent construction, or from its derivative *f'<sub>m</sub>(&varphi;)* via an equal area construction.  


[1] M. Doi, Introduction to Polymer Physics, Clarendon Press Oxford, U.K., 2006. 

[2] http://dx.doi.org/10.1016/j.biomaterials.2012.03.060
 

