---
bibliography: [references.bib]
---

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

Interestingly, @tiwari2021ReproducibilitySystemsBiology, assessed the reproducibility of 455 mathematical models in systems biology and found that about 50% of published models were not reproducible either due to incorrect or missing information in the manuscript. Having reproducibility standards like the ones offered by the frameworks discussed above, as well as having in mind something like the reproducibility scorecard introduced by @tiwari2021ReproducibilitySystemsBiology (@tbl-scoreboard), can be used to overcome these issues.

|Score:|Questions:| 
|--     |:---------|
|1      | Are the mathematical expressions described in the manuscript/supplementary material?|
|2      |Are the parameters and entity initial levels listed (as a table) in the manuscript/supplementary material?|
|3      |Are simulation conditions including software/programming environment, algorithm, changes in parameters/concentration/states and any data normalization described under each simulation figure or attached as a supplementary material?|
|4      |Are the model code(s) for the mathematical expression and simulation shared publicly?|
|5      |Are the model codes available in standard formats, e.g. SBML, COMBINE archive, SEDML and are syntactically validated?|
|6      |Are the model codes deposited in a relevant open model database?|
|7      |Are the model codes well documented to unambiguously identify model entities/variables? (with additional annotation of reactions, mathematical expressions, events, conditions, etc. when relevant.) Are the models in standard formats such as SBML and COMBINE Archive are semantically enriched, i.e. annotated with controlled vocabularies such as Gene Ontology and ChEBI and database resources such as Gene Ontologies?|
|8      |Are the numerical results shared publicly along with the model codes?|

:Reproducibility Scorecard suggested by @tiwari2021ReproducibilitySystemsBiology {#tbl-scoreboard}


We might like to think that scientific research is objective, and simply measuring reality. The reality, however, is that many decisions will be taken when doing research, and these decisions will impact the results of that research. If decisions are not well documented, the validity of the research can become more opaque. Likewise, an important issue in scientific work that makes it difficult for other people to build on is that materials or details of analyses are not freely shared, which is why open science is important when overcoming these issues. 

When it comes to publishing results in science, there is a bias for “positive results” publications, which neglects insights from negative results that could aid in further understanding what works and what doesn’t work for different types of studies @mlinaric2017DealingPositivePublication. Underreporting of negative results introduces bias into meta-analysis, which consequently misinforms researchers, doctors, policymakers and the public in general. Additionally, more resources are potentially wasted on already disputed research that remains unpublished and therefore unavailable to the scientific community. The current competitive mindset of scientific research contributes and is worth mentioning as an important factor for this desire to find positive and novel outcomes in studies, which can sometimes lead to misinterpretation and distortion of results @fanelli2010PressuresPublishIncrease. 

These are some of the reasons why clarity, reproducibility and noting of possible unaccounted for biases, have been an important part of the way that I do research, and I have made as much of my work as reproducible and open possible, taking new items from the Turing Way booklet and Data Hazards project as main inspiration to do so.  
