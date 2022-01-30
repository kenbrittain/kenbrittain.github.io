---
permalink: /posts/20-every-program-you-write-needs-a-log.html
title: "Every Program You Write Needs a Log (Debug Rule #3)"
layout: post
---

Every single program you write needs to write a log. This includes everything
from the command line utility you wrote to large monolith application that runs
your business. 

Why? I have already talked about how I don't want to debug your code. I have
also defined some rules on how I want to debug your code when I have to by
[showing me your variables][1] and [initializing members together][2]. Life 
would be great if I had never had to fire up the debugger in the first place.
That can only happen if you write a log for me to look at.

I have lived in the corporate software world long enough to encounter thousands
custom business programs. They do all sorts of things. They each have their own
timeframe for running on what could be called a schedule. Imagine a program that
is run once every seven (7) years to provide the business with compliance
information to be used during a scheduled audit. Yeah, stuff like that happens.

Others have been incredibly small but performed critical business functions.
Some have been large and rarely used. In all but a few cases the original
developers were long gone. The code was years old. The languages used and tools
available were old and barely supported.

You need to write a log. Some IT departments are pretty good at slurping up logs
into a fairly centralized system that supports searching. Others are less than
optimal and required tickets to get copies from physical servers. The world is
not perfect but, in most cases, there were logs.

Here are my logging rules for your programs to help everyone:

1. **Default to the console**. When running your program the responsible party
   may not have access to the production version or installation. If you are
   relying upon a specific configuration file or environment variable to make
   your log visible you are not helping anyone. Always, and I mean always,
   produce a log appears on the console if there are no other configurations
   options present.
2. **Always show when the program starts.** If your log does not display when
   the program starts then I have to figure it out. I don't want to figure it
   out. Log rotation happens. Files are put in the wrong locations. I don't want
   to have to debug your logging configuration. Just display when the program
   starts with a simple message such
   as `Starting Mighty Little Command Utility Line v1.0`. If you are following
   rule #1 then I won't have to look very far. Believe me, nothing is more
   annoying than having to debug your WinForms application that the business
   requires, that produces no output, displays no user interface, and has no
   log.
4. **Display pertinent configuration options.** You need to show me the
   application configuration options in the log. This helps when changing those
   options, whether through environment variables, or specialized files. If you
   show me, in the log, those options, I can see clearly when the specific
   options I am changing has taken effect. Otherwise, I have to debug your
   program, and as we have discussed before, I really don't want to do that.
5. **Always show when the program stops.** Please see rules #2 about showing
   when your program starts. You might be asking: why do I need to show you when
   the program stops? I should be able to figure that out by the next program
   run starting log line or message. You may be correct with that, but sometimes
   your program will crash and not finish properly. If I am relying upon you
   start message I will never know. You can imagine my frustration in finally
   having to debug your program, only to discover that it crashed before
   cleaning itself up. Yeah, I know. It happens. If you only had a single log
   message that said `I'm Done` it would make everyone's life so easy. I would
   have not seen that message and saved myself three (3) days worth of work.

The rules are simple. All programs should produce something along the following
so everyone can see what is happening.

```text
Starting Mighty Little Command Utility Line v1.0
Using default configuration file => /home/kenbr/config/mighty.config 
Completed successfully!
```

[1]:https://kenbrittain.com/posts/18-show-me-with-temporary-variables.html
[2]:https://kenbrittain.com/posts/19-initialize-members-together.html