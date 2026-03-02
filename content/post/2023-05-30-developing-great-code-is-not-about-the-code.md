---
title: Developing Great Code is Not About the Code
date: 2023-05-30
postindex: 51
url: /post/51/developing-great-code-is-not-about-the-code
---

The other day I was working on a piece of code within an existing project. It was nothing magical but it needed to get done. I located where the change would be made and then it happened.

The original developer has created a useful and extensible block of code, all wrapped up into a class, that I could use. There was an interface and a default implementation that took reasonable defaults. I did not have to make any modifications other than using the defined parameters.

My 3-day planned adventure turned into a 1-hour fix. All because the original developer had thought ahead. There were comments on how to use the functionality that I wanted. There were unit tests to demonstrate how it was used. I was impressed.

Again, I was not the original developer. I had no familiarity with this code. Heck, the project itself is in maintenance mode and only fixes are actively being applied.

I just wanted to document that the difference between a good enough and a great developer are clearly defined. A good enough developer would have just enough to make the feature work:

* It would have hard coded assumptions.

* It would have been brittle to changes.
* It would have just merely worked.

Fortunately, a great developer made the change and left the appropriate amount of documentation and knowledge laying around for others to find.

This person took the time to do it right. It has been three (3) days since I made my change and I am still a bit giddy!
