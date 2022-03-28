---
permalink: /posts/##-enumerable.count.html
title: Calling Enumerable.Count > 0
layout: post

---

I have come across this code. Okay, I wrote the code, then I found it.

```csharp
var data = someObject.GetDataAsEnumerableYouGetThePoint();
if (data.Count() > 0)
{
    // That is a lot of datas
}
else
{
    // Not really!
}
```

SonarQube does like this and neither does Resharper. Both  ask you to change it to use `IEnumerable.Any()` to find our if there is something there.

Resharper tells you that duplicate enumerations may happen.