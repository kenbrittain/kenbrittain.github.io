---
permalink: /posts/30-calling-ienumerable-count-is-a-code-smell.html
title: Calling IEnumerable.Count() is a Code Smell
layout: post
---

Just because something compiles does not mean it is correct.

I recently came across some code that was flagged by [SonarQube][sq] as a [Code Smell][smell]. The code executes as expected, does not affect performance, and has been released to production for over two (2) years. So why would I fix it?

It turns out it is being used all over the place!

## A Problem Waiting to Happen?

In our web application we have a pattern where we display a special message when no items are found to display. After a search for some items to display, usually in the form of a table, the "There were no items found" text will be displayed if the table is empty. The purpose is to let the user know the application did what asked, is not broken, and did not find what they were looking for.

Our controllers have a habit of passing data to the view using the `IEnumerable` interface. This makes sense. The view don't need to know the specific collection type used when displaying the data.

```csharp
public class PageViewModel
{
    public IEnumerable<string> Items { get; }
}
```

 At some point in the past we started using the following code. Once it was in the codebase everyone pretty much just ran with it.

```csharp
@if (Model.Items.Count() > 0)
{
    // Add - There were no items found
}
else
{
    @foreach (var item in Model.Items)
    {
        // Add <tr> table representation of the item
    }
}
```

[SonarQube][sq] does not like this and neither does [ReSharper][rider]. Both  ask you to change it to use `IEnumerable.Any()` to find out if there is, your guessed it, any-thing there.

The issue, or rather the smell, is that the `IEnumerable` could be enumerated to actually count the number of items. This could proves disastrous for performance of an application. In our situation, query results are returned from a REST API call and have been serialized over JSON. When we are calling the `IEnumerable.Count()` extension method we are iterating over an in memory collection at this point. This is not ideal but it works.

The change is make the check use the `Any()` method rather than calling the `Count()` method. Both methods try and determine if the source enumerable is a collection in an attempt to avoid iterating over the entire enumerator. For the `Count()` method our code would have hit one of the type checks and came back pretty quickly.

```csharp
public static int Count<TSource>(this IEnumerable<TSource> source)
{
    if (source == null)
    {
        ThrowHelper.ThrowArgumentNullException(ExceptionArgument.source);
    }

    if (source is ICollection<TSource> collectionoft)
    {
        return collectionoft.Count;
    }

    if (source is IIListProvider<TSource> listProv)
    {
        return listProv.GetCount(onlyIfCheap: false);
    }

    if (source is ICollection collection)
    {
        return collection.Count;
    }

    int count = 0;
    using (IEnumerator<TSource> e = source.GetEnumerator())
    {
        checked
        {
            while (e.MoveNext())
            {
                count++;
            }
        }
    }

    return count;
}
```

But that does not mean every check will end up that way. That is the code smell. If the front end began querying the database, which thankfully it currently does not, it could begin returning other collection types or yielded query results. The results of that could be very bad. 

So why would we fix something that does not currently affect us? In a corporate environment no team lives forever and ours is no exception. If we did not, at the very least, create some level of tickets there would be no record other than the SonarQube report. How long before the next team decides to do things differently and the whole application starts slowing down as a result.

I am not saying this is going to be a full-stop, all hands on deck, fix this now type of problem. Once I have identified the scope we can being to peel back the implementations until they are fixed. The goal is to make the application a better place for our customers and help our teammates make that happen.

Finally, now that I know, I cannot unsee it and it will be fixed eventually. 

[sq]:https://www.sonarqube.org/	"SonarQube Home Page"
[rider]:https://www.jetbrains.com/rider/ "JetBrains Rider"
[any]:https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.any?view=net-6.0#system-linq-enumerable-any-1(system-collections-generic-ienumerable((-0)))	"IEnumerable.Any Documentation"
[smell]:https://en.wikipedia.org/wiki/Code_smell



