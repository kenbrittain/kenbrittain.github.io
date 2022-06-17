---
permalink: /posts/##-1000-true-fans-try-100-customers.html
title: Each Product Should Have Their Own Monorepo to Cut Overhead and Save Time,
layout: post
---

If you develop software professionally you will have a set of tools and practices that help you get the job done. If you have a side project then those very same tools and practices may not be best suited for your solo development.

Yes, they will feel familiar.

Yes, they may be free.

Using the big, team based tools you are used to carry a lot of overhead for a single developer. In your side project adventure you do not need overhead. You are going to be struggling to carve out time to do the work. You do not want to add the time and effort baggage of managing a Jira board in addition to developing or building a product.

[Jira][jira] is a great tool for defining and tracking tickets. When used in a company it provides management the ability to look across projects and pull out trends. It allows for tracking, labeling, and workflows for each issue. Teams can customize their own processes. Multiple people, and teams, can safely co-exist while tracking the work.

For a solo effort do you really all of this? The feature roadmap is a great tool because it saves you from making a similar document in [PowerPoint][ppt] (been there) or [Visio][visio] (done that) or even [Gliffy][gliffy] (yup, done that too). Do you really need a graphical, ghant-like chart for you features as a solo developer (or even a small team)?

In the beginning it feels good because it is familiar not because you really need it. You start to feel like you are making progress because you are doing the things that you do doing the day, at work, with other developers, and other teams. The additional overhead for your side project is not required. It just takes up time.

Here is the abandoned roadmap view for my project. It has not been updated in quite some time. Why? I don't need it. The feature we are talking about can be tracked using pen & paper. The project could be tracked using a simple markdown file if I wanted. 

![Runbook Compiler Roadmap][/assets/img/##-title.jpg]

Do you really need a backlog? No. You need a place to keep track of you bugs. If you are using [GitHub][gh], [GitLab][gl] or something similar, then you will already have an issue tracker. Just use that. Keep you issues close to your repository and forget about Jira for this project. You don't need it.

The goal is setting up a monorepo is to take the overhead of managing a product and put it into one place. For a recent project I had modeled the typical developer breakdown. I created the main repository for the code. I created another repository for a library that was going to be used across projects (maybe). I also created a repository for the documentation. 

That is 3 repositories for the same project. When it came time to add a fourth repository for another aspect of development i knew I was doing something wrong.

For some reason this model of development has been the standard for my career. Each item, or deliverable, will get a repository. it makes sense when developing in a team environment. The repositories can be developed independently and maintain their own life-cycle and as a result: version number.

When developing code as a solo effort maintaining any number of repositories is a chore. My [GitHub][gh] has 12 repositories currently within it. There is some overlap but I sure don't need that many. 

[kinsta]:https://kinsta.com/blog/monorepo-vs-multi-repo/	"Monorepo vs Multi-repo:L Pros and Cons of Code Repository Strategies"
[ppt]:https://www.microsoft.com/en-us/microsoft-365/powerpoint	"Microsoft PowerPoint"
[visio]:https://www.microsoft.com/en-us/microsoft-365/visio/flowchart-software	"Microsoft Visio"
[gliffy]:https://www.gliffy.com/	"Gliffy Diagrams for Atlassian"
[gh]:https://github.com/	"GitHub"



