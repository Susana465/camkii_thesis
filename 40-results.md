---
bibliography: [references.bib]
lightbox: true
---

# Results and discussion of results {#sec-results}

Three principal model versions of the CaMKII/NMDAR model have been developed. The first is a wild-type (WT) model, as described in @sec-model-description. In addition, two mutant (MT) models were constructed: one in which CaMKII is unable to phosphrylate at T286, and another in which CaMKII cannot bind to NMDARs. These mutations were implemented by setting the reaction rates corresponding to CaMKII autophosphorylation and CaMKII–NMDAR binding, respectively, to zero.

## Wild-type model

This section presents a summary of the results obtained from the wild-type (WT) model. In the WT simulation, the final total number of CaMKII_open molecules reaches a mean of approximately 108 molecules at 100 seconds. The shaded area surrounding the mean trajectory in the graph represents the standard deviation (SD), indicating the degree of variability across different simulation runs.

Figure 7.2 provides an overview of the key molecular interactions and states observed in the wild-type (WT) CaMKII/NMDAR model during the simulation. Each subpanel (a–d) captures specific aspects of the molecular dynamics, focusing particularly on the interplay between CaMKII opening, T286 phosphorylation, CaM binding, and NMDAR binding.

Figure 7.2a shows the evolution of the open conformation of CaMKII over time. The brown line represents the total number of CaMKII_open subunits, which steadily increases as the simulation progresses. Two main factors contribute to the stabilization of CaMKII in the open state: (i) CaM binding (light blue line, camkii_cam_unbound_open) and (ii) NMDAR binding (dark blue line, nmdar_camkii_complex). Notably, NMDAR binding can maintain CaMKII in the open conformation even in the absence of CaM binding (Fig 7.2c). Figure 7.2b focuses on T286 phosphorylation dynamics of CaMKII. The orange line (camkii_t286p) shows the total number of CaMKII subunits phosphorylated at T286, while the pink line (camkii_t286p1_bound_nmdar) represents the subset of T286-phosphorylated subunits that are also bound to NMDARs. A large fraction of phosphorylated subunits are found associated with NMDARs, indicating that NMDAR binding promotes or sustains T286 phosphorylation. Importantly, this phosphorylation happens largely independently of CaM, as further illustrated in panels (c) and (d).

Figure 7.2c dissects the T286-phosphorylated CaMKII subunits that are bound to NMDARs into CaM-bound and CaM-unbound populations. Here, the pink line represents all T286-phosphorylated CaMKII subunits bound to NMDARs, while the orange line shows the subset that are CaM-free  (camkii_cam_unbound_t286p1_bound_nmdar). It is clear that the majority of the T286-phosphorylated CaMKII subunits bound to NMDARs are unbound from CaM, emphasizing that CaMKII can maintain phosphorylation at T286 even after CaM dissociates. This further supports the idea that NMDAR binding alone is sufficient to stabilize the active, open, phosphorylated state in this model. Figure 7.2d provides a more detailed look at T286 phosphorylation in relation to CaM binding across the whole CaMKII population. The data shows that roughly equal numbers of CaMKII subunits are phosphorylated at T286 whether they are CaM-bound or CaM-unbound. This demonstrates that although CaM binding facilitates CaMKII opening and activation, T286 phosphorylation does not require continuous CaM binding once CaMKII is locked in its open, phosphorylated conformation.

To further dissect the molecular events underlying these dynamics, the following sections will explore a representative simulation run in detail, focusing on the specific behaviours of CaMKII subunits in relation to NMDAR and CaM binding, and T286 phosphorylation.

::: {.landscape}

