---
title: Keep it Simple Stupid
date: 2021-09-14
postindex: 1
url: /post/1/keep-it-simple-stupid
---

There are companies being funded that solely provide blogging tools for developers: [Hashnode][HN] and [DEV][DEV]. So why not just use that? Well, I went through the usual developer range of solutions:

 * Duh ... WordPress?
 * Do I write my own blog engine?
 * Should I use a static site generator?

Something inside of me did not want to use [WordPress][WP].

While tempting, writing yet another blog engine would be easy, but not too fun. Once started I am sure it would require, yet another feature to be just right. The next thing you know I am maintaining a blog engine. A blog engine with a single user. Scratching your own itch is fine but that itch has been scratched so many times before by so many <a href="https://github.com/topics/blog-engine?l=c%23">others</a>.

I have used <a href="https://jekyllrb.com">Jekyll</a> in the past. It is powerful yet simple to use, and I had a 100% horrible time installing it on <a href="https://linuxmint.com/">Linux Mint</a>. I finally wound up just running from a <a href="https://www.docker.com/">Docker</a> <a href="https://ddewaele.github.io/running-jekyll-in-docker/">container</a>. What to do?

This blog is a static HTML website. It is simple. It is very simple. There is little beyond a single CSS file to keep things in order. I write in HTML as well. <a href="https://commonmark.org/">Markdown</a> is great for what it is but there is very little keeping it from being HTML. Creating tables in markdown means you might as well be using HTML anyway. Do I plan on using a lot of tables? Who knows, I just started.

What about your favicon? Nope ... don't really care.

~~I made a concession to use <a href="https://getbootstrap.com">Bootstrap</a> because it handles a lot of things for me. It provides a decent cross-browser look and feel. That is definitely something I did not want to fuss with.~~

Found and changed styles to use the <a href="https://sukima.github.io/hackcss-ext/">hack.css</a> stylesheet as it is lighter than <a href="https://getbootstrap.com">Bootstrap</a> and handles mobile nicely.

[WP]: https://wordpress.org
[ HN]: https://hashnode.com
[DEV]: https://dev.to/