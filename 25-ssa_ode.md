---
bibliography: [references.bib]
---

#  What are deterministic modelling and stochastic modelling?
As we saw previously, key processes in biological and chemical systems are described by networks of chemical reactions; i.e., all the cascades of interactions between CaMKII with other molecules can be understood as a network of chemical reactions. And, as mentioned above, computational models of these reaction networks can be used to elucidate their dynamics. 

Reaction-based models are formalized as sets of reactions that describe the given system in terms of mechanistic interactions between the species of interest. This is, biochemical networks are a set of chemical species that can be converted into each other through chemical reactions. The focus of biochemical network models is usually on the levels of the chemical species and this usually requires explicit mathematical expressions for the velocity at which the reactions proceed. Biological systems can be simulated in different ways using different algorithms depending on the assumptions made about the underlying kinetics. Once the kinetics have been specified, these systems can be used directly to construct full dynamic simulations of the system behaviour on a computer.

## **Deterministic modelling:**
Deterministic approaches to chemical kinetics are often used to characterize time evolutions of chemical reactions in large systems. A popular representation for these models is to use ordinary differential equations (ODEs) to describe the change in the concentrations of chemical species. Such descriptions are appropriate when the number of particles involved in the biochemical network is large enough to be able to consider continuous concentrations and when spatial effects are negligible, i.e. well-mixed environment is assumed and space has no effect on reactions. In ODE-based models, each chemical species in the network is represented by an ODE that describes the rate of change of that species along time. Therefore, ODE models of biochemical processes are useful and accurate in the high-concentration limit, but often fail to capture stochastic cellular dynamics accurately because the deterministic continuous formulation assumes spatial homogeneity and continuous biomolecule concentrations.

These ODE models can be used to simulate the dynamics of the concentrations of the chemical species along time given their initial values. This is achieved by numerical integration of the system of ODE which can be carried out with well-established algorithms (e.g. simple forward Euler method). They are also useful to find, for example, steady states of the system, which are conditions when the concentrations of the chemical species do not change @maly2009Introduction.

## **Stochastic modelling:**
Another representation that is useful in systems biology is stochastic simulations, which use probability distribution functions to estimate when single reaction events happen and therefore track the number of particles of the chemical species. As a general rule, stochastic simulations are preferred where the numbers of particles of a chemical species is small; the ODE approach is required when the number of particles is large because the stochastic approach might be computationally intractable. When the assumption of continuous concentration fails due to small-scale cellular environment with limited reactant populations, ODE representation also fails. It is here when stochastic simulations are useful. 

[//]: <> (This section about CMEs might delete, not done these references on purpose as need to revisit/reread) 

Chemical stochastic systems are usually represented by a chemical master equation (CME) that describes the time evolution of the probability distribution of discrete molecule quantities, i.e. the CME describes temporal evolution of the probability density function (PDF) for states of a chemical system. PDFs are used to describe the timing of reaction events. This evolution of probability is a continuous time Markov chain, of which any possible realizations can be generated through the Monte Carlo sampling methods. The most famous of these methods for coupled chemical reactions is the stochastic simulation algorithm (SSA) of Gillespie. The theoretical derivation of this method can be found in (Gillespie, 1976)(Gillespie, 1977) as well as a more recent review (Gillespie, 2007).

It is important to stress that one simulation run according to stochastic approaches is only one realization of a probabilistic representation, and thus provides limited amount of information on its own. When running stochastic simulations, it is very important that they are repeated for a sufficient number of times in order to reveal the entire range of behaviour presented by such a system (i.e., to estimate a distribution for each chemical species and its dynamic evolution). An example of what these model runs can look like are shown in Figure 8.

[INSERT FIGURE 8]

