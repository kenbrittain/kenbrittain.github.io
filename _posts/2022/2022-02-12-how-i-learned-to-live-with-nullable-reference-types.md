---
permalink: /posts/22-how-i-learned-to-live-with-nullable-reference-types.html
title: How I Learned to Live with Nullable Reference Types
layout: post
---

I hated the nullable reference types feature introduced in C# 8.0 for 
quite some time and avoided using it.

It made new warnings, and lots of them for some projects. Especially for
existing projects. I was not a fan of this wave of yellow warnings after a
build. Those of you that have grown up on teams that had a strict **no warning**
compile standard should be able to relate.

It is 2022, and I decided to flip the bit, add some new styles to my coding, 
and dive into nullable reference types. Having the compiler help you remove 
bugs is a good thing. I was starting a new project so let's start it right.

## Enabling Nullable Reference Types

Prior to C# 8.0 all types were nullable and that was just how code worked. If
you had a reference then it could be `null`. You were a developer, so you
checked for `null` when required. It was called programming.

Enabling the feature was simple. Add the following to your `.csproj` file, or
check a box in your IDE. You are ready!

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <Nullable>enable</Nullable>
    </PropertyGroup>
</Project>
```

Now the compiler is checking your code for what it calls `null-state`. If you
are going to use a variable the compiler will determine if:

1. The variable has been assigned to a value that is known to be not `null`.
2. or the variable has been checked against `null` and hasn't been modified 
   since that check.

The official docs can be [read here][1] for more details. You just need to 
keep doing what you have, hopefully, been doing. Either assign the variable 
to a known value, or check the variable against `null`,  before using the 
variable.

I have been doing that already. Except when I wasn't.

## Am I Loving Nullable Reference Types?

I would not say that I am _loving it_, but I am enthusiastically supporting it.
Every developer has their own coding style. It is how, when presented with code
you swear you never touched, barring a damning git commit entry, you actually
come to understand that you did write it. No more denying it because it has your
style all over it.

Here is what I have been doing to adopt using nullable reference types:

* Accept the warnings. This was actually tough to do because, as I stated
  before, the warnings introduced a level of stress. I was not used to having
  warnings in my projects and surely not as many as enabling this feature
  introduced (let's be real - there are some there, but they are usually only a
  few and accepted for a reason).
* Fix the warnings. Let's face it, the warnings are there because your code is
  wrong (now). It could allow a `null` reference to sneak in and cause the
  associated pain. This is where I finally grew up and accepted the feature in
  its entirety. You might say that I have been enthusiastically supporting it!
* Use nullable variable annotations. This is the type annotation `?`
  that says this type is nullable. It is appended to the type declaration as
  in `string? name;`. Adding this to your existing code is really documenting
  what already exists. Prior to enabling nullable reference types, all types had
  this annotation applied implicitly. You are now just declaring what you
  already had. My first step was to add it where needed to get a clean compile.
  It can be removed later as my null sensibility increases.
* Keep checking parameters. Just because the compiler tells you that the null
  state of a variable of `not-null` doesn't mean some joker
  (generally yourself) will not pass a `null` value into it (see the
  null-suppression operator below). Do not remove your unit tests for these
  conditions. The compiler is helping you, but it is not writing your code for
  you.
* Use the null-suppression operator. Use this operator to remove warnings, as
  you fix them, when you *must* pass `null` into a method. I use this liberally
  in my unit tests to ensure the parameters are checked and the appropriate
  exceptions are still thrown. Please remember, the compiler is helping remove
  the chances of getting a `System.NullReferenceException`. There are no
  guarantees.

## Next Steps for Better Coding

Part of the coding process is to document your code. I do this in two (2) ways:

0. Write clear code that is easy to understand. I do not try to get fancy. That
   should be enough (but generally is not).
1. Document all your `public` classes and `public` methods on those classes
   using XML doc comments. You may never actually generate the documentation for
   browsing but the IDEs of today will display the help when asked.

I am going to be adding a third tool to the documentation tool chest. That is
the [attributes for null-state static analysis][3]. I am not currently planning
on overhauling any codebase with attributes. This is a process and the
introduction will be gradual. I do believe that once incorporated into my style
it will help.

I know finally enabling nullable reference types was an overall plus for me.

[1]:https://docs.microsoft.com/en-us/dotnet/csharp/nullable-references
[2]:https://stackoverflow.com/questions/54526652/when-to-null-check-arguments-with-nullable-reference-types-enabled
[3]:https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/attributes/nullable-analysis
[4]:https://stackoverflow.com/questions/54526652/when-to-null-check-arguments-with-nullable-reference-types-enabled
