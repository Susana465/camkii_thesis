---
bibliography: [references.bib]
---

# Open and reproducible science
There is increasing awareness, need and want for more open, reproducible and overall FAIR science. In the past 60 years, science has been speeding up, and the publish or perish mindset is not uncommon among scientists who need to publish more and more in order to get more funding [REFERENCES]. Hand in hand with this fast-science, has come something we now call a "reprodicibility crisis", where [enter facts of reproducibloty crisis] have found [facts].

_Much of the criticism and comment about reproducibility and solutions to the crisis—both real and perceived—focuses on statistics and methodology. In the past decade, statisticians have shown how statistics may be unintentionally misused or, in some cases, intentionally abused as researchers try to produce results that appeal to professional colleagues and attract potential funders._ https://www.nature.com/articles/s41746-019-0079-z

_Several methodologists have pointed out [9–11] that the high rate of nonreplication (lack of confirmation) of research discoveries is a consequence of the convenient, yet ill-founded strategy of claiming conclusive research findings solely on the basis of a single study assessed by formal statistical significance, typically for a p-value less than 0.05. Research is not most appropriately represented and summarized by p-values, but, unfortunately, there is a widespread notion that medical research articles should be interpreted based only on p-values. Research findings are defined here as any relationship reaching formal statistical significance, e.g., effective interventions, informative predictors, risk factors, or associations. “Negative” research is also very useful. “Negative” is actually a misnomer, and the misinterpretation is widespread. However, here we will target relationships that investigators claim exist, rather than null findings._ https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124

_Whether the large and growing preponderance of these positive results in the published scientific literatures is a cause, a symptom, or simply a facilitator of irreproducibility doesn’t particularly matter. What is important is that the lopsided availability of positive results (at the expense of negative ones) distorts our understanding of the world we live in as well as retards the accumulation of the type of knowledge that science is designed to provide._

this is something key i wanna reiterate in this thesis:

_1. Even if the majority of these positive effects are not the product of questionable research practices specifically designed to produce positive f indings, and 2. If an unknown number of correct negative effects are not published, then 3. Other investigative teams (unaware of these unpublished studies) will test these hypotheses (which in reality are false) until someone produces a positive result by chance alone— or some other artifact, which 4. Will naturally be published (given that it is positive) even if far more definitive contradictory evidence exists— therefore contributing to an already error- prone scientific literature._ (The problem with science : the reproducibility crisis and what to do about it)

bias: reporting bias, publication bias, social bias

 Selective or distorted reporting is a typical form of such bias.

 what story do i wanna tell here? 

I have spent a long time of my phd thinking about reproducibility (insert turing and ols poderation graphs and ideas of things to do), and I have found that this is actually the part of my phd I am most excited about. In this thesis, I have to write about reproducibility in a way that people know the background and where I am coming from, but at the same time not get lost in all the ideas and philosophical discussions to be had around the topic. I have also therefore made practical applications to the biological research at hand and tried to provide evidence for how I am attempting to not only practice what i preach but also to showcase how emphasis in reproducibility during a phd is possible and helpful. 

## Defining reproducibility vs replicability
There is a long history of these terms being used interchangeably, or their meanings being swapped depending on the field of study [@claerbout1992ElectronicDocumentsGive], [@ivie2018ReproducibilityScientificComputing],[@plesser2018ReproducibilityVsReplicability]. For example, a review on the usage of reproducible/replicable meanings [@barba2018TerminologiesReproducibleResearch] showed that most papers and disciplines use the terminology as defined by Claerbout and Karrenbach, whereas microbiology, immunology and computer science tend to follow the Associtation for Computing Machinery use of reproducibility and replication given by [@ivie2018ReproducibilityScientificComputing]. In political science and economics literature, both terms are used interchangeably. So this quickly shows how having a lack of agreement on such definitions can add even more confusion to the mix. 

Here, we use the definition used by [@turingwaycommunity2019TuringWayHandbook], where reproducible research is understood as "_work that can be independently recreated from the same data and the same code that the original team used_". Reproducible, replicable, robust and generalisable have different meanings as described in the table below.

