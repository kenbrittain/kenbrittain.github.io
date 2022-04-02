---
permalink: /posts/29-step-by-step-strategy-for-writing-unit-tests.html
title: "Step-by-Step Strategy for Writing Unit Tests (Part #2)"
layout: post

---

You have stopped overthinking and planned out your unit tests.

Now all that is left is writing them. You are a developer and you write code. This is supposed to be the easy part.

So let's dive in a being writing our tests.

## Writing the Tests

There are two (2) things to remember when writing your tests.

1. Test one thing per test. It is easy to say but there turns out to be a lot of gray area in what constitute *just one thing*. This rule makes it easy when looking at unit test failure. If you are only testing a single thing, then you know what failed.
2. Follow the [Arrange, Act, Assert][aaa] pattern. This pattern helps keep your tests in order. Remember how your test files are named so they sort similar to your class files? It's the same concept here. You want to be able to locate the different parts of the test. For smaller tests this is not big deal. For larger unit tests with test doubles there is a lot of setup that could be required before the unit test is actually executed. Let's keep things readable out there.

The first unit test we planned was for the parameters to the constructor. You can see from the method name that they are expected to throw exceptions when they are `null` or *empty*. The key point is to remember that all of the parameters need to be checked. I find it okay to check them all here in this method. Wait a minute? Didn't I just say to only check one (1) thing per unit test?

Yes I did. Even though the unit test contains multiple assertions we are only checking a single thing. The single thing is a single concept. This unit test may contain two (2) assertions but we are only check the one argument. In my experience, if there are multiple parameters, I check them all in a single unit test. They are generally one (1) liners and saves you from writing more tests than required. It's up to you so pick a strategy and just stick with it. There are rules and rules are meant to be broken.

```csharp
[Fact]
public void Person_NullOrEmptyName_ThrowsException()
{
    // Arrange
    // Act
    // Assert
    Assert.ThrowsException<ArgumentException>(() => new Person(null));
    Assert.ThrowsException<ArgumentException>(() => new Person(string.Empty));
}
```

The next test, because it is a constructor, has the Arrange and Act sections mashed together. This is not a problem. Please see the above mentioned rule about breaking rules.

### Values and Names

When creating the object under test I try to keep the values passed into the field somewhat predictable. It helps when debugging a unit test gone wrong.

1. All string values get the name of the variable in CAPITAL letters. This is a test. The values are fake but easy to see. Also, if you see the `_name` field with a value of `"TITLE"` you know you did something wrong very quickly.
2. Integer values are generally 666 or 999 because they stand out better as well.

You get the idea. Make your value memorable.

```csharp
[Fact]
public void Person_HasName_SetGreetingToZero()
{
    // Arrange
    // Act
    var p = new Person("NAME");
    
    // Assert
    Assert.AreEqual(0, p.Greetings);
}
```

Back to catching exceptions

```csharp
[Fact]
public void Greet_NullOrEmptyGreeting_ThrowsException()
{
    // Arrange
    // Act
    // Assert
}
```

### Testing for Exceptions

Exception are part of your life as a developer whether you like it not. Writing unit tests to exercise the code to throw exceptions is part of the job. 

There are two (2) 

```csharp
Assert.Throws<T>(Action a);
```



### Arrange

The first section of code to be written is generally the arrange section. This is where you setup create the necessary objects used in the test. For a simple test this could involve a single object. Using our example class, for testing the greeting, we would need to create an instance of the `Person` class.

```csharp
[Fact]
public void Greet_ValidGreeting_IncrementsCount()
{
    // Arrange
    var p = new Person("NAME");
    
    // Act
    // Assert
}
```

A lot of times you will have dependencies that need to be represented. If the dependency is simple enough you can just create the object. However, if the dependency uses external resources you will create what is called a test double. Test doubles have several forms. The two (2) most used are:

* **Fake** - a fake object is a representation of a real object but, as the name suggest, it is fake. I think  of a fake as a dummy object with a default implementation. Dummy objects fill out the programming contract. They don't have an actual implementation. The fake is used and operated upon by the unit tests and they would have data that could be used. For example, when I have a class read from the data fro man external source I will create a fake implementation that operates on a dictionary of hard coded data.
* **Mock** - a mock object is a special object that keeps track of the calls, its parameters, and results. 

You write fake objects yourself. They are small implementations of your code from your project used in testing. I will keep the fake object classes in the unit testing project.

You use a library to implement your mocks. This is code you are not writing. A mock object is setup to work like the object it is mocking but it performs no actual operations. Think of the 

* **Dummy** - a dummy object is used to satisfy a programming contract but perform no actions. After writing a series of fake objects I do not create a dummy object without an implementation of the same type. I use the fake! After all, the dummy object is supposed not be used and only satisfy the programming requirement for a parameter or dependency. If it is not going to be sued then just use the fake you already wrote. I suppose you could derive the fake object from the dummy object and get the best of both world. That just sounds like writing two (2) of hte same thing when writing one (1) would suffice. I am not that much of a unit testing purest to demand writing the extra code.
* **Stub** - a stub provides hard coded data to the callers. I suffer from not writing too many classes here again. I will create a fake class and have it populated with hard coded data to satisfy the unit tests. If there were a `FakePersonData` class that returned `Person` objects, presumably from a database, I would have a few records hard coded into the fake. 
* **Spy** - this test double is supposed to record data about how it is being used. I have not had the pleasure of using, or needing, a spy object. They have a purpose and I am sure there places for them. I have not dealt with them.

### Act

### Assert





###

[aaa]:https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices#arranging-your-tests	"Arranging your tests"
[samelang]:https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices#lets-speak-the-same-language	"Let's speak the same language"
[martin]:https://www.martinfowler.com/articles/mocksArentStubs.html	"Mocks Aren't Stubs"



