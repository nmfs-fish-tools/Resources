Introduction
------------

Every software tool requires documentation, and good documentation can
make the difference between someone using your code and no one using
your code. Moreso, good documentation can greatly reduce the amount of
issues/questions you have to answer directly from users, saving the
developer time. In general, the more documentation and guidance you can
provide via written or online resources, the better. However, at bare
minimum, there are three key types of documentation any software should
have: *code reference*, *user manuals*, and *examples.* Each of these
types of documentation is described below, along with links to resources
to simplify and improve documentation creation.

Code reference
--------------

Code reference is the type of documentation most people are familiar
with. It is also the easiest to create. There is no excuse for providing
insufficient code reference! Code reference consists of an article for
each function, class or object type (if using an object-oriented
language), and dataset in your software package. There is a consistent
and expected format for code reference, such that for each article, the
author is expected to provide:

-   a brief description of the function/class/dataset
-   a description of all of the function arguments, including what type
    of object (integer, string, etc.) each argument is, what the
    argument is named, acceptable values for the argument (if it must
    match a specific input), and the default value for the argument
-   a description of the object(s) returned from the function
-   an example detailing syntax of how the function is used
-   if you are referencing an object, you should detail the name, state
    variables, and methods associated with the object

All commonly-used programming languages and some IDEs (integrated
development environments) have a way to automatically create code
reference. In the `R` language, for example, the `roxygen` package
(sometimes called from the `devtools` package) will generate this
documentation for you if you add comments in apropriate places in an
`.R` file. Other programming languages use standards such as `doxygen`
(C/C++) or `sphinx` (Python). It is important you update this automated
documentation whenever you make changes to the code that affects the
documentation - i.e. changing the inputs or outputs of a function.
Updating the documentation (along with running automated tests and
conducting code review) should become an automatic part of your process
for pushing code changes.

### An R example of how to create code reference

In `R`, the syntax \``#` denotes comments that will be used to generate
documentation. An example of the comments written above an `R` function
to generate this documentation is provided below. Note you can use
markdown syntax within these comments if an `@md` tag is included; see
[here](https://cran.r-project.org/web/packages/roxygen2/vignettes/markdown.html)
for more.

This example is for a helper function that does an assignment of a
variable to a list slot. In addition to describing the behavior, the
inputs, and the outputs, there are extra tags: `@md` allows the use of
markdown syntax, `@export` makes this function an exported object of its
home package, and `@seealso` creates links in the documentation to
related packages.

    #' Assign environment variables to a list
    #' 
    #' A function that may be called by `lapply()` to assign all of the variables in the given environment to slots within a list. This
    #'
    #' @param X - the name of the variable in `function_env` to assign to the list slot named `X`
    #' @param function_env - the environment in which you want the function to search for the variable named `X`
    #' @param return_list - the list item you want to add the value of `X` to in the slot named `X`
    #' @return the `return_list` with the added elements
    #' @seealso [base::get()]
    #' @export
    #' @md
    assign_values <- function(X, function_env, return_list){
      return_list$X <- get(X, function_env)
      return(return_list)
    }

### Organizing code documentation

By default, sytems that auto-generate code reference will organize them
for you according to a standard. The standard way reference is organized
groups functions within their respective software packages (in R) or
header files (in C). A table that outlines all of the reference articles
associated with your software is essential - a user should be able to
scan down this list and click on individual functions to read articles
pertaining to each function/class. This will usually be generated for
you.

### Documenting datasets

You may need or want to provide datasets in your software; these are
particularly helpful to providing good examples. There are many
different ways to document data and we will not exhaustively detail them
here. However, we recommend you adhere to standard data formats and
provide at least some background information and metadata for each
dataset. A common vocabulary is schema.org's. If your software is an `R`
package, you should refer to this excellent
[guidance](http://r-pkgs.had.co.nz/data.html) from Hadley Wickham. You
may also want to provide dynamics links to online databases - many APIs
allow users to download data in a .JSON format, which can be converted
to `R` dataframes using the `jsonlite` package.

Examples
--------

We also require at least one complete example of how to use software.
The requirements to use this example must be installed with the
software, so that every user who downloads your software is able to copy
and paste the example, click "run", and expect for it to work. This may
require adding a testing dataset to your repository (see details above).
Further, the code from your example should be included in your testing
package and continuous integration, such that examples are always tested
and sure to work whenever changes are merged into the code.

It is the most helpful to provide unit examples in the code reference
(for example, with the `@example` tag in `roxygen()` comments) and
integrated examples somewhere in your Github repository. Integrated
examples are not necessary if your software consists of a number of
stand-alone functions whose inputs and outputs are not expected to be
piped to other functions. However, integrated examples are needed if
your users are expected to follow a workflow calling multiple functions,
or if they will need to define a class that can then initiate actions.
Integrated examples are nicely illustrated in a hybrid code/text format,
although they can be adequately explained in comments within a code
file. Some formats we recommend include markdown and Jupyter notebooks.

One best practice that is not required includes creating a shared space
for examples of your code, including your examples and user-generated
ones. You can do this by creating another Github repository within your
software organization.

User Manual
-----------

The most time- and labor-intensive type of documentation is a user
manual. A user manual may be dozens or hundreds of pages long and serves
as a comprehensive reference to using your software. The best user
manuals include example code syntax, textual descriptions of software
functionality, references to inherited or software your code is
dependent on, and often equations describing the mathematical equations
used within more mathematically complex functions. Creating and writing
a user manual can be expected to take several months, a good user manual
will usually need to be reviewed by at least one or a few other people,
and a user manual will need to be continously updated. However, an
effective user manual can link together discrete examples and code
reference in an extremely helpful way. Further, many user manuals count
towards peer-reviewed or "grey literature" publication titles.

We recommend using markdown or a similar markup language to write your
user manual. While some user manuals have been successfully written in
LaTeX or Microsoft Word, the amount of code contained in a typical user
manual makes such systems inefficient. Further, using a markup language
allows you to auto-generate some user manual content. Finally, using a
markdown-based syntax (a good example is `bookdown` in `R`) allows you
to easily create webpages from your user manual, which are much easier
to browse online as opposed to downloading a large .pdf or .docx file.
