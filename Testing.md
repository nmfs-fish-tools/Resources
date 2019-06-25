Introduction
------------

We recommend tool developers create *unit tests* and *integrated tests*
to introduce as many automated checks as possible to validate their
software. Once these test cases are created, they may be added to a
continuous integration tool (such as TravisCI) so that every time a pull
request is merged in on Github, this suite of tests is run.

Unit tests
----------

Unit tests test that a singular piece of code (i.e. a function or
method) does what it is intended to. The benefit of this type of test is
that it is relatively straightforward to create and can catch many
problems in software. The downside is unit tests are simplistic and
therefore somewhat tedious to create. Most software platforms or IDEs
have a way to auto-generate a skeleton of the unit test methods a user
might require. In the Eclipse IDE, for example, generating unit tests is
done via the pull down menu. Selecting "create unit tests" will generate
a skeleton test class for each of the classes/functions in your
software. These are usually stored in some kind of created "Tests"
folder.

### An R example of how to create tests

In `R`, the `testthat`
(package)\[<https://cran.r-project.org/web/packages/testthat/index.html>\]
assists in creation and running of unit tests for an R package. If you
have not already created an `R` package for your software, we recommend
checking out Hadley Wickham's book on the subject here.

After you write your package functions, you can create your test. Tests
are assumed to live in the subdirectory "tests" of a package. This
directory contains four classes of .R files that are denoted based on
the string they belong with. Helper files ("helper..") are run every
time the package is loaded, in other words, when `devtools::load_all()`
is called. Setup files ("setup..") are executed before tests, but not
when the package is loaded. This is a good place to store things like
dataset loads for data needed to run multiple tests. .R files starting
with "test.." are expected to contain tests and are executed in
alphabetical order. Teardown files ("teardown..") are executed after the
tests are run. These files should include things like cleaning up the
workspace by removing objects created during setup or testing. In this
same directory, you need to include a file named `testthat.R` that
contains the minimum code below if you want your test cases to be run
automatically:

    library(testthat)
    library(yourpackage)

    test_check("yourpackage")

Within that .R file, first use the `test_that()` function to create the
test. The goal here is to do simple validation on the function behavior.
Usually, within a call to `test_that()`, you will want to use one of the
`expect` functions provided by the package (i.e. `expect_equal`,
`expect_identical`, etc.). These allow you to compare the output of your
function with metrics calculated elsewhere. These are more robust than
the base R `if` and logic functions because they explicitly take into
account things like rounding error and miscasting. The example below
tests that three trigonometric functions return the expected result
using the `expect_equal` function.

    require(testthat)

    ## Loading required package: testthat

    ## Warning: package 'testthat' was built under R version 3.5.1

    # Create trigonometric function unit tests
    test_that("trigonometric functions match identities", {
      expect_equal(sin(pi / 4), 1 / sqrt(2))
      expect_equal(cos(pi / 4), 1 / sqrt(2))
      expect_equal(tan(pi / 4), 1)
    })

You can also test things like the structure of outputs and if erroneous
input causes the expected error, rather than silently failing.

    test_that("trigonometric functions throw an error with NULL input",{
      expect_error(sin(NULL))
    })

Integrated tests
----------------

There may be isolated cases where your package consists only of a number
of independent functions that are not expected to be called in sequence.
In this situation, unit tests alone may be sufficient. However, most
tools require integrated tests in addition to unit tests. Integrated
tests check the functionality of a suite of functions that work
together. For example, if you have a tool that fits a population model,
you might have unit tests for the functions that process the data, fit
the model, and plot the outputs, but an integrated test that runs a
whole example from start to finish. These types of test can help
identify software problems that occur when outputs of one function are
passed as inputs to the next function.

A clear place to source integrated tests is from your user manual,
vignette, or examples directory. If you are providing these examples for
users to work off of, they should always work, and they should be able
to run with only data, functions, and dependencies loaded with the
package. Therefore, we recommend at minimum including a full example as
one of your integrated tests. These integrated tests can be added to the
build path in Travis so they are also run whenever changes are merged in
on Github. Note: this can be a slow process; Travis often takes several
hours to run even on software packages that load relatively quickly.

If your software relies on a workflow with many different options, each
set of options should have its own integrated test. This could be as
simple as checking that your software returns an error when two
incompatible options are specified, or might mean you need many
different integrated test cases. If you do not find the errors across
multiple cases in an integrated tests, your users will, leading to much
more debugging to find the error than if your code was adequately tested
in the first place. <References on testing coverage?>

If you are using `R`, you can include integrated tests in another
"test....R" file within the `testing` directory so they are run whenever
the `testthat::test_check()` function is called.

Code coverage
-------------

Once you think you have a good suite of test cases created, there are
many automated tools you can use to see how much of your code is covered
by automated tests. If you'd like to track this, you can even create a
badge for your repository (and your toolbox landing page) that
highlights how well-covered your code is by test cases. We recommend
tracking this metric so that you can observe how your test coverage
changes over time - it may not be feasible to achieve 100% code
coverage, but at least strive for keeping the same level of code
coverage over time. This will indicate that you are introducing test
cases to cover new functionality at the same rate that you add new
features to your software.
