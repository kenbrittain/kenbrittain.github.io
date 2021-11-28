---
permalink: /posts/10-unit-testing-system-io.html
title: Unit Testing System.IO
layout: post
---

<p>
    My advice is simple: use the <a href="https://github.com/TestableIO/System.IO.Abstractions">System.IO.Abstractions</a>
    package from <a href="https://github.com/TestableIO">TestableIO</a> for your
    C# projects. I will never use the raw <code>System.IO</code> package again.
    Why? Unit testing of course!
</p>

<p>
    The <code>System.IO</code> namespace has some incredibly useful classes and
    methods. If your code uses the static methods from the <code>File</code> or
    <code>Directory</code> classes, you will have a time of it, unit testing
    with those in there. I have never found a suitable, meaning easy, way to
    write unit test classes without accessing the file system when using
    those methods.
</p>

<p>
    This code represent something fairly common, from my past, when processing
    data from files. Don't get hung up on the code itself but that look at the
    pattern for reading from a file.
</p>

```csharp
public class FileSample
{
    public bool ProcessText(string fileName)
    {
        var exists = File.Exists(fileName);
        if (exists)
        {
            var text = File.ReadAllText(fileName);
            // do something with `text`
            return true;
        }

        Console.WriteLine($"{fileName} not found!");
        return false;
    }
}
```

<p>
    This style of code made it rather difficult to write unit tests when it
    contained references to the static methods in the <code>File</code> class.
    The traditional workaround is to create an interface that can be mocked when
    used in the unit testing code.
</p>

```csharp
public interface IFileWrapper
{
    bool Exists(string fileName);
    string ReadAllText(string fileName);
    // same for all other methods used in your code
}
```

<p>
    The default implementation would be coded that forwarded the calls to actual
    static methods. There is not a lot of code, but it is code that needs to be
    written and maintained. As with all code, there is a cost.
</p>

```csharp
public class DefaultFileWrapper : IFileWrapper
{
    public bool Exists(string fileName) => File.Exists(fileName);
    public string ReadAllText(string fileName) => File.ReadAllText(fileName);
}
```

<p>
    It is the same for every project that uses the <code>File</code> and
    <code>Directory</code> classes. I am sure there are other classes that
    should get the same treatment, but these two (2) are the biggest culprits
    in my coding life. While I enjoy coding this particlar pattern does get
    boring: write code, extract wrapper, write default implementation, and
    repeat (for all things required). After you do this on a few projects you
    begin to contemplate the cost of creating a library to handle this
    nonsense for you.
</p>

```csharp
public class WrapperNonsense
{
    private IFileWrapper _wrapper;

    public WrapperNonsense() : this(new DefaultFileWrapper())
    {
    }

    public WrapperNonsense(IFileWrapper wrapper)
    {
        _wrapper = wrapper ?? throw new ArgumentNullException(nameof(wrapper));
    }

    public bool ProcessText(string fileName)
    {
        var exists = _wrapper.Exists(fileName);
        if (exists)
        {
            var text = _wrapper.ReadAllText(fileName);
            // do something with `text`
            return true;
        }

        Console.WriteLine($"{fileName} not found!");
        return false;
    }
}
```

<p>
    The good news is that the work has already been done! The team at
    <a href="https://github.com/TestableIO">TestableIO</a> has already created
    an abstractions package for making the <code>System.IO</code> namespace easy
    to unit test with: <a href="https://github.com/TestableIO/System.IO.Abstractions">System.IO.Abstractions</a>.
    The only trick left is injecting their <code>IFileSystem</code> interface
    into your class and calling the proper methods. You were doing that already
    for your implementation so it is not a big deal (or you weren't writing unit
    tests and that is a bigger deal). The <a href="https://github.com/TestableIO">TestableIO</a>
    code provides a solution that performs exactly the same operations as your
    code.
</p>

<p>
    This code should look familiar. Access to the abstraction is managed through
    the <code>File</code> and <code>Directory</code> properties. There are others
    in there, including some help with mock objects.
</p>

```csharp
public class AbstractionSample
{
    private IFileSystem _fs;

    public AbstractionSample() : this(new FileSystem())
    {
    }

    public AbstractionSample(IFileSystem fs)
    {
        _fs = fs ?? throw new ArgumentNullException(nameof(fs));
    }

    public bool ProcessText(string fileName)
    {
        var exists = _fs.File.Exists(fileName);
        if (exists)
        {
            var text = _fs.File.ReadAllText(fileName);
            // do something with `text`
            return true;
        }

        Console.WriteLine($"{fileName} not found!");
        return false;
    }
}
```

<p>
    This library allows you to write less code, get the same effect, and have
    the code that you do write be more testable. It was what I was doing anyway!
    It is a win, win!
</p>

<p>
    Using this library for greenfield development is a no-brainer. Existing code
    will be modified to utilize this library as changes are required.
</p>
