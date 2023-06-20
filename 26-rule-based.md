---
bibliography: [references.bib]
---

# What is rule-based modelling?

An intricate network of protein–protein interactions is a prominent feature of any signal-transduction system @gomperts2009Signal, @hunter2000Signaling. Yet despite the high relevance of modelling site-specific details on protein-protein interactions of signalling systems, there has been a lack of standards for explicitly representing the composition and connectivity of molecular complexes @ezkurdia2009Progress. Models that incorporate complex protein-protein interaction details are generally difficult or impossible to specify and analyse, largely because of the combinatorial number of protein modifications and protein complexes that can be generated through protein–protein interactions. As explained in the Complexity Systems section of this report, this is known as combinatorial complexity which is a common challenge to our understanding of cellular regulation. We will see below how this can be resolved with rule based modelling, and more specifically with BioNetGen tools.

## BioNetGen 

BioNetGen is a set of software tools which facilitate a rule-based approach to modelling biochemical reaction kinetics, where we can largely overcome the problem of combinatorial complexity. BioNetGen language (BNGL) is a formal language which uses the BioNetGen software @faeder2009Rulebased. It allows for site-specific details of protein-protein interactions to be captured in models for the dynamics of these interactions in a systematic fashion, which also alleviates nomenclature and reusability issues. Hence, using this RBM approach is notable as it facilitates writing of multi-state modelling and can significantly, reduce the number of reactions that need to be written due to its “don’t write, don’t care” characteristic. Thereby dramatically improving the ability to model CaMKII as a dodecamer; I can make a model with multistate molecules, and specify the states of the reactants that are relevant for a particular reaction, and leave the rest unspecified. 

## Simple example of RBM using BioNetGen

An example of how RBM and it’s don’t care, don’t write capacity works can be found here, where the reader can access instructions on how to run a rule-based model written in BioNetGen. Additionally, some snippets of how this works in the code can be found below on Figure 9. Likewise, another example is given in Figure 10 which has a similar model with diagrams to explain how BNGL specific binding sites modelling functions. The name “BioNetGen” is a mnemonic for “Biological Network Generator”, but the name does not encompass all the software’s capabilities. The software not only generates reaction networks from rules, but also simulates such networks using different methods. It uses iterative application of rules to a set of seed species, which may be used to generate a network in advance of a simulation; the simulation may subsequently be carried out either by numerically solving ODEs or by implementing SSA approaches (Figure 13). So, for example, using the same model as described in Figure 2, the same model can be simulated using either the SSA or ODE method; these models are available to run online using a jupyter notebook here too. A screenshot for each simulation type can be found below in Figure 11.

[INSERT FIGURE 11 - check how to render ipynb here]


## Compartmental BionetGen

Compartmental BionNetGen is an extension of BNGL to enable explicit modelling of the compartmental organization of the cell and it’s effects on system dynamics (Figure 12). It introduces localization attributes for molecular species, as well as appropriate volumetric scaling of reaction rates. When modelling with BNG, a well-mixed environment is assumed and space has no effect on reactions. Importantly, cBNGL considers the division of the system into well mixed sub-volumes. Counterintuitively, a volume can be specified, which allows for further calculations of molecule concentrations, but it has no real effect on space since BNGL assumes the environment to be well-mixed @harris2009Compartmental. We use cBNGL for describing our multimeric models of CaMKII, so that we can model certain molecules interacting inside a cytoplasm and receptors to be modelled in a plasma membrane. 

## Network generation in BioNetGen
Every time a BNG model runs, a network of reactions can be created. This can be modified through the command “overwrite>1/0” (detailed specification can be found here @faeder2009Rulebased) , which allows you to choose whether you want to overwrite and create or not a new network each time you run the model. In network-based simulations, the full reaction network is enumerated. This is okay for smaller systems without a big number of reactions, but can become a liability when huge networks need to be computed every time the simulation is run, running into the combinatorial explosion problem. On the other hand, network-free simulations, such as the Network-Free Stochastic Simulator (NFsim) that BNG can use (Figure 13), only keeps track of the state of the system that actually exists, not every possible set of reactions (the reaction network). This makes simulating systems with a large reaction network and a high degree of combinatorial complexity not only possible, but also fast. Additionally,  BNG has  an  ”on-the-fly”  capability available for stochastic simulations,  which does not re-quire a pre-existing network and instead generates the full  network  using  the  model  rules  as  the  simulation takes place @faeder2009Rulebased.

## Why are we using Rule-Based Modelling to model CaMKII interactions?

So now that we have the background knowledge on how RBM works, let’s look into how and why I chose to model CaMKII interactions using this approach. Firstly, this way CaMKII can be modelled as a multi-subunit, multi-state complex, defined using BNGL syntax. This syntax allows for explicit representation of individual CaMKII hexamers with distinguishable subunits. 

Each subunit can independently undergo state changes: CaM binding, NMDAR binding, phosphorylation at Thr-286 and flicker between active and inactive state. Each subunit is bound to each other through their “left (l) and right (r) arms” bonds (Figure 14).

[INSERT FIGURE 14]

### CaMKII combinatorial explosion: how do we resolve this?

Even though RBM does help with combinatorial explosion in the ways explained above, CaMKII, even if modelled as a hexamer, can have a very high number of possible states per subunit. To quantify the combinatorial explosion, let’s consider each of the states in which each CaMKII subunit can be found (as per Figure 14). The activation flag can be in one of two states. The T286 phosphorylation site can also have two states. The CaM-binding flag can also be in two states, either be bound or unbound. Same goes for the NMDAR binding site which has two states. This means there is a total of 16 possible state combinations that a single subunit can exhibit.

[EMBED R CODE]
