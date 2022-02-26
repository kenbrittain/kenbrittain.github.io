---
permalink: /posts/11-dont-settle-for-bad-commit-messages.html
title: Don't Settle for Bad Git Commit Messages
layout: post
draft: true
---

I grew up using not-git. This doesn't mean that I have not used version control
during my career, but rather, git is a recent addition to the arsenal. I have
been using git for approximately 10 years now but I used a ton of other tools
prior. Here is a brief list of those that I can remember using, with varying
degrees of success, in roughly reverse usage order):

* [Git](https://en.wikipedia.org/wiki/Git)
* [TFS](https://en.wikipedia.org/wiki/Azure_DevOps_Server#TFVC)
* [Serena](https://en.wikipedia.org/wiki/Serena_Software)
* [PVCS](https://en.wikipedia.org/wiki/PVCS)
* [ClearCase](https://en.wikipedia.org/wiki/Rational_ClearCase)
* [Perforce](https://en.wikipedia.org/wiki/Perforce)
* [Visual SourceSafe](https://en.wikipedia.org/wiki/Microsoft_Visual_SourceSafe)
* [CVS](https://en.wikipedia.org/wiki/Concurrent_Versions_System)
* [RCS](https://en.wikipedia.org/wiki/Revision_Control_System)
* [XCOPY](https://en.wikipedia.org/wiki/XCOPY)

All of these tools, except for the brutal `XCOPY` your source files to the
network share process I'd rather not talk about (but was considered version
control by the company), had the ability to enter a message when a change was
committed. It has been my experience that there are three (3) types of
developers on the commit message spectrum. This post defines the three (3) types
of developers, my rules for commit messages, and why I am in the third category
of developers.

The three (3) types of developers who write commit messages are:

* Good - Consistent Commit Message Writers
* Bad - Maliciously Compliant Commit Message Writers
* Reformed - Learning to be Consistent Commit Message Writers

## The Good

The first group of developers are the individuals you want to work. They write
good commit messages. This includes anyone who tries to write good message and
are still learning such as new developers or reformed teammates. The messages
are generally helpful, they let us know why a change was made but don't make
assumptions about their familiarity with the original problem. Explain things
like they are 10 years old. Well, a 10 your old who can code.

Each commit message will be broken down into two (2) parts. The subject is
separated from the description by a blank line when editing.

* __Subject__ - this is what most individuals will see when interacting with
  your code. Keep this line below 52 characters (per GitHub guidelines). It
  should be a very brief description of what was changed. This message is
  generally displayed in tooling.
* __Body__ - this is where you get to tell us why you change something. There is
  no real limit on what you can type here. Limit these lines to 72 characters.
  Git does not wrap for you so this limit will help when folks are looking are
  your commits more in depth.

Here is an example of what I am trying to go for:

![Good Message](/assets/img/11-github-commit-message-good.png "Good Commit 
Message")

## The Bad

The next group of developers are those that write commit messages. They are not
helpful and are only doing so to comply with the coding standard, or a team
rule, that states all commits will have a *commit message*. You have seen these
messages before, and perhaps, maybe, you have written one yourself.

The classics are:

* fixed a bug
* Checking in my code

and my all-time favorite:

* nobody reads commit messages

These folks are generally up to no good and
being [maliciously compliant](https://en.wikipedia.org/wiki/Malicious_compliance)
. I could argue that no commit message is better than what they are doing.

I would also make an argument the these developers are coached into reforming
themselves.

## The Reformed

Let's face it: you are never going to write great commit messages 100% of the
time. But, if you are improving overall, and generally trying to get better,
then I won't complain.

I count myself in this category.  
