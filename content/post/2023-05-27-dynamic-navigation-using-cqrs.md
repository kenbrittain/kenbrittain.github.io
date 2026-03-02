---
title: You Aren't Gonna Need It - Right Now!
date: 2023-05-27
postindex: 48
url: /post/48/dynamic-navigation-using-cqrs
---

The database for my project will be a read-only [SQLite](https://sqlite.org/index.html) file. The application will need to navigate through different content categories, query for the latest, and find related items. This is perfect for a relational database.

A goal is to allow for dynamic navigation. There will be tables for the different types of technology. There will also be tables for the different tasks to be accomplished. If I use the database to map the navigation then the application does not need to be modified to handle the change. I really do not want hard code the page transitions for a CMS.

But do I need this for the MVP?

This falls squarely in the YAGNI type of programming. However, I would like to argue that YAGNI needs to be changed to YAGNI-RN. The RN standards for Right Now. You Aren't Gonna Need It Right Now.  Just because I don't need it now doesn't mean I should code myself into a corner.

By relying too heavy on YAGNI as a design principle I have coded myself into corners before. I am adding things I won't need right now but will later. Things like user accounts, security, logging, and metrics.

That does not mean that I have to code a fully implemented user account model into the application. There will be no registration and no login forms. However, there will be a user, and an account. They just won't be used. Same for the rest.

In order to save time later and so I don't want to have to extend the application, and the data model, after the fact I am going leave in YAGNI-RN placeholders.