![Final value means of total molecule counts (mean ± SD): camkii_open (108.00 ± 5.12); camkii_cam_ca4 (79.22 ± 3.85); nmdar_free (0.00 ± 0.00); nmdar_camkii_complex (30.00 ± 0.00); camkii_t286p (50.56 ± 5.96); camkii_t286p1_bound_nmdar (27.11 ± 1.37); camkii_cam_unbound_t286p1_bound_nmdar (24.67 ± 1.25); camkii_cam_ca4_t286p1 (24.33 ± 4.45); camkii_cam_unbound_open_t286p1 (26.22 ± 2.35)](40-results-figures\WT\t286p-means.PNG){#fig-t286p-means fig-scap="abcd"}

:::

![blablaneeds](40-results-figures\observable_names.PNG)


### Calcium release and initial CaM saturation
In the WT model (described in detail in @sec-model-description), a release of 1000 calcium ions occurs within a dendritic spine volume of 0.50588 $\mu\text{m}^3$. This calcium subsequently binds to CaM, which can bind up to four calcium ions. Full saturation of CaM is required for subsequent binding to CaMKII, resulting in the formation of the CaMKII–CaM complex (CaMKII_CaM_Ca4).

This progression is illustrated in [@fig-calcium-binding], where the gradual formation of partially and fully calcium-bound CaM species is shown. Although calcium itself is not displayed (due to its relatively high concentration distorting the plot scale), the stepwise increase in CaM species bound to one, two, three, and four calcium ions is clearly visible. The appearance of CaMKII bound to fully saturated CaM (camkii_cam_ca4) further confirms the expected dynamics. as per the set reaction rates and established literature, CaM fully bound to four calcium ions is immediately available for binding to CaMKII, whereas CaM bound to fewer calcium ions is less readily available for this interaction.

The simulation reveals a rapid decrease in the concentration of free CaM, which stabilises at approximately half of its initial value, suggesting that roughly half of the CaM molecules remain unbound to calcium. Upon further investigation, this suggests that calcium is acting as a saturating factor. Given that each CaM molecule can bind up to four calcium ions, the 290 CaM molecules would require at least 1200 calcium ions (290 × 4 $\approx$ 1200) for full saturation. However, the model uses 1000 calcium ions, which is slightly below this threshold. It is also worth noting that calcium ions are continuously binding to and dissociating from CaM as part of the ongoing reactions, so as some calcium may dissociate from one species, it might then associate to another, allowing for dynamic and emergent molecule behaviours. Even if the calcium concentration were increased (the difference between 1000 and 1200 calcium ions would be relatively small, from 3.282 μM to 3.938 μM, respectively), we would expect an increase in the number of CaM molecules bound to four calcium ions, but the change might not be substantial. 

![CaM binding to 1,2,3 and 4 calcium ions (calcium not shown) and formation of CaMKII-CaM complex (CaMKII_CaM_Ca4). _For reproducibility, this figure was obtained from plotting "run_2025-04-03_08-45-21_seed_2."_](40-results-figures\WT\calcium-binding.png){#fig-calcium-binding fig-pos='H' fig-scap="CaM binding calcium"}

### CaM stabilises CaMKII in the open conformation, but is not required for CaMKII/NMDAR binding
Next, we examine CaM–CaMKII binding (@fig-cam-camkii-binding), focusing on how CaMKII's open conformation of subunits stabilises over time. Out of the 720 CaMKII subunits released (not shown), a total of 104 molecules remain in the open conformation (camkii_open), at 100 seconds. Camkii_open represent the total population of CaMKII subunits that are structurally in their open state. To determine how many of these open subunits are simultaneously bound to CaM, we refer to the pink trace in @fig-cam-camkii-binding, which indicates that 79 subunits are CaM-bound by the end of the simulation. This shows that approximately 75% of the open CaMKII subunits are being stabilised in this state through CaM binding up until the end of the simulation. 

In contrast, the population of open CaMKII subunits that are not bound to CaM reaches equilibrium just before the 20-second mark, maintaining a steady count of just above 20 molecules until the end of the simulation. This accounts for the remaining 25% of the open CaMKII pool. These observations indicate that the majority of open CaMKII subunits are stabilised in their active conformation via CaM binding, while a smaller proportion is maintained in the open state by alternative mechanisms.

In the model at hand, CaMKII is defined as dynamically transitioning between open and closed conformations, and unless stabilised in the open state —either through CaM binding, T286 phosphorylation, or NMDAR association— it will revert to the closed state (see @fig-tbl-1). So we can see in @fig-cam-camkii-binding that the majority of CaMKII open is stabilised by CaM, however, there is another mechanism that is keeping CaMKII open. This other mechanism is in direct relation with NMDAR interaction as we will explore next. 

By examining @fig-camkii-opening-nmdar, we observe that the levels of CaMKII binding to NMDARs (dark blue line: nmdar_camkii_complex) closely follow the same pattern as CaM unbinding from CaMKII (medium blue: camkii_cam_unbound_open). In other words, as CaMKII associates with NMDARs, this interaction maintains CaMKII in an open state, without the need for CaM binding to CaMKII. 

Interestingly, the proportion of CaMKII free from CaM that are still in their open conformation (medium blue: camkii_cam_unbound_open, @fig-camkii-opening-nmdar) fluctuates up and down frequently, which comes from CaMKII opening and closing (as CaM is not bound yet). 

Initially, the level of CaMKII free from CaM that are still in their open conformation (camkii_cam_unbound_open) fluctuates and exceeds the amount of CaMKII bound to NMDARs (nmdar_camkii_complex). This indicates that while a pool of open CaMKII is available, not all of it is bound to NMDARs at once. Over time, as CaMKII binding to NMDARs progresses and the system approaches a steady state, newly opened CaMKII subunits are quickly captured by available NMDAR binding sites. Consequently, the amount of free, open CaMKII stabilizes at a level consistently lower than the amount of NMDAR-bound CaMKII, indicating that binding to NMDARs efficiently sequesters and stabilizes open CaMKII in the later phase.

Moreover, in @fig-camkii-opening-nmdar, we observe a three-step, ladder-like progression of CaMKII binding to NMDARs. Each step corresponds to an increase in the number of CaMKII subunits bound: first reaching approximately 12 subunits, then 24, and finally 30. This pattern suggests that entire CaMKII holoenzymes (each containing 12 subunits) sequentially bind to NMDARs.

Initially, one holoenzyme binds rapidly, with its subunits quickly associating with available NMDARs. Once 12 subunits are bound, a second holoenzyme begins binding. However, this process is slower, likely because after the first 12 subunits are bound, there are fewer free NMDARs left. Now, the second holoenzyme has fewer choices, and it may need to "search" or "diffuse" around more to find free receptors. Finally, after the second holoenzyme binds (up to 24 subunits), a third holoenzyme binds partially, occupying the remaining 6 NMDARs. By the time the third holoenzyme tries to bind, only 6 NMDARs are free — not enough for all 12 subunits. The progressive slowing reflects decreasing availability of free NMDARs for binding. The implications of these findings are discussed in the REFERENCE-SECTION; however, this particular mode of CaMKII binding to NMDARs may be an artifact of the model. Although not necessarily invalid, this aspect warrants further scrutiny and should be revisited in future research.

In summary, the majority (75%) of CaMKII subunits in the open conformation are stabilized by binding to CaM. However, while  CaM helps stabilize CaMKII in the open state, the binding of CaMKII to NMDARs is not dependent on CaM. As CaMKII binds to NMDARs, it maintains its open conformation even without CaM binding, indicating that the interaction between CaMKII and NMDARs can stabilize the open state of CaMKII independently of CaM. 

::: {#fig-camkii-open layout-ncol=1 fig-pos='H' fig-scap="Stabilisation of CaMKII in the Open Conformation" width="70%"}

![](40-results-figures\WT\cam-camkii-binding.png){#fig-cam-camkii-binding}

![](40-results-figures\WT\camkii-open-nmdar.png){#fig-camkii-opening-nmdar}

Stabilisation of CaMKII in the Open Conformation. _For reproducibility, this figure was obtained from plotting data from "run_2025-04-03_08-45-21_seed_2."_

:::

### CaMKII subunits remain open and autophosphorylate at T286 upon NMDAR binding, even in the absence of CaM
Next we look at total number of CaMKII subunits phosphorylated at T286. CaMKII_T286P reflects the full amount of T286-phosphorylated CaMKII, irrespective of any other concurrent molecular states. All CaMKII subunits categorised as camkii_t286p are necessarily in the open conformation. Therefore, camkii_t286p represents a subset of the camkii_open population [@fig-subsets-of-open-t286p1_p0]. This is consistent with both the model's coding and biological evidence, as phosphorylation at T286 locks CaMKII in an autonomously active, open conformation by preventing the regulatory segment from re-binding to the catalytic domain, which physically prevents closing of the subunit.

Out of the 104 CaMKII subunits that are open at the end of the simulation, 45 are found to be phosphorylated at T286 [@fig-subsets-of-open-t286p1_p0], and the rest (104 - 45 = 59) are therefore not phosphorylated at this site. This indicates that approximately half of the open CaMKII subunits are in a T286-phosphorylated state. 

Of the 45 T286-phosphorylated CaMKII subunits, a subset of 25 are found to be bound to NMDARs (pink line: camkii_t286p1_bound_nmdar as shown in @fig-camkii-t286p-nmdar-b). The difference between these two molecules, corresponds to the number of CaMKII molecules that are T286-phosphorylated but not associated with NMDARs. This is, out of all the CaMKII subunits that are phosphorylated at T286, about half can be found bound to NMDARs, and the other half is not. Figure @fig-subsets_nmdar-t268p further demonstrates that the majority of CaMKII subunits bound to NMDARs and phosphorylated at T286 are unbound from CaM. This complements observations in @fig-camkii-t286p-nmdar-b, where 25 CaMKII subunits are both T286-phosphorylated and bound to NMDARs, of which 23 are CaM-free and only 2 remain CaM-bound by the end of the simulation.

Further, within the population of T286-phosphorylated CaMKII that is also bound to NMDARs (pink line: camkii_t286p1_bound_nmdar), only a very small number of subunits remain bound to CaM [@fig-subsets_nmdar-t268p]. Thus, the majority of CaMKII subunits that are bound in a NMDAR/CaMKII complex are both phosphorylated at T286 and free from CaM (which is consistent with literature, as further discussed in REFERENCE-SECTION). This is, once CaMKII is bound to the NMDARs, the holoenzyme subunits can remain open, and autophosphorylate even in the absence of CaM. 

![1](40-results-figures\WT\subsets-of-open-t286p1_p0.png){#fig-subsets-of-open-t286p1_p0 fig-pos='H' fig-scap="CaMKII open and T286 phosphorylated"}

![2](40-results-figures\WT\camkii-t286p.png){#fig-camkii-t286p-nmdar-b fig-pos='H' fig-scap="CaMKII T286 phosphorylated and bound to CaM"}

![alt text](40-results-figures\WT\subsets_nmdar-t268p.png){#fig-subsets_nmdar-t268p fig-pos='H' fig-scap="CaMKII T286 phosphorylated and bound to CaM"}

### CaMKII phosphorylation at T286 is not more likely when CaM is present
As explained in @sec-cam-binding-and-t286-p, we use a 'conformational selection' approach to modelling CaMKII activation, where CaMKII can exist in both open and closed states independently, and CaM selectively binds to and stabilizes the open conformation, without _inducing_ a conformational change. In order to understand how CaM is interacting with CaMKII T286 phosphorylation, we look at @fig-subsets-of-camkii-t286p-cam-binding. Here we can see that among all CaMKII subunits phosphorylated at T286, approximately half (23 molecules) are also bound to CaM, represented by the peach-coloured trace _"camkii_cam_ca4_t286p1"_, while the remaining half (22 molecules) are unbound from CaM (brown-coloured trace: _"camkii_cam_unbound_open_t286p1"_). 

This indicates that, although CaM binding co-occurs with T286 phosphorylation, T286 is not necessarily more likely when subunits are bound to CaM. In fact, subunits that are both CaM-bound and T286-phosphorylated emerge more slowly during the simulation [@fig-subsets-of-camkii-t286p-cam-binding], suggesting that CaM binding is not the main event leading to the increase of initial CaMKII T286 phosphorylation, but as we will see next, NMDAR binding is (by keeping CaMKII subunits in their open conformation and allowing subsequent T286 autophosphorylation).

T286-phosphorylated CaMKII which is free from CaM (peach-coloured line in @fig-xsubsets_nmdar-t268p) corresponds in timing with the formation of the CaMKII/NMDAR complex [@fig-subsets_nmdar-t268p]. This suggests that, once CaMKII binds to NMDARs and its subunits are held in the open conformation, autophosphorylation at T286 is further facilitated in the CaMKII subunits that are part of the CaMKII/NMDAR complex. 

Interestingly, a slight increase in the population of CaMKII free from CaM and T286 phosphorylayed is observed around 80 seconds. This rise suggests that subunits of holoenzymes locked into the CaMKII/NMDAR complex undergo further autophosphorylation of neighbouring subunits, resulting in a momentary increase in CaMKII subunits that are free from CaM and phosphorylated at T286.

![note for figure: its a redundancy that camkii_cam_unbound_optent28p1 has open in it because all camkii that is t286p1 is open anyway. ](40-results-figures/WT/subsets-of-camkii-t286p-cam-binding.png){#fig-subsets-of-camkii-t286p-cam-binding}

subset of camkii bound to ndmdar, of which x is p and x is not p

![1](40-results-figures\WT\xsubsets_nmdar-t268p.png){#fig-xsubsets_nmdar-t268p}

![1.1](40-results-figures\WT\subset-of-nmdar-p-not-pt286.png)

![2.2](40-results-figures\WT\camkii-nmdar-unphospho.png){#fig-xsubsets_nmdar-t268p0}

### NMDAR binding promotes CaMKII autophosphorylation at T286 and T306 sites
Phosphorylation at the T306 site is known to occur at a slower rate than phosphorylation at T286 [@otmakhov2015Fast; @chang2017CaMKII], and this is reflected in the model outputs. A total of 25 CaMKII subunits become phosphorylated at T306 over the course of the simulation (marroon trace: camkii_t306p in @fig-t306p), of which 21 are bound to the NMDAR (golden trace:camkii_cam_unbound_t306p1_bound_nmdar in @fig-t306p) —indicating that approximately 84% of T306-phosphorylated subunits are part of NMDAR complexes. 

Moreover, the accumulation of doubly phosphorylated subunits (T286P and T306P; here referred to as CaMKII_PP, hot pink trace in @fig-t306p) appears to track closely with the rate of T306 phosphorylation. This indicates that T306 phosphorylation typically follows T286 phosphorylation, particularly during the earlier stages of the simulation. This behaviour is consistent with both the modelled mechanisms and findings reported in the literature [REFERENCE].

![alt text](40-results-figures\WT\t306p.png){#fig-t306p fig-pos="H"} 

Interestingly, after around 60 seconds, subunits that are solely phosphorylayed at T306 continue to increase, whilst CaMKII_PP does not (@fig-t306p). This suggests that, at later stages in the simulation, T306 phosphorylation can occur and persist independently of T286 phosphorylation. Extending the simulation time may offer further insights into this dynamic, as it could support the biological hypothesis that initial T286 phosphorylation enables subsequent T306 phosphorylation, but that T306P can then be maintained even in the absence of T286P [REFERENCE].

Furthermore, T306 phosphorylation follows NMDAR binding dynamics closely. As shown in @fig-t306p-nmdar-binding, CaMKII subunits initially bind to NMDARs in an unphosphorylated T306 state (slate-green: camkii_t306p0_bound_nmdar in @fig-t306p-nmdar-binding). Once the CaMKII–NMDAR complex reaches equilibrium, levels of T306 phosphorylation increase correspondingly, as unphosphorylated T306 decreases. 

![alt text](40-results-figures\WT\t306p-nmdar-binding.png){#fig-t306p-nmdar-binding fig-pos="H"} 

In the final phase of CaMKII binding to NMDARs, after approximately 40 seconds —when all NMDARs are saturated, T306 phosphorylation continues to rise. This is likely supported by the concurrent increase in T286 phosphorylation, and by a decrease in CaM binding to CaMKII subunits already bound to NMDARs. That is, by 40s, a greater proportion of CaMKII subunits are free from CaM (as seen in @fig-subsets-of-camkii-t286p-cam-binding). This aligns with expectations, as CaM binding and T306 phosphorylation are mutually exclusive processes —CaM must be unbound for T306 phosphorylation to occur. Therefore, as the model shows a decrease in CaM binding to CaMKII subunits that are already part of the CaMKII–NMDAR complex, the opportunity for T306 phosphorylation increases. In other words, the less CaM is bound to CaMKII subunits, the more likely it is that T306 can become phosphorylated, and the less likely CaM is to bind. 

@fig-t306p-nmdar-binding shows three distinct peaks, each representing CaMKII subunits that are in the "p00" state — meaning they are not phosphorylated at either T286 or T306. This pattern highlights three important insights. First, CaMKII binds to NMDARs before any phosphorylation has occurred. Second, although phosphorylation is not required for binding, once CaMKII is incorporated into an NMDAR complex, autophosphorylation becomes more likely. Third, phosphorylation at T306 follows phosphorylation at T286, following a sequential phosphorylation mechanism as expected.

These findings show that the formation of CaMKII-NMDAR complexes does not depend on prior phosphorylation at T286. However, once T286 phosphorylation occurs, it can initiate a cascade of further autophosphorylation events, including at T306, within the same NMDAR/CaMKII complex. Previous studies have shown that CaMKII does not need to be phosphorylated at T286 in order to bind to NMDARs or to perform its catalytic functions. That said, phosphorylation at T286 can modulate or enhance both the binding affinity and the enzymatic activity of CaMKII, making it an important regulatory step rather than an absolute requirement.

## T286 and CaMKII/NMDAR binding mutant models

The T286 mutant model is simialr biologically to the CaMKII T286A mutant, in which the critical autophosphorylation site threonine 286 is substituted with alanine, preventing phosphorylation at this site. This mutation has been extensively characterised in both _in vitro_ biochemical assays and _in vivo_ using mice that were genetically modified. T286A mutation has been shown to impair LTP and spatial learning in rodents. he computational implementation allows investigation into how the loss of T286 phosphorylation alters CaMKII dynamics and downstream NMDAR interactions under different stimulation conditions [REFERENCES].

The NMDAR/CaMKII binding mutant model simulates a mutation that disrupts the interaction between CaMKII and the GluN2B subunit of NMDARs. This disruption can be achieved through mutations in either CaMKII or GluN2B, preventing their binding without necessarily altering other functions such as kinase activity [REFERENCES]. A well-characterized example is the CaMKII I205K mutation, where isoleucine is replaced by lysine. This substitution significantly impairs binding to GluN2B while leaving kinase activity intact [REFERENCE]. Experimental evidence shows that this mutation also reduces CaMKII accumulation at synapses following LTP induction [REFERENCE].



---
okayyyy, so becayse t286 phosphorylation increases the chances of camkii subunits remaining in their open conformation, abolishing t286 phosphorylation we would exxpect a decrease in this opening. so we would expect iverall decrease of total camkii_open - but contrary to these expactions, we don't see that!

---

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

# STATSSSS

NORMALITY TEST RESULTS:

camkii_open

WT: 9 values | MT-t286: 9 values

📊 Shapiro–Wilk test for WT
  W = 0.9399, p = 0.5811
  ✅ Data appears normally distributed.

📊 Shapiro–Wilk test for MT
  W = 0.8739, p = 0.1353
  ✅ Data appears normally distributed.

MT -NMDAR :10 

📊 Shapiro–Wilk test for MT
  W = 0.9458, p = 0.6189
  ✅ Data appears normally distributed.


![camkii_open](40-results-figures\statistics\camkii_open2.png)

ANOVA F-statistic: 8.498, p-value: 1.528e-03

Tukey's HSD Post Hoc Test:
      Multiple Comparison of Means - Tukey HSD, FWER=0.05      
===============================================================
     group1      group2 meandiff p-adj   lower    upper  reject
---------------------------------------------------------------
NMDAR_CaMKII_MT T286_MT  -8.5667 0.0023 -14.1775 -2.9558   True
NMDAR_CaMKII_MT      WT     -0.9 0.9161  -6.5109  4.7109  False
        T286_MT      WT   7.6667 0.0076     1.91 13.4233   True


no stat difference for t306p

ANOVA F-statistic: 1.493, p-value: 2.441e-01

![camkii_t306p](40-results-figures\statistics\t396p.png)

https://blog.4dcu.be/programming/2021/12/30/Posthoc-Statannotations.html

https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.tukey_hsd.html 

for camkii_cam_ca4 

Tukey's HSD Post Hoc Test:
      Multiple Comparison of Means - Tukey HSD, FWER=0.05      
===============================================================
     group1      group2 meandiff p-adj   lower    upper  reject
---------------------------------------------------------------
NMDAR_CaMKII_MT T286_MT  -6.7111 0.0042 -11.4067 -2.0155   True
NMDAR_CaMKII_MT      WT   0.6222 0.9419  -4.0734  5.3178  False
        T286_MT      WT   7.3333 0.0024   2.5158 12.1509   True
---------------------------------------------------------------
(mcell4-env) 

# Limitations

# discussion of results
future step: having fully bound CaM can be useful to test whether the system can even reach peak activity, and CaMKII can be phosphorylated at levels shown in literature. 

. It is also important to understand whether the proposed constitutive enzymatic activity of such subunits leading to T286 phosphorylation is critical for maintaining the CaMKII-NMDAR complex. What is clear is that given the ∼40-fold higher concentration of CaMKII subunits than GluN2B subunits (see sects. 9.2.2 and 13.2),  https://journals.physiology.org/doi/full/10.1152/physrev.00034.2022


# Future directions [#sec-future-directions]

to see if more t306 p leads to indirect higher camkii closing, run for longer: Notably, the sustained presence of T306P may contribute to the closure of CaMKII subunits, thereby reducing their catalytic activity. This aligns with hypotheses that link T306 phosphorylation to the functional inhibition of CaMKII. The observed co-occurrence of NMDAR binding and T306 phosphorylation in the majority of subunits further supports a mechanism by which these interactions contribute to reduced CaMKII activity. A competing hypothesis, discussed in the Reference Section, posits that NMDAR binding suppresses T306 phosphorylation; however, our model does not support this outcome under the simulated conditions.

Further developments of this model to account for a more complex NMDAR molecule are possible, as I propose in [DISCUSSION SECTION].

The combined phosphorylation of Thr286, Thr305, and Thr306 is considered vital to the mechanism of subunit exchange because the regulatory domain needs to be accessible to interact with negatively charged residues located on the hub at the vertical interface between subunits, leading to the release of dimers.  https://www.proquest.com/docview/3165639837?pq-origsite=gscholar&fromopenview=true&sourcetype=Dissertations%20&%20Theses

decrease volume
increase calcium
calcium pulses chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://mcell.org/documentation/MCellQuickReferenceGuide.pdf release pattern interval

adding structural proteins to psd
make drawing figures of what i expect, could do in future. 
t306 mutant too. what would i expect?

effects of dephosphorylation could be interesting to look at:

In the GluN2B-bound state,
the enzyme becomes resistant to the action of phosphatases
(Cheriyan et al., 2011) indicating GluN2B-induced structural
changes which can be abolished by specific mutations in CaMKII (Mayadevi et al., 2016). file:///C:/Users/susan/Downloads/fnmol-15-855752.pdf 

we dont model this, but could be an emergent behaviour? 

Importantly, the CaMKII/GluN2B complex was also shown to endure for hours even after dissociation of CaM from the kinase [@barcomb2016CaMKIIa].

discuss why biodynamo not used, the idea at the beginning and how it could be used in the future. 

Because binding of CaMKII to the NMDA receptor is enhanced by CaMKII phosphorylation, the structurally mediated strengthening could be reversed by dephosphorylating CaMKII through the phosphatase-dependent processes (Fig. 4c,d) that are involved in DEPOTENTIATION73. https://www.nature.com/articles/nrn753
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

This is good stuff: CaMKIIα activation, but not CaMKIIα-CaM binding, integrates Ca2+ pulses. This suggests that most of the active CaMKIIα population is in a CaM-independent, autonomous activation state. 

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
