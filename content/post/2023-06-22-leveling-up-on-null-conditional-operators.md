---
title: Leveling Up on Null Conditional Operators
date: 2023-06-22
postindex: 74
url: /post/74/leveling-up-on-null-conditional-operators
---

The null conditional operator short circuit bad code from executing. The `?.` and `?[]` operators will return the operand if the operand is not `null`.

This operator allows code like the following to execute without throwing an exception. In the following example, `B` isn't evaluated if `A` evaluates to `null` and `C` isn't evaluated if `A` or `B` evaluates to `null`. This example was taken from the [Microsoft documentation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

```csharp
A?.B?.Do(C);
```

Why don't I just use an example from my code? I can't. I don't code like this. I get what this language feature is doing. What I don't get is why a developer would want to have a statement like that in their code.

This kind of programming needs to have `if..then` checks to determine what is being used in the subsequent calls. Allowing the null conditional operators to handle this drives me crazy.

How am I supposed to debug this nonsense? Long lines of calls make it incredibly hard to debug. When I have to maintain your code, and I see this, I am going to rewrite it. That is, unless it works, then I would have no business trying to understand what you are doing anyway.

```csharp
// assume A, B, and C all have values (or not)

var A = GetA();
if (A != null)
{
    var B = A.B;
    if (B != null)
    {
        B.Do(C);
    }
}

```

That's how you do it so I can see what is happening in the debugger.
