---
title: Yet Another Blog but this Time with AI
date: 2026-03-09
postindex: 86
url: /post/86/yet-another-blog-but-this-time-with-ai
---

Truth be told, this blog does not have AI integrated into it. I used AI to rewrite and remove a custom blog engine and then relaunched. Again.

*Say what now?*

The story of this blog is one of experimentation. I have always used it as my personal testing ground for ideas I have been mulling over. As they say, every developer either writes their own blog engine or is thinking about it. I have done both. Multiple times.

## The MVP HTML Launch (2021)

The original blog was a git repository of hand-coded HTML hosted on GitHub Pages. That was the entire plan. My goal was to launch something and not spend two (2) weeks fiddling with themes and blog engines before writing a single word. I found a terminal-style Markdown stylesheet, dropped it in, and called it done.

It worked. The theme was simple enough that I actually liked it. Post [zero][p0] went up in September of 2021 and the aesthetic has stuck ever since.

## The Great Jekyll Conversion (2021)

By December I was already tired of copy-pasting the same HTML navigation snippets into every new post. That gets old fast. [Jekyll][JKL] was the obvious next step for a GitHub Pages blog and I made the move.

Jekyll is powerful. It is also a pain to install on Linux. I eventually got it running in a Docker container, which is not exactly the frictionless writing experience I was after. The posts kept coming but the setup nagged at me.

## The Great Blogstatic Migration (2023)

I had a good run with Jekyll but by January of 2023 I wanted to focus on writing, not managing a blog. Managing a blog is not writing. [Blogstatic][BST] showed up at exactly the right time. Nice editor, simplified theme management, and I did not have to think about infrastructure.

The trade-off was that I was now dependent on someone else's platform. That is a trade I was willing to make. For a while, anyway.

## The Twitter Detour (2024)

I missed the entire year of 2024. Not missed as in "I was too busy shipping software." Missed as in I spent it being a spectator on Twitter and calling it entrepreneurship. I posted about things I was going to build. I did not build them. I have written about this at length in [I've been LARPing as an entrepreneur][p84] so I will not repeat myself here. It is embarrassing enough the first time.

## The Greatest Migration Ever (2025)

By 2025 Blogstatic had become [BlogMaker][BST] and I had migrated the blog onto a custom ASP.NET Core application. The ambition was reasonable. The execution was a solo developer trying to maintain a blog engine, write posts, and build other software simultaneously. Something had to give and it was the posts.

There were a handful of posts that year. The engine ran fine. Nobody was reading it anyway.

## The AI MVP Markdown Launch (2026)

At the end of 2025 I decided to simplify yet again. The database was the first thing to go. I used [GitHub Copilot][COP] to gut the persistence layer and replace it with flat Markdown files. A few prompts and an afternoon later the database was gone. That part genuinely impressed me.

The result is what you are reading now. Static Markdown files, edited in [Typora][TYP], built with [Hugo][HGO], and deployed to GitHub Pages. No database. No custom engine. No infrastructure to babysit. Full circle back to where this started in 2021, only this time with better tooling and five (5) years of hard-won opinions about what actually matters.

What actually matters is writing the posts.

[p0]: /post/0/zero-based-blog
[p84]: /post/84/larping-as-an-entrepreneur
[JKL]: https://jekyllrb.com "Simple, blog-aware, static sites"
[BST]: https://blogmaker.app "BlogMaker Blog Engine"
[TYP]: https://typora.io "Simple yet powerful Markdown editor"
[HGO]: https://gohugo.io "The world's fastest framework for building websites"
[COP]: https://copilot.microsoft.com/ "GitHub Copilot"
