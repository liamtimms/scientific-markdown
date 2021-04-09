# Scientific Markdown

Scripts and templates for writing a scientific paper in markdown formatting. Make sure you view the actual templates in "Raw" markdown, github does not handle the yaml header appropriately. You can either hit the "raw" button here or clone the repo and go through it with your prefered text editor.

```bash
git clone https://github.com/liamtimms/bashscripts.git
```

## Why?

### Current solutions

- LaTeX

  - Pros:
    - easily the best existing language for dealing with complex formatting and type setting
    - many journals provide templates for use with LaTeX
    - FOSS compilers and plain text source files
  - Cons:
    - often uncomfortable for collaborators outside of physics, math, and comp sci
    - difficult to parse as plain text while writing (verbose syntax)
    - not all journals accept LaTeX source files

- Microsoft Word

  - Pros:
    - very simple to get started in
    - everyone knows how to use it
    - journals always accept it (in my experience)
  - Cons:
    - type-setting nightmare once you have a complex document
    - unpredictable formatting
    - proprietary (can lose access to your own work)
    - difficult/impossible to work with actual source files (`docx` is actually a `zip` archive of some really complex `XML` files)

### Markdown + Pandoc

_Compiles to both MS Word (`.docx`) and LaTeX (`.tex` or `.pdf` with LaTeX as an intermediate step) from a single source file._ You can choose the pros or cons of either based on your current need without having to deal with complex processing in either. Additionall for markdown itself:

- Markdown

  - Pros:
    - very simple to get started in
    - many people already know how to use it (used for formatting on websites - github, reddit, etc.)
      - if you don't know it you can try <https://www.markdowntutorial.com/>
    - easy to write and parse (simple syntax)
    - automatic formatting available ([prettier](https://prettier.io/))
    - FOSS compilers and plain text source files
    - many editors offer good support
    - bibtex based citations which translate to both Word and LaTeX
  - Cons:
    - cannot be submitted for journals or assigments directly
    - may require you to backport collaborator's changes from docx which wastes time

#### Goals for this repo:

1. keep templates as simple as possible

2. cover all common issues which are not clear in existing templates

3. explain the syntax using the syntax

4. maintain maximum compatibility for both Word and LaTeX where possible

5. never require more than one compilation command

6. never require/push the use of an external website

## Templates

### General Template

Goes over the basics for a general purpose document.

PDF output:

```bash
pandoc ${inputfile} --filter pandoc-crossref -C -N --highlight-style zenburn -o outputfile.pdf
```

MS Word output:

```bash
pandoc ${inputfile} --filter pandoc-crossref -C --csl ieee.csl -o outputfile.docx
```

### Thesis

Should be looked at in addition to the `general_template.md`. Requires additional install of [pandoc/lua-filters](https://github.com/pandoc/lua-filters).

PDF output:

```bash
pandoc --filter pandoc-crossref --lua-filter=/${some_path}/lua-filters/short-captions/short-captions.lua -C -N --highlight-style zenburn -o outputfile.pdf ${inputfile}
```

note: You can see my script for this to automatically recompile documents on changes here: <https://github.com/liamtimms/bashscripts/blob/master/pdfpreview>

# See also:

- [A paper covering a much more indepth version of this idea](https://peerj.com/articles/cs-112/)

- [Connor McDaniel's video which inspired me to start with markdown.](https://youtu.be/wh_WGWii7UE)

- [Castel's famous blog post](https://castel.dev/post/lecture-notes-1/)

- [A way bigger set of templates aimed at generating LaTeX only,](https://github.com/Wandmalfarbe/pandoc-latex-template)

- [More complex version of the same idea but template is not in english and it is pushing some website.](https://github.com/maehr/academic-pandoc-template)
