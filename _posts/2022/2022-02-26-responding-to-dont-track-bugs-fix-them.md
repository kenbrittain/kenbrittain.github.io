---
permalink: /posts/24-responding-to-dont-track-bugs-fix-them.html
title: Responding to Don't Track Bugs, Fix Them
layout: post
---

On February 25, 2022, [Allan Holub][0] published a post titled
"[Don't Track Bugs, Fix Them][1]" to his blog. He is not hiding much as the
title sums up the post pretty well. Then folks starting talking. 

Allan is arguing for not tracking bugs and for fixing them as soon as possible.
If a bug needs to be tracked then it probably won't be fixed.

> You do not need a bug tracking system. In fact, a bug tracking system is a
> symptom of a deeper problem—insufficient focus on quality.

He describes his style of writing code as fixing the bugs as he goes. I think
this goes along with most professional developers. Writing code that is bug free
is the desired end state. I don't remember ever working with another individual
that actively injected bugs on purpose. I do remember developers that were so
sloppy with their practices that you began to wonder if it wasn't intentional.
But alas, it turns out they were just not very good at what they do. Now you can
see how the last bit from quote is relevant. The bit about *insufficient focus
on quality*. The corporate focus has been deadlines and delivery. Quality is
represented but nobody stops shipping code.

If one follows the pattern that Allan describes I believe it covers the majority
of competent developers I have encountered in my career. I am not using the
word *competent* in a negative sense. By competent, I mean referring to the
developers who can write code, write unit tests, and understand the systems they
are developing. I would also add that they do not require extensive on the job
training for simple tasks such as reverting a git commit. They can figure 
things out.

They have also figured out that writing code introduced bugs. We are all not
perfect and they get it. That is why unit tests, functional tests, and
integration tests are written. These tests are run all the time. We don't want
to write code that has bugs, but sometimes, just sometimes, there are bugs that
work their way into the software. Nobody is perfect even Allan Holub.

> I don’t use a bug tracker because I don’t need to. There are no bugs to
> track.

What some folks are not getting is that he is not claiming to write bug free 
code. He is not tracking bugs because for two (2) reasons:

 1. If a bug is unknown then there is nothing to track and,
 2. If a bug is going to live long enough so that it needs to tracked you 
    are probably not going to fix anyway so why bother tracking it.

This is where things diverge for me. There are lots of bugs in any system, let
alone one developed by more than 2+ developers. Why? While I am sure that you
are quality focused, write good unit tests (and run them) some of your teammates
may not. That is why builds break. Developers are people. We make mistakes. 

I agree with Allan that all bugs should be fixed. We can go a step further and
say that all known bugs should be fixed before shipping. This last statement is
generally overridden by someone who wants most of a product, with bugs, than
waiting for all of a product without bugs. Allan would say that this a
prioritization problem, and he is right. Someone is priorizing functionality
over quality. However, I would prefer to have that bug recorded in a defect
tracking system. It is not that we wont ever fix the bug. It just won't be fixed
now.

![Twitter Quote](/assets/img/24-allenholub-twitter.png)

Twitter helped. I agree with the author more than I did when reading the blog
post alone. He is not claiming he writes bug free code. He is not saying there
are never any bugs. What he is saying is that he tries to fix all known bugs as
close to as when they were found.

That is something that I agree with.

[0]:https://holub.com/#about
[1]:https://holub.com/bugs/