---
permalink: /posts/12-minimum-viable-jekyll-website.html
title: Minimum Viable Jekyll Website
layout: post
---

It has been 82 calendar days since pushing the first commit for this website.
The initial blog was a hard coded, static website that contained a minimalist
look and feel in the form of
the [hack.css](https://sukima.github.io/hackcss-ext/)
stylesheet. It used [prismjs](https://prismjs.com/) for syntax highlighting, and
that was segregated into two (2) different post template files. In reality, I
was doing a lot of copy+paste to get things done. Mistakes were made but the
goal of getting something out, that is shipped, there was accomplished .. . and
that change everyting!

This is the 12th real post, and I have been averaging 1 post every 6 days. In
order to reduce the overhead of site maintenance I have ported my static website
into a Jekyll based website (kind of where I started). This time there is no
screwing around with the themes as all of that was already taken care of. I like
the markdown style theme.

## RSS Feed

The major reason for the introduction of Jekyll was to get an RSS feed. I
originally tried to produce one manually, in keeping with the spirit of the
static website plan. It went well for the first batch of test posts but never
made it into production.

The manual nature of creating the XML, while not difficult, brought about the
review of the exiting content. As I was creating the XML I needed to get the
titles and dates of the existing posts. That is where I discovered numerous
errors in dates and titles. SO much for manual. I knew I would get to a point
where manual would no longer cut it the RSS Feed was it.

## Enter Markdown

Once the decision was made to create a minimum website using Jekyll that led
to `permalink` entries for posts to get the same URL format that already
existed. I liked the sequential numbering of the posts. It makes more sense to
me than a more traditional date base linked system. In reality, nobody cares
when a post was made so long as the information it contains it pure gold.

When creating the HTML files and doing all of this manually the URLs were
created, and by definition, were permalinks. By converting the posts to use
the `_posts` directory to get the RSS feed that bit was lost. Every post needed
to have a front matter section added. Some posts required to be changed to
Markdown `.md` files while other could be kept as `.html` files. Both needed to
have the front matter to be added. The actual content of the file was
negotiable.

## Exit Prism

Once the files were properly converted to handle the front matter there was very
little need to keep the files from *NOT* processing the syntax highlighting.
Jekyll handles that during the website generation. This was currently being
handled on the client using JavaScript. This was not ideal, in my mind, as it
caused a lag when displaying code that was sometimes visible.

In order to enable Jekyll to handle this I created the `_config. yml` file and
selected the proper markdown processor for GitHub Pages. A few changes later I
had removed the Prism and nothing was highlighting. Some searching found that I
need to include a stylesheet from the `rouge` themes to get the display to work
properly.

## Conclusion

Now I have what I call a *Minimal Viable Jekyll Website*. It has the same look
and feel as the static website. It doesn't use any Jekyll theme or other Git
repositories. It has all the content previously published, and it works great
under GitHub Pages. I think this is still fitting of the
original [Keep It Simple Stupid](/posts/1-keep-it-simple-stupid.html) philosophy
espoused in post #2.
