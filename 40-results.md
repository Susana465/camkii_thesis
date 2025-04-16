---
bibliography: [references.bib]
lightbox: true
---

# Results and discussion of results

Following a preliminary sensitivity analysis (can I/should I do statistical methods?) [REFERENCE SECTION], and initial model validation [REFERENCE SECTION], three principal model versions of the CaMKII/NMDAR model have been developed. The first is a wild-type (WT) model, as described in @sec-model-description. In addition, two mutant (MT) models were constructed: one in which CaMKII is unable to undergo autophosphorylation, and another in which CaMKII cannot bind to NMDARs. These mutations were implemented by setting the reaction rates corresponding to CaMKII autophosphorylation and CaMKII–NMDAR binding, respectively, to zero.

## Wild-type model

In the WT model (described in detail in @sec-model-description), a release of 1000 calcium ions occurs within a dendritic spine volume of 0.50588 $\mu\text{M}$.  This calcium subsequently binds to CaM, which can bind up to four calcium ions. Full saturation of CaM is required for subsequent binding to CaMKII, resulting in the formation of the CaMKII–CaM complex (CaMKII_CaM_Ca4).

This progression is illustrated in [@fig-calcium-binding], where the gradual formation of partially and fully calcium-bound CaM species is shown. Although calcium itself is not displayed (due to its relatively high concentration distorting the plot scale), the stepwise increase in CaM species bound to one, two, three, and four calcium ions is clearly visible. The appearance of CaMKII bound to fully saturated CaM (CaMKII_CaM_Ca4) further confirms the expected dynamics. as per the set reaction rates and established literature, CaM fully bound to four calcium ions is immediately available for binding to CaMKII, whereas CaM bound to fewer calcium ions is less readily available for this interaction.

The simulation reveals a rapid decrease in the concentration of free CaM, which stabilises at approximately half of its initial value, suggesting that roughly half of the CaM molecules remain unbound to calcium. Upon further investigation, this suggests that calcium is acting as a saturating factor. Given that each CaM molecule can bind up to four calcium ions, the 290 CaM molecules would require at least 1200 calcium ions (290 × 4 ≈ 1200) for full saturation. However, the model uses 1000 calcium ions, which is slightly below this threshold. It is also worth noting that calcium ions are continuously binding to and dissociating from CaM as part of the ongoing reactions, so as some calcium may dissociate from one species, it might then associate to another, allowing for dynamic and emergent molecule behaviours. Even if the calcium concentration were increased (the difference between 1000 and 1200 calcium ions being relatively small, from 3.282 μM to 3.938 μM, respectively), we would expect an increase in the number of CaM molecules bound to four calcium ions, but the change might not be substantial.

