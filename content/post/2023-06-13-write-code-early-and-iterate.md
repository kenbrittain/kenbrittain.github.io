---
title: Write Code Early and Iterate
date: 2023-06-13
postindex: 65
url: /post/65/write-code-early-and-iterate
---

DevOps has the concept of controlling the blast radius for a change. You gradually make the intended change, expanding it's reach in iterations, until you finally achieve your roll out goals. At any point during the process, if something went wrong, you were in control. If you deployed everything at all once to production and it failed you would need to roll everything back. If you deployed a piece of the change to a segment of your environment any errors would only affect a smaller portion of you customers. You get the idea.

When writing code I like to apply the same principle. For greenfield development I will implement the design and then use that code in a few unit tests. Using a unit test framework allows you to control the blast radius of a bad idea.

If I had went ahead and implemented a skeleton web application or perhaps command line program to utilize the classes there would be more support code and infrastructure involved. The surrounding code solidifies the design and the resulting code. The project becomes less flexible as it becomes more established.

If you use a unit test framework there is no surrounding code. The framework already exists. This allows you to code so you can determine if the style, or flow, is what you would like. Ideas can be changed rapidly with little impact here. Once the core set of classes and functionality are to your liking then you expand outward.

Use a test framework as the first client to your code and control the blast radius of your bad ideas.
