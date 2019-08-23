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

The concept of literate programming was introduced by Donald Knuth. It
is a programming paradigm by which code is interspersed with text, in
the goal of making computer code more literate and follow the logic of
human thought and intention rather than adhering to a structure imposed
by the computer. Although literate programming approaches have been
criticized for being less efficient, when attempting to create a
reproducible tool, example, or user manual, it is usually more important
to clearly convey what the software is doing than to it in the fewest
lines of code. The most effective examples combine text and code, and we
recommend doing this in markdown when possible. Markdown is a framework
for converting text to HTML and has several benefits: it allows for
seamless integration of code, rich text, and equations, and it can
quickly generate web content (i.e. HTML pages) that can be quickly and
easily styled without the manual formatting and repositioning required
by LaTeX, for example. Below are a number of my favorite resources on
literate programming using Markdown. -
[Knitr](https://datacarpentry.org/rr-literate-programming/) - [Using
Rmarkdown for scientific
writing](https://github.com/karthik/markdown_science) -
[bookdown](https://bookdown.org/yihui/rmarkdown/html-document.html)

Provenance tracking
===================

Tracking provenance is explained in this excellent
[reference](https://rrcns.readthedocs.io/en/latest/provenance_tracking.html),
but in short refers to tracking the knowledge needed to recreate a
scientific result, from raw data, to filtered data, to the code used to
run the analysis, to the code used to create the result. This can be
thought of the software analogue to the lab notebook. There is overlap
between these categories; provenance tracking tools can include things
like notebooks (described below) and markdown (described above). They
can also include workflow tools, which track the steps in your workflow
and which inputs and outputs were used and produced at each time. I have
only used drake (for R, linked below) but there are a number of
alternative workflow management tools described in the linked article
above ([Kepler](https://kepler-project.org/),
[Taverna](https://taverna.incubator.apache.org/)). -
[drake](https://ropensci.github.io/drake/)

Notebooks
=========

In an even more direct parallel with the lab notebook concept, lately
more and more tools are available to create interactive notebooks. These
notebooks capture the benefits of literate programming approaches, as
they incorporate descriptive text with code. However, they go farther by
allowing real-time editing and re-running of the code. Notebooks can now
be created directly in RStudio. For a more flexible framework that can
be used across programming languages, - [R
notebooks](https://bookdown.org/yihui/rmarkdown/notebook.html) -
[Jupyter
notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html)

Capturing/emulating software environments
=========================================

Finally, a very important aspect of reproducibility is perhaps so simple
it is often overlooked. If a different version of software is used, or
if paths are set to be specific to the original author, it can create a
barrier to reproducible results. This might seem like a small issue, but
it often doesn't take much to dissuade someone from creating custom code
rather than re-using published, reproducible example. A really great
reference describing this can be found
[here](https://www.tidyverse.org/articles/2017/12/workflow-vs-script/).
Luckily, there are a number of tools you can use to capture software
environments, emulate them in remote instances or on different
computers, or simply clearly document the dependencies and versions
required to run your software. The cadillac way to do this is to use
virtual instances, such as virtual machines. You can use desktop
applications, such as VMware or VirtualBox, or remote instances using
virtual machines on cloud instances like Amazon Web Services (AWS) or
Microsoft Azure. Such instances can also be really helpful to test out
software to work on multiple environments; for example, if you are
programming on a Mac but would like to ensure Windows users can run your
code. More lightweight options for reproducing a work environment are
web-based remote containers for software environments.
[conda](https://docs.conda.io/en/latest/) and
[Docker](https://www.docker.com/) are two of the most widely-known and
used of these options. See below for more options for tools that
integrate R code with Docker instances (Binder), or conda via Jupyter
notebooks. - [Binder](https://mybinder.org/) - [Holepunch- a.k.a.
creating Docker instances from R Github
repos](https://github.com/karthik/holepunch) - [Jupyter and conda for
R](https://anaconda.org/chdoig/jupyter-and-conda-for-r/notebook)
