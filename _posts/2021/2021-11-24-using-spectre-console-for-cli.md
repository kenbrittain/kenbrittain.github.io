---
permalink: /posts/9-using-spectre-console-for-cli.html
title: Using Spectre.Console for CLI
layout: post
---

<p>
    I have used the <a href="https://github.com/fschwiet/ManyConsole/">ManyConsole</a>
    project for several years for processing command line arguments in console
    applications (in C# of course). I had been sitting in .NET Framework land
    doing corporate development writing web and console-based applications for
    automating the DevOps journey. After working through many homegrown
    implementations and variations of parsing <code>string[] args</code>, it
    was always lacking something, and never had a good help display, ManyConsole
    was a breath of fresh air. It was (almost) everything I was looking for.
</p>

<p>
    Now that .NET 6 is out (<em>The One SDK to Rule Them All</em>), and
    developers are beginning to plan migrating from the older .NET Framework
    technologies, I began taking a fresh look at command line argument
    processing options. I looked for projects that met the following criteria:
</p>

<ul>
    <li>It was actively being developed during the past year (2021)</li>
    <li>Sub-commands are handled without jumping through programmatic hoops</li>
    <li>Support for the .NET 6 platform</li>
</ul>

<p>
    Originally the ManyConsole author did not plan on supporting the .NET
    Standard 2.0, which was .NET Core at that time. I can see his reasoning,
    and at that time, I was still squarely within .NET Framework land, so my
    concern was negligible. You can look at the issue, logged in the repository,
    for the explanation and resulting implementation:
    <a href="https://github.com/fschwiet/ManyConsole/issues/34">Support for .NET standard</a>
</p>

<p>
    I went hunting around <a href="https://nuget.org">NuGet</a> and
    considered the following packages. This list is not inclusive, as 500+
    packages comes up for a search on <em>commandline</em>. I always include
    the venerable <em>Mono.Options</em> because, for me, that is where this all
    began.
</p>

<ul>
    <li><a href="https://github.com/xamarin/XamarinComponents/tree/main/XPlat/Mono.Options">Mono.Options</a></li>
    <li><a href="https://github.com/dotnet/command-line-api">System.CommandLine</a></li>
    <li><a href="https://github.com/natemcmaster/CommandLineUtils">CommandLineUtils</a> (McMaster)</li>
    <li><a href="https://spectreconsole.net/">Spectre.Console</a></li>
</ul>

<h2>Mono.Options</h2>

<p>
    This package was the go to command line processing, in my programming
    library, for quite some time. Back when single executable programs were not
    really a thing, one could simply copy the source for <code>Mono.Options</code>
    into a project and be done. This is still a valid option for simple projects.
</p>

<h2>System.CommandLine</h2>

<p>
    This was a Microsoft project before it wasn't. Now it appears to be managed
    by the <a href="https://dotnetfoundation.org/">.NET Foundation</a>. IIRC,
    this package was supposed to be <em>THE</em> package for processing command
    line arguments. Hence its namespace: <em>System.CommandLine</em>.
</p>

<p>
    This project seemed promising at first but over time became more annoying
    to use. Why? While I appreciate a good lambda to help me code I really prefer
    a simple programming style myself. IMO, the fancier you get, with lambdas
    strung together, and really long fluent style lines of code, the harder
    everything is to debug. I have never had any great affection for fluent
    style programming, or nested lambdas to get things done, because I like very
    predictable debugging. This library appeared to really fall in love with
    lambdas. I prefer a more modest approach. Additionally: the DragonFruit
    namespace. Enough said.
</p>

<h2>CommandLineUtils</h2>

<p>
    This package has stood the test of time and powers a number of the tools that
    were written as part of my current professional projects. There is nothing
    wrong with this library, and it should work just fine for my current
    development needs.
</p>

<p>
    It handles sub-commands, has an attribute based model, and can limit the
    amount of lambda code I write. Before you wonder about my strange obsession
    with avoiding lambdas, please wait, and let me explain. This block of code
    is pure nonsense, and not debuggable. It all executes at once, and you cannot
    predict what is happening, before it happens. To me, that is a key point
    for debugging. You need to make the decision about what is happening before
    the debugger executes a line of code. Only then can can step over the code
    and observe the result.
</p>

```csharp
static async Task Main(string[] args) => await BuildCommandLine()
    .UseHost(_ => Host.CreateDefaultBuilder(),
        host =>
        {
            host.ConfigureServices(services =>
            {
                services.AddSingleton&lt;IGreeter, Greeter&gt;();
            });
        })
    .UseDefaults()
    .Build()
    .InvokeAsync(args);
```

<p>
    However, I found <a href="https://spectreconsole.net/">Spectre.Console</a>
    and it is, to me, all brand new and shiny. I cannot resist.
</p>

<h2>Spectre.Console</h2>

<p>
    It has a programming model very similar to ManyConsole, so it seemed to fit
    for me. Yes, there are lambdas but, in this context, they seem to work.
    It may be that there is a single level present, but I always appreciate
    just calling the methods. The command structure replicates a lot of what
    I had been doing with ManyConsole. It could be just a level of comfort with
    the programming model, but in my view, that is what makes this library
    great. It works like you want it to, without learning something new (ahem,
    DragonFruit!?)
</p>

```csharp
var app = new CommandApp();
app.Configure(config =>
{
    config.AddCommand&lt;AddCommand&gt;("add");
    config.AddCommand&lt;CommitCommand&gt;("commit");
    config.AddCommand&lt;RebaseCommand&gt;("rebase");
});
```

<p>
    Spectre also provides way better screen handling. The progress bar, which
    looks a lot like Docker, is really nice. The
    <a href="https://spectreconsole.net/live/status">status</a> view is better
    than my traditional printing dots for showing continuous activity. There
    will be less clutter on the screen!
</p>

<p>
    So far, the only downside that I can come up with is that examples are
    global and shown at the usage level. I would have preferred to have examples
    at the sub command level. Since I never included examples in my current
    applications this is something I can live with. Heck, it might even support
    this right now.
</p>

<p>
    Frankly, there is not a lot to complain about. I have just begun working
    with this library, and I am enjoying it so far.
</p>
