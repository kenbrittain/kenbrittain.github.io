---
title: Leveling Up on Local Functions
date: 2023-06-20
postindex: 72
url: /post/72/leveling-up-on-local-functions
---

Local functions are a scoping trick to prevent other methods from calling your function. They are like special case private methods as they cannot have any other scope applied.

There are all sorts of cases for using local function according to the documentation. I have encountered any of them in real life. Maybe if I was writing a large, general purpose framework I would. Alas, I work in an insurance company and have no desire to hide a private method from my coworkers.

There are multiple use case described for forcing exceptions, lambda expressions, variable capture, and heap allocations. I'm sorry but I see myself using none of these.

My only use case for local functions is where I have a large function and I want to hide certain repeating code. I could use a local function but I probably won't. I would just write a regular old private method.
