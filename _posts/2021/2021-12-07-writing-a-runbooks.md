---
permalink: /posts/13-writing-a-runbook.html
title: "Writing a Runbook"
layout: post
---

Let's face it: runbooks are a form of system documentation. Nobody likes to read
documentation. So how do you get people to read your runbooks? It is not likely
that your runbooks will be able to garner the same amount of rapt attention as
say, a [Harry Potter][hp] novel, or perhaps a [Game of Thrones]
[got] entry. Most of the time a runbook will be read, by an engineer, under
duress, while a system anomaly is being addressed. Most likely in the middle of
the night. Here are some guidelines to make your runbooks helpful.

## Standard Pattern

While each runbook would address a different problem the structure of all
runbooks should follow the same pattern. This will make it easier to scan for
the relevant sections. I already said that nobody is going to read your runbook.
It will be scanned, and quickly, looking for relevant information. So let's make
it easily scannable and help folks out.

* **Title** - each runbook should have clear and unambiguous title. The goal is
  to be able to reference the runbook, and understand it's major purpose,
  without opening it. For example, "_Restarting the Foobar Application_" lets
  you know what how to do something for a specific application, while
  "_Restarting the Application_" is truly only helpful if yo have a single
  application to support. Let's be honest though, if you are looking at writing
  runbooks, you have more than a single application.
* **Summary** - include a summary that gives a brief overview of what the
  runbook actual will accomplish. This should include the keywords for the major
  actions taking place. For example, "_This runbook explains how to restart the
  Foobar application runnning on our Windows web servers. You will need
  administrator access to the server_"  pretty much lets everyone know what is
  going on.
* **Note** - I prefer to include any specific notes that are not really part of
  the other section in a notes field. This makes it standout as special rather
  than including it into a big blob of text, like the summary.

```yaml
title: Restarting the FooBar Application
summary: |
  This runbook explains how to restart the FooBar application runnning on 
  our Windows web servers.
note: You will need administrator access to the server
```

The next two elements are required because the person resolving the issue may
not be on your team, or even know who you are. If they are paged out and
handling an issue, and your system is either involved, or itself having
problems, there needs to be a way to contact the responsible parties.

I have worked at places where if you were the engineer on call it was all your
problem. You had to figure it out. Runbooks and documentation helped, but you
did not call other individuals to help solve the problems. I know, spare me the
lecture. It wasn't right but the expectations were what there were. And yes,
things did not get fixed quickly or accurately. This is why the author and
contact fields are so important. If I am troubleshooting something in my system,
and I discover the issues is actually within your system, then I need a way to
contact you.

* **Author** - this could be an individual or a team depending upon the size of
  the company. The goal is to give the runbook reader some context on who is
  write, or maintains, this documentation.
* **Contact** - this field is the key for the runbook. It answers the "_How do I
  contact the Author_" question. This could be an email, phone number, or
  anything else needed to locate somebody who can help.

```yaml
author: Ken Brittain
contact: team - teamdl@yourcompany.com or oncall cell 555-555-1212"
```

The next section is the meat of the runbook: steps. If someone has scanned
enough to find a resolution to their problem, they are going straight to this
section to determine how to resolve their issue. The steps give them the simple,
stept-by-step instructions, or activities to move them toward solving their
problem.

The goal is to provide enough information so that someone, who is not intimately
involved with your project, enough information to perform the required
activities to resolve the issue. While a DevOps approach of the development team
owning the production system is admirable, not all corporate teams are their
yet. So you should assume a level of system engineering or developer related
background, but write the step for someone not on your team. I think it is safe
to say that nobody from the marketing department will be jumping onto a bridge
to help stop your service from flapping.

* **Name** - the name of the step should give an indication to the major 
  purpose of the step. Just let everyone know what wil happen with the name. 
  Remember, the runbook will likely not be read thoroughly, unless your 
  solution doesn't work, in which case, a second more in depth read may happen. 
* **Summary** - the summary gives details the activity to perform. I like to 
  keep this section short and only give enough information to perform the 
  specific activity. This is not the time expand upon your creative writing 
  tendencies. Just let the person know what to do.

Assuming you are still in the automating the manual phase, and have not created
a set of scripts to perform a service restart, the following is sufficient. You
give the person enough information to get to a solution but does not get stuck
in the weeds. Like describing what RDP is, or where to find it.

```yaml
steps:
  - name: Log into production web server
    summary: Connect to the PRD-APPWEB01 server with RDP using your admin 
    account.
```

These steps go for however long you need to help get the problem solved. The
number of steps will be different for each runbook. The details should include
enough information to get the job done.

```yaml
  - name: Restart the IIS Service
    summary: Run the *Services* control panel "Run > services" and locate 
    the "W3SVC" service. Click the "Restart" link.
  - name: Log Off
    summary: Be sure to log off the server. Use the "Run" menu and type
    "logoff" into the text box.
    note: Use the logoff command to limit chances of accidental restarting
    the server from the menu. 
```

## Start from Where You Are

As you already know I recommend keeping your runbooks in an easily parsed format
such as YAML. Writing a runbook, in a non-structured manner, such as
in [Microsoft Word][365] (likely the worst possible solution),
or [Atlassian Confluence][conf] (better), leads to non-standard runbooks. No
matter how much you strive to keep it all in the same format there will be
deviation.

You need to look at the tradeoffs at this point. If you have no runbooks, or
system documentation at all, you can pretty do anything and make the system
better. You are starting from zero. If you are looking at using Microsoft Word,
and storing the runbooks in [SharePoint][sp], I would argue that is better than
a network shared folder of documents.

If you are writing your runbooks in YAML, similar to what I have descrbied 
above, then you have three (3) benefits:

1. They are easily scannable because the sections are clearly defined by the
   markup language.
2. You will be able to generate the desired views at a later time. For example,
   into Confluence or whatever your corporate standard defines where durable
   documentation resides.
3. They can be checked into git. This, in my opinion, drastically increases the
   likelihood that developers will actually create, and update documentation.
   Nothing kills the desire (or mandate) to actually write documentation then to
   log into, yet another tool. Let's keep the source close to where the author
   works.

[sp]:https://www.microsoft.com/en-us/microsoft-365/sharepoint/collaboration
[365]:https://www.microsoft.com/en-us/microsoft-365
[conf]:https://www.atlassian.com/software/confluence
[hp]:https://www.wizardingworld.com/
[got]:https://en.wikipedia.org/wiki/Game_of_Thrones