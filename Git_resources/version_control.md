# Version Control Tutorial

## What is version control

 >Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

There are many types of [version control](https://en.wikipedia.org/wiki/List_of_version-control_software).
We will focus here on the Distributed Model:

> In the distributed approach, each developer works directly with his or her own local repository, and changes are shared between repositories as a separate step.

Although there are several open source tools available for this approach. We use Git.
> Git is a distributed version-control system for tracking changes in source code during software development.[8] It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed,[9] data integrity, and support for distributed, non-linear workflows.

> Git was created by Linus Torvalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development.Its current maintainer since 2005 is Junio Hamano.

> As with most other distributed version-control systems, and unlike most client–server systems, every Git directory on every computer is a full-fledged repository with complete history and full version-tracking abilities, independent of network access or a central server.

> Git is free and open-source software distributed under the terms of the GNU General Public License version 2.

## GIT


## Git Server as a Service
Thereare many open-source and private systems that offer Git Server as a Service that each have additional tools and benefits.  The main one being the ability to push code to a server for backup and easy collaboration.  Some of the well know systems are:
- Github
- Gitlab
- Bitbukect

We will focus on use of Github herein.

### Installing GIT
general installation directions (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
you will need admin privlages.
- configure git
- youll want to be aware of your user name and user email for setting up your Github account



### Creating a Github account
- for general information on creating a github account.  For NOAA specific users there are specific requirements.
Please note that if you have multiple Github identities ( perhaps a personal one and a work one).  Youll want to be careful about which identity you use.  See Multiple Identities below to set up automated ways of dealing with this.



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


