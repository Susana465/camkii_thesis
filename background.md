---
bibliography: [references.bib]
---

# Background

## Report style and philosophy
As we go through this report, you will notice here and there how I chose to write about the personal struggles and successes throughout my second year. Additionally, I also highlight and talk about some of the things I care most in research: making it transparent, inclusive, and accessible. Another unusual thing about this report is that you will see asides mentioning bias in the research I use, or potential oppressive bias on how my research could be used. This is the unfortunate reality of much of the history of the field, and I didn’t want to highlight any scientific achievements without also acknowledging a legacy of scientific racism, speciesism, ableism or any other kind of oppression.
This report’s format and philosophy are heavily inspired by Zelenka’s thesis, which you can find here @nataliezelenkaPhenotypeGenotype. In this section, I’ll explain a little about my approach to the work in this report. This is to add clarity about the lenses through which I did this work, as well as what I consider to be a meaningful scientific contribution.

## Complexity Science and Systems Biology
Complexity science is the study of systems of interacting parts and the emergent behaviours that appear when looking at these interactions; applications of complexity science are predator-prey models, epidemiological modelling (for example,  of pandemics), protein-protein interaction networks, or models of neurons. When applied to biology, it often falls under the banner of Systems Biology. Systems biology, then, refers to the quantitative analysis of the dynamic interactions among several components of a biological system and aims to understand the behaviour of the system as a whole. 

Systems biology involves development and application of systems theory concepts for the study of complex biological systems through iteration over mathematical modelling, computational simulation and biological experimentation. Systems biology serves as a tool to increase our understanding of biological systems, to develop more directed experiments, and to allow accurate predictions. In systems biology, it is helpful to understand and clarify what complexity means also in respect to: 

- **The model**: the large number of variables that can determine behaviour. Some hallmarks of complexity are usually the number of parameters, order of equations and evolution of networks. For example, a protein containing n peptide substrates of kinases can potentially be found in up to 2n distinct phosphorylation states. This feature of protein–protein interactions, which arises because a typical protein involved in cellular regulation contains multiple sites of posttranslational modification and multiple binding sites, has been called combinatorial complexity and is a common challenge to our understanding of cellular regulation @klamt2002CombinatorialComplexityPathway, @green2018NetworkAnalysesSystems. This point relates to the explanations given below too. 

- **The natural system**: the connectivity and non-linearity of relationships. In biological systems large numbers of functionally different, and often multifunctional, sets of elements interact selectively and non-linearly to produce complex behaviours. A biological system is not always necessarily equal to the sum of its parts @nurse1997EndsUnderstanding, where functions emerge from the properties of the networks rather than from any specific element. On the contrary, in biological systems, functions rely on a combination of the network and the specific elements involved. CaMKII interaction pathways serves as a good example here. This protein can be activated, inhibited and degraded by reactions such as phosphorylation and de-phosphorylation, while its targets are selected by the different modification patterns that exist; these are properties that reflect the complexity of the element itself.

- **The technology**: the limited precision and accuracy measurements. When modelling biological systems we encounter more layers of complexity such as, for example, looking at quantitative measures by experimental biologists: for instance, which parameters are available for modelling the system? Which ones do we infer? And in doing so, what are the model parameter sensitivity and initial values sensitivities? The popular measure of complexity for dynamical system is the computational complexity (discussed in the “Computational modelling” section below). For example, although a calculated measure in a mathematical model can characterize the amount of information necessary to predict the future state of the machine, it fails to address its meaning in the world of molecular and modular cell biology. CaMKII serves as a good case here, as mathematically it has been calculated that CaMKII’s dodecamer could have up to 1020 states @pharris2019MultistateModelCaMKII. However, which ones of these states are biologically relevant is a key question that has no answer yet.

- **The methodology**: the uncertainty arising from the conceptual framework chosen. The noise in complexity of the systems increases even further by introducing issues of robustness, noise-resonance and bi-modal behaviour. For example, once we have some outcomes in the model, how can we make sure results are robust and certain?

## Open and reproducible Science
### Defining reproducibility vs replicability
There is a long history of these terms being used interchangeably, or their meanings being swapped depending on the field of study  @claerbout1992ElectronicDocumentsGive @ivie2018ReproducibilityScientificComputing @plesser2018ReproducibilityVsReplicability. For example, a review on the usage of reproducible/replicable meanings @barba2018TerminologiesReproducibleResearch showed that most papers and disciplines use the terminology as defined by Claerbout and Karrenbach, whereas microbiology, immunology and computer science tend to follow the Associtation for Computing Machinery use of reproducibility and replication given by Ivie and Thain, 2018. In political science and economics literature, both terms are used interchangeably. So this quickly shows how having a lack of agreement on such definitions can add even more confusion to the mix. 
Here, we use the definition used by @turingwaycommunity2019TuringWayHandbook, where reproducible research is understood as work that can be independently recreated from the same data and the same code that the original team used. Reproducible is distinct from replicable, robust and generalisable as described in the table below.

[INSERT TURING WAY TABLE]

The different dimensions of reproducible research described in the matrix above have the following definitions, taken from the Turing Way booklet (Bowler et al., 2019):

- **Reproducible**: A result is reproducible when the *same* analysis steps performed on the *same* dataset consistently produces the *same* answer.

- **Replicable**: A result is replicable when the *same* analysis performed on *different* datasets produces qualitatively similar answers.

