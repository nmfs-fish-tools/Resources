What is code review and why should I do it?
-------------------------------------------

The point of code review is to improve code quality. By drawing on the
expertise of reviewers in addition to code authors, code quality can be
enhanced and both authors and reviewers will improve their coding
skills. Automated testing is a subset of procedures undertaken in a code
review, but the most thorough review and feedback comes from other
people.

If code review is done correctly, it saves author time. Other developers
who review your code must understand why the change has been made and
how it works, so if a bug is detected they are able to debug and/or fix
it. Reviewing code before it is merged upstream increases the chances
that bugs are caught before propogating to the master branch. Reviews
should be done often on small chunks of code, therefore each review
should not take a substantial amount of time.

### Preparation for code reviews

Code reviews can happen in person or via Github. Often, in-person
reviews are the most expedient - in an hour or two you can go over quite
a few changes and get them all approved, whereas on Github it is likely
to take a few days for everyone to talk about and commit to a
resolution. On Github, a code review commences when you initiate a pull
request. Below are some steps you can take (from this [blog
post](http://fperez.org/py4science/code_reviews.html)) before your
in-person or Github code review to make things go more smoothly.

1.  Make sure the motivation for your code is clear. Someone who isn't
    intimately involved with your project should understand from the
    module documentation and the comments what you are trying to do,
    what approach you're taking, and why they should expect it to work.
2.  Take some time to prepare a presentation about your code that will
    answer the above questions even for someone who hasn't read the
    code. You're more likely to get useful feedback, rather than
    nitpicking about syntax, if the audience can see the big picture.
3.  Get the code sent out at least a few days beforehand along with some
    background about what to look at (if large), whether suggestions
    should be about architecture/implementation/algorithm/requirements,
    etc. Make sure everyone has enough time to read the code beforehand,
    and don't send a series of updated versions immediately before code
    review.
4.  Don't try to present too much. 200 lines is an absolute maximum - 50
    is usually more reasonable.
5.  Include examples, either as unit tests or standalone scripts.
6.  Before sending the code out, review the checklist below and
    proactively improve your code in ways you can anticipate receiving
    feedback about. This will save time during the meeting.

Code review checklist
---------------------

Mozilla science has an excellent
[checklist](https://mozillascience.github.io/codeReview/review.html) for
scientific code review. Without reiterating too much of the article,
they categorize things to look for into intrinsic and extrinsic issues,
which could be described as internal or bigger-picture issues. We will
continue to add to the bullet list below as we review more toolbox
submissions.

### Intrinsic issues

-   Argument handling - are there too many arguments, or conversely are
    global variables assumed? Could redundant argument passing be
    simplified? Should we be dragging along objects with inputs and
    outputs. Input arguments and initializing to null?
-   Function location, structure, and size
-   Efficiency - reducing duplication and using mapping if possible
-   Consistent and meaningful name standards
-   Documentation
-   Error handling - are inputs checked?
-   Are unit tests performed?

### Extrinsic issues

-   Is there functionality in the new code that is duplicated elsewhere
    in the package?
-   Does the new code follow the project standard?
-   Are the user guides/tutorials updated?
