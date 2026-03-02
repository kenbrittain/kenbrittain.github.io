---
title: Leveling Up in Pattern Matching (Part 1)
date: 2023-06-16
postindex: 68
url: /post/68/leveling-up-in-pattern-matching-part-1
---

I know developers that use the pattern matching feature every chance they get. They love the flexibility it provides. I never saw the utility because you can accomplish its effect with traditional programming constructs. That means `if..then..else` statements. The documentation explains it is so much more:

* Null checks
* Type tests
* Compare discrete values
* Relational patterns
* Multiple inputs
* List patterns

I am supposed to leveling up so I began using switch expressions which Microsoft calls *comparing discrete values*. I am making the effort but it has been slow. At least I see the utility of the switch expression.

## Null checks

I have never used the `is` operator to check for `null`. The example provided is something I would probably never actually do in real life. I just don't see the utility of the words `is not` over the symbol `!=` in that statement. That may make me old fashioned and I would agree. Also, I said I would probably never. One thing that is certain is to never say never.

```csharp
string? message = "This is not the null string";

if (message is not null)
{
    Console.WriteLine(message);
}
```

## Type tests

This is what I would call the traditional usage of the `is` operator. I have used this generously in the past. If the need arises I can see me continuing with that code.

The only addition is the support for the declaration pattern. This is a newer and well deserved language feature. It saves me from creating another variable in the scope, having to initialize it, and then use it.

```csharp
object greeting = "Hello, World!";
if (greeting is string message)
{
    Console.WriteLine(message.ToLower());  // output: hello, world!
}
```

## Compare discrete values

This is the switch expression that I have been learning recently. When I encounter the need for a `switch` statement I am starting to think about how to use a switch expression. I think it will begin to starting naturally soon.

I think the addition of the pattern is good because it reduces the amount of code you need to write. Whenever I was using the `switch` statement before it was to either do something or return something based upon a value.

This language feature handles that and with less code.

```csharp
public State PerformOperation(Operation command) =>
   command switch
   {
       Operation.SystemTest => RunDiagnostics(),
       Operation.Start => StartSystem(),
       Operation.Stop => StopSystem(),
       Operation.Reset => ResetToReady(),
       _ => throw new ArgumentException("Invalid enum value for command", nameof(command)),
   };
```

* More in Part 2 about relational, multiple, and list patterns.
* You can refer the Microsoft docs on [pattern matching](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching).
