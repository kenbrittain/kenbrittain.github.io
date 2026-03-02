---
title: Leveling Up on Nullable Reference Types
date: 2023-06-21
postindex: 73
url: /post/73/leveling-up-on-nullable-reference-types
---

Nullable reference types define a world where not all reference types can be null. When enabled, and it is enabled by default, when using or assigning to `null`, you need to let the compiler know about it. Otherwise you will get a warning or error (depending upon your compiler settings).

Prior to C# 8.0 all types were nullable and that was just how code worked. If
you had a reference then it could be `null`. You were a developer, so you
checked for `null` when required. It was called programming.

I belie the goal is to make the programmer explicitly accept the responsibility for `null`. You can annotate with an attribute, using a special symbol, or using an old school `if..then` check for `null`.

I would only like to say that it is easy to use when you are aware of the goal. You can always pass a value to a method that can be `null`. You just need to use the `!` symbol to accept the responsibility. You can explicitly make a type nullable by using the `?`. Again, it is up to the developer to accept the responsibility for nullability (sp?).

Enabling the feature was simple. Add the following to your `.csproj` file, or
check a box in your IDE. You are ready!

```csharp
<span class="nt"><Project</span> <span class="na">Sdk=</span><span class="s">"Microsoft.NET.Sdk"</span><span class="nt">></span>
    <span class="nt"><propertygroup></propertygroup></span>
        <span class="nt"><nullable></nullable></span>enable<span class="nt"></span>
    <span class="nt"></span>
<span class="nt"></span>
```

Now the compiler is checking your code for what it calls `null-state`. If you
are going to use a variable the compiler will determine if:

1. The variable has been assigned to a value that is known to be not `null`.
2. or the variable has been checked against `null` and hasn’t been modified
   since that check.

The official docs can be [read here](https://docs.microsoft.com/en-us/dotnet/csharp/nullable-references) for more details. You just need to
keep doing what you have, hopefully, been doing. Either assign the variable
to a known value, or check the variable against `null`, before using the
variable.
