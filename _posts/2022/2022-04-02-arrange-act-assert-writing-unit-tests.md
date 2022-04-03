---
permalink: /posts/29-arrange-act-assert-writing-unit-tests.html
title: "Arrange/Act/Assert (Writing Unit Tests Part #2)"
layout: post
---

This is where your unit testing writing work begins.

You test your code by executing your methods. All public methods. Each method is executed in isolation. This means that each unit test creates an object, of the class being tested, and then executes the method.

Getting to that point alone can be a journey of setup and configuration. The executing of the method is the easy part. 

## Arrange, Act, and Assert

Your unit tests have three (3) sections:

* **Arrange** - setup and prepare the objects in the test.
* **Act** - execute the required methods to perform the test.
* **Assert** - validate the scenario as expected.

### Arrange

This section is where you create the necessary objects used in the test. For a simple test this could involve a single object. Using our example class, for testing the greeting, we would need to create an instance of the `Person` class.

```csharp
[Fact]
public void Person_HasName_SetGreetingToZero()
{
    // Arrange
    var p = new Person("NAME");
    
    // Act
    // Assert
}
```

If there were external dependencies that needed to be managed you would handle them in the arrange section. Keeping all of the setup code together helps when the setup for the dependencies are longer than the test itself. When dependencies and test doubles are introduced the code get longer.

### Test Doubles

A lot of times you will have dependencies that need to be represented. If the dependency is simple enough you can just create the object and use it. Thing along the lines of `StringBuilder` or `XmlDocument` here. They are standalone classes that can be utilized. They don't affect system or have any lasting changed. Everything they do and effect is contained with the objects themselves. If the dependency uses external resources you will want to create what is called a test double. Test doubles have several forms.

The two (2) most used in my testing arsenal are:

* **Fakes** - a fake object is a representation of a real object but, as the name suggest, it is fake. I think  of a fake as a dummy object with a default implementation. Dummy objects fill out the programming contract. They don't have an actual implementation. The fake is used and operated upon by the unit tests and they would have data that could be used. For example, when I have a class read from the data fro man external source I will create a fake implementation that operates on a dictionary of hard coded data.
* **Mocks** - a mock object is a special object that keeps track of the calls, its parameters, and results. 

You write fake objects yourself. They are small implementations of code used in your project for testing purposes. Keep these fake object classes in the unit testing project.

You use a library to implement your mock object. I generally use [Moq][moq] or [NSubstitute][nsub] depending upon the project and what has already been implemented. There are more but the important point is that this is code you are not writing. 

A mock object is an object that is setup to look and act like another object. You have heard about using interfaces to isolate your object domains to make them more testable. This is because you use interfaces to setup mock objects. Given an interface mocking library generates an object, that implements the interface, but the mock performs none of the operations. It records  what method was called and with what parameters. This call can be validated later.

Let's pretend out example class was going to call the `File.WriteAllText` method. This is a static method on on a sealed class. This kind of type is generally not mockable. The `System.IO.Abstractions` package provides an interface based implementation that forwards all of the calls to the appropriate `System.IO` methods. Why go through all of the effort? To use mocking to enable out tests. 

This example create a mock object for the `IFileSystem` interface type. One the mock is created, as passed to our object, the code can execute. It execute on the mock which does not write any text to the any file. This allows the test to execute the proper code but create no dependency on the local file system.

```csharp
[Fact]
public void Person_HasName_SetGreetingToZero()
{
    // Arrange
    var mockFileSystem = new Mock<IFileSystem>();
    mockFileSystem.Setup(fs => fs.File.WriteAllText(It.IsAny<string>(), It.IsAny<string>()));
    
    var p = new Person("NAME", mockFileSystem.Object);
    
    // Act
    // Assert
}
```

This `Setup` tells our mock file system object to expect a call to the `WriteAllText` method. You can specify parameter values or, as the code explains, anything of the `string` type. 

There are other types of test doubles. 

* **Dummy** - a dummy object is used to satisfy a programming contract but perform no actions. It is a concrete object that is created in your unit tests. After writing a series of fake objects I do not create a dummy objects without an implementation. I just use the fake! After all, the dummy object is not supposed to be used and only satisfy the programming requirement for a parameter or dependency. If it is not going to be used then just use the fake you already wrote. I suppose you could derive the fake object from the dummy object and get the best of both worlds. That just sounds like writing two (2) of the same thing when writing one (1) would suffice. I am not that much of a unit testing purest to demand writing the extra code.
* **Stub** - a stub provides hard coded data to the callers. I suffer from not writing too many classes here again. I create the fake class and have it accept data as parameters to the constructor. The data then populates the fake. If you make them optional then you have a stub. 
* **Spy** - this test double is supposed to record data about how it is being used. I have not had the pleasure of using, or needing, a spy object. They have a purpose and I am sure there places for them. I have not dealt with them.

### Act

This section of the test is where you call your method. The object has been isolated from all other dependencies using test doubles. The scenario is set and ready to be called. 

```csharp
[Fact]
public void Greet_ValidGreeting_IncrementsCount()
{
    // Arrange
    var p = new Person("NAME");
    
    // Act
    p.Greet("GREETING");
    
    // Assert
}
```

If the method returns a value that can be asserted directly then it should be. If there are some side effect after calling the method then it would be validated using the object. Finally, if you had called methods on a mock object you can validate they were called appropriately.

### Assert

Each unit testing framework will have an assertion framework. [xUnit][xunit] and [MSTest][mstest] have similar `Assert` framework for values and collections.

The assertion frameworks have method for comparing values, and collections of values. The pattern is to pass the expected and actual values into the comparison methods. The methods `Equal` and `AreEqual` are used to check if values are equal. Each method has numerous overloads to handle many different types. 

```csharp
Assert.Equal(expected, actual);    // xUnit
Assert.AreEqual(expected, actual); // MSTest
```

There are also method for comparing collections, catching exceptions, and ensuring boolean value.

#### The Single Assertion

There is a school of thought that recommends only using a single assertion in your test. Rubbish! The goal of the unit test is validate a single concept. The number of assertions that you have is immaterial as long you are validating that single concept.

Here we are checking the parameter to the constructor.

```csharp
[Fact]
public void Person_NullOrEmptyName_ThrowsException()
{
	Assert.Throws<ArgumentException>(() => new Person(null));
	Assert.Throws<ArgumentException>(() => new Person(string.Empty));
}
```

## Leave the Comments?

I have read numerous posts and comments on the value of leaving in the comments: Arrange, Act, and Assert. I agree that it is redundant. I also agree that your code should be clear and not require the comments to delineate the sections. I go back and forth between keeping and removing them.

If the unit test is small enough then I will remove them (most of the time). As the tests grow I tend to leave them in as it helps keep the code organized. The sample class unit tests would not have the comment in real life. I have removed them from some methods to give the look and feel of a real test ;) 

[10]:https://kenbrittain.com/posts/10-unit-testing-system-io.html
[nsub]:https://nsubstitute.github.io/
[moq]:https://github.com/Moq



