---
title: Leveling Up in Covariant Return Types
date: 2023-06-19
postindex: 71
url: /post/71/leveling-up-in-covariant-return-types
---

Let's begin with some definitions because this one is confusing (liberated from the original [Microsoft docs](https://learn.microsoft.com/en-us/dotnet/standard/generics/covariance-and-contravariance)).

**Covariance** enables you to use a more derived type than originally specified. You can assign an instance of `IEnumerable<Derived>` to a variable of type `IEnumerable<Base>`.

**Contravariance** enables you to use a more generic (less derived) type than originally specified.
You can assign an instance of `Action<Base>` to a variable of type `Action<Derived>`.

**Invariance** means that you can use only the type originally specified. An
invariant generic type parameter is neither covariant nor contravariant.
You cannot assign an instance of `List<Base>` to a variable of type `List<Derived>` or vice versa.

The covariance examples are pretty much what you are used to in the real world. You can make assignment the look like ordinary polymorphism (Microsoft's words not mine).

```csharp
// Assignment compatibility. 
string str = "test"; 
// An object of a more derived type is assigned to an object of a less derived type. 
object obj = str; 

// Covariance. 
IEnumerable<string> strings = new List<string>(); 
// An object that is instantiated with a more derived type argument 
// is assigned to an object instantiated with a less derived type argument. 
// Assignment compatibility is preserved. 
IEnumerable<object> objects = strings;   

```

Covariance makes sense when doing assignments. You can always cast down. Covariant return type now makes sense. This feature allows you to return a more derived type.

```csharp
class Compilation
{
    public virtual Compilation WithOptions(Options options)...
}

class CSharpCompilation : Compilation
{
    public override CSharpCompilation WithOptions(Options options)...
}  

```

The only problem is I don't know when I would ever use this. Maybe I am just too used to naming the method something different.
