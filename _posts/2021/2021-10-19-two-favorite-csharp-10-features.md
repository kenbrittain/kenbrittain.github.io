---
permalink: /posts/5-two-favorite-csharp-10-features.html
title: Two Favorite C# 10 Features
layout: post
---

<p>
    C# 10 is being released in November 2021 along with .NET 6. There are several
    new language features being released. You can read about them
    <a href="https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-10">here</a>.
    The list has some interesting features, most of which are solutions to
    problems that I don't have.
</p>

<p>
    The two (2) new features that excite me appeal directly to a desire to write
    less code, or at the very least, a chance to be more efficient with the code
    that I do wind up writing.
</p>

<ul>
    <li>Global using directives</li>
    <li>File-scope namespace declaration</li>
</ul>

<h2>Global using directives</h2>

<p>
    This language feature is a modifier that has been added to the existing
    <code>using</code> directive. You can read the official documentation for the
    <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-directive#global-modifier">global modifier</a>.
</p>

<p>
    By applying this modifier to a using directive the directive will be
    available in all files in the project. I like to think of this as an
    <code>#include</code> from the good ol' days. Just remember that the
    <code>global</code> directive must first and before your <code>namespace</code>
    declaration.
</p>

<p>
    This block of <code>using</code> directives gets added to pretty much every
    source file I am working on lately. Using this new feature I create a
    <code>Globals.cs</code> file and add it the project. I prefer this method to
    the <code>csproj</code> addition of the <code>&lt;Using /&gt;</code> element.
    To me, it makes more sense to have a visible file, clearly named, rather than
    relying upon developers to check the project file.
</p>

```csharp
global using System;                     // for all files (if needed or not)
global using System.Collections.Generic; // obvious reasons
global using System.Linq;                // makes playing with collections better
global using System.Threading.Tasks;     // mostly for web projects
```

<p>
    This method of including namespaces does not affect the .NET from removing
    assemblies when it is publishing a trimmed self-contained deployment.
</p>

<h2>File-scope namespace declaration</h2>

<p>
    This new feature is pure syntax gold. Why? I do not think I have ever created
    multiple namespaces within a single source file. I know it can be done, but
    it is not my normal convention: single namespace, single class per file. I
    have found that be a reasonable approach to organizing code. Of course, there
    are exceptions but never for multiple namespaces.
</p>

```csharp
using System;                     // for all files (if needed or not)
using System.Collections.Generic; // obvious reasons
using System.Linq;                // makes playing with collections better
using System.Threading.Tasks;     // mostly for web projects

namespace TheNamespace
{
  // Everything is now tabbed over - 4 spaces!
  public class SampleClass { }
}
```

<p>
    That is why the file-scoped namespace feature makes so much sense to me. It
    saves me code and give me back an entire level of indenting. When combined
    with global using directives the above code becomes:
</p>

```csharp
namespace TheNamespace;
// Everything is now tabbed over - 4 spaces!
public class SampleClass { }
```

<p>
    This works for me!
</p>

<h2>Conclusion = Less Typing</h2>

<p>
    The reality is that these two (2) features are really just syntactic sugar.
    We currently get the same result by typing some extra characters. The
    compiler will still produce the same code. So why be lazy?
</p>

<p>
    Frankly, I feel that file-scoped namespace is just being lazy ... for sure.
    I will take it, however, because it is useful. The global using directives
    saves time. If kept in a <code>Globals.cs</code> or similar file it provides
    a clear understanding of what to expect for the project. There is no digging
    in the <code>csproj</code> file. It can handle additions clearly and simply.
    Once a team decides that is how they are going to manage their code, it
    documents itself.
</p>

<p>
    <em>Updated: edited using block code to include <code>global</code> to be more clear.</em>
</p>

