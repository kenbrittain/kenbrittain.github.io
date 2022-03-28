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

The first unit test we planned was for the parameters to the constructor. You can see from the method name that they are expected to throw exceptions when they are `null` or *empty*. The key point is to remember that all of the parameters need to be checked. I find it okay to check them all here in this method. Wait a minute? Did I tell you to only check one (1) thing per unit test?

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
    Assert.AreEqual("NAME", p.Name);
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

## Writing Test Doubles

There is a good discussion on what constitutes a mock object.

### Mock Objects

### Stub Objects



###

[aaa]:https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices#arranging-your-tests	"Arranging your tests"
[samelang]:https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices#lets-speak-the-same-language	"Let's speak the same language"
[martin]:https://www.martinfowler.com/articles/mocksArentStubs.html	"Mocks Aren't Stubs"



