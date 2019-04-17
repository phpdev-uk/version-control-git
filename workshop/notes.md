---
title: Version Control with Git
author: Paul Waring
geometry: margin=2cm,vmargin=2.5cm
papersize: a4
fontfamily: palatino
fontsize: 11pt
---

## Introduction

These notes outline the topics which will be covered in the workshop. They are
not a verbatim transcript of the workshop, but you should be able to use them
as a standalone resource.

If you are attending the workshop, you are welcome to read the notes beforehand
and send any questions or comments to the tutor at:
[paul@phpdeveloper.org.uk](mailto:paul@phpdeveloper.org.uk).

## The tutor

Paul Waring is a freelance PHP developer and Linux system administrator who works
with a range of businesses across the UK.

Before going freelance, Paul supported software for teaching at the University
of Manchester, and was the IT Director and Technical Manager at a wholesale
insurance broker.

Paul can be contacted via email at [paul@phpdeveloper.org.uk](mailto:paul@phpdeveloper.org.uk) and has
a website at [phpdeveloper.org.uk](https://www.phpdeveloper.org.uk).

## Audience

This workshop is aimed at people who are familiar with programming and who are
new to either version control or Git.

## Version Control

Version control is a mechanism for keeping a history of changes made to a set
of files. Some of the benefits of version control include:

 1. Finding out which change caused a bug.
 1. Rolling back to a previous 'known to work' copy.
 1. Finding out who made a change and why.

Generally all changes will be sent to a single central location, although some
version control systems also support distributed repositories.

Version control also allows more than one developer to work on a project
without having to transfer files and attempt to deal with a naming convention
which shows which copy of a file is the latest one. Any changes which do not
*conflict* can be automatically distributed to all developers.

Although version control makes team working easier, you can still get many of
the benefits as a sole developer. For example, the notes for this workshop are
kept in version control, even though they were written by a single author.

## History

One of the largest open source projects in terms of the number of contributors
and amount of code is the Linux kernel. Until early 2005, the kernel developers
had used a proprietary piece of software called BitKeeper for version control.
The owner of BitKeeper had allowed the kernel developers to use the software
for free, instead of having to purchase commercial licences.

In April 2005 BitKeeper withdrew the option of free licences, citing the efforts
of some developers to reverse-engineer the metadata associated with changes made
with BitKeeper. Linus Torvalds responded by developing a new version control
system, Git, and within a couple of months it was being used to manage a
release of the kernel.

Although Git was written with the Linux kernel in mind, many other projects
found that it met their needs and offered advantages over other popular version
control systems such as CVS and Subversion.

## Why Git?

There are several distributed version control systems available, including
Mercurial and GNU Bazaar, which have a similar feature set to Git. However, a
number of factors -- including an active community and ecosystem -- have
resulted in Git being the modern version control system of choice for most
developers. The alternatives offer no compelling advantages for the majority of
use cases, although they are still used by some major software projects such as
Ubuntu (GNU Bazaar) and Mozilla (Mercurial).

You may be wondering why people decided to create Mercurial and GNU Bazaar if Git
has the same functionality and a larger community. The simple reason is that
Git, Mercurial and GNU Bazaar were all initially released within a few weeks of
each other (March/April 2005), so at the time they were all fixing a problem
for which there was no open source solution.

## Distributed version control

Git is a *distributed version control system* or DVCS. This means that you can
create a local repository without the need for a central server, which is useful
for testing. Unlike Subversion, Git does not require a working network
connection for many tasks, so it is possible to make changes locally and then
*push* these to another repository at a later date.

## Git workflow

Git repositories consist of a sequence of *commits*, each of which contain
changes to one or more files. Each file must be *staged* using `git add`, and
then all the files can be commited using `git commit`.

## Setting up Git

Before you use Git for the first time, you need to set up your name and email
address that will be used in commits. If you forget to do this, Git will remind
you the first time you try to make a commit.

For the purposes of this workshop, we will assume that you are going to use the
same name and email address for all of your commits. However, you can also specify
this information on a per-repository basis if required.

To set the name for all of your commits:

```
git config --global user.name "Your Name Here"
```

To set your email address:

```
git config --global user.email "me@example.org"
```

You can check that both options have been set by running `git config --list`:

```
$ git config --list
user.email=paul@xk7.net
user.name=Paul Waring
push.default=simple
```

The output of `git config --list` may contain more options on your machine, as
some distributions set additional options by default. You will also see more options
if you run the command inside an existing Git repository. Some options have default
values, e.g. `color.ui` may be set to `true` even though it is not listed in
`git config --list`.

Ideally you want your `user.email` value to match the one you use on your Git
service (e.g. GitHub), otherwise you may notice that your avatar does not appear
etc.

## Creating a repository

Unlike centralised version control systems, Git allows you to create, or *initialise*,
a repository anywhere you want. All you have to do is run `git init` to create
a repository in the current directory, or `git init project` to create a
repository in a directory called `project`:

```
$ git init project
Initialised empty Git repository in /tmp/project/.git/
```

You can check that a repository has been created by changing into the directory
and running `git status`:

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

There should also be a `.git` directory in the top level of the repository:

```
$ ll
total 12
drwxrwxr-x  3 paul paul 4096 Sep 26 18:44 ./
drwxrwxrwt 15 root root 4096 Sep 26 18:45 ../
drwxrwxr-x  7 paul paul 4096 Sep 26 18:45 .git/
```
