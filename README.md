# Morinlab-manuscript Format

This is a quarto extension to simplify the writing of the manuscripts in the Morin Lab.


## Installing

```bash
mkdir my_morinlab_manuscript
cd my_morinlab_manuscript
quarto use template morinlab/morinlab-manuscript
```
While executing the last command, the prompt will ask you 3 questions:

- `? Do you trust the authors of this template (Y/n) ›`  Here, answer `Y`
- `? Create a subdirectory for template? (y/N) ›` Here, answer `N`
- `? Would you like to continue (Y/n) ›` Here, answer `Y`

This will install the extension and create an example qmd file that you can use as a starting place for your article.

## Using

After installation, the directory will be populated with required files and directories. The support files are placed in the directory `src/`, while the main required files are in the directory home.

```
.
├── _extensions
│   └── morinlab
├── my_morinlab_manuscript.qmd
├── _quarto.yml
├── src
│   ├── authors.yaml
│   ├── blood.csl
│   ├── process_authors.R
│   └── references.bib
├── SupFig.qmd
└── SupTab.qmd

3 directories, 8 files
```

Described below are several main components for the manuscript:

### Author list

The list of authors can be assembled by modifying the `src/authors.yaml` file. The author list will be composed according to the order of the authors in this file. Each author's affiliation can be specified through a series of associated abbreviation-full descriptor pairs, with examples for SFU, BC Cancer, and CLC already pre-filled for you. The authors with equal contributions, as well as corresponding author, are specified through the optional `attributes` key. The affiliations will be auto-numbered and the corresponding numbers will be auto-associated with each author.

### Manuscript formatting and submission style

As different journals require different formatting styles, we can prepare the manuscript accordingly. The template is pre-formatted for you according to the _Blood_ journal guidelines. When necessary, the style can be adjusted through the `.csl` file. Please head over to the github repository [Styles](https://github.com/citation-style-language/styles/tree/master) that hosts a large collection of journal styles. Since github only displays 1,000 files, you can search for your journal after pressing `T` on the page. This will show you the `.csl` file for your journal. Download it to the `src/` of `my_morinlab_manuscript` folder and modify the file `_quarto.yml` to point to the file you just downloaded. The new style will then be automatically applied during rendering.

### Manuscript content

The manuscript content can be written directly in the `my_morinlab_manuscript.qmd` file - please note that the exact name of this file will match the name of the folder. The abstract, acknowledgements, COI, and data availablity statement can be edited through the `src/authors.yaml` file and will be auto-populated during the manuscript rendering.

### References

The template file includes example on how to insert a single or multiple references. The referencing style, ordering, and the content of each reference is dictated by the journal style. The references are contained in the bibTex format and are contained in the file `src/references.bib`. If you are using Zotero, the references can be exported directly as bib file.

### Supplemental Figures

The provided template file `SupFig.qmd` contains structure and example of how to generate single pdf file with supplemental figures. You can follow the provided example to edit it with relevant code that generates your supplemental figures, and re-use the provided example to generate more supplemental figures. If you do not have any supplemental figures to include, simply delete the file `SupFig.qmd`.

### Supplemental Tables

The provided template file `SupTab.qmd` shows how the single Excel file with one table/sheet can be generated directly from R code. Please follow the provided examples to populate it with relevant code. If you do not have any supplemental tables to include, simply delete the file `SupTab.qmd`.

### Rendering manuscript

Once the content is populated and adjusted accordingly, you can render the full content of the manuscript by running a single command:

```bash
quarto render
```

This will automatically render all qmd files in the directory and generate the `my_morinlab_manuscript.docx`, `Supplemental_Figures.pdf`, and `Supplemental_Tables.xlsx` files to be circulated with co-authors directly.
