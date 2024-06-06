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
camkii_thesis/               # Root directory
├── _quarto.yml              # Configuration file for Quarto
└── chapters-figures/        # Subdirectory for chapters figures
    ├── figures.png
├── index.qmd                # The main entry point of your dissertation
├── 10-intro.qmd             # Directory for the introduction part, containing subchapters
│   ├── 11-philosophy.md
├── 20-background.md         # Directory for the background part, containing subchapters.
│   ├── 21-complex_systems.md
│   ├── 22-reproducibility_open_science.md
│   ├── 23-memory_learning.md
│   ├── 24-why_modelling.md
│   ├── 25-ssa_ode.md
│   ├── 26-rule_based.ipynb
│   ├── 27-software.md
│   └── 28-necklace_numbers.rmd
├── 30-methods.md
├── 40-results.md
├── references.qmd           # File for managing references
├── references.bib           # There's different .bib files that need organizing. 
```