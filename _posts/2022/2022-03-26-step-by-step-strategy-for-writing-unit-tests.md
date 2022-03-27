---
permalink: /posts/28-step-by-step-strategy-for-writing-unit-tests.html
title: "Step-by-Step Strategy for Writing Unit Tests (Part #1)"
layout: post
---

Stop overthinking about how to write your unit tests.

Whether your project code is brand spanking new or was written years about by former employees and teams you still need to write unit tests. Knowing where to start is only half of the battle. Having a plan for getting those unit tests written is better than wishing they were done.

Follow these steps for planning your unit tests and the code will write itself.

## Steps for Planning the Tests

Wikipedia defines unit testing as:

> Unit tests are typically [automated tests](https://en.wikipedia.org/wiki/Automated_test) written and run by [software developers](https://en.wikipedia.org/wiki/Software_developer) to ensure that a section of an application (known as the "unit") meets its [design](https://en.wikipedia.org/wiki/Software_design) and behaves as intended.

That's it. The code is not meant to be clever. They need to run fast ... and pass. The code is meant ensure your design is met. Unit tests are code written to test the smallest unit of a system. For C# this would be the methods of a class.

I use the following four (4) steps to create an outline for my unit tests before I begin writing the code. My outline is actual source code so don't worry about having another artifact to babysit. Once these steps are complete I know what tests needs to be written. I can then proceed to use any technique in my arsenal of programming to help me get the job completed, accurately, and quickly.

Here are my steps (and some of the reasoning behind it):

1. [Create the Unit Test Project](#1-create-the-unit-test-project)
2. [Add the Project Reference](#2-add-the-project-reference)
3. [Create a Unit Test File](#3-create-a-unit-test-file)
4. [Outline the Test Methods](#4-outline-the-test-methods)

### 1. Create the Unit Test Project

Creating the unit test project is simple. You can use your IDE, editor, or command line to generate the appropriate project or files. You can also use the [template project][template] from my [GitHub][gh] projects. 

I have recently changed to naming my unit test assemblies **UnitTests**. This is a change from my original C# development days of using **{Project}.UnitTests** assembly names. I think refers back to some original projects that Microsoft published, or at least recommended. Both ways are valid. Both keep the projects sorted properly in a directory. To me, knowing where to look, in the editor or the folder tree, is the important part.

```
runbook-compiler/
├── Runbook
└── UnitTests
```

I think the redundant project name in the directory just made it longer for no reason. So I switched. This was a hold over from Windows development where the command line was less relied upon and Visual Studio hid most of the tooling. Now that I am doing all of my development on Linux I prefer the shorter naming. Your mileage may vary.

 ```
 general-software/src
 ├── GeneralSoftware
 └── GeneralSoftware.UnitTests
 ```

### 2. Add the Project Reference

Now that the project created and properly named you need to add the reference to the project you will be testing. It is very rare that the project source code and the unit tests are in the same project. If that were to be the case then the unit tests would released with the main assembly. Common practice is to have the project assemblies and the unit test assembly separate. 

This means that the unit test project needs to have a reference to the original source project. This will make all of the public classes and methods in the that project accessible for testing.

There are two (2) methods available for you to use. 

My preferred way is to edit the  `.csproj` and include a `<PackageReference/>` element. The `{Project}` name is the actual name of the project that is being tested. If you are keeping your projects in a directory similar to that defined above then this will work just fine. 

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <!-- other elements from your project -->
    <ItemGroup>
        <ProjectReference Include="..\{Project}\{Project}.csproj" />
    </ItemGroup>
</Project>
```

You can also use the `dotnet` command line to add a project reference. From the unit test project directory use this command:

```bash
dotnet add ..\{Project}\{Project}.csproj reference UnitTests.csprog
```

Finally, perform a quick build to make sure everything is in working order.

### 3. Create a Unit Test File

Next, create a new file in the unit test project and name it to hold the unit tests for a class. I try to keep all of the unit tests for a single class in a single unit test file. This makes naming and finding everything nice and easy. 

To name the file there is a prefix and postfix. The file prefix is the class name of the class being tested, and the postfix is the word *Tests*. For example the `Person` class would have an associated unit test file called `PersonTests.cs`. It may seem redundant to name a source file full of tests with the name `{Class}Tests.cs`, and remember, I got rid of the redundant naming in the projects themselves. Trust me, this part makes sense.

This prefix/postfix pattern is used for two (2) reasons:

1.  If you are keeping your tests for a class in a single file, your can use the class name as the prefix to help you identify its contents. By creating, and maintaining, your unit tests in a source file named after the class you can easily located the tests you need. The tests for the `Person` class are located in the file that begin with the prefix `Person`. Also, the unit test files sort the same as the class files. 
2. The postfix is used to differentiate the unit test file from the actual source file. They are in different projects which presumes different directories. However, some editors will display the path to a source file and some don't. If the path is displayed in the tab (and they are for [Visual Studio Code][vcs] and [JetBrains Rider][rider] at least) the tabs get longer. Longer tabs mean less visible open tabs. I find it easier to have the postfix applied, making the file different names, but keeping the context.

Finally, copy the code from the *Unit Test Template* and paste its contents into the file. Change up the `namespace` and the class name are you are now ready to start creating your testing plan.

```csharp
namespace Persons;

public class PersonTests
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

### 4. Outline the Test Methods

Each unit method will be composed of a three (3) part name: `Method_Scenario_Expectation`.

* Method is the name of the method that is being tested.
* Scenario is why you are writing the unit test.
* Expectation is what you are expecting to happen.

This pattern is helpful for two (2) reasons:

1. It groups the names of the methods being testing alphabetically. This helps when you are looking for methods. Your editor or IDE can help a lot here but nothing beats knowing where to look. You will find that I like to able to find things. My patterns and convention have developed over time to help me in that regard.
2. It allows you to read the name, know what you are testing, and what to expect, all in a single line . This helps when looking at failures. In the past I have experimented with naming conventions like `LongNamesThatExplainTheReasonForTheTest` and `Long_names_that_explain_the_reason_for_test_test` as well as `WhenSomething_ExpectResults`. I think the three (3) part name combines all of the conventions into a readable, understandable method name, with the appropriate context. 

The outline will consist of a list of empty unit test methods. The names of the methods describe the unit tests and expectations. This class of empty methods is your plan. 

This class is the sample class that I will be using to explain the outlining unit test approach. It is simple and somewhat contrived, but has the necessary components for filling out our outline.

This is our example class.

```csharp
/// <summary>
/// Person is an example class used to demonstrate unit testing.
/// </summary>
public class Person
{
    privare readonly string _name;
    private _greetingCount;
    
    /// <summary>
    /// Initializes a new <see cref="Person"/> with the specified name.
    /// </summary>
    /// <param name="name">Name of the person.</param>
    /// <exception cref="ArgumentException">thrown when name is null or empty.</exception>
    public Person(string name)
    {
        if (name == null)
        {
            throw new ArgumentNullException(nameof(name));
        }

        if (name == string.Empty)
        {
            throw new ArgumentException("{nameof(name}} must have a value!", nameof(name));
        }

        _name = name;
        _greetingCount = 0;
    }
    
    /// <summary>
    /// Get how many times the person was greeted.
    /// </summary>
    public int Greetings => _greetingCount;    
    
    /// <summary>
    /// The person's name.
    /// </summary>
    public string Name => _name;
    
    /// <summary>
    /// Greet the person.
    /// </summary>
    /// <param name="greeting">Message for the greeting.</param>
    public void Greet(string greeting)
    {
        if (string.IsNullOrEmpty(greeting))
        {
            throw new ArgumentException(nameof(greeting));
        }
        
        var text = $"{greeting} {_name}";
        Console.WriteLine(text);
        
        _greetingCount += 1;
    }
    
    /// <summary>
    /// I needed a method that throws an exception.
    /// </summary>
    public void EnsureGreeted()
    {
        if (_greetingCount == 0)
        {
            throw new ArgumentOutOfException("There have been no greetings!");
        }
    }
}
```

#### 4.1 Check All Parameters

For each method create a unit test for each parameter check. In the example `PersonTests` class that means the constructor and the `Greet` method are the only methods getting their parameters checked. I do this for all public methods with parameters. The parameters to a public method are the contract for that method. If you are doing any validation you should include a unit test to make sure the validation is correct.

Our unit test class will start out with these methods. There is no code in them at this point. We are just making the list of methods that we intend to write.

```csharp
[Fact]
public void Person_NullOrEmptyName_ThrowsException()
{
    // Arrange
    // Act
    // Assert
}

[Fact]
public void Person_HasName_SetGreetingToZero()
{
    // Arrange
    // Act
    // Assert
}

[Fact]
public void Greet_NullOrEmptyGreeting_ThrowsException()
{
    // Arrange
    // Act
    // Assert
}
```

#### 4.2 Check All Thrown Exceptions

If a method throws an exception then you should write a unit test for that as well. Our unit test plan is getting longer. You can see that I included a test for the exception that would be thrown. Generally, exceptions are thrown for major errors within an application. Our unit test plan keeps growing.

```csharp
[Fact]
public void EnsureGreeted_NeverGreeted_ThrowsException()
{
    // Arrange
    // Act
    // Assert
}
```

I include unit tests for all exceptions because they are documented. If the docs are going to be showing showing a unit test to ensure that happens it worth the effort. 

#### 4.3 Include the Happy Path

This one is a must as well. The **Happy Path** is the code path taken when all things are correct and all assumptions are met. This path may not be the positive route for the code but it should be the most common path.

```csharp
[Fact]
public void Greet_ValidGreeting_IncrementsCount()
{
    // Arrange
    // Act
    // Assert
}
```

You would include Happy Path unit tests for all of the methods in the class. This should include all, non-trivial public, methods. You do not need to test properties unless the getter or setter is doing something special. Treat them the same as methods.

#### 4.4 Include Alternative Paths as Needed

Finally, include any additional code paths that need testing. Which paths need testing? Anything that is non-trivial! That means that if you are using branching logic then you should include unit tests to exercise those paths. 

```csharp
[Fact]
public void EnsureGreeted_GreetedOnce_NeverThrows()
{
    // Arrange
    // Act
    // Assert
}

[Fact]
public void EnsureGreeted_GreetedMany_NeverThrows()
{
    // Arrange
    // Act
    // Assert
}
```

That is it. You now have a single unit test file, in this case called `PersonTests` that contains seven (7) unit test methods. Using this approach you can write unit tests for existing projects easily. More importantly you will soon be able to determine how many unit tests will be required for your new and existing code. This allows for better estimating and ticket creation during your planning sessions.

In Part #2 we will cover actually writing the tests. For now, here are the templates.

# Unit Test Templates

I have borrowed my standard `Globals.cs` files and extended it for the unit tests. This allows for reduced typing in the `using` section of the source code files. It may not seem like a lot but is it worth it. 

## Unit Test Globals

```csharp
global using System;                     // for all files (if needed or not)
global using System.Collections.Generic; // obvious reasons
global using System.Linq;                // makes playing with collections better
global using System.Threading.Tasks;     // mostly for web projects
global using Xunit;                      // xUnit for tests             
global using Moq;                        // Object mocks
```

This is the template that I use for writing unit tests. The commented out section is my method template. I keep this section at the end of the file and copy the contents of the comment as needed. The Arrange/Act/Assert comments may not survive and that is okay. They are there as a guide for writing the test.

## Unit Test Template

```csharp
namespace NS;

public class {Class}Tests
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

[tests]:https://github.com/kenbrittain/runbook-compiler/tree/main/UnitTests	"Runbook Compiler Unit Tests Project"
[template]:https://github.com/kenbrittain/unit-tests

[gh]:https://github.com
[vsc]:https://code.visualstudio.com/
[rider]:https://www.jetbrains.com/rider/

