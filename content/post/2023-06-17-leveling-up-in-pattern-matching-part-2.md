---
title: Leveling Up in Pattern Matching (Part 2)
date: 2023-06-17
postindex: 69
url: /post/69/leveling-up-in-pattern-matching-part-2
---

Relational pattern matching is used to test a value against a range of constants. This is clearly the modern replacement for an `if..then..else` block that I am used to.

It is a switch expression statement. It departs from the traditional `switch..case` statement by allowing multiple checks per case. Here I thought Microsoft was granting immense power when they enabled the `switch` statement with the `string` type.

```csharp
string WaterState(int tempInFahrenheit) =>
    tempInFahrenheit switch
    {
        (> 32) and (< 212) => "liquid",
        < 32 => "solid",
        > 212 => "gas",
        32 => "solid/liquid transition",
        212 => "liquid / gas transition",
    };
```

This example, from the Microsoft documentation, is a great example of this language feature. I was expecting nothing less. What I am struggling with is to find and actual real life example of using this feature.

I am sure that I have written something of this nature in the past. It appears to well suited to handling date spans. This code has all sorts of conditional nonsense. If you have ever dealt with the health insurance industry you know that it is all about date spans.

The relational pattern has a purpose. I can see that purpose. I am looking forward to the time when I can apply this pattern in real life. I just hope that I don't forget about it by then.
