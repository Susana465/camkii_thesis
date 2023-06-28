---
bibliography: [references.bib]
---
# Methods

## Model validation

The same processes used in software development can also be applied to biological model development. Therefore, when developing the models in this project, four main points were considered throughout, as suggested by @husar2022MCell4:

1.	Create incremental development where the model is built step by step, relying on solid foundations of modelling done and validated before, 

2.	Create a modularity that provides the capability to create self-contained, reusable libraries,

3.	Perform unit testing and validation to verify that parts of the model behave as expected and,

4.	Create human-readable and writable model code that can be stored using git or other code version control software which also allows code reviews so that other team members can inspect the latest changes to the model.

## Model description

I have constructed the models at different scales to validate CaMKII interactions with other molecules like calmodulin and NMDARs, at increasing levels of complexity. First I re-created a model of CaMKII as a monomer that was previously completed in 2017. The model created uses cBNGL and represents CaMKII as monomers to serve as a proof of concept as well as a starting validation point, as dynamics of this model were previously shown to be within biologically accurate limits. Secondly, I created a model of CaMKII as a hexamer since modelling this molecule as a dodecamer gave rise to a combinatorial explosion due to the high number of possible states and the network of interactions generated. This is currently in the works of being resolved as I run the model using the network-free simulation using MCell. We will then be able to model CaMKII as a dodecamer. Finally, I aim to validate this work against a model from @ordyan2020Interactions, where they successfully modelled CaMKII as a twelve subunit holoenzyme using BioNetGen simulations. 

## Model creation and visualization in CellBlender

I began the model of CaMKII monomers as described in the 2017 model I created using MCell and CellBlender. At the time, MCell did not allow for molecules be modelled as multi-complexes. Thus, for example, one phosphorylated CaMKII molecule in the model was just a single subunit phosphorylated –not twelve phosphorylated subunits. This model includes Ca2+ binding rates to CaM, CaM binding rates to monomeric CaMKII, and phosphorylation rates of active CaMKII monomers by one another, all depending on how many Ca2+ ions are bound to the CaM molecules involved. CaMKII dephosphorylation by PP1 is modelled, as well as binding interactions of CaMKII with NMDARs. In order to replicate and validate the results obtained from the CaMKII monomer in 2017, I re-wrote all reactions into a cBNGL model using the same parameters used originally. we define a volume previously modelled of 0.5μm3, which is within ranges of spine volume of 0.004 to 0.6 μm3 in hippocampal CA1 neurons (Harris and Stevens, 1989). Using cBNGL, I can specify the above mentioned 3D volume, with a 2D surface compartment acting as the cell membrane, where NMDARs can diffuse. Inside the cell volume, all of the interacting molecules are released as per table 1.


