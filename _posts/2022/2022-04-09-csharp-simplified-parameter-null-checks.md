---
permalink: /posts/31-csharp-simplified-parameter-null-checks.html
title: C# 11 Simplified Parameter Null Checks
layout: post
---

I learned to program first C and then C++. I wrote Windows 3.1 applications. Windows applications required a lot of code to get them running. 

Later I followed the wave into Java and J2EE. There were a lot promises on that wave but you were still required to write a lot of code to get thing working.

Then C# came along. It was easy to pick given the similarity to the other languages. I am sure that was by design. Speaking of design my original observation when learning C# was: 

> Java is designed **by** programmers but C# is designed **for** developers.

I felt that Microsoft went out of their way to make things easier for the developer. Reading or writing text to a file, in a single line, was the original standout. In Java there were buffers, readers, etc. that needed to be setup. It made C# fell like a breath of fresh air.

Do not get me wrong. There is still boiler plate code written to get things running. Especially in a web applications. I am not saying the other platforms have not progressed. They have. Then along came C#11 null validation.

## C# 11 Simplified Parameter Null Checks

The C# 11 language has introduced the `!!` null validation operator. When appended to a parameter definition it performs the null check on the parameter. Do you how many times I have written the following code?

```csharp
void SendEmail(string to, string @from, string subject, string body)
{
    if (to == null)
    {
       throw new ArgumentNullException(nameof(to));
    }
    if (@from == null)
    {
       throw new ArgumentNullException(nameof(@from));
    }
    if (subject == null)
    {
       throw new ArgumentNullException(nameof(subject));
    }
    if (body == null)
    {
       throw new ArgumentNullException(nameof(body));
    }
    // Send some email
}
```

I am sure you have as well. Using the null validation operator the compiler will write that for us now. Your code now becomes clearer. It will be less cluttered with repeating null validation code. You will still have to perform other validation as required.

```csharp
void SendEmail(string to!!, string @from!!, string subject!!, string body!!)
{
    // Send some email
}
```

The next C# language revision has just removed a lot of that parameter checking boiler plate code. I am sure there will be special situations where you will still need to write this code.  I suspect those will be very rare. 

I recommend you check out the language reference for the [null validation][null] operator.

C# was designed for developers.

[null]:https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-parameter-check

