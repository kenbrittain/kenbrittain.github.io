---
title: The Final Leveling Up Roundup
date: 2023-06-25
postindex: 77
url: /post/77/the-final-leveling-up-roundup
---

The goal was to look into the newer C# language features. I felt that some of them may not have gotten an adequate hearing. Some of the features are actively being used, while others are still, in a word, shunned.

## Records

This new type is a shorthand for data classes. It can be useful some applications but has it's limitations. Primarily, once you begin applying attributes, you would be better served just writing a full class.

## Pattern matching

This is a broader category and I am currently only experimenting with switch expressions. Ranges and multiple patterns are still something that could slide into my workflow. Just not yet.

## Target-typed new()

Loving it for class members. Liking it when I want to be expressive for types. I am using it about 80% of the time.

## Covariant return types

It took a while to understand this feature. I can see the application for factory extension methods. I have not begun utilizing because I still rely on the different method name convention.

## Local functions

I don't see the point, have not, and will not be integrating local functions into my development workflow.

## Nullable reference types

This feature is actively being used. I like the concept. I still check for null because it can still happen from the calling code. It is just a fact of life.

## Null conditional operators

I see the point and may use them in certain case. I do not like long, chained method calls so this does have never been a problem for me.

## Anything Linq

I still do not see the benefit of creating long, single statements that are hard to debug. So I will not be using Linq any time soon.
