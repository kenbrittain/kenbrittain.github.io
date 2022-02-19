---
permalink: /posts/23-runbooks-document-the-failures-in-your-system.html
title: Runbooks Document the Failures in Your System
layout: post
---

If you know about a failure in your system and don't fix it does that make your
system worse? Does it make you a bad engineer?

Not in the least (on both counts). You are supposed to fix the failures that you
can directly affect and change. Some parts of the system are not under your
control and can only be influenced. They are never managed.

## The Big Org Dilemma

The *Stay Sassy* blog has an admonishment to [Stop Writing Great Runbooks][1]
and fix your production issues instead. I think this is great advice and adhere
to it where applicable. However, some of us will find ourselves in a situation
where this is just not possible.

If you work in a large organization, with different groups with different areas
of responsibility, you may run into the issue where fixing a failure is not
really an option. Writing a runbook is the fix.

I write software that automates the build and deploy of other software within a
company. This company is just a small part of another really, big company. I am
not allowed access, or can perform operations, upon certain resources. It is how
the system are set up and managed. None of those responsibilities fall to me, my
team, or even engineers in my company.

If you are working within a company that has strict rules surrounding
segregation of duties you get the idea. We can discuss how this should not be
the case. We can talk at length about how DevOps will eliminate the need for
segregation of duties. Those discussions are about where we want to be. I have
an issue right now where I cannot restart the dependency for my product. It is
owned by another group entirely as part of a consolidation that is happening.

Our runbook is to create an incident ticket and assign it to the other group. It
is usually resolved pretty quickly. To those in similar organizations you will
understand when I say that 24 hours is quick. I know. I hear you! We have
already talked to the other group. We got time with their managers. They are
going to fix their process just not on my timeline.

## You Already Have a Job

I can hear folks telling me that I have failed for not getting this issue
addressed. One of the things that I have learned, over time, and in successively
larger companies, is that it is ok for some things to just be broken. This
particular issue only affects once per month. I already have a job and do not
want to spend countless amounts of my time, and good will, to fix a once per
month issue. I am thinking along these lines:

![Xkcd - Is It Worth the Time?](https://imgs.xkcd.
com/comics/is_it_worth_the_time.png "Is It Worth the Time?")

The *Stay Sassy* post says:

> The problem is that runbooks are documented failure: failure to fix things
> properly, failure to automate solutions, failure to prioritize.

None of those points are untrue. I will, however, accept a different
interpretation for the *failure to prioritize* statement. Yes. There is a
failure there. The failure is that I have not made enough of a deal to get this
issue prioritized. Why? The other teams proprieties are not aligned with mine
and, quite frankly, they never will be. My team no longer owns this system, and
we migrated our customers to theirs, because of decision made at another level.
I get the decisions. They save the company money. Lots of it.

So, for now we cannot fix the system, but only write a runbook that documents
this failure as part of our system.

[1]:https://staysaasy.com/software/2022/02/12/runbooks.html