- **Robust**: A result is robust when the *same* dataset is subjected to *different* analysis workflows to answer the *same* research question (for example one pipeline written in R and another written in Python) and a qualitatively similar or identical answer is produced. Robust results show that the work is not dependent on the specificities of the programming language chosen to perform the analysis.

- **Generalisable**: Combining replicable and robust findings allow us to form generalisable results. Note that running an analysis on a different software implementation and with a different dataset does not provide generalised results. There will be many more steps to know how well the work applies to all the different aspects of the research question. Generalisation is an important step towards understanding that the result is not dependent on a particular dataset nor a particular version of the analysis pipeline.

### Defining Open Science

The Organisation for Economic Cooperation and Development defines open research as the practice of making “the primary outputs of publicly funded research results – publications and the research data – publicly accessible in a digital format with no or minimal restriction” @heise2020OpenAccessOpen. In order to achieve this openness, it is suggested that each element of the process should:

1.	**Be publicly available**: It is difficult to use and benefit from knowledge hidden behind barriers such as passwords and paywalls.

2.	**Be reusable**: Research outputs need to be licensed appropriately, so that prospective users know any limitations on re-use.

3.	**Be transparent**: With appropriate metadata to provide clear statements of how research output was produced and what it contains.

The Turing Way booklet offers a good starting guideline on what the process of creating open research looks like, including definitions around open data, open source software, open hardware, open access and open notebooks. The Open Definition also offers a set of principles that define “openness” in relation to data and content @OpenDefinitionOpen. In relation to describing openness in research, “open scholarship” is an additional and helpful concept that extends the definition further. It relates to making additional aspects of scientific research open to the public. For example, having open educational resources available to the public to be re-used and modified; or ensuring principles of equity, diversity, inclusion are followed, i.e. ensuring science is open to anyone without barriers based on factors such as race, background, gender, and sexual orientation; and citizen science, allowing for the inclusion of members of the public in scientific research. 

Creating open practices has multiple benefits. Firstly, researchers can benefit from it first hand by creating open access articles, as these have been shown to be cited more often @mckiernan2016HowOpenScience. Another benefit of openness is that while research collaborations are essential to advancing knowledge, identifying and connecting with appropriate collaborators is not trivial. Open practices can make it easier for researchers to connect by increasing the discoverability and visibility of one’s work, facilitating rapid access to novel data and software resources, and creating new opportunities to interact with and contribute to ongoing communal projects. Creating science that follows the open definitions above can therefore also foster a deeper sense of community, which contrasts starkly with the usual competitiveness of science. 

Of course it is worth noting that open science it’s not just “sharing absolutely everything”, as many fields of science involve working with sensitive personal data, with medical research being the most obvious example. Privacy and data protection, as well as consent, and national and commercially sensitive data can be some of the most common examples of when data cannot always be open @regulation2016RegulationEU2016. If access to data needs to be restricted due to security reasons, however, the justification for this should be made clear. Free access to and subsequent use of data is of significant value to society and the economy. That data should, therefore, be open by default and only as closed as necessary. 

### Why is reproducibility and open science important?
During my PhD work so far, one aspect of the research that has come with quite a lot of struggle is to find accurate parametrization of values for protein dynamics. This is a known issue for most of us who create computational models of biological systems. @wieber2020ModelsParameterizationSoftware call it an “epistemic opacity” when talking about lack of clarity in Computational Chemistry, where this opacity is entangled in methods and software alike. 

This of course leads to reproducibility issues, and as this unfolds, it becomes clear that the “untrustworthiness” of research is also an issue for many other researchers. In fact, a survey of 1576 scientists published in Nature @baker2016500ScientistsLift reported that over 70% of the participants failed to reproduce others’ experiments and over 50% failed to reproduce their own results. 

Interestingly, @tiwari2021ReproducibilitySystemsBiology, assessed the reproducibility of 455 mathematical models in systems biology and found that about 50% of published models were not reproducible either due to incorrect or missing information in the manuscript. Having reproducibility standards like the ones offered by the frameworks discussed above, as well as having in mind something like the reproducibility scorecard introduced by @tiwari2021ReproducibilitySystemsBiology (table 2), can be used to overcome these issues. 

<table>
  <tr>
   <td>Score:
   </td>
   <td> 
   </td>
  </tr>
  <tr>
   <td><strong>1</strong>
   </td>
   <td>Are the mathematical expressions described in the manuscript/supplementary material?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>2</strong>
   </td>
   <td>Are the parameters and entity initial levels listed (as a table) in the manuscript/supplementary material?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>3</strong>
   </td>
   <td>Are simulation conditions including software/programming environment, algorithm, changes in parameters/concentration/states and any data normalization described under each simulation figure or attached as a supplementary material?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>4</strong>
   </td>
   <td>Are the model code(s) for the mathematical expression and simulation shared publicly?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>5</strong>
   </td>
   <td>Are the model codes available in standard formats, e.g. SBML, COMBINE archive, SEDML and are syntactically validated?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>6</strong>
   </td>
   <td>Are the model codes deposited in a relevant open model database?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>7</strong>
   </td>
   <td>Are the model codes well documented to unambiguously identify model entities/variables? (with additional annotation of reactions, mathematical expressions, events, conditions, etc. when relevant.) Are the models in standard formats such as SBML and COMBINE Archive are semantically enriched, i.e. annotated with controlled vocabularies such as Gene Ontology and ChEBI and database resources such as Gene Ontologies?
<p>
 
   </td>
  </tr>
  <tr>
   <td><strong>8</strong>
   </td>
   <td>Are the numerical results shared publicly along with the model codes?
<p>