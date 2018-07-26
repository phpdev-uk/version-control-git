---
title: Version Control with Git
author: Paul Waring
geometry: margin=2cm,vmargin=2.5cm
papersize: a4
fontfamily: palatino
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

## Requirements

In order to complete all the exercises, you will need to have installed Git
version 2.6 or later. You will also need the ability to run Git on the command
line, for example using Git Bash in Windows.

Linux users can install Git through their distribution's package manager.

Windows and Mac users can download the latest version of Git from
[git-scm.com/downloads](https://git-scm.com/downloads)

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

You may be wondering why people decide to create Mercurial and GNU Bazaar if Git
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
