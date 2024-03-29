---
permalink: /posts/2-new-keyword-interview-question.html
layout: post
title: New Keyword Interview Question
---
<p>
  Part of the duties of a senior team member is to interview
  candidates for open positions. This task comes up for various
  reasons: attrition, growth, and new projects. Interviews are often
  done for other teams as well. Let's face it, interviews are part of
  the job.
</p>

<p>
  When interviewing developers I give them the opportunity to self
  rank (from 1..10) on their understanding of a language or
  technology. I will ask something along the lines of:
</p>

<blockquote class="blockquote">
  <p>
    If 1 is a complete beginner and 10 means you're an expert in X,
    where would you rank your understanding between 1 and 10?
  </p>
</blockquote>

<p>
  Yes, this is a loaded question. However, I like it because it allows
  the candidate to consider where they stand, and more importantly,
  what they want to share.  A rank of 10 would seem arrogant. Even if
  you were an expert I would guess that you should not say 10. The
  goal is to be honest with yourself first. There are always things
  you do not understand. You can see the calculation going as most
  candidates will say ... 7.
</p>

<p>
  If you are a C# developer, and you say 8+ you will then get this
  question: "How many uses of the keyword <code>new</code> exist in
  the C# language?" In the C# programming language
  the <code>new</code> keyword can be used as:
</p>

<ul>
  <li>operator</li>
  <li>constraint</li>
  <li>modifier</li>
</ul>

<p>
  Most developers use and will provide examples of using the operator
  to instantiate objects and arrays.
</p>

<p>
  The <code>new</code> <b>operator</b> used to invoke constructors,
  arrays, and instantiating anonymous types. This is the most common
  usage and
  documented <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/new-operator">here</a>.
</p>

```csharp
// object
var str = new StringBuilder();
str.Append("new operator");

// array
var newTypes = new int[3];
newTypes[0] = 1;
newTypes[1] = 2;
newTypes[2] = 3;

// anonymous
var a = new { Text = "anonymous object" };
Console.WriteLine($"{a.Text}");
```

<p>
  Someone who has programmed C# professionally, for any length of
  time, will have used generics. If they wrote generic classes they
  may have encountered the constraint usage. This is good indicator
  they are writing libraries or shared code for their projects. This
  constraint is used when the generic class is required to instantiate
  a type. I have used this to create domain objects and then fill them
  up with data programmatically, generally with reflection.
</p>

<p>
  The <b>constraint</b> <code>where T : new()</code> ensures the type
  has a default (parameterless) constructor and is
  documented <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters">here</a>.
</p>

```csharp
// constraint
public class Factory&lt;T&gt; where T : new()
{
  public T Create()
  {
    var o = new T();
    // initialize 'o' with common params
    return o;
  }
}
```

<p>
  Experience has shown that the new constraint usage is usually
  associated with creating and setting up some object or
  properties. The generic type will also have an interface implemented
  that can be used to properly initialize the newly created object.
</p>

<p>
  The final usage for the keyword <code>new</code> is as a
  modifier. This modifier is used to when a method in a class
  conflicts or hides the base class method of the same name.
</p>

<p>
  I have only used the modifier when integrating into an existing
  library or shared code, and I absolutely refuse, or cannot, change
  the name of the class member. If you are okay with changing the
  derived member name, even just adding a character, then this
  modifier is generally not required.
</p>

<p>
  The <b>modifier</b> usage is
  documented <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/new-modifier">here</a>.
</p>

```csharp
// modifier
public class BaseClass
{
    public string Name { get; } = "Base";
}

public class DerivedClass : BaseClass
{
    public new string Name { get; } = "Derived";
    // just change the name b/c they really are 2 different members
    public string Name2 { get; } = "Derived";
}
```

<p class="fst-italic">
  Is <code>Name2</code> a properly named member? Depending upon your
  review standards ... well ... NO! In the real world if you find
  yourself using that you may just want to consider using
  the <code>new</code> modified.
</p>
