---
permalink: /posts/40-taocp-volume1-chapter1-basic-concepts-algorithms.html
title: "TAOCP: Volume 1, Chapter 1 - Basic Concepts, 1.1 Algorithms"
layout: post
---

This is the first real chapter in the volume. The previous [notes on exercises][notes] chapter was more informational on how to tackle the exercises.

The text begins with a bit of history, and etymology of the word *algorithm* itself. It is somewhat interesting some but after wandering through the history Knuth arrives at the modern definition:

> By 1950, the word algorithm was most frequently associated with Euclid's algorithm, a process for find the greatest common divisor of two numbers that appears in Euclid's Elements (Book 7, Propositions 1 ans 2).

Euclid's Algorithm, titled as Algorithm E, is then presented in textual and flowchart forms. I think this is important to mention because the format of the algorithms description is the style that will be used to describe all of the algorithms for the rest of the book.

> **Algorithm E** (Euclid's algorithm). Given two positive integers *m* and *n*, find their *greatest common divisor*, that is, the largest positive integer that evenly divides both *m* and *n*.
>
> **E1.** [Find remainder.] Divide *m* by *n* and let *r* be the remainder. (We will have 0 &le; *r* < *n*)
>
> **E2.** [Is it zero?] If *r* = 0, the algorithm terminates; *n* is the answer.
>
> **E3.** [Reduce.] Set *m* &larr; *n*, *n* &larr; *r*, and go back to step E1.

Each algorithm will be identified by a letter, in the case of Euclid's algorithm, the letter *E*. Each step in the algorithm is identified by the algorithm's letter followed by a number. Each step is further identified by a phrase the sums up the activity or purpose of . the step. This phrase will appear in any flowchart of the algorithm.

I am not going to detail all of the algorithms in the books but I think it important to record this here. These posts are my notes. Knuth obviously thought about this style to help describe an algorithm, in text. Today we rely upon too many visual artifacts to express oursevles. During the 1990s we went through the diagramming wars with [Booch][booch], [Jacaboson][jacobson], and [Rumbagh][rumbaugh], until we arrived at [UML][uml]. My personal favorite was the [Yourdon][yourdon] champion Coad/Yourdon method for Object Orient Analysis and his follow-up efforts with Mainstream Objects. I do love the old days diagramming and the methodologies back then. Try tossing a UML diagram out there these days and see where that gets you.

When referring to the algorithm within a section only the letter is used. When referring to an algorithm in another section the section number will be prefixed. For this example, Euclid's algorithm, referred to as *E* in this section, would be referred to as *Algorithm 1.1E* when in other chapters.



## Exercises

The exercises are 9 exercises with the most difficult being a level M30. Referring back the notes, this means that it is a moderately hard mathematically oriented problem. Let's give this a go then.



[notes]:/posts/35-taocp-volume-1-notes-on-the-exercises.html	"TAOCP: Volume 1, Notes on the exercises"
[booch]:https://en.wikipedia.org/wiki/Grady_Booch	"Grady Booch"
[jacobson]: https://en.wikipedia.org/wiki/Ivar_Jacobson	"Ivar Jacobson"
[rumbaugh]:https://en.wikipedia.org/wiki/James_Rumbaugh	"James Rumbaugh"
[uml]:https://www.uml.org/	"Unified Modeling Language"
[yourdon]:https://en.wikipedia.org/wiki/Edward_Yourdon	"Edward Youdon"
[mso]:https://www.amazon.com/Mainstream-Objects-Analysis-Approach-Computing/dp/0132091569	"Mainstream Objects: An Analysis and Design Approach for Business"







