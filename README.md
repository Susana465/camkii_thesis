## How to use this repository
- You don't need to have installed Quarto to work with the scripts in this repo, as you can read the markdown files without Quarto. 
- However, I recommend that in order to get the full rendering of the structure in pdf and html formats, you download and work with Quarto either via VS code or RStudio. 
- More instructions on how to get started with Quarto can be found [here](https://quarto.org/docs/tools/vscode.html).

## How to contribute
- You can branch from 'main' and add/remove content that way, and give feedback by adding comments.
- You can also render the document into pdf, and add comments that way if you prefer that.
- Add issues for tasks that need actioning.
- Close issues that have been actioned.

## Repository and Thesis Structure
The repository is organized to mirror the structure of the thesis document. The following project file structure provides an overview of the thesis' structure. Consult the code in the repository for a better understanding of how Quarto ties everything together. 

You might find some files in the repository that are not part of the below diagram, this is likely because I have added them as extra notes for myself, or I have not decided yet where to put their content. 

```python
camkii_thesis/               # Root directory of the thesis project
├── _quarto.yml              # Quarto configuration file
├── chapters-figures/        # Folder containing all chapter figures
│   ├── figures.png
│
├── index.qmd                # Includes: Abstract, Lay Summary, Acknowledgements,  List of Figures, List of Abbreviations, Publications and Author Contributions Declaration
│
├── 10-intro.qmd             # Chapter: General introduction and chapter overview
├── 20-intro-biology.qmd     # Chapter: Biological Research Background
├── 30-modelling_background.qmd  # Computational Modelling Background
│
├── 20-repro_open.qmd        # Chapter: Open, Reproducible and Ethics-focused PhD
├── 20-data-hazards.qmd      # Chapter: A Case Study in Ethical Reflection: Data Hazards in this PhD
│
├── 30-model.qmd             #5 Chapter: In Silico Model of CaMKII, NMDARs, and Associated Signalling Molecules
├── 40-results.qmd           # Results, summary and discussion chapters
│
├── publications.qmd         # List or discussion of related publications
│
├── references.qmd           # Reference management (Quarto format)
├── references.bib           # Bibliography file (may include multiple .bib sources)
```