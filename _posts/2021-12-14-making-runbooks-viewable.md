---
permalink: /posts/15-making-runbooks-viewable.html
title: Making Runbooks Viewable
layout: post
---

Runbooks should be written by the developers building the system. Keeping them
close to the development process is [recommended](1). Runbooks should also be
read, but will most likely only be scanned, so a standard format
is [recommended](2). Finally, runbooks should also be viewable wherever they are
needed.

Writing your runbooks in markdown is a step toward getting them viewable. It
gets you 50% of the way toward our goal of making the runbooks: viewable.
Being **viewable** means having the runbook document available, in any system
that your organization uses, to ease the burden of finding them when needed.

The first phase of being viewable is to generate a text based format from your
runbook sources. Markdown is recommended for two (2) reasons:

1. It is a text based format that can easily be checked into a repository and
   edited with any text editor.
2. Markdown is easy to understand and presents a view that can previewed or
   rendered in any modern text editor.

# Why Markdown?

If markdown is so great why don't I just write my runbooks in markdown? While
markdown is great for many things, including writing this blog post, it is not
meant to be used for structured documentation. What? Markdown is a structured
language for making documents? We can both agree that markdown is great for
writing documents. A runbook, however, while a form of system documentation, is
not to be considered a document similar to Word or even a wiki page.

People usually do maintain their runbooks in some form of document based
management system. [Atlassian Confluence](3) comes to mind as a fairly popular
one. The issue with maintaining a runbook in a document management system, is
that it treats the runbook as a document. The runbook is not a document but
content. The content is dedicated to solving a system problem. It is not meant
to be read like a novel. It is meant to be read to solve a problem. That content
needs to structured in a language that is easily parsed so that we can process
it programmatically.

This requirement allows the runbook to be translated to any number of supported
formats, including markdown. I argue that markdown is great for writing prose
and exposition. The YAML format, for runbooks, supports using markdown for the
text based fields that describe things. It is perfect for that type of job.
While the runbook is not written in markdown there may be some contents that
are.

```yaml
summary: >
   The summary section can contains *Markdown* formatted text 
   but the content itself is still structured in the YAML.
```

Let's not get hung up on where or when markdown can be used. Remembers that
runbooks provide context to solving a problem. They describe the steps to be
accomplished. Putting that into markdown, or other document language, would
strip out the context. Once that is gone you have long string characters that
require a human to interpret and derive meaning from. Similar to this blog post,
which was written using markdown. It is required to be read for the meaning to
be grasped.

# Generate all the Things

If you are using YAML then it can easily be parsed. This allows us to take a
YAML formatted document, read it into a program, and then generate something
else from it. This something else is the view components of our runbooks.

We want our runbooks to be a in a machine-readable, or parsable format. For that
I recommend YAML. You can use XML if you want but the 90s are long gone. The
format does hold some advantages but being easy to write, as a human, is not one
of them. JSON could be used as well, but it has some of the same misgiving as 
XML. If that were not the case then [HSJON][4] would not have been created.

The power of using YAML for runbooks comes into play when you want to 
generate a view of your runbook. By default, all runbooks should be 
generated into a markdown view. This makes them all easily viewable with the 
lowest of technology. 

```shell
more runbook.md
```

You cannot get much simpler than that. It is not pretty, but it is supported on
pretty much every system used professionally these days (including Microsoft
Windows). So, you may be asking yourself: why am I generating a markdown file
when I could have just written a markdown file to begin with? That is a very
good question.

It has been my experience that documentation is always evolving. That means
two (2) things and one (1) them is not what you think. The first meaning is that
documentation is always evolving as the product it is written for changes. This
goes for runbooks as well. If you are not changing your runbooks then you are
not changing your systems, which means that your project is dead. In that case
you should be looking for another project work on.

The second meaning to evolving, in my experience, is what we call tactical
migrations. You wrote your runbook, as wiki pages, in a Confluence instance.
That is ok, we have all done that at some point. We even felt pretty good about
for a while. Then, the company evolved. This is where your company was either
purchased, sold, or found an incredible way to save money (on software that is)
and now requires you to spend an large amount of effort, usually in a short
amount of time, to move your content to the newm *cheaper*, system. For example,
the system you used for your documentation is no longer going to be supported,
and you have 13 weeks to move your content before the system is retired. Move it
or lose it! This type of evolving happens all the time in larger organizations.
It has happened more times than I care to count. This is why the runbooks are
written in a structured format that can be parsed, and then translated into
another format quickly and easily.

When moving day comes you just regenerate all of your runbooks into the new
system. There is no copying. There is no exporting. The runbooks are portable
and the view is generated. That is why the first view, and for making runbooks
available to developers, is to generate a markdown view. This format is easy to
understand. It takes no special tools to use (just an editor). Other tools will
accept markdown as a published format.

As a developer, you get paid to write software. This software must implement or
support a business process. This business process either directly or indirectly
helps generate money. This money is then used to pay your salary. The less time
you spend moving your runbooks, and other documentation around, the more time
you have to spend writing software.

[1]:[/posts/6-yaml-runbooks.html]
[2]:[/posts/13-writing-a-runbook.html]
[3]:[https://www.atlassian.com/software/confluence]
[4]:[https://hjson.github.io/]