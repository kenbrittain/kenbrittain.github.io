---
title: I Outsourced My Project Toil to AI
postindex: 87
url: /post/87-i-outsourced-my-project-toil-to-ai
---

What is project toil? 

It's the stuff in the middle of a project. The unfun stuff. Wrapping and hoisting interfaces to make 3rd part libraries fit into your programs. It's the glue code required to render a template. It's the stuff that is needed but not really interesting. Toil is the stuff jobs are made of.

I have outsourced the bulk of my project toil to [Claude][CLAUDE]. For this blog, that means updating and converting things to yet another format. I know, I know. I should just chill and let this project be the same for some length of time > **REALLY_SMALL_AMOUNT_OF_TIME**.

So you may ask yourself (I know I did) ... should Claude write any posts?

The answer is a big fat no but if you check the commit history you will see that it did. I may be full of contradictions, and if you read my posts you find many, but I'm okay with that.

So is writing project toil? This is, after all, a blog and this project consists of writing.

# Claude for Toil

Project toil for this blog has traditionally been moving to different formats: 

```mermaid
graph LR
  A[HTML] --> B[Jekyll]
  B --> C[Blogstatic]
  C --> D[ASP.NET Core]
  D --> E[Hugo]
```
That is the toil. You can look at this [post][TOIL] and see what I am talking about.

# Ken for Writing

You can look into this repository and see my [CLAUDE.md][MDFILE] file. The contents of this file will change but right now it setup to work on this repository under Hugo. It has a writing style section. The previous post was an outline when I found it. I used Claude to complete the writing of it. 

What a minute? I know I just said Claude was for the work between the writing ... but I just had to try it. The results ... meh (please see my previous comment about contradictions).

I will continue to use Claude for all sorts of project toil though. It converted my ASP.NET Core application to a Hugo website in a suprising low amount of prompts. There is more that needs to be done with the content and formatting. I won't be doing that. That is toil.

The writing will still be me.

# 

[CLAUDE]: https://claude.ai/
[MDFILE]: https://github.com/kenbrittain/kenbrittain.github.io/blob/main/CLAUDE.md
[TOIL]: /post/86/yet-another-blog-but-this-time-with-ai