![How the Turing Way defines reproducible research.](22-reproducibility-figures/repro_definintions.PNG){#fig-repro-definitions width=65%}

- **Reproducible research**: is obtained when same analysis is performed on the same data, to produce the same results.

- **Replicable research**: refers to conducting the same analysis on different datasets, resulting in qualitatively similar outcomes. 

- **Robust research**: entails subjecting the same dataset to different analysis workflows to address the same research question, such as employing distinct pipelines in R and Python. Robustness demonstrates that findings can remain consistent regardless of different methods used for analysis, indicating validity and resilience to various factors like changes in conditions or methods (such as different programming languages).

- **Generalisable research**: refers to findings or conclusions that can be applied beyond the specific context in which they were derived. It indicates that the results are not limited to a particular dataset, methodology, or experimental setup, but instead can be extended to broader populations, situations, or conditions. By combining replicable and robust research, we can obtain more generalisable results. Generalisability is important as it allows us to make inferences for bigger groups of datasets, for example a target population, by only studying a part of it (the sample).

## Defining Open Science

Open science is an approach to the scientific process that promotes cooperative work and new ways of diffusing knowledge accessible to everyone, without barriers such as paywalls or restrictions on use. By making research more accessible and transparent, open science seeks to accelerate scientific progress, enhance reproducibility, and increase the societal impact of research findings. In order to achieve this openness, [@turingwaycommunity2019TuringWayHandbook] and [@heise2020OpenAccessOpen] suggest that the research process should:

1.	**Be publicly available**: It's hard to benefit from knowledge hidden behind barriers like passwords and paywalls.

2.	**Be reusable**: Research outputs should be licensed adequately, informing potential users of any restrictions on reuse.

3.	**Be transparent**: With appropriate metadata to provide clear statements of how research output was produced and what it contains.

Creating open practices has multiple benefits. Firstly, researchers can benefit from it first hand by creating open access articles, as these have been shown to be cited more often [@mckiernan2016HowOpenScience]. Another benefit of openness is that while research collaborations are essential to advancing knowledge, identifying and connecting with appropriate collaborators is not trivial. Open practices can make it easier for researchers to connect by increasing the discoverability and visibility of one’s work, facilitating rapid access to novel data and software resources, and creating new opportunities to interact with and contribute to ongoing communal projects. Creating science that follows the open definitions above can therefore also foster a deeper sense of community, which contrasts starkly with the usual competitiveness of science. 

Open science is not “sharing absolutely everything”, as many fields of science involve working with sensitive personal data, with medical research being the most obvious example. Privacy and data protection, as well as consent, and national and commercially sensitive data can be some of the most common examples of when data cannot always be open [@regulation2016RegulationEU2016]. If access to data needs to be restricted due to security reasons, however, the justification for this should be made clear. Free access to and subsequent use of data is of significant value to society and the economy. That data should, therefore, be open by default and only as closed as necessary. 

## Why are reproducibility and open science important?
During my PhD work so far, one aspect of the research that has come with struggle is to find accurate parametrization of values for protein dynamics. This is a known issue for most of us who create computational models of biological systems. @wieber2020ModelsParameterizationSoftware call it an “epistemic opacity” when talking about lack of clarity in Computational Chemistry, where this opacity is entangled in methods and software alike. 

This of course leads to reproducibility issues, and as this unfolds, it becomes clear that the “untrustworthiness” of research is also an issue for many other researchers. In fact, a survey of 1576 scientists published in Nature [@baker2016500ScientistsLift] reported that over 70% of the participants failed to reproduce others’ experiments and over 50% failed to reproduce their own results. 

Interestingly, @tiwari2021ReproducibilitySystemsBiology, assessed the reproducibility of 455 mathematical models in systems biology and found that about 50% of published models were not reproducible either due to incorrect or missing information in the manuscript. Having reproducibility standards like the ones offered by the frameworks discussed above, as well as having in mind something like the reproducibility scorecard introduced by [@tiwari2021ReproducibilitySystemsBiology] (@tbl-scoreboard), can be used to overcome some of these issues.

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
