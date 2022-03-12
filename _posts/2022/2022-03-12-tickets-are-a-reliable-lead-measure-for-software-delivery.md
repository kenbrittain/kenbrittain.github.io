---
permalink: /posts/26-tickets-are-a-reliable-lead-measure-for-software-delivery.html
title: 'Tickets are a Reliable Lead Measure for Software Delivery'
layout: post
---

Ever since reading the [The 4 Disciplines oif Execution: Achieving Your Wildly Important Goals][4d], way back in 2014, I have been searching for a reliable lead measure to use for software development. In my mind there was never a distinct, measureable thing, that could be automatically tracked. _If you had figured this out years ago, congratulations, you are smarter than me, and you deserve kudos ... but this is my blog so bear with me._

I have tried to track various things over the years but nothing seemed correct. Schedules were not a lead measure and just bad in general. They rarely reflected the actual project timeline. Time spent coding was another red herring. As a professional developer you generally spend the bulk of your time, well, coding. Measuring how much just gave me a good indication of how much admin work there was. It was just overhead and usually accounted for in the schedule. It didn't help me predict when software was being delivered, or more importantly, when it would not be delivered. Managers tend to care more about the latter than the former but, as usual, both are important.

During a recent retrospective we examined why certain features were not being completed. If a ticket spans more than a single sprint it means it should have been split. If it is falling in the third sprint, uncompleted, and not split, there is a problem. This problem was causing our releases to delivery less value to the customers. There were multiple external forces at play and some internal ones as well. After ruling out time sunk into complying with corporate mandates we determined that our tickets were just not specific enough.

We use [Jira][jira] to track our sprint work. The tickets that were not getting completed were overly large and mostly vauge. They had descriptions similar to "make X work" and other nonsense text. We are a small team and this type of verbiage worked in the past. Each member of the team had a certain level of history and understanding of what making "X" work would mean. As the team grew and team members were replaced, that history was lost. The understanding was not there because the individual had not been there. If you were not around for the design and building "X" then the ticket was confusing and, thankfully, the developer said so! That is why we started looking at our tickets.

Our pattern for tickets has evolved over the years from the "As a ..., I want to ..., So that I..." model to the following:

> What?
>
> Why?
>
> How?

The title or summary line is generally descriptive enough to get you there. The description lists the three (3) items above and provides as much detail as possible. A lot of times the **How?** block is left sparse and filled in after a refinement session.

The most important activity we could begin doing right now was to reduce the scope of each ticket. As the scope was reduced the specificity of a ticket would go up. We found that generally happens when describing smaller things. Ticket splitting tended to give us more tickets. Seems natural but we are not making tickets for tickets sake.

In our sprint planning tickets rarely go over 3 points. We count 1 point as the amount of effort required to initiate and track a request from another team (*ahem*, with a ticket). The work is small and the effort is usually a background task. Our 3 point tickets would require 1 or maybe 2 days of coding effort. That includes validation, unit tests, and documentation updates. This new guideline has helped us create a system where we can measure daily progress toward our goals.

I know, you are thinking we were probably supposed to be doing that already. Well, it turns out that we were not. Until it was actually verbalized by a senior member of the team is just didn't click.

> Closing tickets ensures progress on the features.

That was when it dawned on me that closing tickets is the lead measure for software delivery. A project cannot be finished if the tickets associated with them are not closed. A closed ticket represents work completed. If you are using sprints, kanban, or just a checklist, completed tasks = progress!

I am sure there are some out there who are reading this and wondering what I have been doing all these years. Maybe it made perfect sense to you and you have been excelling at this for years. In my particular case, I am not a personality type "D" or your traditional *git 'r done* come hell or high water type of person. I have taken a few [DiSC][disc] personality tests over the years. I have always scored a hard "C" . That is, there is no drifting toward "SC" or "CD". I am C all the way through.

> They are data-driven, highly organized, detail-oriented perfectionists.

Working with a delivery minded manager has helped. I have had a relaxed relationship with delivering software. The deadlines are generally artificial, made up by managers, and have no relation to the reality of software development itself. I get it. Without deadlines I would work on a project forever, or until it is perfect. Now, perfectionist tendencies aside, I also realize that things need to get done. Don't get me wrong. I enjoy writing software and delivering projects. I have been doing it for over 30 years. When I say that I am type "C" personality it says that I enjoy the solving of the problem more than checking off something on a list.

When it clicked that having tickets closed is going to be good lead measure for delivery my view point changed. The 2-week sprint cycle is an artificial checkpoint. It serves no other purpose than for those checking to have a place to look. In corporate software development there are always people looking.

Now, if the ticket is specific enough, and small enough, it serves as the perfect guide. I can watch myself, and my team mates, approaching completion of a feature or project in real time. The whirlwind of corporate life will alway be present in everything that we do, but now we have automatic, and reliable way to let us know if we are on track. In the 4 Disciplines they call them scorecards. Our is [Jira][jira] and it is automatic. You just have to remember to close your tickets.

[4d]: https://www.amazon.com/Disciplines-Execution-Expanded-Achieving-Important-ebook/dp/B08BZW8NGC/
[25]: https://kenbrittain.com/posts/25-tracking-a-daily-coding-habit-with-the-github-contribution-graph.html
[disc]: https://www.indeed.com/career-advice/career-development/disc-personality-types
[jira]: https://www.atlassian.com/software/jira

