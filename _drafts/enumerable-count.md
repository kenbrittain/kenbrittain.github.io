---
permalink: /posts/##-enumerable.count.html
title: Calling Enumerable.Count > 0
layout: post

---

I have come across this code. Okay, I wrote the code, then I found it.

```csharp
var kids = parent.GetChildren();
if (kids.Count() > 0)
{
}
else
{
}
```

[SonarQube][sq] does like this and neither does [ReSharper][rider]. Both  ask you to change it to use `IEnumerable.Any()` to find our if there is something there.

Resharper tells you that duplicate enumerations may happen.

[sq]:https://www.sonarqube.org/	"SonarQube Home Page"
[rider]:https://www.jetbrains.com/rider/ "JetBrains Rider"
[any]:https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.any?view=net-6.0#system-linq-enumerable-any-1(system-collections-generic-ienumerable((-0)))	"IEnumerable.Any Documentation"

