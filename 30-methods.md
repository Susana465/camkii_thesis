---
bibliography: [references.bib]
---
# Methods
**Abstract**
This chapter delves into the methods used to model molecular interactions of interest. Using Monte Carlo algorithm simulations with MCell and CellBlender, I modeled the interactions of initial molecules released inside the cell, including Ca2+, CaM, CaMKII, PP1, and NMDARs on the cell surface. The binding dynamics of calcium to calmodulin and subsequent interactions with CaMKII ware examined, alongside the states of CaMKII (open/closed, active/inactive) and the phosphorylation processes of CaMKII. 

The results should highlight the importance of CaM binding to CaMKII, and NMDARs, and its regulation through phosphorylation, as well as the role of these interactions in maintaining the phosphorylated state of CaMKII within the postsynaptic density.

## Model validation

The processes used in software development can also apply to biological model development. Following @husar2022MCell4, four key points were considered for this project:

1.	Incremental model development: build the model step by step on validated foundations.

2.	Modularity: create self-contained, reusable libraries

3.	Unit testing and validation: ensure parts of the model behave as expected.

4.	Human-readable code: store using version control such as git for easy review by team members. 

What have pharris, ordyan and other people done and how does my model relate and differ.

## Model description

I have constructed the models at different scales to validate CaMKII interactions with other molecules like calmodulin and NMDARs, at increasing levels of complexity. First I re-created a model of CaMKII as a monomer that was previously completed in 2017. The model created uses cBNGL and represents CaMKII as monomers to serve as a proof of concept as well as a starting validation point, as dynamics of this model were previously shown to be within biologically accurate limits. Secondly, I created a model of CaMKII as a hexamer since modelling this molecule as a dodecamer gave rise to a combinatorial explosion due to the high number of possible states and the network of interactions generated. This is currently in the works of being resolved as I run the model using the network-free simulation using MCell. We will then be able to model CaMKII as a dodecamer. Finally, I aim to validate this work against a model from @ordyan2020Interactions, where they successfully modelled CaMKII as a twelve subunit holoenzyme using BioNetGen simulations. 

## Model creation and visualization in CellBlender

I began the model of CaMKII monomers as described in the 2017 model I created using MCell and CellBlender. At the time, MCell did not allow for molecules be modelled as multi-complexes. Thus, for example, one phosphorylated CaMKII molecule in the model was just a single subunit phosphorylated –not twelve phosphorylated subunits. This model includes Ca2+ binding rates to CaM, CaM binding rates to monomeric CaMKII, and phosphorylation rates of active CaMKII monomers by one another, all depending on how many Ca2+ ions are bound to the CaM molecules involved. CaMKII dephosphorylation by PP1 is modelled, as well as binding interactions of CaMKII with NMDARs. In order to replicate and validate the results obtained from the CaMKII monomer in 2017, I re-wrote all reactions into a cBNGL model using the same parameters used originally. We define a volume previously modelled of 0.5μm3, which is within ranges of spine volume of 0.004 to 0.6 μm3 in hippocampal CA1 neurons (Harris and Stevens, 1989). Using cBNGL, I can specify the above mentioned 3D volume, with a 2D surface compartment acting as the cell membrane, where NMDARs can diffuse. Inside the cell volume, all of the interacting molecules are released as per table 1.


## How are these interactions modelled?
Initial molecules released inside the cell are: Ca2+, CaM, CaMKII, and PP1, inside the cytosol, and NMDARs as cell surface molecules. Since four calcium ions are needed to fully saturate CaM (CaM_Ca4) [REFERENCES], five times more calcium than CaM and CaMKII was released to ensure it would not be a limiting factor [TABLE REFERENCE]. 


#### Binding of calcium to calmodulin
CaM can bind one, two, three, and four calcium ions progressively. 

#### Binding of calmodulin to CaMKII
- Saturated CaM_Ca4 binds to CaMKII ring, T306 needs to be unphosphorylated
-> 5.1 CaMKII + CaM_Ca4 < - > CaMKII_CaM 
_In addition, CaMKII can be made insensitive to Ca2+/CaM by autophosphorylation at T305/T306 located within the Ca2+/CaM binding site [23],[24], a process that is facilitated by interaction with the membrane associated guanylate kinase (MAGUK/CASK) [25],[26]. The balance between the Ca2+/CaM-sensitive and -insensitive CaMKII pool is critical for the regulation of post-synaptic plasticity [27],[28]._

_Moreover, Ca2+/CaM binding to CaMKII with unphosphorylated T306 effectively prevents phosphorylation of this residue [26]. These data are in agreement with our co-crystal structure that showed that both threonine residues (T306/T307) were deeply buried within the Ca2+/CaM complex (Figure 4B)._

_Human CaMKII kinase domains bound Ca2+/CaM with affinities between 1.6 and 3.4×106 Mol−1 (KD: 0.6–0.3 µM)_

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2910593/

The microscopic kon for CaM binding to CaMKII has been measured, using a 215 CaMKII peptide and fluorescently labeled DA-CaM, as 1 × 108 M-1s-1 [50].(Pharris et al.,).

CaM only binds at high affinity to CaMKII, skipping binding at "initially bound", closed CaMKII. 
Can CaM bind if CaMKII is closed? - what do studies say.

#### States of CaMKII
open/closed, active/inactive, docked/undocked.

Active~1 means a subunit is undocked and open.
CaM can only bind if subunit is active.
Pharris is modelling undocked, closed state; but I am modelling flickering directly from docked/closed to undocked/open. Skipping the middle step. 

Can CaMKII close/become inactive if it's phosphorylated?
Electron microscopy of rat alpha-CaMKII in Sf9 cells, as per @myers2017CaMKII, suggests that less than 3 percent of subunits adopt a compact conformation (Figure 6).


#### Phosphorylation of CaMKII

Modelling studies (Lisman, 1985; Miller et al., 2005) have suggested that intersubunit autophosphorylation can maintain the phosphorylated state of the kinase once it is located in the PSD; each subunit is catalytic and, if itself phosphorylated at T286, can phosphorylate T286 on a nearby subunit that might become dephosphorylated (this reaction requires that the substrate subunit has calmodulin bound as a result of basal Ca2+ levels (Hanson et al., 1994)). Recent reconstitution experiments directly demonstrate this mechanism (Urakubo et al., 2014).

 CaMKII phosphorylation
# When CaMKII_CaM, neighbouring subunit, if bound to CaM, can P
	CaMKII(l!1,T286~0,cam!2).CaM(ca~4,camkii!2).CaMKII(r!1,cam!+) -> CaMKII(l!1,T286~P,cam!2).CaM(ca~4,camkii!2).CaMKII(r!1,cam!+) k_pCaM4
# When CaMKII_CaM_P, can phosphorylate neighbouring subunit
  	CaMKII(l!1,T286~0,cam!2).CaM(ca~4,camkii!2).CaMKII(r!1,T286~P) -> CaMKII(l!1,T286~P,cam!2).CaM(ca~4,camkii!2).CaMKII(r!1,T286~P) k_pCaM4_P	

Pharris et al., also do a detransition of different steps for dephosphorylation. In this model we have the requirement that cam be not bound to a camkii subunit but otherwise PP1 can act and dephosorylate directly (we don't have a step for binding of pp1, then dephosphorylation
)
#### Binding of CaMKII to NMDARs

# What have other people done?
Parris model looks at CaMKII dynamics with CaM particularly, uses mcell 

Ordyan looks at CaMKII and NMDARs with mcell and bionetgen but does not look at space dynamics - I think? 