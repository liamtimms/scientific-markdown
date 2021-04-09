---
title: "Your Title Here"
subtitle: "If you really need a subtitle you do it like this."
author: Liam Timms, your other authors
indent: True
geometry: margin=0.6in
secnumdepth: 3
linkReferences: true
toc: true
figPrefix:
  - "Fig."
  - "Figs."
tblPrefix:
  - "Table"
  - "Tables"
secPrefix:
  - "Sec."
  - "Secs."
eqnPrefix:
  - "Eq."
  - "Eqns."
bibliography: ./library.bib
csl: ./ieee.csl
date: \today
header-includes:
  - \usepackage{float}
  - \floatplacement{figure}{H}
---

# Introduction {#sec:intro}

This is a section. You can refer to this section using [@sec:intro]. If you want to cite literature you can do so with a citation [@important_paper]. Note that tables, sections and figures will all get some prefix in front of them (in labeling, referencing and compiling) but citations are just `@` followed by the label defined in the `.bib` file.

<!--
This is a comment. It will not appear in compiled versions.
-->

## What is that stuff in the header? {#sec:header}

1. `indent` leads to hanging indents rather than spaced out paragraphs.
2. `geometry` allows you to set options for LaTeX's geometry package. Usually just changing the margin is sufficient.
3. `toc` indents a table of contents, only useful for long documents.
4. `secnumdepth` determines how many subsections deep are assigned numbers.
5. `secPrefix` `figPrefix`, `tblPrefix`, etc. these set the text used to refer to a specific type of reference object ("Fig. 1" rather than "figure 1" for example)
6. `bibliography` should point to a `.bib` "bibtex" library file. I commonly output this from Zotero but Mendeley and other literature managers work too. You'll need the keys from this file to make citations.
7. `csl` this is what determines the formating of references. Most of the time the IEEE standard is fine but alternatives canbe found here:
8. `date` this is totally optional but here we are calling the LaTeX command `\today` to add the date the document is compiled.
9. `header-includes` these are additional options which will get inserted into the LaTeX header before pdf compilation. I recommend these two in particular to change the default behavior of "floats" in LaTeX but more could be added.

I also recommend setting a nicer font for better computer screen reading in the compiled versions. Personally, I set `fontfamily: utopia` but you may want to checkout which fonts are available on your system.

## Why Markdown? {#sec:plaintext}

# Methods {#sec:methods}

You can refer to tables with [@tbl:imagequality]. If you want to add a footnote you can just do [^footnote].

[^footnote]: this is a footnote.

# The Pandoc commands and recommendations

Subsections use the same label and reference syntax as full sections (see [@sec:plaintext]). Inline math uses the same syntax as LaTeX, $\gamma=m\chi+\beta$.

Table: This is a table caption. I strongly recommend using the table syntax below. It works by far the best when combined with Prettier. The ":" determines alignment and it's also one of the most readable options.
{#tbl:tablename}

|        | A           |     B      |           C |
| -----: | :---------- | :--------: | ----------: |
|   Mean | $20\pm5$    |    $13$    |         $9$ |
| Median | $27$        |    $13$    |        $10$ |
|   Mode | $546\pm189$ | $54\pm144$ | $8000\pm82$ |

We need to end with a blank section for "References." This will be filled out during `pandoc` citation processing (`-C` options).

## Figures

![This is a normal figure. Here is the caption.](./figs/figurefilename.png){#fig:figurelabel}

![This is a figure with an additional option. Note that the figure label comes last and the other options don't need a #. Options are passed to LaTeX during compilation.](./figs/smallerfigure.png){ height=50% #fig:threshold }

<div id="fig:multifigure">
![a caption for the first part](./figs/part1.png){#fig:part1}

![a caption for te second part](./figs/part2.png){#fig:part2}

This is a multi-part figure where you can refer to each section independently and each is coming from its own file. In general, I do not recommend this but I have found it useful before. The caption for th whole figure is given like this.

</div>

# References
