---
permalink: /posts/19-initialize-members-together.html
title: "Initialize Members Together (Debug Rule #2)"
layout: post
---
When debugging code I want to follow the flow and not get bounced around in the
source like a ping pong ball.

The statement below is very simple. We are creating a single object using the
constructor that takes a `DateTime` value. When I step into this code I want to
be taken to the constructor.

```csharp
var pp = new PingPong("Sample", DateTime.Now);
```

My experience has shown the following class to be common type of coding format.
A bunch of private variables that are used in the class, then comes the
constructors, and finally the methods. The methods are usually grouped by scope,
or in alphabetical order, and sometimes both. It's a pattern, and it is easy to
follow.

```csharp
public class PingPing
{
    private Dictionary<string,int> _scores = new Dictionary<string, int>();
    private string _title = "Untitled";
    private DateTime _when;
    
    public PingPing(DateTime when)
    {
        _when = when;
    }

    public PingPing(string title, DateTime when)
    {
        _when = when;
        _title = title;
    }

    public void AddScore(string name, int points)
    {
        _scores[name] = points;
    }

    public void DisplayScore(TextWriter output)
    {
        output.WriteLine($"{_title}");
        foreach (var score in _scores)
        {
            output.WriteLine($"{score.Key}: ${score.Value}");
        }
    }
}
```

When it comes time to step into the constructor though is where I run into
issues. The initializers will be executed before the constructor code. The
debugger will jump around at the top of this class before entering the
constructor. This example is not bad but have your ever stepped through a
kitchen sink class, waiting for the constructor, but what feels like the entire
BCL is being created first?

Why would you do that me? We have already established that I am a lazy
developer. I don't want to debug your code, let a lone mine. So why make me set
a break point in the constructor, or constructors, just to see what is going on?

This variation allows me to have a single location to debug. You can either like
it or find issues with it. I am telling you that debugging is easier when you
have a single place add and remove initialization logic. The debugger does not
ping pong around the initializers for your collections, defaults values, and
loggers. I'll concede `static` text because, well, it has to be in there
somewhere.

```csharp
public class InitializedTogether
{
    private static readonly string UntitledText = "Untitled";
    
    private Dictionary<string, int> _scores;
    private string _title;
    private DateTime _when;
    
    public InitializedTogether(DateTime when)
        : this(UntitledText, when)
    {
    }

    public InitializedTogether(string title, DateTime when)
    {
        _scores = new Dictionary<string, int>();
        _when = when;
        _title = title;
    }
    
    /* AddScore and DisplayScore methods */
}
```

I have found this pattern to help debugging. For some, it may look a little off,
but once you get into the habit of looking for all initialization in the same
place life gets easier. If, due to your various parameters you cannot make this
work, you can always create an `Initialize(...)` method and call that from the
constructors. 
