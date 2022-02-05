---
permalink: /posts/21-write-useful-log-messages.html
title: "Write Useful Log Messages"
layout: post
---
I have said that every [program your write should have a log][20]. What you
write in the log is just as important.

There is nothing worse than slogging through thousands of lines of banal log
messages to get to the diamond. That singular error message. The one that gives
you a clue. The one sliver of hope that could help solve your problem.

You need to write better log messages.

## Display values at the end

One of the things that has transformed my logging efforts is keeping the values
at the end of the log message. This allows for static text in the front, which
is easy to search for, and keeps the changing parts, the values in a consistent
location. Prior to adopting this my log messages would be written in long form
similar to this:

```csharp
_logger.LogDebug($"Bing search '{searchUrl}' returned '{response.StatusCode}'!");
```

I tried to make them sentences and keep them readable. Yes I used punctuation. I
will admit that this was a pattern I started with when doing Java development.
Nobody told me what to log or even how to do it properly. I am sorry to say
there is lots of code running, in WebSphere someplace, trying to tell a story in
the logs.

This style had two (2) major disadvantages that I found.

1. Changing the log message to add additional display values was cumbersome. I
   was rewriting the message and still trying to keep it readable. They got
   longer and more unusable as time went on. Even worse, they started to
   represent something that was not actually happening as additional changes
   were layered into the code. Out of date comments are bad. Out of date log
   messages are terrible.
2. Grepping for a condition, or specific message, was a nightmare. There was a
   lot of unneeded text that matched and gave more hits than desired. This was
   compounded by stylistic changes in the grammar and tense over time. You are
   not writing a book. These are log messages!

Now I display all of my values at the end of the log message. as a comma
separated list. The format is this:

```csharp
_logger.LogDebug($"STATIC TEXT [name=value]");
```

The previous message looks like this:

```csharp
_logger.LogDebug($"Bing search [searchUrl={searchUrl},statusCode={response.StatusCode}]");
```

I have experimented with using the `ToString()` method returning the properties
for a class in this format. It was easy enough to manage but turned out to be
too verbose. Most of the time I just want specific information and not
everything. You can hate me for admitting this, but I really got tired of adding
the `ToString()` method to all my classes just in case I was going to use it in
a log statement.

Besides, adding additional values to a log statement is easy. Just put them 
at the end in the order or importance.

## Use static lead text

My recommendation is to use static lead text. This allows for easy searching in
the log aggregation tools. If you are aggregating your logs using [Splunk]
[splunk] or [ElasticSearch][elastic] then it makes it easier to grep locally as
well! As an aside, I know there are other tools available but in the regulated
corporate environment these two (2) are the big ones that I had to contend with.

The pattern that I have adopted is using a short sentence or text that can
easily searched and understood. It should be unique enough so it does not clash.

```csharp
var searchUrl = $"https://bing.com?q={query}";
var response = await httpClient.GetAsync(searchUrl);
if (response.IsSuccessStatusCode)
{
    var content = await response.Content.ReadAsStringAsync();
    _logger.LogInformation($"Bing results. [query=${query},length={content.Length}]");
    // Do whatever you needed the query for here.
}
else
{
    _logger.LogLError($"Bing error. [query=${query}]");
}
```

One of the gotchas that I have discovered in my own logging has been not
differentiating the static text enough. This text is meant to be searchable. I
feel it should be readable, but it does not have to be a perfect sentence (see
above).

## Info for business, Debug for technology

I will admit that this recommendation was liberated from a blog post by Thomas
Uhrig titled [My Logging Best Practices][tuhrig]. I came across his post and
felt some kinship upon reading that we arrived, independently I might add, upon
putting the values at the end of the message. So, when I liked his take on the 
`info` versus `debug` messages, I added it to my tool chest.

In the past, I would log all exceptions as `error` and everything else
as `debug` or `info`. I would rarely use the `trace` log level for no reason 
I can explain. The level `info` and `debug` were where I landed with no real 
thought put into it.

Conceptually, I really like the idea of using the pattern of `info` level for
business logic and `debug` for technology. It has a nice separation. I think it
will help avoid the _enable debug for everything because you do not know where
the message was writte_” problem. I will continue to log exceptions and such as
`error`.

[tuhrig]:https://tuhrig.de/my-logging-best-practices/
[splunk]:https://www.splunk.com/
[elastic]:https://www.elastic.co/elastic-stack/
[20]:http://127.0.0.1:4000/posts/20-every-program-you-write-needs-a-log.html

 