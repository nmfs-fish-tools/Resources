Introduction
------------

Most tools have dependencies on at least one other software package; if
you write in `R` you likely depend on both the version of the `R`
language and other `R` packages, if you write in `C` you may need to use
specific compilers, and nearly all software will be supported
differently by different operating systems. This guide aims to clarify
how to declare and manage software dependencies, as well as how to deal
with backwards compatibility.

Declaring/listing dependencies
------------------------------

If you do nothing else, a first and necessary step is to make it *very
clear* to the user what dependencies your software needs to run. This
sounds simple, but very few tools actually do this adequately. One of
the best places to declare dependencies is on your Github repository's
README page. You can use badges to do this for things like the `R`
version:

<a href="https://cran.r-project.org/package=drake"><img src="https://www.r-pkg.org/badges/version/drake" alt="CRAN"></a>

If your software uses a different platform, you can create a (custom
badge)\[<https://shields.io/>\] to outline dependencies in the same way,
or you can simply create a "Dependencies" header in the README and list
the dependencies out.

### The DESCRIPTION file in R packages

In `R`, dependencies are listed within the package directory in a file
named "DESCRIPTION" (note, there is no file extension) that is
auto-generated when you turn a directory into a package directory. You
should include which `R` version is needed to run your package under
"Depends:". There are two ways to include package dependencies - `R`
packages that are required for your software to run should be declared
under the "Imports:" section of your DESCRIPTION file, while packages
that are merely helpful (i.e. to run examples or the user manual) can be
listed under "Suggests:". Ideally, you can also specify which version of
each package your package depends upon in parentheses following the
package name.

Some best practices worth noting: it is annoying to users if a package
has a huge number of dependencies, so try to limit how many dependent
packages you call. If a package is only used in one or two "optional"
functions, you can list it under "suggests." Secondly, requiring a
package will make sure it is downloaded when your package is installed,
however, it will not load it for the user. Rather than making the user
need to manage this, you should reference package functions using
`<packagename>::<function>` or, if you are using many functions from the
same package, put `@import package` in the NAMESPACE file of your R
package. Many more details are covered in Hadley Wickham's `R` package
(book)\[<http://r-pkgs.had.co.nz/description.html#dependencies>\].

    ## in DESCRIPTION file
    Depends: R (>= 3.1.0)
    Imports:
        dplyr,
        ggvis
    Suggests:  
        dplyr,
        ggvis
    ## in NAMESPACE file
    importFrom(methods,setRefClass)

Backwards compatibility
-----------------------

It is admirable to want to make software work with older software
versions of dependent packages. However, it is irresponsible to say
software is backwards compatible unless the software is explicitly
tested with multiple versions. This can create headaches as the number
of situations to test explodes very quickly. For this reason, we think
it is important to maintain backwards compatibility only when previous
versions of software have a legitimate reason for use and continue to be
used by a large variety of users. If it is expected that users continue
to move forward (for example, updating their `R` version), there is no
need to support backwards compatibility.

If backward compatibility is maintained, we recommend using Github
versions to release older, backwards compatible software. This way,
newer software can continue to be released while a stable build that
supports older software versions is maintained. Each older version
should have its own test cases which are run using the appropriate
software versions. This means that if you find a critical error in your
code that existed in prior versions, you can deploy a "hotfix" to the
old version and ensure it still works. For more on this, see the
resource guide on versioning and release management. If you decide to
follow this approach, make sure the dependencies of each of your release
versions within your Github repositories are clearly outlined.

It is rarely a good idea to have many "if"" statements throughout your
code that detect the users' version and modify code behavior
accordingly. This makes it harder to test and understand code behavior,
and it makes everything slower because conditional statements in
programming are highly costly. It means you will need to run test cases
for every version at each build time, slowing down continuous
integration. It is also not very user-friendly, as it requires users who
may want to stick with an older code version to constantly update to
newer versions as they are released. At maximum, we recommend
maintaining compatibility for two software versions only.
