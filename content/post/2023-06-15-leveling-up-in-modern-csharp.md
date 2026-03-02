---
title: Leveling Up in Modern C#
date: 2023-06-15
postindex: 66
url: /post/66/leveling-up-in-modern-csharp
---

I started with C# in the .NET Framework 1.1 days.  
  
It has changed a lot since then (obviously) but recent events have made me realize just how long I have been holding onto my old-school development patterns.

Here is my list of things I am proactively going to learn about:

1. Records
2. Pattern matching
3. Target-typed new()
4. Covariant return types
5. Local functions
6. Nullable reference types
7. Null conditional operators
8. Anything Linq

## Records

I still write Data Transfer Objects (DTO) and sometime name them that. This is from my J2EE days.

Properties may have replaced getter and setter methods and calling it a model doesn't change the fact it is just data.

I need to look into records.

## Pattern Matching

because I still use `if..then..else`. After watching a video recently from [@ShawnWildermuth](https://twitter.com/ShawnWildermuth) I realize just how outdated some of my language patterns are.

Pattern matching look powerful and I've just been lazy in this regard.

## Target-typed new()

This one holds potential b/c I prefer to initialize all of my class members in the constructor for debugging purposes.  
  
They are class members so `var` is not an option. Less typing and letting the compiler figure it out is a win.

## Covariant return types

this is more of a knowing thing to keep in my back pocket. I have created tuples to return things like this before. It works but this may be better.

## Local functions

They seem like a frivolous thing but maybe they are not. My initial take on them was for reducing complexity in longer functions. I did not see any real benefit over a private method.

## Nullable reference types

This is the default now. I don't think about it much and I get caught by the compiler a lot. I am also using `<warningsaserrors>Nullable</warningsaserrors>` so I don't miss out on the fun.

## Null conditional operators

I use null coalescing when checking parameters but that is pretty much it. Time to up my null check game now that I am committing to the warning as errors setting.

## Anything Linq

Honestly I hate Linq. I don't know why but I avoid it all of the time. It might be time to get some solid Linq knowledge under my belt.
