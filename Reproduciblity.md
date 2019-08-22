What is reproducibility?
========================

"An article about computational results is advertising, not scholarship.
The actual scholarship is the full software environment, code, and data,
that produced the result." - Claerbout and Karrenbach, 1992

Reproducibility in software/science refers to the ability of others to
repeat your analyses and come up with the same result. Traditionally,
the way scientists work is not amenable to reproducibility - code is
scattered and highly customized, the steps taken to perform an analysis
are not documented and/or shared, and the data for the analyses are kept
private. Although there are of course cases where data must be
protected, we encourage striving for reproducibility when possible. Many
scholars have thought and written much about reproducibility that I will
not repeat here, but a good starting place is rOpenSci's
[reproducibility
handbook](https://ropensci.github.io/reproducibility-guide/sections/introduction/).

The NOAA Fisheries Toolbox is an example of a storage repository for
common software tools, tools which encourage reproducibility by making
shared software accessible to and tested by other researchers. However,
common software tools are only one component of making research
reproducible. A large part of reproducibility is ensuring others can
follow the steps and set up the same data and environment as you did to
complete a task. Tools to enable and simplify this fall broadly into a
number of categories: 1. literate programming tools (i.e. `Rmarkdown`,
`knitr`, Doxygen) 2. provenance-tracking tools, in other words, tools to
track to origin and chronology of data, code, figures, and results (i.e.
`drake`, Kepler), 3. interactive notebooks, and 4. tools to
capture/emulate a specific software environment.

Literate programming
====================

-   [Using Rmarkdown for scientific
    writing](https://github.com/karthik/markdown_science)
-   [bookdown](https://bookdown.org/yihui/rmarkdown/html-document.html)

Provenance tracking
===================

-   [drake](https://ropensci.github.io/drake/)

Notebooks
=========

-   [R notebooks](https://bookdown.org/yihui/rmarkdown/notebook.html)
-   [Jupyter for R with
    conda](https://anaconda.org/chdoig/jupyter-and-conda-for-r/notebook)

Capturing/emulating software environments
=========================================

-   [Workflow/paths](https://www.tidyverse.org/articles/2017/12/workflow-vs-script/)
-   [Binder](https://mybinder.org/)
-   [Holepunch- a.k.a. creating Docker instances from R Github
    repos](https://github.com/karthik/holepunch)
