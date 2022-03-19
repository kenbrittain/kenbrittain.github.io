---
permalink: /posts/27-defining-a-full-test-suite-for-command-line-applications.html
title:
layout: post
---

The runbook-compiler project is a command line application. It is used for compiling [YAML][yaml] structured runbook definitions into other formats for publishing and execution. Like any other modern software project, automated testing is a key component, always under development, and *hopefully* making the project better.

I have found that when developers talk about their testing efforts the definitions they use, and the deliverables they create can all mean different things. It really depends upon the team and the course they took to get where they are. I have heard it said that _that this is not what we intended but this is where we are_.

This post defines the unit test framework. The goal is define where we want to go so we don't arrive where we don't want to be. This project will be follow this testing stratgey:

* **Unit Tests** - exercise the source code functionality and run quickly. These tests will be run during development and after builds.
* **Integration Tests** - exercise the integration with and usage of external dependencies. These tests will be run after builds are performed.
* **Functional Tests** - exercise the use cases at the user level for expected behaviors and operational consistency. These tests will be run daily to manage changes and ensure a consistent interface for the user.

As we go down this list of testing the answers will get more vague. Why? Well, I currently do unit testing. Choices were made and code was written. The integration tests are coming into play now as I am approaching a release. I want to ensure that there is some level of integration tests available. Finally, the functional tests are being defined. Functional testing a web application is easy and packages are available to make that happen. Functional testing a command line application will be different. 

## Unit Tests

Writing tests may involve more than a framework but you still need to choose one. While it is possible to write your own framework, and I have been on teams that has done this, the amount of work is probably beyond what you would want to accept. Besides, once you accept that burden, you are alway playing catch up. 

This project is build on the .NET 6 SDK. There are three (3) major testing frameworks for the .NET ecosystem that I know of. I have used two (2) of them professionally. I recommend one (1).

* [MSTest][mstest]  - I have used this framework extensively on projects but have been migrating away from it recently.
* [NUnit][nunit] - I have only used this framework for evaluation purposes. This is a fully functional framework for writing unit tests and has great documentation. I just did not choose it over [xUnit][xunit].
* [xUnit][xunit] (recommended) - I currently use this framework unless working on legacy code with another framework in place.

I have only used the [MSTest][mstest] and [xUnit][xunit] frameworks. Each framework comes with a set of functionality that allows for the running of a set of tests. These tests are defined, usually in a test project, but always as classes following the framework conventions. The following attributes are used to identify tests. I am currently using and recommending the [xUnit][xunit] framework over the [MSTest][mstest] framwork. Both frameworks run within Microsoft [Visual Studio][vs], JetBrain's [Rider][rider], and under the `dotnet` command line tooling. 

| Feature           | MSTest           | xUnit                 |
| ----------------- | ---------------- | --------------------- |
| Test class        | [TestClass]      | No attribute required |
| Test method       | [TestMethod]     | [Fact]                |
| Test setup        | [TestInitialize] | Uses the constructor  |
| Test teardown     | [TestCleanup]    | implement IDisposable |
| Ignore tests      | [Ignore]         | [Fact(Skip="Reason")] |
| Test properties   | [TestProperty]   | [Trait]               |
| Data driven tests | [Datasource]     | [Theory]              |

I am using [xUnit][xunit] because it feels like there is less code related to get something running. I find myself writing unit test classes using just the `[Fact]` attribute most of the time these days. You cannot get any leaner than that.

```csharp
using Xunit;

public class ManifestTests
{
    [Fact]
    public void AddSource_AddNonNullObject_IncreasesSources()
    {
        var manifest = new Manifest();
        var source = new ManifestSource();

        manifest.AddSource(source);
        
        Assert.NotNull(manifest.Sources);
        Assert.NotEmpty(manifest.Sources);
    }
    
    // More like this for each method
}
```

## Integration Tests

These tests are testing the system as it integrates with other systems and external dependencies. The [xUnit][xunit] framework will be used to write these tests as it is a known technology, can be easily automated, and provides a platform for managing the results of operations.

The goal of integration tests are to exercise the functionality of the system as it relates to these external dependencies. These tests will be run after builds in the CI/CD pipeline. 

The external system will be simulated, mocked, and available as test doubles. The goal is exercise the software and not test the external systems. For example, a feature that requires access to a git repository would use a local repository. If the feature required the repository to be cloned locally, then a mock git server would be used (there are options for this). We are not testing the implementation of cloning a git repository. We are testing the software's integration with a cloned external git repository.

By utilizing a mock server we can create test cases that time out, have network issues, and generally perform poorly. All without actually setting up or interacting with said systems. These tests will be contained in a container that can be run to perform the tests.

## Functional Tests

What once began as an exercise in utilizing the [Test Anything Protocol][tap] to validate our software became a more full fledged testing framework. Over time, our home grown implementation was replaced with a package that allowed for testing similar to TAP.

The goal of functional testing is to run the actual commands the user would run. All externals services would need to be available and operational. Similar to using TAP this is a very black box style of testing. The inputs are command line parameters. The outputs are the console messages.

I have not identified a library to handle the running of the project. The test framework will still be [xUnit][xunit]. This is because each test case, or `[Fact]` in xUnit parlance is easily run and managed. The only special code would be the executing of the runbook-compiler executable and capturing the output. This is a know problem and can easily solved. I will be looking in to the Test Anything Protocol to see what can be leveraged there.

## Summary

I am looking forward to integrating these testing strategies into this project. Mike Cohn described the test pyramid as something similar to this. As you go up the pyramid, so does the integration, and time to run. In the end, exercising a fully working system is the goal. The approach would be automation using an existing testing framework.

![Testing Pyramid](../../assets/img/27-testing-pyramid.png)



In the end it is all just a simple matter of programming.



[ghrc]:https://github.com/kenbrittain/runbook-compiler
[mstest]:https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices
[xunit]:https://xunit.net/
[nunit]: https://nunit.org/
[yaml]:https://yaml.org	"YAML Specification"
[so]:https://stackoverflow.com/search?q=unit+test+naming+convention	"Stack Overflow"
[rider]: https://www.jetbrains.com/rider/	"JetBrain's Rider"
[vs]:https://visualstudio.microsoft.com/	"Microsoft Visual Studio"

[tap]:https://testanything.org/	"Test Anything Protocol"

