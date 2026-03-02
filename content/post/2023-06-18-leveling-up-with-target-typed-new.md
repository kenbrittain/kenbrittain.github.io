---
title: Leveling Up with Target Typed new()
date: 2023-06-18
postindex: 70
url: /post/70/leveling-up-with-target-typed-new
---

I was originally exposed to this language feature when looking at some code published by Microsoft. I don't remember the project and it is not important for this discussion. What is important is that I saw an approximation of this:

```csharp
public MyConstructor(string param1)
    : base(new(new()), param1)
{
}  

```

I had no clue what was going on or what types were involved. As a language feature I was not pleased. Eventually and using the editor I was able to figure things out. That should not be case. I hated and avoided this feature.

Fast forward to now and I am using the new language features. More so to test them out and seeing which ones stick. I went through a cycle where I used target typed new() for almost all of my member initialization. It seems to be a good thing.

This feature is a syntax sugar coating that allows you to type less. Much like the `var` keyword. The compiler knows more things that it lets on and it can help us. The `var` keyword is one of those feature. The target typed new() is similar.

Does it really help?

It lets us type less. Nothing is sweeter than allocating a new collection and not having to type out `new Dictionary<string,string>();` again. That is why I get it. The target type new() saves us some time.

Remember though, what the language the language can take away. So, yes, there is less redundant types listed in your code. But the you will encounter things like this `this.Build = new();`. This is from my own code. I had to look up the type of the `Build` property.

Is saving time typing > understanding your types? I don't know yet.