![CaM binding to 1,2,3 and 4 calcium ions (calcium not shown) and formation of CaMKII-CaM complex (CaMKII_CaM_Ca4). run_2025-04-03_08-45-21_seed_2](40-results-figures\WT\calcium-binding.png){#fig-calcium-binding fig-pos='H' fig-scap="CaM binding calcium"}

## T286 mutant model

This model simulates the CaMKII T286A mutant, in which the critical autophosphorylation site threonine 286 is substituted with alanine, preventing phosphorylation at this site. This mutation has been extensively characterised in both _in vitro_ biochemical assays and _in vivo_ using mice that were genetically modified. T286A mutation has been shown to impair LTP and spatial learning in rodents. he computational implementation allows investigation into how the loss of T286 phosphorylation alters CaMKII dynamics and downstream NMDAR interactions under different stimulation conditions [REFERENCES].

## CaMKII/NMDAR binding mutant model
This model represents a mutation that prevents CaMKII from binding to the GluN2B subunit of NMDARs, a key interaction implicated in synaptic plasticity, as discussed in SECTION-REFERENCE. When it comes to _in vivo_ and _in vitro_ mutants of CaMKII and NMDAR binding, the mutation can tackle either molecule to prevent their binding. For example, a CaMKII I205K mutation in which isoleucine is replaced with a lysine impairs binding to GluN2B without affecting kinase activity [REFERENCE], and is demonstrated to reduce CaMKII accumulation at synapses after LTP induction [REFERENCE]. 

example of nmdar mutant https://link.springer.com/article/10.1186/1756-6606-6-10 impaired by the mutations L1298A and R1300Q [22]. https://www.embopress.org/doi/full/10.1038/emboj.2011.482

Why L1298 and R1300?
These residues are located in a short, conserved sequence motif within the cytoplasmic tail of GluN2B (often referred to as the CaMKII-binding site), which spans approximately amino acids 1290–1309. Structural, biochemical, and mutational studies have pinpointed L1298 and R1300 as essential contact points for high-affinity binding to the CaMKII kinase domain.
 Leucine 1298 (L1298)
A hydrophobic residue, crucial for fitting into a hydrophobic pocket on CaMKII.

Mutating it to alanine removes hydrophobic bulk, destabilising this core interaction.

This significantly reduces binding affinity without disrupting the structure of GluN2B broadly.

2. Arginine 1300 (R1300)
A positively charged residue, likely involved in electrostatic interactions or hydrogen bonding with CaMKII residues.

Substituting arginine with glutamine (neutral, polar) removes the charge and disrupts those interactions.
In biological systems, this has been examined using GluN2B mutants that disrupt the CaMKII-binding motif, or CaMKII mutants that selectively impair binding without affecting kinase activity. Both in vitro studies and in vivo models have demonstrated that disrupting this interaction impairs LTP maintenance and learning-related plasticity. The computational model isolates this mechanism by setting CaMKII–NMDAR binding reactions to zero, allowing for a focused analysis of how this interaction contributes to model behaviour.

# Limitations


# Future directions

decrease volume
increase calcium
calcium pulses chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://mcell.org/documentation/MCellQuickReferenceGuide.pdf release pattern interval

adding structural proteins to psd
make drawing figures of what i expect, could do in future. 

<!--
# limitations
need to add a list

- could do with more runs, could do with further parameter analysis? 
# Results

9.96181304\times10^{-8} concentration of NMDAR/CAMKII complex at equilibrium (30 molecules converted to Molar) following equation in modelling chapter. 

## CaMKII dodecamer

mutant CaMKII/NMDAR binding abolition and how this replicates in the cBNGL model too.

## in camkii286p mutant


### Does this model reproduce previously suggested results of CaMKII activation?

### CaMKII interaction with NMDARs

Some conditions/hypotheses:
Binding of cam_ca4_camkii is favoured to bind nmdar vs camkii_free, and camkii_p286 should also be favoured to bind nmdar. This is currently not included with how the model stands. 

Yes it is included actually just not explicitly. Because camkii bound to camca4 is already more likely to exist in the open state; and so is camkii_p – so we expect these will be the ones binding more readily to nmdar (biology explanation because kinase domain is available to bind nmdars)
-	Do we need to specify different reaction rates? Or will camkii_camca4 bind more readily to nmdar anyway because camkii_camca4 is favoured to exist at higher quantities? How will this affect the model?

Cam_ca4 binding to camkii favours phosphorylation at t286 -> this is also modelled but not expliclty. 
Camkii t306 P does not happen when camkii bound to nmdar (see condition reaction #8)


our results indicate that CaMKII binds with high affinity to NR2B/C when autophosphorylated on Thr286 independent of the presence of Ca2+ and calmodulin (Fig. 1)

does our model show that camkii_p, independent of cam binding, binds at higher rates? id expect camkii_p to be found bound to nmdar independently of cam_bound_camkii, so higher number of camkii_p_camfree, and less of camkii_p_cam_ca4

->model where camkii cannot p

CaMKII/GluN2B binding requires an initial Ca2+/CaM stimulus but then persists even after dissociation of CaM from the complex. https://www.jbc.org/article/S0021-9258(20)42434-2/fulltext

Both protein phosphatase 1 (PP1) and protein phosphatase 2A (PP2A) dephosphorylated pS1303 in the GluN2B CT [17]. In the PSD, PP1 is a major phosphatase catalyzing S1303 dephosphorylation [18]. https://pmc.ncbi.nlm.nih.gov/articles/PMC4435801/


- not checking for this but for future discussions: CaMKII binding to GluN2B even blocks this phosphorylation (Bayer et al., 2001).  https://www.sciencedirect.com/science/article/pii/S0896627319304866

- Secondary T305/T306 autophosphorylation takes place at ~100-fold slower rate than the T286/7 reaction, https://link.springer.com/chapter/10.1007/978-3-319-24364-1_3

# same as before, most activity of camkii is from autonomous, not due to bound to cam:

CaMKIIα activation, but not CaMKIIα-CaM binding, integrates Ca2+ pulses. This suggests that most of the active CaMKIIα population is in a CaM-independent, autonomous activation state. 

Taken together with our previous studies of CaMKIIα activation during repetitive Ca2+ pulses in the spine6,10, CaMKIIα activation, but not CaMKIIα-CaM binding, integrates Ca2+ pulses. This suggests that most of the active CaMKIIα population is in a CaM-independent, autonomous activation state. Our kinetic model also predicts that the CaMKIIα bound to CaM accounts for only a small fraction of CaMKIIα activity (~1/4), and most of the activity is from autonomous activation.

from paper: Mechanisms of Ca2+/calmodulin-dependent kinase II activation in single dendritic spines

# t305/306 p

this is what we see in our model too: These results suggested that inhibitory phosphorylation at Thr305/Thr306 dynamically occurs during CaMKIIα activation, which inhibits the rebinding of Ca2+/CaM on CaMKIIα. However, preventing this regulation during the induction of sLTP (enhancing binding affinity to Ca2+/CaM) did not result in a higher level of Ca2+/CaM binding. https://link.springer.com/article/10.1038/s41467-019-10694-z?fromPaywallRec=false
 
**Aim 1.** Develop a computational model of CaMKII/NMDAR interactions based on published models and known findings on CaMKII regulation. This way, the model itself functions as a testable hypothesis that synthesises literature knowledge about CaMKII/NMDAR interactions.

**Aim.** Perform parameter sweeps for reaction rates that have not been measured experimentally. This allows mapping the model's response to parameter changes and determining plausible ranges of the unknown parameters.

**Aim 2.** Determine in detail how functional states of CaMKII contribute to stabilizing the CaMKII/NMDAR complex, defined as achieving long-lasting binding that reaches equilibrium. This includes investigating how conformational states of CaMKII and phosphorylation events influence the stability of the complex.

- our results indicate that CaMKII binds with high affinity to NR2B/C when autophosphorylated on Thr286 independent of the presence of Ca2+ and calmodulin (Fig. 1)

does cam binding make a difference to camkii/nmdar binding 

camkii_p free from cam binds more readily to nmdars than when camkii_p is bound to cam

does our model show that camkii_p, independent of cam binding, binds more readily than when camkii is free from cam binding? id expect camkii_p to be found bound to nmdar independently of cam_bound_camkii, so higher number of camkii_p_camfree, and less of camkii_p_cam_ca4

**Aim 3.** Investigate how CaMKII/NMDAR binding influences CaMKII activity and function by examining an _in silico_ mutation model where CaMKII-NMDAR interaction is disrupted. 

**Aim 4.** Investigate how CaMKII phosphorylation influences CaMKII/NMDAR binding by examining an _in silico_ mutation model where CaMKII cannot be phosphorylated at key functional residues.  

**Aim** reproducibility. model follows fair principles. for details see chapter...
**aim** ethics - data hazards. 

## Parameter accuracy

# Trying to understand how parameters are limiting or not

::: {#fig-diffparams layout-ncol=2}

![a](40-results-figures/2024-05-20_17-43-18_out.png){#fig-a}

![b](40-results-figures/2024-05-22_16-05-00_out.png){#fig-b}

![c](40-results-figures/2024-05-22_16-16-27_out.png){#fig-c}

![d](40-results-figures/2024-05-23_12-52-50_out.png){#fig-d}

Famous Elephants
:::

<!--
### Released molecules for run A

Value,Parameter
200.0,CaMKII_i
200.0,CaM_i
10000.0,Ca_i
300.0,NMDAR_i
100.0,PP1_i
30000.0,ITERATIONS

### params for B
Value,Parameter
2000.0,CaMKII_i
2000.0,CaM_i
10000.0,Ca_i
300.0,NMDAR_i
1000.0,PP1_i
3000.0,ITERATIONS

### params for C
Value,Parameter
2000.0,CaMKII_i
2000.0,CaM_i
100000.0,Ca_i
300.0,NMDAR_i
1000.0,PP1_i
3000.0,ITERATIONS

### params for D
Value,Parameter
2000.0,CaMKII_i
2000.0,CaM_i
10000.0,Ca_i
300.0,NMDAR_i
1000.0,PP1_i
3000.0,ITERATIONS
-->


| Parameter  | Run A        | Run B       | Run C         | Run D       |
|------------|--------------|-------------|---------------|-------------|
| CaMKII_i   | 2 x 10<sup>2</sup> | 2 x 10<sup>3</sup> | 2 x 10<sup>3</sup> | 2 x 10<sup>3</sup> |
| CaM_i      | 2 x 10<sup>2</sup> | 2 x 10<sup>3</sup> | 2 x 10<sup>3</sup> | 2 x 10<sup>3</sup> |
| Ca_i       | 10<sup>4</sup> | 10<sup>4</sup> | 10<sup>5</sup> | 10<sup>4</sup> |
| NMDAR_i    | 3 x 10<sup>2</sup> | 3 x 10<sup>2</sup> | 3 x 10<sup>2</sup> | 3 x 10<sup>2</sup> |
| PP1_i      | 10<sup>2</sup> | 10<sup>3</sup> | 10<sup>3</sup> | 10<sup>3</sup> |
| ITERATIONS | 3 x 10<sup>4</sup> | 3 x 10<sup>3</sup> | 3 x 10<sup>3</sup> | 3 x 10<sup>3</sup> |



| Parameter  | Run A                            | Run B                            | Run C                            | Run D                            |
|------------|----------------------------------|----------------------------------|----------------------------------|----------------------------------|
| CaMKII_i   | <span style="color:#D55E00">2 x 10<sup>2</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   |
| CaM_i      | <span style="color:#D55E00">2 x 10<sup>2</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   | <span style="color:#0072B2">2 x 10<sup>3</sup></span>   |
| Ca_i       | <span style="color:#009E73">10<sup>4</sup></span>     | <span style="color:#009E73">10<sup>4</sup></span>     | <span style="color:#F0E442">10<sup>5</sup></span>     | <span style="color:#009E73">10<sup>4</sup></span>     |
| NMDAR_i    | <span style="color:#56B4E9">3 x 10<sup>2</sup></span> | <span style="color:#56B4E9">3 x 10<sup>2</sup></span> | <span style="color:#56B4E9">3 x 10<sup>2</sup></span> | <span style="color:#56B4E9">3 x 10<sup>2</sup></span> |
| PP1_i      | <span style="color:#CC79A7">10<sup>2</sup></span>     | <span style="color:#E69F00">10<sup>3</sup></span>      | <span style="color:#E69F00">10<sup>3</sup></span>      | <span style="color:#E69F00">10<sup>3</sup></span>      |
| ITERATIONS | <span style="color:#999999">3 x 10<sup>4</sup></span>  | <span style="color:#D55E00">3 x 10<sup>3</sup></span>  | <span style="color:#D55E00">3 x 10<sup>3</sup></span>  | <span style="color:#D55E00">3 x 10<sup>3</sup></span>  |


### Table of known reactions to replicate

| Description                        | Parameter        | Value                    | Reference            | Parameter           | Value                    | Reference            |
|------------------------------------|------------------|--------------------------|----------------------|---------------------|--------------------------|----------------------|
| Ca2+ binding to CaM                | k1Con            | 4 μM<sup>-1</sup>s<sup>-1</sup>    | [21, 30, 45, 46]     | k1Coff               | 40.24 s<sup>-1</sup>               | [47–49]              |
|                                    | k2Con            | 10 μM<sup>-1</sup>s<sup>-1</sup>   | [21, 30, 45, 46]     | k2Coff               | 9.3 s<sup>-1</sup>                 | [49]                 |
|                                    | k1Non            | 100 μM<sup>-1</sup>s<sup>-1</sup>  | [21, 30, 45, 46]     | k1Noff               | 2660 s<sup>-1</sup>               | [47, 49–51]          |
|                                    | k2Non            | 150 μM<sup>-1</sup>s<sup>-1</sup>  | [21, 30, 45, 46]     | k2Noff               | 990 s<sup>-1</sup>                | [47–51]              |
| CaM binding to unphosphorylated CaMKII | kCaM0on         | 3.8 x 10<sup>-3</sup> M<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM0off             | 6.56 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM1Con         | 59 x 10<sup>-3</sup> μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1Coff            | 6.72 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM2Con         | 0.92 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM2Coff            | 6.35 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM1C1Non       | 0.33 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1C1Noff          | 5.68 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM2C1Non       | 5.2 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             | kCaM2C1Noff          | 5.25 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM1Non         | 22 x 10<sup>-3</sup> μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1Noff            | 5.75 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM2Non         | 0.1 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             | kCaM2Noff            | 1.68 s<sup>-1</sup>               | [30, 52]             |
|                                    | kCaM1C2Non       | 1.9 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             | kCaM1C2Noff          | 2.09 s<sup>-1</sup>               | [30]                 |
|                                    | kCaM4on          | 30 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 52]             | kCaM4off             | 1.95 s<sup>-1</sup>               | [30, 52]             |
| Ca2+ binding to CaM-CaMKII         | kK1Con           | 44 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 49]             | kK1Coff              | 29.04 s<sup>-1</sup>               | [30, 49]             |
|                                    | kK2Con           | 44 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 49]             | kK2Coff              | 2.42 s<sup>-1</sup>                | [30, 49]             |
|                                    | kK1Non           | 75 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 49]             | kK1Noff              | 301.5 s<sup>-1</sup>               | [30, 49]             |
|                                    | kK2Non           | 76 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 49]             | kK2Noff              | 32.68 s<sup>-1</sup>               | [30, 49]             |
| CaMKII binding to CaM-CaMKII *     | kCaMKIIon        | 50 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 53]             | kCaMKIIoff           | 60 s<sup>-1</sup>                 | [27, 30, 54]         |
| CaMKII phosphorylation             | kCaM1Cp          | 0.032 s<sup>-1</sup>               | [21, 30]             | kCaM2Cp              | 0.064 s<sup>-1</sup>               | [21, 30]             |
|                                    | kCaM1C1Np        | 0.094 s<sup>-1</sup>               | [21, 30]             | kCaM2C1Np            | 0.124 s<sup>-1</sup>               | [21, 30]             |
|                                    | kCaM1Np          | 0.061 s<sup>-1</sup>               | [21, 30]             | kCaM2Np              | 0.12 s<sup>-1</sup>                | [21, 30]             |
|                                    | kCaM1C2Np        | 0.154 s<sup>-1</sup>               | [21, 30]             | kCaM4p               | 0.96 s<sup>-1</sup>                | [21, 30]             |
| CaM binding to phosphorylated CaMKII | kCaM0p,on      | 1.27 x 10<sup>-3</sup> μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1Cp,on           | 19.7 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             |
|                                    | kCaM2Cp,on       | 0.3 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             | kCaM1C1Np,on         | 1.1 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             |
|                                    | kCaM2C1Np,on     | 1.73 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1Np,on           | 7.3 μM<sup>-1</sup>s<sup>-1</sup>  | [30, 52]             |
|                                    | kCaM2Np,on       | 0.03 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             | kCaM1C2Np,on         | 0.63 μM<sup>-1</sup>s<sup>-1</sup> | [30, 52]             |
|                                    | kCaM4p,on        | 10 μM<sup>-1</sup>s<sup>-1</sup>   | [30, 52]             | kCaMp,off            | 0.07 s<sup>-1</sup>                | [52]                 |
| Ng binding to CaM                  | kNgon            | 5 μM<sup>-1</sup>s<


|   | kon = 1000000.0 | kon = 10000000.0 | kon = 100000000.0 | kon = 1000000000.0 | kon = 10000000000.0 |
|-------|-------|-------|-------|-------|-------|
| koff = 0.0001 | 1e-10 | 1e-11 | 1e-12 | 1e-13 | 1e-14 |
| koff = 0.001 | 1e-09 | 1e-10 | 1e-11 | 1e-12 | 1e-13 |
| koff = 0.01 | 1e-08 | 1e-09 | 1e-10 | 1e-11 | 1e-12 |
| koff = 0.1 | 1e-07 | 1e-08 | 1e-09 | 1e-10 | 1e-11 |
| koff = 1.0 | 1e-06 | 1e-07 | 1e-08 | 1e-09 | 1e-10 |
