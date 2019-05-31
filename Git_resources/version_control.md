# Version Control Tutorial
(in progress...)

## What is version control
(from wikipedia)
 >Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

There are many types of [version control](https://en.wikipedia.org/wiki/List_of_version-control_software).
We will focus here on the Distributed Model:
(from wikipedia)
> In the distributed approach, each developer works directly with his or her own local repository, and changes are shared between repositories as a separate step.

Although there are several open source tools available for this approach. We use Git.
> Git is a distributed version-control system for tracking changes in source code during software development.[8] It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed,[9] data integrity, and support for distributed, non-linear workflows.

> Git was created by Linus Torvalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development.Its current maintainer since 2005 is Junio Hamano.

> As with most other distributed version-control systems, and unlike most client–server systems, every Git directory on every computer is a full-fledged repository with complete history and full version-tracking abilities, independent of network access or a central server.

> Git is free and open-source software distributed under the terms of the GNU General Public License version 2.

## [GIT](https://git-scm.com/)
### Installing GIT
General installation [directions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
You will need admin privlages.
- configure git

Although you could just use Git locally for version control, it is best to use with a server systen
- youll want to be aware of your user name and user email for setting up your Github account



## GIT Server as a Service
There are many open-source and private systems that offer Git Server as a Service that each have additional tools and benefits.  The main one being the ability to push code to a server for backup and easy collaboration.  Some of the well know systems are:
- [Github](https://github.com/)
- [Gitlab](https://about.gitlab.com/)
- [Bitbucket](https://bitbucket.org/)

We will focus on use of Github herein.



### Creating a Github account
- for general information on creating a github account.  For NOAA specific users there are specific requirements.
Please note that if you have multiple Github identities ( perhaps a personal one and a work one).  Youll want to be careful about which identity you use.  See Multiple Identities below to set up automated ways of dealing with this.
add links to documentation on github .. three config files


- it is good pracitce to use 2-factor authentication
- sign up for a github account here
- for NOAA users, use your @NOAA.gov email and have your user name and email the same as you vlab account - this will make it easier to connect through either service.

-link to mult



### Multiple Identities
There are various ways to deal with multiple identities.
To check which identity you are using inside of a git repositiory by default
'''
git config user.name
gi config user.email
'''
- you can set user.name and user.email for each repository as you go.  This works but know that there is a global setting and if you forget to initialize your repository withthe correct corredntials , the global choice will be used
- better: set up a .gitconfig to deal with multiple identities


### SSH and security measures


### Basic workflows
  -Starting on your computer with a basic git repo
  - create a folder and initiliaze

```git init```

check user config for repo is correct

If you have multiple identiies it is a good idea to check which identity this folder is using and change if necessary

```
   git config user.email
   git config user.name
```

- create a README document as text or markdown which will hold basic ifnormation about your code repository


```
   echo README.md > README file for Repo Name
   git add README.md
   git commit -m"addd readme"
```


go onto github and create an empty repository

    git push master ssh... -u

- once you are set up you will want to get into a standard git [workflow]
(https://www.atlassian.com/git/tutorials/comparing-workflows)
where you commit changes locally often  and push to your remote master at least daily if changes have been made or when many changes have occurred. Commiting often will help when you want to revert ( go backwards ) or if you are actively working with several others. For more details on managing multi-user workflows, see this [cheat sheet](https://github.com/nmfs-fish-tools/Resources/blob/master/Git_resources/version_control.md). 


### Branching..
Branching can be thought of as creating a copy of your code with a flag at the point where you started the branch.  This allows you to try out a different path or set of functions.  It is good practice when you are adding a new feature to solid working code or working on a siginificant piece of code that will likely need to be incorporated to the larger code base at a later time. You can always just go back to your branching point.  You may choose to use local branches only and merge your code, or send your branch up to the master repostitory.  Good practice dictates not having several "orphan" branhces  or using branches as specific features; once a branch is ready to be merged into the main repository, the branch should be deleted so it does not cause any confusion in the development process

### Helpful hints
git stash
git pop
git revert
git head



### Free online Github tutorials
[more info from Atlassian](https://www.atlassian.com/git/tutorials)
