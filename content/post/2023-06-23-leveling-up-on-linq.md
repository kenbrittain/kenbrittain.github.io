---
title: Leveling Up on Linq
date: 2023-06-23
postindex: 75
url: /post/75/leveling-up-on-linq
---

I've never liked Linq. There is something about writing code like a SQL statement that rub me the wrong way. This makes sense because I not a fan of SQL either. So you can see how I never took a shine to Linq and started sprinkling it throughout my code.

Linq is not bad. I think it has it's purposes. What I have seen of it reminds of the really smart kids trying to fool everyone else into thinking they are smarter than they really are.

Example from [Microsoft documentation](https://learn.microsoft.com/en-us/dotnet/csharp/linq/).

```csharp
// Specify the data source.
int[] scores = { 97, 92, 81, 60 };

// Define the query expression.
IEnumerable<int> scoreQuery =
    from score in scores
    where score > 80
    select score;

// Execute the query.
foreach (int i in scoreQuery)
{
    Console.Write(i + " ");
}

// Output: 97 92 81
```

This code does not strike me as maintainable. It not readily understandable. You can make it out but why? The actual implementations method `Select()` and `Where()` make more sense. They are still a reach for me though and I don't use them.

The purpose was to level up with using Linq. At this time still feel a bit \*uneasy\* when using Linq. There is something not right about it.

I am sure Linq is a great technology for you. It is just not my cup of tea. I tried to get into (again) and failed.
