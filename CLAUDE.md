# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Serve locally with live reload
hugo server -D

# Build for production
hugo --minify

# Create a new post
hugo new post/YYYY-MM-DD-post-title.md
```

## Architecture

This is a Hugo static site deployed to GitHub Pages at `https://kenbrittain.com`. Pushes to `main` trigger the GitHub Actions workflow (`.github/workflows/hugo.yml`) which builds and deploys automatically.

**Content:** All posts live in `content/post/` as Markdown files named `YYYY-MM-DD-title.md`. Posts use TOML front matter with a required `postindex` field (integer) that controls the display order on the homepage. The `url` field is used to set clean URLs like `/post/87/title`.

**No theme submodule** — the site uses a custom layout with no Hugo theme. CSS/JS assets are served from `static/` (terminal-style CSS + highlight.js).

**Templates:**
- `layouts/_default/baseof.html` — base HTML shell with highlight.js and analytics
- `layouts/index.html` — homepage lists posts sorted by `postindex` descending
- `layouts/_default/single.html` — single page template (renders `.Content` + back link)
- `layouts/post/single.html` — post-specific single template

**Post front matter pattern:**
```toml
+++
title = 'Post Title'
date = 2026-01-01
postindex = 88
url = /post/88/post-title
draft = false
+++
```

The `postindex` must be unique and incremented manually for each new post.

## Writing Style

When drafting or editing blog posts, match this established voice:

**Voice & Tone**
- First-person, direct, opinionated — take a position and defend it
- Honest about failures and shortcomings without wallowing
- Dry wit and understatement; humor is incidental, not performed
- Practitioner perspective: 20+ years of industry experience, not academic

**Sentence & Paragraph Structure**
- Short paragraphs: 2–4 sentences, rarely more
- Mix sentence lengths: short declarative statement, then a longer follow-up
- Topic sentence leads every paragraph — main point comes first
- No throat-clearing intro; get to the point immediately

**Distinctive Quirks**
- Numbers as word + numeral in parentheses: "two (2) years", "three (3) days" — apply consistently
- Conversational asides as their own line: *"Say what now?"*, *"Ouch! Yeah."*
- Italics for emphasis on specific words; bold used sparingly for key assertions

**Structure**
- Posts are short: 200–500 words is the norm
- H2 headers only when a post has 3+ distinct sections
- Bullet lists are brief and parallel; not used as a crutch
- External links embedded naturally in prose, never bare URLs

**Content Patterns**
- Enter via personal anecdote or reaction to something read/experienced
- Use external articles or opinions as a foil to sharpen your own position
- Conclusions are pragmatic — no grand calls to action, just what works
- Technical specificity when it matters: exact product names, version details

**What to Avoid**
- Filler phrases: "In conclusion...", "It's important to note..."
- Hedging language when stating opinions
- Lists that replace an argument instead of supporting one
- Inspirational or motivational tone
