---
permalink: /posts/40-taocp-volume1-chapter1-basic-concepts-algorithms.html
title: "TAOCP: Volume 1, Chapter 1 - Basic Concepts, 1.1 Algorithms"
layout: taocp
tag: taocp
summary: |
  Section 1.1 defines the syntax and method for documenting the algorithms
  that will be presented in the book.
takeaway: |
  I think the methods presented are to be utilized within the larger suite of
  projects and requirement definition writing that is undertaken professionally.
  In fact, I would say the key takeaway is what I will call the algorithm syntax.
---

The text begins with a bit of history and etymology of the word *algorithm* itself. After wandering through the history Knuth arrives at the modern definition:

> By 1950, the word algorithm was most frequently associated with Euclid's algorithm, a process for find the greatest common divisor of two numbers that appears in Euclid's Elements (Book 7, Propositions 1 ans 2).

Euclid's Algorithm, titled as Algorithm E, is then presented in textual and flowchart forms. I think this is important to mention because the format of the algorithm description is the style that will be used to describe all of the algorithms for the rest of the book.

> **Algorithm E** (Euclid's algorithm). Given two positive integers *m* and *n*, find their *greatest common divisor*, that is, the largest positive integer that evenly divides both *m* and *n*.
>
> **E1.** [Find remainder.] Divide *m* by *n* and let *r* be the remainder. (We will have 0 &le; *r* < *n*)
>
> **E2.** [Is it zero?] If *r* = 0, the algorithm terminates; *n* is the answer.
>
> **E3.** [Reduce.] Set *m* &larr; *n*, *n* &larr; *r*, and go back to step E1.

Each algorithm is identified by a letter, in the case of Euclid's algorithm, the letter *E*. Each step in the algorithm is identified by the algorithm's letter followed by a number. Each step is further identified by a phrase the sums up the main activity or purpose of the step. This phrase will appear in any flowchart of the algorithm.

When referring to the algorithm within a section only the letter is used. When referring to an algorithm in another section the section number will be prefixed. For this example, Euclid's algorithm, referred to as *E* in this section, would be referred to as *Algorithm 1.1E* from other chapters. 

Knuth designed this style to help describe an algorithm as text. Today we rely upon too many visual artifacts to express ourselves. During the 1990s we went through the diagramming wars with [Booch][booch], [Jacaboson][jacobson], and [Rumbagh][rumbaugh], until we arrived at [UML][uml]. Try tossing a UML diagram out there these days and see where that gets you. Descriptive text is timeless.

## Features of an algorithm

After defining how to represent an algorithm, the text moves on to define the features of an algorithm. It is only 1 page and a half of the book but I think it is important to call attention to it. This book is is called "Fundamental Algorithms" so I have a gut feeling that algorithms, and their representation, are going to play a big part of my learning.

1. *Finiteness* - the algorithm will end after a certain number of steps.
2. *Definiteness* - each step must be *precisely* defined. Many of the algorithms will be presented in English and as a computer program to avoid ambiguousness.
3. *Input* - the algorithm has zero or more inputs.
4. *Outputs* - the algorithm has one or more outputs.
5. *Effectiveness* - here Knuth defines effectiveness as "its operations must all be sufficiently basic that they can in principle be done exactly and in a finite length of time by someone using pencil and paper." If you can work it out on paper then you either understand it, or it is clear enough to be understood. 

The section of algorithms closes with a mathematical discussion. I got  to the *computational method* part that discussed the quadruple (Q,I,&#937;, f) where Q is a set containing subset *I* and &#937; ... and then it all fades into math. Kuth references [*The Theory of Algorithms [Trudy Mat. Inst. Nauk 42 (1954), 1-376]*][ttoa] as a source I am sure I will never venture a look at. If you check out the link you find a $130 textbook. That is cheap in the realm of textbooks but not something I will ever be interested in.

Even reading, then writing about it in this post is enough. 

## Exercises

The exercises are 9 exercises with the most difficult being a level M30. Referring back the notes, this means that it is a moderately hard mathematically oriented problem. 

Questions 1-6 were easy to determine the answers with Q6 actually taken time to work out. It was not complex but you just need to run through the algorithm. 

Question 7, 8, and 9 dive into the realm of math. 'nuf said.

[notes]:/posts/35-taocp-volume-1-notes-on-the-exercises.html	"TAOCP: Volume 1, Notes on the exercises"
[booch]:https://en.wikipedia.org/wiki/Grady_Booch	"Grady Booch"
[jacobson]: https://en.wikipedia.org/wiki/Ivar_Jacobson	"Ivar Jacobson"
[rumbaugh]:https://en.wikipedia.org/wiki/James_Rumbaugh	"James Rumbaugh"
[uml]:https://www.uml.org/	"Unified Modeling Language"
[yourdon]:https://en.wikipedia.org/wiki/Edward_Yourdon	"Edward Youdon"
[mso]:https://www.amazon.com/Mainstream-Objects-Analysis-Approach-Computing/dp/0132091569	"Mainstream Objects: An Analysis and Design Approach for Business"

[ttoa]:https://www.amazon.com/Theory-Algorithms-Mathematics-its-Applications/dp/9027727732

