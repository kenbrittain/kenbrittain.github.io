---
title: The Magical Multi-Platform Pipeline Writer
date: 2023-06-11
postindex: 63
url: /post/63/the-magical-multi-platform-pipeline-writer
---

I have seen enough build pipelines to know that they are all the same. The syntax is different but concepts are the same. This makes sense as each vendor is trying to do the same things: automate builds.

Each build definition begins with a file. This file defines the actions required to transform the source code into something usable. I use the work transform because the act of compiling source code works for many language but not all.

The work of defining the build is really just a list of commands or scripts to run in sequence. The sequences are broken up into blocks. These blocks are given names and displayed in the user interface.

What the pipeline actually does is left up to the developer. What the blocks are called is left up to the developer as well. This allows for builds and deploys to be defined in a pipeline. In fact, with the ability to run the pipeline I have seen many jobs defined as pipelines.

The system can be simplified down to this level:

1. **Pipeline** contains blocks
2. **Block** contain actions and other blocks
3. **Action** contain programs, scripts, and commands to run

One you allow the actions to write themselves in a platform specific manner you have a magical multi-platform pipeline writer.

What?

There is an accepted sequence of events to transform any particular type of source code into an artifact. This object model is the pipeline. Writing that out in a specific format is just a simple matter of programming.
