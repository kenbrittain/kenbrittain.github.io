---
permalink: /posts/18-show-me-with-temporary-variables.html
title: "Show Me with Temporary Variables (Debug Rule #1)"
layout: post
---
Interactive debuggers are great. They can show many aspects about your code
while it is running. The best thing is the ability to look at variables and
their values at runtime. As the name interactive implies, this requires some
activity on the part of the developer. A mouse, or even keyboard shortcuts, can
be used to step over, step into, or view the results of code being executed.

While debugging, I have established a pattern of setting a breakpoint at the
desired location and then using the step over/into keys to examine a block of
code. Stepping over conditions are particularly interesting. You have seen this
generic `if` statement numerous times.

```csharp
if (condition)
{
    // statements
}
```

When I am debugging I want to know what the code is going to do before it
executes. That is why I am stepping through the code. If what I am expecting
does not happen, then the bug has been identified. Using the debugger will allow
me to inspect the condition before it executes. I just have to move my mouse, or
cursor, to the condition, and it will be displayed as a popup. Some debuggers,
depending upon the platform, may expand and display the value in another section
where all local, or class, variables are displayed as well.

I am lazy developer. I don't want to move the mouse to display a value. I
already have my hands on the keyboard while I am stepping through the code. I
want to watch what is happening in the debugger. I do not want to interact with
the debugger. My preferred pattern is the following:

```csharp
var result = condition; 
if (result)
{
    // statements
}
```

Using the temporary variable to store the conditions result may seem overkill. I
like it because I can see the result of the condition **before**
the code executes the `if` statement. I know there a developers who will call me
crazy (I have already admitted that I am lazy). They will say the debugger will
expand the values for you. They will say writing the extra code either takes too
long, is a code smell, makes the code confusing, or make the compiled program
slower. All of these things have been fired at me for using this coding pattern.

For starters, they are all wrong. I have never actually checked but I would bet
a cup of coffee that the compiler will optimize out the assignment. See not
slower! It is not a code smell because it makes the code clearer. I will concede
that it takes a little longer to write this type of code. It may be longer, but
it is clearer, and I write my code for others to understand. 

> I do not write my code to prove how amazing I am at writing code. I have 
> worked with those individuals. Understanding their code is a problem and
> debugging it is painful.

Now I can see what the code will do before it does it. That is debugging code.
If you are just watching code execute then you are learning nothing. It's like
TV. It's too passive. If you participate in the debugging, and do the mental
work to debug your code, it's called learning.

Show me what your code is going to do by processing things, in order, a couple
of statements at a time. Store the result in a temporary variable so I can see
that in the debugger. I know the example above is rather basic. You may may
question this pattern and ask why bother. If you have ever written business rule
validation the following should look familiar. Which version would you rather
debug?

This code is not real, but I have seen, and worked on numerous examples such as
this. Leave aside the arguments for a validation library, specialized classes,
or attributes to handle this validation work. When writing line of business code
to process transactions, according to a specification or requirement from a
business partner, this type of code is far too common.

```csharp
public bool IsValidAddress(Address addr)
{
    return addr.First != ""
      && addr.Last != ""
      && addr.Street != null
      && addr.Street.Length > 3
      && addr.City != ""
      && addr.State != null
      && addr.State.Length == 2
      && addr.Zip != null
      && addr.Zip.Length >= 5;
}
```

I would rather debug the following code. It uses temporary variables to show me
what is going to happen before it happens. As I have said before: I like know
what the code is going to do before it does it. I can see where something is 
or will go wrong before it does.

```csharp
public bool IsValidAddress(Address addr)
{
    bool validName = addr.First != "" && addr.Last != "";
    bool validStreet = addr.Street != null && addr.Street.Length > 3;
    bool validCity = addr.City != "";
    bool validState = addr.State != null && addr.State.Length == 2;
    bool validZip = addr.Zip != null && addr.Zip.Length >= 5;

    return validName && validStreet && validCity && validState && validZip;
}
```
