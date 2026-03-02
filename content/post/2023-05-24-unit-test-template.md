---
title: Unit Test Templates to Make Your Life Easier
date: 2023-05-24
postindex: 45
url: /post/45/unit-test-template
---

When writing unit tests I like to make an outline of the intended tests. Actively thinking and writing the structure of a test suite allows me to focus on what I want to test. Writing the actual tests just becomes work.

There is a lot of debate on how to write your test method names. My patterns allow me to locate the test in question quickly.

* All test classes should be in the same namespace as the class under test. I admit this is a hold over from my Java days and not sure it is needed anymore.
* Test class name is the name of the class under test with the word \*Tests\* appended.

I use the following snippet of code in all of my test projects. It is the first thing that add to my unit test files. I could make a template for this but having it available on the web is easier for me.

```csharp
namespace NSName;

public class ClassNameTests
{
    /*
    [Fact]
    public void Method_Scenario_Expectation()
    {
        // Arrange
        // Act
        // Assert
    }
    */
}
```

The only aspect of the template that I do not appreciate is that my method names are not renamed when refactoring. I will be looking into using nested classes to limit the amount of refactoring. The template would then resemble this more.

```csharp
namespace NSName;

public class ClassNameTests
{
    public class MethodNameTests
    {
        [Fact]
        public void Scenario_Expectation()
        {
            // Arrange
            // Act
            // Assert
        }
        */
    }
}
```
