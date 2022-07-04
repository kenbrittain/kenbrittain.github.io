---
permalink: /posts/39-should-you-use-parameter-prefixing.html
title: Should You Use Parameter Prefixing?
layout: post
---

If you have only coded in an IDE then please remember that there was a time when developers actually had to write all of the code, references were in a paperback book, and compile times were a thing.

I was writing some code recently and I created an interface to abstract the loading an object called a `Package`. The interface was pretty straight forward. 

*FYI - all comments are removed to protect the innocent.*

```c#
public interface IPackageLoader
{
    Stream LoadPackage(string name, string location);
}
```

If you don't know I have switched to Emacs as my daily driver for coding. So I had to implement this interface by writing the code.

```c#
public class FilePackageLoader : IPackageLoader
{
    public Stream LoadPackage(string packageName, string packageLocation)
    {
		throw new NotSupportedException();
    }
}
```

I revisited the file and two (2) things stood out:

- The parameter names have the `package` prefix on them.


- The parameter names are different are in the implementation than from the interface.

## Why would you use parameter prefixing?

First, I noticed that the `LoadPackage` implementation used the `package` prefix on the `name` and `location` parameters. The compiler does not care but apparently I do. 

Names for derived or implemented methods are usually handled by the IDE. Visual Studio or Rider generate the source code for the method and the parameter names all with a single command. They both carry forward the parameter names from the method being implemented.

My point is that by writing the code by hand, and not relying upon the tool to handle the *drudgery* of writing the code I can see old habits are coming through. Look at the `FilePackageLoader` class again. There are a whole lot of `package` names in there. 

Was all of this really needed? No, but I apparently thought that I needed it. Why?

Once I was removed from the practice of generating interface methods and writing the source code by hand I think I regressed. I think this sort of naming falls back to when you did not have the *Find References* type of commands available. You had to actually search of the text by hand. There was `grep`, `Find in Files`, and, of course, `ctags`! The longer, more specific the name the easier it was to find. Nothing will break your spirit more than finding hundreds of references to the variable `name` when you actually looking for the `packageName`. 

## Should you use parameter prefixing?

This recent revelation, from my habits of coding past, is a by-product of switching to Emacs. Not having code generated in the manner I have grown accustomed to brought this out.

I don't think the longer prefixed names are helpful to the code. There are seven (7) lines of code in the default implementation of that interface. There are five (5) identifiers using the word package. I get it. It loads a package.

The exercise of actually writing the code again has forced me to make a decision. That is kind of why I started this whole exercise to begin with :-)